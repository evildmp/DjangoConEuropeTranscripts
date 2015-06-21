====================================================
Thomas Turner: Using Django in a desktop application
====================================================

NEW SPEAKER:	 Hello everybody, like to introduce Tom from Joinerysoft; Joinerysoft is the UK's biggest supplier of joinery software and talking about using it in a Django application so hello. {applause}.

THOMAS TURNER:	 I did it the wrong way round ... other way round, start again, that's better.  Right so it's a bit unique this talk.  It's using Django in a desktop application.  About me, I'm Thomas Turner, I own 2 - am part of 2 family companies.  One is somcom which does technical web-sites, done stuff to do with people like NICEIC, which does all the electrical stuff and has done technical searching web sites.  The other company is joinerysoft which does joinery software for joinery manufacturing or carpentry.  I've been using Django since - for about 7 years since 0.96 I think, there is my twitter account and git hub account.

Using Django as a desktop application.  Is it a good idea or a bad idea?  Let's find out.

So, as I said, the programme that I'm talking about is joinery programme which is called JMS so if I call it JMS, I refer to the programme.  So JMS, it is a desktop application but is running Django so let's find a bit more information.

What technologies do we use?  Python and Django obviously otherwise I wouldn't be here.  It's an MFC application so it's Microsoft foundation classes.  We use a library called DHTMLx for all our grids and all the sort of tables and all our sort of framework.  We use reportlab for all our printing.  And we use fire Bird SQL database and we use CEF as our web browser which is basically Google chrome.  And we use openGL and sikuli for testing.

Why did we choose Django for a desktop application?  It makes it future proof.  So, in the end we want to make the programme go on to the internet to actually go on to as a cloud service.  It's faster writing - well can be faster writing in Python than C++.  HTML can look better than normal Microsoft dialogue boxes and becomes more network compatible and we did a similar thing before.

What problems did we have?  Lots!  One was securing Python and Django code.  One was securing the HTML code.  And one was finding a Django web server that could be embedded into C++.  We also found there were too many programming languages.  It's quite a nightmare that is.  Finding a database engine that is simple to install.  Our customers don't even know what a mouse is so they wouldn't know how to install postgres.  It gets picked up by virus checkers because it's using port and it's harder to distribute tan the normal bog standard application and it's a nonstandard set up.  And testing, we had a lot of problems with testing.

So, securing the Django and Python code.  We put our own encryption into python.  We took Python and found where the - so we took Python and put our own encryption into it.  We had to build Python and so people could stop reverse engineering because we only distribute the PYC files not the PY files and of course you can still reverse engineer PYC files to get back to a PY file so we stopped that by putting our own encryption into Python.

We also had to modify Django to allow for the PYC because there is one bit that says asterix dot PY.  It would be great if it said asterix dot PYC.

We also had problems securing the HTML code.  The HTML code we didn't want our customers to be able to change it and do something wacky on the page so we actually put our own encryption I won't go through all the how we encrypted down the side.  So we wrote our own template loader to do it first of all I didn't even know template loaders existed so I overrode all the template class but then we worked out that you could override the template loader.

So, finding a web server that could be embedded into C++.  We tried Django development server - that's a really bad idea, at the time we were using Django 1.1 and that was a bad idea because it wasn't multi-threaded.  It says not to do that.

We tried somebody's project, somebody's own C++ web server and that was too slow and too unreliable.

So, we settled on cherry py.  Cherry py if you have used it, it is all written in Python, it is a very good web server, so we embed cherry py into our C++ app.

So finding a database that is easy to install.  As I said earlier, our customers don't even know what a mouse is or some of them don't.  So they wouldn't have known how to install postgres and postgres actually conflicts - because this is a windows application, it actually conflicts with other software.  So, we found it's easier, so we couldn't really use postgres.  And SQ light is not very good for networks.  Our current version which is out there in the field, we use both of those products and we've had problems with both SQLite and postgres.

So the one we chose was firebird.  Has anyone used firebird?  Anyone know about it, put your hands up?  A few of you but not many.  So, it's easy to install.  It's open source.  It is not owned by oracle.  And it works with Django using a third party plugin.

It actually came from a D base so there is the logo.

So, finding a - obviously we needed to put a web browser into the programme so we had to embed a whole web browser into our C++ application.  We tried to embed Microsoft internet explorer and me we ran like a mile.  It's a nightmare, we didn't want to go there.  So we went for CEF.  CEF is basically Google Chrome.

Why CEF?  It's open source, it's cross platform, it's used in many big applications.  I expect a lot of you have got these programmes installed or some of them installed: spotify, steamclient, github and Dreamweaver.

So what CEF is, it's a web browser, it's basically Google Chrome so yes it can be embedded thanks to somebody taking Google code and putting it into - making it so you can embed it into a C++ application.

So, another thing we had problems with was testing we couldn't get selenium to work because there was no web driver, we went for Sikuli, it works by image recognition, it is a bit of a nightmare, the problem is, if you do a star sheet change, you have to redo all the tests again.  So that is basically why we had to use Sikuli.

Reports.  We needed a way of generating our own pdf, we, a Django application will be running on a different thread to what the C plus plus is using, so we can't directly talk to a printer, so we had to go via a print preview.  So we had to generate a pdf but settled on reportLab it wasn't up to the job, so we had to modify it.  It is sort of written in Python, not well coded it is actually written like a C plus plus act, one letter variables, so, that was another problem we had.

