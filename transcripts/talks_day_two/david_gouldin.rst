================================================
David Gouldin: Django's role in the polyglot web
================================================

OLA SITARSKA:	 So, our next speaker is David Gouldin, he is using Django since 2007 so quite some time.  He is currently working at start up in San Francisco so a long way to Cardiff.  He was going to talk about Django's role in a polyglot world so give a hand to David.  {Applause}.

DAVID GOULDIN:	 Let's get started, if you want to follow on with me this is actually a hero: app as well, let's see where this is going ... sorry about the technical difficulties.  I may have to go without my speaker notes here ... of course going to give up on the speaker notes.  That's fine.

Yeah so let's start with just a brief history about Django.  Django is 10 years old as of this month.  It was started in Laurence Kansas in July 2005.

Django was originally built as part of a CMS project called Ellington.  The Laurence journal where people decided that they would split out the code base into 2 parts, license Ellington the CMS and open source Django as a more generic web framework.

So Django's mantra is perfectionists with deadlines.  This kind of sets the trajectory of the entire project and you can map all of Django's strengths and weaknesses to this sort of ideal.

The web is a very different place in 2015 than it was in 2005.  Do you remember the days when you could describe your entire application stack using a single acronym?  You could say I'm a lab developer and people knew what that meant, usually had one day a store, usually relational, your service side code encapsulated all your business logic and views on the server were used to render your entire HTML pay load which you'd send down to the server.  A very simple design.

So we've moved from a web that looked like this which by the way Django is developed to solve, to one that looks more like this.  Weight, that's not right.  Something like this, yeah.  OK.

Much more service oriented where we have public and private services that are talking to each other via http, we can also use something like pub sub when we need to communicate one to many, one to many other services but most importantly our client in this model is just another service so web browsers have advanced to the point where we can treat the browser as a service consumer from our public services provided by our server.

This changes dramatically people's expectations of what the web is and how it acts.  People now are used to dealing with web applications like native applications so there is an expectation of responsiveness that comes from these interactions and server side N VC just does not adequately fulfil these expectations any more.

So let's talk about a few of Django's strengths.  First of all, Django is written in Python.  I don't think we can really under represent the strength that this provides the framework.  The Python community is super deep and super rich and provides all kinds of libraries for us to use that other less mature less longstanding communities just don't have.  This is a huge advantage for Django.

This same perfectionists with deadlines mantra means Django is built for getting stuff done which I really appreciate and you really appreciate when you work with frame works that weren't necessarily built with that in mind.  So Django makes some compromises to achieve this. One of its most famous compromises is in its orm.  Django's orm is kind of blamed by some people for not being entirely expressive or inclusive of the entire SQL standard but I find I can get most of what I want done in it pretty quickly and easier then the orm allows us to build other tools on top.

Ola spent her entire talk talking about how powerful and expressive Django's admin is truth is nobody really wants to build this stuff from scratch, the fact that this is included with Django is a huge advantage.

The Django rest framework makes it easy to build on top of the orm and get cloud working for resources very, very quickly and then allows you to continue from there to create customer actions.

If you've heard me talk before you know a live celery.  I feel it's a vesting class application of synchronous work cue which pretty much any non {inaudible} application needs in a function.  The fact that you can have this pretty much out of the box with python and Django puts it leaps above lots of other solutions.

But for all of Django's strengths it obviously has weaknesses.  The most I guess talked about weakness is the C 10 K problem.  For those who don't know what it is it's handling 10,000 concurrent connections to a single process.  And Django just does not do this very well.  Python or at least Python 2 wasn't built with massive concurrency in mind and Django was built on a Python 2 world so your alternatives here are to use something like A sink IO, or twisted which gives up a lot of the library support which makes Python strong in the first place or it's monkey patch the world with something like G event which gives you all kinds of edge case problems.  You know it's patched event loop.

So with the proliferation of client side tools comes the necessity of proliferating Java script as well because Java script is a de facto language in the browser so when you are developing on client side Java side tools you enter this community that expects Java script everywhere, expects Java script on the server too to take full advantage of the tools so you are hamstrung if you are not willing to run Java script on the server.

