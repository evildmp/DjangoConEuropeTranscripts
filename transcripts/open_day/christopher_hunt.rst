==================================================================
Christopher Hunt: Arduino sensors, mobile apps and virtual reality
==================================================================

Hello and welcome to the final session of talks today, we are going the kick off with Christopher Hunt, the lead developer, research assistant and ... at Plymouth university, he will be talking about Arduino sensors.

CHRISTOPHER HUNT:  Are we all caffeinated ready for the last session, tried to Welsh cakes?  Hopefully you have.

So welcome, today I am talking about we are going to talk quickly and speed through, try and scare these people doing a lovely job in the corner here.

So, come in people, you have missed the start.

So the Django and the data system.  Objectives for today, understand the concept and come points of the data system, a metaphor for the things I have been using, the different processes and systems.

Discover we, i-DAT is using Django, try and provide two live demo, only one now, because some of these didn't survive the train journey up here.

I am from institute of digital art and technology, we are an open research lab for playful experimentation with creative technology.  Very fancy.  I didn't come up with that, my boss did.

We exist at Plymouth and support the digital art and technology undergrad course, research, environmental things, social stuff, domes and different environments, biological and lots of other key things.

Key line from our description of our strands tat bottom.  From data to code to experience to behaviour.

This is the process and this is what the systems and what we can do enables.  So as we go through, keep that in mind and keep thinking, what kind of things, what stuff you can enable, tools and technologies we can play with as we go through this stuff.

So, the data system.  This is my model with lovely ASCII art I am proud of this.  Start at the top.  Circular system because it goes around in circles.

At the top we have sense and collect.  This is sensors, these are these devices, things that you know, like sensors, a few other things, they transmit to somewhere we can store and process that data.  This is where Django comes in and that is where I will talk about that.  Then that enables interpretation and understanding of that data.  This is visualisation, this is oculus rifts, and cool stuff at the end.

Hopefully through all of it.  So first step.  Sense and collect.  Which transmits to somewhere we store and process.

In here, this set of transactional props comes from PhD projects this is done with myself and one of my colleagues, John and in here, we have these tiny little formally sparkled now particle.  So I have got the re-wipe that bit of code in my head.  Renaming things it is annoying.

These are little Arduino light devices, programme them using the same languages, wired directly into the device.

So, what is going to show that but because, in the interest of time and with a few network issues, what happens with this project two people sit down.  Then, these devices all have different sensors the funnel has an fsr, you squeeze and then it, certain cups vibrate and little nozzle tips light up and do things.  The idea you are using the sensors and exploring the relationship and the system beneath.  So behind this, there is this Django page which is receiving all the data over something called message cue ... transport.

All these devices sending up to here, we can see this going on, this goes to another back end, we can explore and see the data then different stuff happens there., I may need to ask whether somebody has a soldering iron.

Pretty standard code, except extra bits for connecting to a broker, connecting to NQTP.  It is a publishing subscribe protocol, nice and easy to connect with., here we are connecting to our NQTP broker, then publishing our information our messages, so, the green glass, what happens here in its loop, checks if it is connected.  Every time I tap that, that would then send that message, that fault it received over NQTP then make it vibrate, but we will show you that later.

So that is sensor, those are Arduino's and different devices but, at the essence of that, that is just data, data can be any kind of thing, we have done a lot of project and research with arts organisations around different, about how you gain and manage feedback.  Traditionally someone would pull, go around an art gallery, someone pull you aside with a clipboard to answer lots of boring questions.  What comes to your mind when you think of science?

That is, then you have got this open ended, this event did not match my expectations dry and not interesting boring things.  You start to see lots of ways to get around this.  This is a happy or not sensor, the question here:  Please rate our check outs.

You may have seen these at airports as you go through the security gates.  You go through, then slam on the button say, hey I enjoyed it or this went badly.

I can imagine sometime next week you might see something like this, dotted around Cardiff! just in case you need to voted on Zain, say you are a one direction manager, find out who next to put on the bottle of fragrance, we will get back to that later.

This is developed into our quali project, this is where the mobile apps come in.  This is the same kind of thing, an app for the Cheltenham Festivals.  As you go around the festival, as you explore and find out stuff about it you get to rate and leave feedback.  Say what mood you are in or did you enjoy the event.  In the micro-interactions, instead of having a big long essay of things to fill out.  Tiny bits of data, as we collect more and more of that, we build up a better picture of what is going on.

So, devices, sensors, mobile apps all cool.  They all transmit back to somewhere to store and process the information then enables interpretation and understanding.

So, we could use fi base or pass or all the platforms of the service thing, we are at Djangocon, I would encourage you, why not build your own?  A good question.  You could save time with those, but you want to learn and, boar reed this quote from my boss's talk mike.  I will give it my best Tom Hardy impersonation.

"take control of your city.  This is the instrument of your liberation!"

I really should have been an actor not a developer clearly.

But that is it.  It is for us, it is being able to control a platform rather than rely on someone else or worry about things degrading, things being unable and falling apart so, patch ... cosm and xively, lots of stuff out in the field broke.  Great.  Amazing that.