So, yes.  It was obviously hard to understand the code.  So I am going the show you a little demo of the programme now.

So this is right.  I can't see that side.  Let me go over here, forgotten not duplicating.  Hopefully.  I can work out which side it is.  Right.  So, that is the database there obviously so it is a single file database and I am just about to call the programme up here.  Yes, at the top is all the files, so it doesn't really look like a Django application.

So back to call it up.  So to a user, they wouldn't even know it is written in, they wouldn't even know it is a web application.  So back to log in.  Obviously that is Django.

Obviously this is all written in, this is all the html web pages and obviously these are all in Django as well.  About to get something more interesting, so don't fall asleep yet.

So about to call up a window.  So.  All of this is written in, apart from this bit here, this bit over on the right hand side is actually written in C plus plus, so we had some difficulties getting information from Python to the C plus plus engine.

So back to come out.  Again that is all written in Python, the costing.  Back to print a report.

Obviously this is reportLab so we had to modify this so it worked for our requirements, this is the sort of thing that our customer send out to their customers, so that is it anyway for the thing.

Go back to that.  Slide show from current slide.  Not from the beginning.

Be there in a second.

Right.  So was it a good idea?  You tell me.

We are currently recruiting, do a small sale pitch, just in Bristol, if you want to get more involved, join our team, any questions?

(APPLAUSE).

DANIELE PROCIDA:  Thank you very much Tom that was absolutely amazing.  I don't think anyone here has seen anybody try to do something like that.  Was really Django the best way to do this?  Was there, surely (LAUGHTER), I mean it is.

THOMAS TURNER:  I wouldn't do it again.  No! I proved it could be done, I proved its been done.

DANIELE PROCIDA:  I think that shows another round of I (APPLAUSE).  (APPLAUSE).

I am slightly lost for words because that is honestly one of the most radically, different ways of using Django that I have ever seen, congratulations.

THOMAS TURNER:  I was expecting them ...

FROM THE FLOOR:  Excuse me, I am here mostly to disprove what Daniele just said about 2009 I think I did something similar.  We wrote an outlook plug in actually which was presenting html generated by Django for very similar concerns of making the thing, network transparent with intention to later make it available from servers.

We also, we had a lot of the same experiences and just wanted to say that I share a lot of your ...

THOMAS TURNER:  Thank you very much.

FROM THE FLOOR:  Thanks for the great talk, different application how to use Django, I thought about using Django or in particular for application for desk top application, basically as a data source for (NAME - INAUDIBLE) would you recommend me to do it or not do it?

THOMAS TURNER:  Just don't do this! just stay away seriously, just don't do desk top, it is too complex! I just would stick with a desk top, stick with something like C sharp if you are going to do desk top work.

FROM THE FLOOR:  Hello, thanks for the talk.  NFC and Django, that is kind of a weird combination, is there a reason why you didn't try to use something like GDK or something like that?

THOMAS TURNER:  The reason we did it we wanted to go on to the internet.  My other company did web applications, I prefer doing web applications than desk top applications, so I probably pushed more for doing this than we should have done it.

FROM THE FLOOR:  Yes but for the desk top part why not use GDK or another Python solution?

THOMAS TURNER:  Our current version is written in MSC, so it is an extension, it evolved to this.  We didn't get there by taking a browser, we only had half the window as a browser at the start.  That is why, we got there in iterative steps rather than one big sweep.

FROM THE FLOOR:  Okay.

FROM THE FLOOR:  Hi there, thanks for your talk, it was interesting.  I have got two questions, one you have embedded Django in a C plus plus application, did it ever cross your mind to try and, I don't know how it is easy to do, embed the C plus plus into the Django web page?

THOMAS TURNER:  We thought of doing that, our customers wouldn't want to call it up in a web browser, they would want to call it up as an application, we would have still needed an exe for them to call up.  So that is why we have done it this way.  We use a lot of open GL which is also rendering to the page.  So, some of the views we use a, one of the main view uses a canvas which actually does all the open GL part.

FROM THE FLOOR:  Yes and my second question was, you mentioned at one point your users don't really know what a mouse is.  At the same time, ... to hide it away from them, worried about the users fiddling?  Is this copyright...

THOMAS TURNER:  The programme is protected with a dongle okay, so one of these dongles so, people would hack it but it is, it ranges from the type of users.  Some of them don't even know what a mouse is, but some are large organisations which would have technical people yourselves in there which could reverse engineer.

FROM THE FLOOR:  Thanks very much.

THOMAS TURNER:  No problem.

FROM THE FLOOR:  The question I wanted to ask was just ask before but I wanted to congratulated you for making windows, inside windows, inside windows (APPLAUSE).

I wanted to say we did a similar thing and we experienced many of the same problems you have some others with some other stuff we have a lot of hardware communication going on, I may do a lightening talk.

THOMAS TURNER:  Those were a brief amount of the problems, I could carry on and on, seven years’ worth of problems.  So.

DANIELE PROCIDA:  Thanks again very much Tom.

(APPLAUSE).

Go and visit Tom at his stand in the sponsor’s hall if you would like a chat with him.