Look at problems you could run into trying to run the ocean with Django.  Pushing the web clients is a very comment problem for modern web applications and Django doesn't have a good solution to it.  You can try to use long pulling but during the time your connection is being held by the server you're consuming a precious Python web worker and this is a really good way to deal less your server really quickly.

However if we look to the wider community we see there are lots of options for solving this.  Socket IO is the most famous one for web socket communications.  There is also built in web socket support with go, which uses not blocking IO.  Native solutions like web sot {inaudible} hold the web socket open.  Things like using tornado where they sink OI or twisted like I mentioned before.

So, let's say that you your IPA has a point that issues a celery task but for your clients who continue with its interface it needs to get the results of that task before it can move on.

This is common problem in like search engines.  Let's say building a travel search site you want to execute a search but you can't show anything to the user until you have the results of that search back.  How do you solve this problem with Django?

What I'd do is I would organisation meant my API response with a list of celery task IDs that were launched as a result of that end point and then create a separate end point to allow me to get the status and result of each of those tasks then set an interval in the client to check you know check over and over again for the results of those tasks and move on once I have the information I need but there is a more elegant way to do this.

If we build on the ability to push the clients, then we can treat a web socket server as a bridge to pub sub and if we are standing up pub sub on the service with something like Reddis our ancillary workers can push direct to it using {inaudible} as channel name then our client can using web socket's subscribe to tasks they receive through the same augmented API end point with task ID then have information streamed down to them as if they're a pub sub subscriber to that task and then all of a sudden you've got this complete push loop going on where your client can in real-time know updated information from asynchronous processes on the server.

As I mentioned before there are a bunch of Java script specific tools which are helpful when building rich clients not least of which is server side rendering of your initial page state.  This became possible with reacting has been adopted by ember and some other web frameworks but to do this you pretty much have to have Java script running on the server.  In the early days of react Eric was telling me he tried to sub possess out to node in order to render react components to grab the HT mode back and send it down through Django and this is obviously just not an optimal solution.  So, I would not recommend doing this, it's very slow.

If you on the other hand are willing to run no JS to serve directly to your client as well as Django API side by side, then you can just use the native reactor render to string and have your node web server actually serving your client application.  Remember you are treating the browser as just a service consumer so it doesn't really matter where that application pay load comes from, it just matters that it's responsive, it matters that it is fast and you can work with different services side by side.  So in this world you would probably want to use something like cores to be able to have a node on may be a dub dub dub sub domain and your API on a separate sub domain and have node render the initial pay load of your page, sent it down with all of your static assets then treat the Django part as simply an API provider for the client.

So as soon as you have more than one service serving web traffic you have the problem of shared authentication with the client and there are 2 mechanisms you can use for statefulness in a web browser, there is cookies and local storage.

You can refer your off to Django contrib and just using it willy-nilly happily.  You can go to an off load in page for your client, get a set cookie back in response, set your session ID on a domain that again will go to both your other public services and to your Django service and then any requests you make to your other services they can pull that session ID out of the cookie header and actually defer over to Django to ask who is this user and get an authentication response then be able to have authenticate user for their service.

If you don't want to use contrib auth because you don't want multiple methods for KPI you can use it directly same sort of mechanism, issue and access talking to your client, your client either stores it in cookie local storage sends it up on API requests and also request to the initial page though if you are using local storage you can't take advantage of authenticate service side rendering because you need {inaudible} pull it out of local storage and send to it node that's something to keep in mind.

Another option is defer authentication to a separate service which is the {inaudible} SLA approach because all of your public services are treated equal and but there are moving parts involved and it's more complicated to get this up and running so you may prefer the lighter approach.

In conclusion, say no to full stack by python I know a few years ago there was an idea we should be pursuing ass a community full stack Python, Python everywhere, this just isn't feasible for the web and it will cause you pain if you try to solve all your problems with Python.  Choose the right tool for the job.  Not all nails are - I don't know what - mice, no, not all nails are mice.

HTP is your friend.  All of your web services know how to speak it how to listen to it, use it to your advantage.  Talk your services in http and when you need something more flexible than direct one-to-one communication use something like publisher subscriber model for your letis(?) for your post stress for your cofca(?) whatever.

