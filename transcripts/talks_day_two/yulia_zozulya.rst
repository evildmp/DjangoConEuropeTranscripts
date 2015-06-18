=================================================
Yulia Zozulya: Using Python to load-test web apps
=================================================

DANIELE PROCIDA:	 While we're getting connected to let you know at lunch time lunch will be served both on that side and in the other dining room at that end so you can go to either one.  Peter Finch's city walks are both now fully booked up for this evening and tomorrow evening, so if you've got a ticket you don't want please cancel it to give somebody else a chance.  If you are going to the clink tonight or tomorrow night it's not really compatible with going on the city walk so cancel the walk for that night.  OK.

VINCE:	 Before we start remind everybody about the photo that will be in this room, we'll do that just before lunch.  Which brings me to introduce Yulia who will talk about load tests {applause}.

YULIA ZOZULYA:	 Hello everybody my name is Yulia and work for {inaudible} we develop tools for developers to make their lives better and the most recognisable in this community would be of course {inaudible} Python but we do not only make desktop tools.  We also provide a bunch of services such as tracking system, bug tracking system or CI servers or code review tools and when we started our latest web servers which was review tool named outsource we decided we want to somehow re-think the way how we do the performance testing.  And this thought brought us to a lot of questions for example the first one would always be what tool to use to do the performance testing?

There are a lot of tools out there from {inaudible} ones to encryption languages which provide a lot of frameworks for you and they can be configured via XML any files so vast majority of options are really hard to cover in one slide.

So if you actually select scription language to do performance testing you might want to understand why you do that and choosing Python over other scription language might not be a question in this community because you already use that language to the web server development.

And why to use scripting language at all?  It's quite easy to load servers which require some complicated logic for example for the game in our services me even use sockets for the task and it's not easy with IO oriented tools or if you need complicated data over complicated requests over performance testing it's also easy just to write code tan to fill all those strange forms with a lot of fields and stuff.

Still, in Python there are a lot of tools which provide you such ability and I will cover only few of them and I would like to start with funk load here because it is the simplest one.  As you can see it looks a lot like simple unit tests here with test set up and tear down method so you get code in easy recognisable matter and has special set up and cycle methods which I'll explain later.  It configured with a in you like configuration file.  It may scary because of a lot of parameters but it helps you to tune to your needs.  And it can be easily reduced actually.  So it is not that bad at all.

So what actually happens when you run crunch runner over your written tests? it actually spawns a number of configurate number of threads one by one with a little day so you don't get all your tests run in a single moment which almost never happens in real life and in each thread test is run in a loop.  During configured of amount of time and this time starts only when the last thread had been spawned so you don't get into situations where you don't have all the concurrency that you configured.

When this has ended all the tests attempted to be created are killed so this should not be a problem.

Top cycle and down cycle methods I mentioned before, those are meant to be for configuration parameters that all the users have in common for example URL, web server or some other configuration you might want to pick up from your files.

Those cycles - sorry ... those cycles form a branch in which you can configure different amounts of concurrent threads and this allows you just to compare the performance of your web server over different amount of load.

So why do you actually use funk load?

It allows you to write your tests in easy manner just like your IT or unit tests and there is a runner provided that allows you to run this in single user mode so you can use them as smoke tests for example.

And other advantage would be that it has benchmark more, benchmark - it has a distributed mode and you can easily adapt for virtual glance to your load environment just by 2 lines in the configuration file.

Other thing about funk load is that it is extremely well documented.  It has a lot of examples it has a lot of tips and tricks about performance and I really advise its recommendation.

And the last thing would be that it is written in a way that it can be easily extensible.  In our company we are actually over written some methods of default bench runner so it would communicate with our CI server and provide the data to our default graphics and it was really easy actually.  But why not to use it?  The main reason would be it uses default Python threading module only and that's quite a problem because Python threads can use only one cord, Python internal architecture, and it might be OK with IO tasks but if there is at least something you do which is CPO which loads your CPU, you will have ... hmm... sorry, just a moment ...

There might be a problem with that and you won't get to use all the resources of your motive {inaudible} glands(?) and ..., and the other thing about funk load is default reports of this framework is not really good because there is only one type of graphics here and it is not configurable at all, you just get the timers that library think you should get and you are not able to influence it in any way.

And a lot of problems of - some of the problems of funk load library can be solved with multi-mechanise framework and the core here of this framework is transaction class basically an object which should have a run method defined.  And it has configuration file in your like - just like the funk load library.  It has a lot less parameters here so it looks more light weight than funk load.  So it would be easier to start with it actually.

So, what happens when you run multi-mechanise runner over your written class.  It loads your transaction into configured number of threads which is spawned one by one with a little delay and it seems a lot like funk load up to this point but the main difference that those threads can be formed into user groups and those user groups are spawned not in different processes using different processing model of Python.  Its user group is started simultaneously and if you want - you may turn up the load with several user groups and configure amount of threads so you get load you need.

