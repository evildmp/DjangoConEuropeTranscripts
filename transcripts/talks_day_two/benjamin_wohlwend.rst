======================================
Benjamin Wohlwend: Give your pony wings
=======================================

OLA:  So our next speaker is Benjamin, works at (NAME - INAUDIBLE) works in Copenhagen.  He is going to talk about best practices and how to give your pony wings.  (APPLAUSE).

BENJAMIN WOHLWEND:  So Hi everybody, my name is Benjamin and I have to make a confession.  I am a lazy programmer which I mean what I mean with that is I like my code to be lazy or in other words I like my code to do not too much work.  That is something I learned after a few dozen Django projects I am not a fast learner so the thing is, making your code faster or making your code not do too much work makes your code faster.

To illustrate this, I would like to take you on a journey on a project that may or may not have happened in 2009 my boss said to build a stack overflow clone, but with a twist, should be for pony owners.  I have Django, should be a piece of cake right?

Jump in, create a few models, question model, easy stuff with the foreign key to a user, a title, body.  Then an answer model can with the key to the question, again with the foreign key to user, body, because it was 2009 and it was cool back then, added a tag field, yes, then let's move on to views.  There we didn't really have class based views back then, I never said that this story was true.  (LAUGHTER).

Yes, really simple stuff.  To finish it up we added some templates, again really basic stuff.  Here we have a template for a question list, we looked through the questions, we displayed the title and the user name, the body, back then we had the mark down filter then we show how many answers the question got and the text of the question.

So I guess we are finished with the stack overflow clone, let's put it live, so everybody is happy, fist pumping and clapping and partying until this happened.  Somebody linked to us from this cool site called pony news, where people hang out to yell at each other.  So yes, what happened?

Apparently we have a performance problem.  Or a more realistically have several performance problems.

So, problem now is how do you even find where your performance issues are?  That is the really hard work, everything before it was just child's play.

What I usually do, I run tools that people run that are way smarter than me, different kind of tools, tools to use when you are developing locally and tools to run in production.  I am concentrating on a few local tools on this talk.  Especially Django debug tool bar and Django deverser.

If you not heard of Django debug tool bar, I use it all the time, gives you insight into the cache access, but gives you a nice overview of all your sequel queries, it is more the visual impression that you can see here, lots of sequel queries, it is an indicator that something is wrong.

If we zoom in, remember we just are displaying a few questions, so why should it take 121 queries, that is insane.  Something is wrong here.  Let's look at what Django defserver, it is similar to the tool bar, but with the more bare bones interface, outputs everything to the console, really nice having it running on the site.  Sit on the side while developing what is going on.

What is really cool, there is 59 queries, we queried the same thing 59 times, something is wrong there.  Found ourselves an issue.  What are we going to do now?

I usually have to, big three-points I am looking at when I try to fix performance issues, first to reduce database queries and round trips database, then what seems obvious, do less work with the code.  If everything else fails start to cache stuff.

Django gives two really cool tools, select related first.

Select related is nice if you have a foreign key and you want to pre-fetch or preload the data in one single query.  In our code if you remember we had this question model with the author and we are looping through the questions to display the user name.  So, when we don't use select related what happens in the database is, first we get all the questions in one query, and then for every single time we access the user model we do another query to get the user.  So if you count it you can see we queried first user three times and the second 12 times, that is where the applicants come from.  Did a lot of round trips that are necessary.

Select related there.  Select related and the name of the field and what happens then is we do it all in one query, so we get all the objects that we need at once and Django maps it for us and everything works beautifully.  Back in Django devserver, we are back to sixty one queries, we had 1,211th, half of them are gone, we don't have duplicates anymore.  That is great, let's move on to pre-fetch related.

This is really cool for reverse foreign key relations and many o to many fields, we have examples of those in our code and the tech model which is a many to many field.  We loop over the questions in the template and display all the terms for that question.  Without pre-fetch related.  This happens.  Again we get all the questions in the first fetch and then for every single time we loop over the questions again, we go back to the database and then get the text related to that question, which again is not ideal.

So let's add pre-fetch related.  Pretty easy, cool API, what happens then is we do two queries first we get all the questions and then Django magically figures out which text needs to do, gets them all in one query and matches them back to the questions we got before.

So, in the end we end up with three sequel queries, 121 first, then back to, we can say we accomplished our mission to reduce the queries.

The next chapter is do less work, which seems less obvious, different ways to achieve that.  One way is to move work out of your request response cycle because that is our priority here to reply to the user or to sent cob tent back to the user as quickly as possible, so you can move work that is not necessary for the response out of that code path we are can answer to the user way quicker like API calls to track accounts or stuff like that.

