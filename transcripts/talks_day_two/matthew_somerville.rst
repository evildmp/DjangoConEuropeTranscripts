========================================================================
Matthew Somerville: Using Django’s StreamingHTTPResponse for JSON & HTML
========================================================================

MATTHEW SOMERVILLE: Hi, I work for mySociety, a charity that builds things that
empower citizens, in the UK and around the world, such as FixMyStreet and
Alaveteli (FOI).

MapIt is a Django application for mapping points or postcodes to administrative
areas, either standalone or within a Django project. Our UK installation powers
many of our own and others’ projects such as TheyWorkForYou; Global MapIt is an
installation that uses all the administrative boundaries from OpenStreetMap.

A few months ago, one of our servers fell over, due to running entirely out of
memory. Looking into what had caused this, it was a request for information on
every “level 8” boundary in Global MapIt. This turned out to be just under
200,000 rows from one table, along with associated data in other tables. Most
uses of Global MapIt are for point lookups, returning only the few areas
covering a particular latitude and longitude.

Using python’s resource module, I manually ran through the steps of this
particular view:

50Mb initially. Plus 500Mb fetching/creating a lookup of associated identifiers
for each area, plus 675Mb attaching those identifiers to their areas, which
runs the query to fetch the areas, plus 400Mb creating a dictionary of the
areas for output, plus 250Mb outputting the dictionary as JSON. A total of 1875Mb!

The associated identifiers were added in Python code because doing the join in
the database (with select_related) was far too slow, but I clearly needed a way
to make this request using less memory. There’s no reason why this request
should not be able to work, but it shouldn’t be loading everything into memory,
only to then output it all to the client asking for it. We want to stream the
data from the database to the client as JSON as it arrives; we want in some way
to use Django’s StreamingHTTPResponse.

The first straightforward step was to sort the areas list in the database, not
in code, as doing it in code meant all the results needed to be loaded into
memory first. I then tweaked our JSONP middleware so that it could cope when
given a StreamingHTTPResponse as well as an HTTPResponse. The next step was to
use the json module’s iterencode function to have it output a generator of the
JSON data, rather than one giant dump of the encoded data. We’re still
supporting Django 1.4 until it end-of-lifes, so I included workarounds in this
for the possibility of StreamingHTTPResponse not being available.

But having a StreamingHTTPResponse is not enough if something in the process
consumes the generator, and as we want to output a dictionary, creating a
dictionary for json’s iterencode will suck everything into memory, only then
iterating for the output – not much use! I need a way to have it be able to
iterate over a dictionary…

The solution was to invent the iterdict, which is a subclass of dict that isn’t
actually a dict, but only puts an iterable (of key/value tuples) on items and
iteritems. This tricks python’s JSON module into being able to iterate over
such a “dictionary”, producing dictionary output but not requiring the dict to
be created in memory; just what we want. I then made sure that the whole request
workflow was lazy and evaluated nothing until it would reach the end of the
chain and be streamed to the client. I also stored the associated identifiers
on the area directly in another iterator, not via an intermediary of (in the
end) unneeded objects that just take up more memory.

I could now look at the new memory usage. Starting at 50Mb again, it added
140Mb attaching the associated codes to the areas, and actually streaming the
output took about 25Mb. Whilst it took a while to start returning data, it also
let the data stream to the client when the database was ready, rather than wait
for all the data to be returned to Django first.

But I was not done. Doing the above then revealed a couple of bugs in Django
itself when using StreamingHTTPResponse with GZip middleware:

* It would die with any Unicode data;
* Gzipped responses were larger than non-gzipped.

Both of these I patched and were included in Django 1.8.

Lastly, in all the above, I’ve ignored the HTML version of our JSON output.
This contains just as many rows, is just as big an output, and could just as
easily cripple our server. But sadly, Django templates do not act as
generators, they read in all the data for output. So what MapIt does here is a
bit of a hack – it has in its main template a placeholder, and creates an
iterator out of the template before/after that placeholder, and one compiled
template for each row of the results.

Now Django 1.8 is out, the alternate Jinja2 templating system supports a
generate() function to render a template iteratively, which would be a cleaner
way of dealing with the issue (though the templates would need to be translated
to Jinja2, of course, and it would be more awkward to support less than 1.8).
Alternatively, creating a generator version of Django’s Template.render() is
Django ticket #13910, and it might be interesting to work on that at the Django
sprint later this week. Thank you!