So you learn and that ability to control and build stuff really is valuable.  This is an old screen shot from digital ocean, but the cost of computation, the cost of running the server is so small you know, you can easily do quite a lot of big project work on just a tiny VPS, easy peasy,  -- got 5 minutes left.

Dive through the last few bits, why Django?  Why use it?  Because it is awesome.  Why else?  Obviously you need a few more reasons than that.

So top of my list, models and migrations, that makes it easier to prototype the data.  Here is my model our happy or not button, ignore the code, only for demos, I have forgotten to remove a certain someone from the member choices, that is depressing, the value of Django, that makes it easy for us to prototype, we can iterate, get stuff out.  Get people playing with stuff.

REST API libraries, allows us to enable different things so we can talk to tasty py and the rest, there is the data from earlier, of course you have got Python.  The only way to describe the power of that, well with that.  You have got all the sorts of things, as you have been listening today, you have got numpy, scipi all sorts, takes the work away from you, you can get on with doing amazing cool things.  Of course, the kit most important thing in Django, is the community, is you lot.  Everyone who is really friendly all the core developers, or core committers are so friendly and helpful.  That makes a big difference when we are teaching and working with people, then aren't afraid to get involved, mix in, ask questions, that is brilliant.

So lastly, so we have stored it somewhere, built our Django back end, now we need to interpret and understand the data.  Because we are working with arts organisations we can do something like this, just the templating language, so build basic views on demographics, feedback, we can look at hot spots and send Norwegian puppeteers where people are building the apps.  Create systems to create questions, get interested and involved in the data we have the immersive vision theatre which is our planetarium, here we can fly you to the edge of space or through the bosses colon, which is the weirdest experience I don't want to experience again!

Or take you into data scapes.  So this is something we have been developing for one of our conferences and lastly, I can dive straight into another demo.

Fingers crossed.  A ha.

Fantastic.

So, interesting effects, so in here, I can now can't see you obviously.  You are all just floating bits of data.  But, if I look up there is some pictures been down loaded through one of our back ends, here some blobs of data, bits of orange there.  You can come along and experience that later.

But that is all about engaging and getting people involved in the interpretation and the exploring what is available in that data.

Okay.  How much longer have I got?

One minute.

Cool.  Fantastic.

That means I can do the last few examples, from i-DAT's work, we have a building, we have sensors in a building including a vision system.  Can you see this thing moving?  Should now start going backwards because the video is looping backwards.  So this is our Slofbot, using the whole model.  So the sensor is at the top of the atrium, that is looking for detecting people going across the room, as you go along to your lecture, there is suddenly a wall in the way.  The idea of that is to kind of get you thinking about the space because you don't think about this corridor, then something is there, I must realise what is going on.

Or, this is very old video now, but or you, or you will look at how people use the space and the building.  Then you decide as a long term intervention you put a random duff button in the lift, to get people exploring through the data.

That is the data system, that is all the elements, I will open up to questions before I get pulled off the stage, thank you very much.  (APPLAUSE).

NEW SPEAKER:  Can I take any, Chris take any questions?

So you mentioned briefly at the start of your talk, how is your work explaining  -- do you want to explain?

CHRISTOPHER HUNT:  So, the internet thing was, when you say interneter things, you think a smart house, smart car, smart things going on.  I don't like using that term, so that is why I use the models with the students and the people I work with, to break down the system going on.  It isn't just remote controlling something, but it is interesting things going on with that data.



FROM THE FLOOR:  So obviously Python and Django on the server side, but the nasty language in the ... side of things, is there a way of fixing that?

CHRISTOPHER HUNT:  That is a good question.  There has been some attempts at porting, having Python then generate that C code for you?  But, unfortunately, you can't just run Python on these sadly.

RUSSELL KEITH-MAGEE:  Is it a hard way limitation?

CHRISTOPHER HUNT:  It is a so, on here, what that C code is done, compiled down and then run on a devices.  What these devices are, they are essentially dumb.  All these are doing is sending their data up to the Django server and then waiting for messages to come back.  So we can add all the intelligence, all the interactivity server side and manipulate that and change that without having to change the code on these devices.

FROM THE FLOOR:  There are slightly more powerful devices that can run.

CHRISTOPHER HUNT:  Yes, these are simple ones here, raspberry pies or eagle bones, it is all becomes enabled and available.

FROM THE FLOOR:  How did you make Django talk in PDP?

CHRISTOPHER HUNT:  Django is using the pay, ... library, then a written a management command which is supported by supervisor, then runs in the background, listening for messages coming in, validating them and then to the models.  If you are interested I can show you the core stuff that is going on.

NEW SPEAKER:  I think we have time for one more quick question?  If not, then we can thank Christopher Hunt again.

(APPLAUSE).

NEW SPEAKER:  While the next talk is getting set up, there has been a slight alteration to the time for tonight’s meal, aiming to be at the restaurant for quarter past 7 now.

NEW SPEAKER:  Could you repeat that?

NEW SPEAKER:  Change in the time for the meal, aiming for quarter past 7 now.