Another one is to not, another way is to not fetch data, Django by default fetches all the columns for a model when you query for it.  There is a cool thing, defer, you can tell Django not to fetch data that you don't need.  If you have a huge column, which contains the body of the question, you can say defer, and then the data won't come over the wire.

What I like the most is to let other people or other layers do the work.  One thing that we can do in our code that we looked at is to calculate stuff with annotate or aggregate, if you remember, we are showing in the question overview or in the question list how many answers the question got.  To do that we are fetching all the answers from the database and then counting them which seems kind of not very smart to get all the questions and just count them.  So let the database do that count.  That is really easy to do with annotate if you look at the code there, we just tell Django to count all the answers and put it on a property called answer count and all we end up there in the end is a number which we can display to the user and we are done.

So, this actually talk about this 20 past noon I think, if you are interested in annotate and aggregate, check the talk out.

Meanwhile let's move on to caching.  It is an interesting topic.  If you do it properly, you can like scale to infinity basically but, doing it properly is really, really hard.  Cache invalidation is a hard part because the danger that you are running in if you do caching is that you end up serving stale data to your users which might be okay in certain cases like in a Blog or in a stack overflow clone, there sit doesn't really matter if the content that you are showing is couple of minutes old but if you are running a web shop organisers perhaps an e-banking website that might be pretty bad if you served account balance from a few minutes ago, so caching is dangerous, after experience, adding caching to your code can make it hard to test and to reason about how your code actually works so, my advice is to use caching only when it is really necessary.

I am not saying that caching is bad not at all.  It is one of the more important tools to have at our disposal but only start using it when you think it is really necessary.  Let's say it is necessary for our case.  I really easy way to get started with caching is to cache page decorator.  What you do here is you just wrap your view with the cache page decorator, Django will check if it served that request in a, the last 60 seconds in this example.  If it did, it return it from the cache if not, recreate the content and put that in the cache.  Really easily cache the content of that view.  There is a few problems with that, there is a couple of box open in the Django box checker, but generally it is a nice way to get started with caching.

There is way more options to do with caching.  The cache template tech, wrap complete pieces of code of your template in a cache tag and then Django caches the content of the template tech, what is nice, there is ORM caching, really cooed tools for, that one is Johnny cache which is the best named cache out there.  Another one caching machine.  They give you a quick win.  Then there is the big ones like varnish for instance which handles a lot of caching up for you, but it is difficult to set it up correctly.

If this has peeked your interest, look at high performance Django which came out a few months ago, there is a lot of stuff in there about caching and a lot of ways to get your Django side faster, I recommend to read it.

So in retrospect, really watch out for those sequel queries they tend to come back and bite you.  Being lazy is good, don't do too much work in your code, try and reduce the work that your code does.  If everything else fails bring out the big caching guns and start caching.  So, yep.  That is all.  (APPLAUSE).

OLA SITARSKA:	 Yeah we've got time for a couple of questions.

NEW SPEAKER:	 Great talk, thanks.  You mention defer.  I don't think you mentioned only which is a parallel to defer with the logic going that way.  I wondered if you had any thoughts about when you draw that line, when it is worth deferring because obviously there is a service side cost you pay for constructing a slightly more complex object and there is a long term engineering cost weight you've got to carry in terms of if you accidentally start using an attribute that you said you were deferring then you introduce additional queries so do you have any suggestions about when to make that decision, what sort of criteria you use to make that decision to use defer or -

BENJAMIN WOHLWEND:	 So my brother is a carpenter and he told me always measure before you cut so benchmark, try it out with defer, try it out without defer, see what happens.  Yeah, that's I guess most important point.  Always benchmark before you try it out.

NEW SPEAKER:	 Sure thanks.

NEW SPEAKER:	 So the devserver looks like a very good top level profiling tool.  Do you have any favourite one that delves a little more, gives you more data, more finally carrying data?

BENJAMIN WOHLWEND:	 Well, it depends a bit what you want to do.  I mean the Django debug tool bar for local development gives you fine grain data about what's going on in your request, for production tools there is stuff like nurelike or upbeat(?) which this company - which gives you fine great data about your production code so yeah there are so many tools in the market just find to write one for your task.

NEW SPEAKER:	 Thank you.

DANIELE PROCIDA:	 I don't think you have to feel shy about mentioning upbeat because it's exactly part of this endeavour so do go and visit the upbeat stand they're one of our sponsors one of the companies making this possible so thank you very much.  {Applause}.