And think about web browsers as service consumers rather than as special displayers of content or something.  Web browsers are sufficiently advanced enough at this point and the tools are sufficiently mature that you can build much more modern web application architecture by treating your client as an API consumer or as a consumer of your public services rather than trying to make it more like a dummy terminal.

So a little pitch, heroku is hiring got employers all over the world, if you are interested go to the careers page.  Now I will take questions if there are any.  {Applause}.

FROM THE FLOOR:  Hi, so, the polyglot stuff is really cool and great but screams often over-engineering to me, how do I go about working out when my website is big enough worth, to be worth bothering to do all of this.  Writing the API's, all the services, front end, is a lot more work than is necessary to whack up a single Django only site, do you have advice on how to get, when is it worth starting to moving a service ...

Dave:  If you are building a Blog, you don't need the real-time responsive stuff.  But if you are building Google docks, then obviously you want something that acts more of an application, to what degree does your project look like a website versus a app.  There are shades of grey in in between, the more it looks like a app, if more people expect for a native application.

Be thinking about is, my product also a platform play, like is it going to need an API anyway, if it needs an API then you get a lot of advantage of dog feeding that in your web client.  You are using your API all the time, you will feel the pin points and make it better.

RUSSELL KEITH-MAGEE:  I would like to get your details on the assertion at the end, Python can't be used for that right now the tools are not there, not anywhere near as mature, do you think that is a fundamental limitation of Python that it shouldn't be like that or never develop the tools or something inherently good about java script, I can't believe I said that word.

DAVID GOULDIN:  You are writing java script on the client, if you want to write V eight in Python, I don't want to.

Python can do all of this stuff, Django itself is not particularly well suited to things like you know, web sockets and A syncI o, there are a lot of ..., weren't built with the con currency in mind.  A sync io are promising and it is possible we could get to the point that the only benefit of doing the ... is for isomorphism.

FROM THE FLOOR:  Making dynamic responsive applications is something that is obvious for us but for example, in my company, each time we are trying to do something new, right front end ... java script, somebody from a department that is responsible for (INAUDIBLE) comes to us, no, no we need to render everything on the pages, needs to be traditionally.

DAVID GOULDIN:  I am having trouble hearing you.

FROM THE FLOOR:  Closer to the mic?  Better now okay, so, my question is, how do you like handle the situation when you have to choose between making responsive web app and like classic website where everything is rendered from the controller view template and stuff like that for this co purposes?

DAVID GOULDIN:  Are you saying when you would choose which?

FROM THE FLOOR:  Yes, Google robots don't have the capability for now to grow the web size that are rendered by java script, I think.

DAVID GOULDIN:  They have (INAUDIBLE) I see the point in that, you are departing from web standards right and so, like you are going to lose some of that goodness that comes along with like really simple just like full responses in the original page, is that what you are talking about yes., I would point to isomorphic java script, get the goodness of the client application, ... fully rendered server page, have things like push state to keep track of your urls's, the user fields like they are using a regular old website even though like java script is powering it on the client.  Copy, paste ...

Shipped down fully in html to the client and then the client uses the Django API as a consumer, does that make sense?

FROM THE FLOOR:  Thank you.

FROM THE FLOOR:  Thanks for the talk, my question is, how would you go about like integration testing in an environment that has lots of services or you just have like, the unit test level things where you test like the service in isolation and you maybe use marks and how do you make sure that the mark for a certain service stays or has the same API as the service, it doesn't change over time, and you are testing something that is not there.

DAVID GOULDIN:  This is edging in on the world of distributed computer, where service contracts are extremely important and they should be versioned and they should be enforced.  I know a lot who use the Json schema to document the ..., as long as you have strict "contracts between one service and another., you can test a service in isolation, know that the integration will work, you always want to have integration tests, to run those in like a sand boxed environment probably want to use something like docker or ... or something like that, to spin up virtual machines so run your services in is way that has party with ... I know ... launched with what they call dev cloud, the 20 something services they will spin up that number of services in order to test all of the integration points, the more services you have, the more difficult it is, as long as you have strong contracts most of the time you don't need the integration level and you can mock out or stub out calls according to the contract established between the services.

FROM THE FLOOR:  Thank you.

DANIELE PROCIDA:  Thank you very much David.

(APPLAUSE).