So why to use multi-mechanise, it uses multi-processing along with threading so you use multi-core with your clients easily and default report graphics is more configurable in multi-mechanise, just for example you can configure your own timers and it show you the results and graphics that you really want to see and actually it has more types of graphics - more than one - it is quite easy - and it looks better for my taste because it uses different graphics back end so it's generally better.

But why not to use it?  For me API is not as obvious as simple unit testing because you are not get the idea from the start which helps object would be peak topped by the runner which are not and it's quite frustrating not to understand what's happening and the other draw back would be that distributors work flow of them is not supported out of the box and you will have to come up with the solution to that yourself, for example with some other Python module which you prefer.

And the last but not least would be rather fresh and actually developed framework called locust IO.  The runner actually forms randomised locust which will fled your server and the rules of how they will be formed actually described in the related tasks set class which is basically set of tasks.  The frequency of each task for each locust are defined with weight attributes and weight time between those tasks are also is not fixed but in some interval so it's getting really randomised here.

And what actually happens when you run locust scripts.  The key difference here is that this runner doesn't use threads at all.  It uses {inaudible} and greenlets and those are proven to be more efficient in IO tasks than threads and ... that would be it I guess. So while locust IO?  Greenlets are much more faster with IO tasks than default p.threads and thing I forgot to mention locust runs light weight web, web server in the background saw you can share the results of testing between your colleagues or even you can monitor what's happening in the real-time or you can change parameters of the load and it is really convenient.

The other thing would be that distributed work flow is supported is not that easy as in funk load but you just need to run slave for agent on your clients so it will, you will get distributed load here.

The other thing would be you'll get total heterogenic tests it's not like in other frameworks where you get all your tests run in a loop one by one.  It is completely randomised and that's a good thing because you get something like real life experience here.

And last but not least it doesn't have any configuration files, all the configuration is done in Python code and there is not much to consider actually.

The only thing why not to use locust is it has rather tricky terminology and all this weird weighted randomised relations can be really hard to get into but once you get into you will see the bite brightness of it.

And all of the examples why not to use Python for performance testing and by Python I mean Python 2 here because all of the frameworks I've covered today can be run only under Python 2 even the fresh locust guys picked up Python 2 and if you already migrated to Python 3 I am sorry for you guys and the reason would be is level interpret to log which doesn't allow you to fully use all the resources of your load glands and you will have to end up with some solutions with multi-processing or adding clients to your load cluster.

In je(?) we ended up with using multi-mechanise along with jeneta(?) because we need a big load here and that is the reason why we abandoned Python because for the performance testing is not as perform itself.

So if you have any complaints about how the things are going in performance testing, please share them with me, I know that feeling, I've been there.  Thank you for listening.  Do you have any questions?  {Applause}.

VINCE:	 Thank you very much.  I see 4 people have gone up keep the questions short in interests of time.

NEW SPEAKER:	 Do you know of any of the tools you mention have some kind of functionality that allow you to see the synchronised impact on the server like the CP usage, memory usage and the server -

YULIA ZOZULYA:	 In Python no they don't but jeneta I mention that use Java it has this.

NEW SPEAKER:	 Thanks for your talk, I always struggle with understanding the output of my load test, I can run them compare them with previous runs and get a sense if it's faster or slower than previous ones but do you have any tips on how to get more information to that?  More knowledge?

YULIA ZOZULYA:	 Um ... actually what knowledge do you mean?

NEW SPEAKER:	 For example I would like to know which URLs should I consider for improvement to make my service health better in general based on globe testing I guess that should be possible.

YULIA ZOZULYA:	 Actually if you see on the graphics that all the tools are or providing that some of the requests are not replying in the way you need them to, you can compare them between each other and actually a lot about impact on each URL as in locust 2 you have weight attribute for example which defines how much users will use this URL for example and if those weighted URLs are not performing really good probably you should look into them at first and only after that compare them with another for example.  I guess that would be my answer.

NEW SPEAKER:	 Thank you very much.

VINCE:	 One last question I'm afraid in the interests of time.

NEW SPEAKER:	.

YULIA ZOZULYA:	 I am here for the rest of the conference.

NEW SPEAKER:	 It is not really a question.  Actually I'm more keen that modular cloud services team and we have the same problem each time we want to release a service and we built a tool that is called load and can spawn the test on many machines at the same time and it chooses statistics D to get some real-time statistics as well as CPU and memory and you write it is almost like funk load, you write a send are you how you want to test, what a user will do with your application and then it runs it a lot of time and it break everything.  And we built second version using doc S and now you can write your loader in any languages then spawn 2000 machine running your documentation at the same time and break everything again so if you are interested contact me.

VINCE:	 Thank you very much.  Thank Yulia one more time.  {Applause} various people pointing at each other.  We're going to do the photo now.

DANIELE PROCIDA:	 So you'll direct us for the photo.  You are the photographer.  You give instructions.  If you want to be in the photo stay here for a couple more minutes.  It only takes 150th of a second to take a photo.  The Django for social will be on Wednesday not today.

(Lunch)
