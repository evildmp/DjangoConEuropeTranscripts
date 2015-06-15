=======================================================
Russell Keith-Magee: What on earth are Python & Django?
=======================================================

By the way, if you are just an Open Day visitor and don't have a lanyard but would like one of these lovely, member of the Djangocon Community badges, go the Council Chamber and ask for one, then you will have an official badge.

Okay, very pleased to welcome Russell Keith-Magee who is the President of the Django Software Foundation, a job glamorous as it sounds, travelled from Perth in Australia, I will let him say all the rest thank you Russell.

(APPLAUSE).

RUSSELL KEITH-MAGEE:  Thank you.  Well good morning everyone as I am Russell Keith-Magee, I would like to ask you a question, what do you see when you look at a computer?  A lot of people look at a computer and what they see is a fancy typewriter or a fancy calculator or a fancy postman delivering your electronic messages.

What I see?

I see Lego, now a typewriter, a calculator, these are tools when the postman comes with the parcel and doesn't ring the doorbell.  ... These tools are single purpose devices they do one thing, a computer is also a tool, like Lego, infinitely recon fig rabble, just as Lego can be any toy you want it to be, a computer is a tool you want it to be. You want to have an idea of what you want to do.  If you need a typewriter you can make one.

If you need a calculator, you can make one.

If you need someone to deliver your mail, it can do that as well.

Anything you can conceive of, or you can programme a computer to do it, the catch of course is that in order to make any of your dreams into reality, you have to be able to programme the computer to realise your dream.

Over the years, two things have changed, if first is the size of computers the first ones were big, filled an entire room.  These days almost everyone who is in this lecture hall can be carrying in their pocket a computer considered a supercomputer decades ago.

But, secondly, the way you programme computers has changed a lot ore the years as year, this was ... patch chords, you ran wires through, you can see the ladies doing.

The configuration of the chords can control the calculation that was being made, after a while, people worked out how the replace the patch chords, but then you are working close with the metal.  You are working with low level instructions.

This is Grace Hopper, in this picture, holding the piece of magic, the Cobol programming manual, a machine independent programming language, the idea to express the solution to a complex problem using a high level abstract language...

Interestingly, this actually exploit it is strength of computer to make them more powerful, computers are really good at taking a set of instructions and following the rules over and over again.  Converts from a high level to a machine language is a matter of following a set of rules over and over and again.

As a result you now have abstracted higher level way of communicating what it is you want to computer to do.

This gains you two things, first the concepts you can express that you are able to express easily, become more complex.

If you want to bake an apple pie from scratch, first create the universe, early computing was like that.  You had to make everything from scratch.

High level language, when you bake the pie, assume flour, ... the less time you have spent time bogged down in flour, the more time you can spend making pies.

The second thing is you make mistakes they are a lot easier to find, in computing circles those are often refer to as bugs, why?  Because in the early day they were bugs, this is Grace hopper's logbook, a moth stuck in a mechanism, causing the calculations to go haywire.

So these newfound powers to ability to encode complex ideas, the ability to fix problems, computers started to be used to do more interesting things, twenty years ahead, this lady, Margaret Hamilton.  The reason that Neil Armstrong walked on the moon.

In this picture, standing next to the code for the lunar landing, if you listen to the transcripts, the last thirty seconds, you can hear him say, programme alarm code ... that is an error condition being reported by the computer on board the lunar lander, warning, too many requests passed to the computer and certain operations ignored as a result.

Now the reason that that error message wasn't a problem, programmed the computer to prioritise important over other operations, one of the reasons they got it right, using a high level programming language that allowed them to express the priorities in the case of an overload.

Okay, wind toward another twenty years, Commodore 64.  Commodore 64.  Gave me a blinking prompt, started in basic, it was called that for a reason, an approachable language compared to other that is existed at the time.

Of course that didn't mean it was great, but just better than the alternatives F you wanted to do anything interesting had to understand all sorts of internal details, drawing on the screen, using operations to write into the memory of the machine I was able to programme, it could be done.  Now a lot of time that was just meant typing in code I found in the back pages of computer magazines.  It was coding, my first game, sand castle type the number appeared on the screen.  The length of time, every time you typed in the number, a bit of sand thrown on to the sand castle, the tide was coming in, eventually the tide wash away your sand castle.  Grand Theft Auto, eat your heart out!

To me as a nine year old, I turned this into a new source of fun, it could do something tangible, that an hour before it couldn't do.

So wind forward another twenty years, so what do our tools look like today?  The languages continue to be more and more expressive, the first part of the talk, Python. It isn't named after a snake; it is a high level programming language, not only does it abstracts away the hardware, but the operating system.

Where BASIC likes to call itself a beginner’s all-purpose language, Python has a much better claim to the crown, descended from language, abc, designed as a teaching language to replace basic.  Python replaces a lot of the properties, but extended the ideas into a powerful all-purpose language.

Now one of the reasons that it is a good teaching language, the underlying philosophy, aimed to be straightforward and not too clever, it has a set of unofficial guiding principles referred to as the ZEN of Python.

[on screen].

Now, hopefully, it is clear why these are all good properties for a language that you are going to teach someone to programme, explicit you always know what is going on, simplicity means it is easy to understand what is going on, readability and beauty, make it easy to consume whatever it is you are reading.

But as it turns out, these principles make for expert programming language as well.  A running joke that you are only half as smart when you are debugging code as when you wrote it.

Having a language that encourages you to be explicit about what you are doing encourages you to embrace your ability ... these are properties that make it easier to read your code in a year's time, but for someone else in the team, decipher what it is that you have done.

Just because Python is clear and legible doesn't mean it can't be powerful.  It has really strong housing introspection, code that is running; work out what is running, why it is running and change the way it is running as a result.  An object can look at another object and say, does that have property X and respond appropriately.  Means you can Meta programme, write programmes that write programmes.

... the further you can abstract the more power you get, the more power you gain and the more specialised you can become.  Plus, programmes that write programmes are the happiest programmes in the World.

Python comes out of the box with a library of built in tools, maths, dates and times, data compression if you have all you have got a standard install, you have got a huge amount of power.

Python community, congregates ... known as the Cheese Shop, the Cheese Shop is a massive library, everything they couldn't put into the box ... it is a huge range of packages for every conceivable purpose, reading every possible file time and interfacing with any possible system you can think of.

So when faced with the problem of exploiting a wonderful international telecommunication networks we call the internet, inevitable someone will come up with a Python package to help you to build in a website.

That is where Django comes in.

What is it?  It is a high level Python web framework that encourages rapid development and clean pragmatic design.

A web framework is a library of software that abstracts out the common development, short cuts for tasks that you have when building a website, dealing with log ins and maintaining a session state.  Permissions to make sure that the right people can see the content you need.

A good web frame work finds the pain points and smooths them over but not getting in the way, working at the high level abstraction, so you don't need to worry about the protocol or cookies or how the database is working, shouldn't get in your way if you want to dig into the internals to make it work.

Django, it builds on top of what Python does.  If you are using Django, you can use Python.

So, it encourages rapid development, regardless of how many powerful features a language has or a framework has, a web framework is worthless if it doesn't save you time ... with Django, build websites in a matter of hours not days.

This comes out of a set of real world programmers.

When a big story broke they didn't have the luxury of a long development cycle, the tools are there in Django to make you more productive, to help you get your grand idea from your head into the world as quickly as possible.

Encourages clean pragmatic design, maintains a, tries to maintain a clean, desire through its own code and makes it easy to follow best practices in the applications you are creating.  The philosophy to make it easier to do the right thing.

For example, there is a group out there on the internet, open web application security project.  Who its name suggests, draws attention to the security in applications, every couple of years, publishes the top ten security issues.

One of the reason the organisation exists, many of the tools outed there for developing web software don't have a good security story, sure you can build a secure website in php, it can be done ... if you learn php by reading tutorials on the web, the chances are you have unwittingly embedded some security problems in the website, slow the pick up on the fault, having security as a default, having something difficult to do something the wrong way, ... in Django, it is the default setting, it is (INAUDIBLE).

But, if you follow the path of this resistance, if you do what the documentation is telling you to do, you at least won't introduce security problems accidentally.  As the professor said before, the (INAUDIBLE).

Like I said, Django came from the pressures of the news room, to the credit, news rooms that it came out of, the small newspaper in Kansas, they didn't think of the website as the way of printing newsprint on screens, they introduced the idea of data journalism, it is presenting the information to the reader in a way that is compelling.

So you don't just write a thousand words saying the crime is on the increase, you show a map, showing you where the crimes occurred, trends over time, break them down by crime time, interesting highlights but let the user explore the data for themselves, given access creates content and perspective to the argument you are trying to make, allow it is user to draw their own conclusions, what is compelling to you, may not be to someone else the things that convinced you of the argument, won't be the connection that convinces someone else that the argument you are putting forward is correct.

For me, that is why it is worthwhile learning Django, some much of our lives are governed by data, logs, use of a resource, ... if you look at your computer as a fancy note pad, you might be inclined to take the data, stick it in a word document and be done with it.

But that is hardly a good use of that data.  I am constantly amazed how many businesses I encounter, where the core is the "spread sheet" the master list of things can be done, how it is managed.  This document can be used by one person, the master of the spread sheet.  Nothing gets done unless you talk to the person, master of the spread sheet.

My day job...

I use Django all day every day to solve this exact problem, at its core, (INAUDIBLE) is a business, we ... a customer has a leaking pipe, every customer has an address, the business owner needs to know what is outstanding and what needs to be done.

Employees need to know ..., how much the customer is invoiced for.  When I go to the company, the admin strategy, one of two things, a huge pile of printed work orders this deep, of everything they need to have done or "the spread sheet" which lists all the jobs to with done.

We are able to replace it with a website that anyone in the company can look at and anyone in the company can update.  Everyone has a full history of everything that is done on the website, they can see it on the website, or sitting on the beach in Bali.

The more you look through the lens of data, the more you see day ... to be visualised in a more engaging way and while in the past turning the dreams into a reality, might be a pipe dream., with ... you have the tools to make the vision a reality if you have, if you have got a problem ... easy to start a business, the website, rent servers by the hours, pay tens of dollars a month.

But you don't want to start your software empire, you don't have to publish the...

If you need to know how to turn the bricks together, you can turn the computer into whatever you want it to be.

Python and Django, all open-source projects, doesn't anything to down load them, when you get them, you get all the source code as well.  Lego kit, a set of instructions, most people follow the instructions, if you are curious, you can pull it apart, see how it works, connect it to another model.

If something breaks you can fix it yourself, if you find something interest you can share the knowledge.

Open-source...

If you find a problem ... (INAUDIBLE) ... not only can you add the new feature, you are encouraged to add the new feature and...

So that is my pitch for why you should learn Django and Python.  I hope that has teased your interest.  ... I hope you have a great day and I hope I can see you around the community very soon.  (APPLAUSE).

DANIELE PROCIDA:	 Thank you very much Russell, you'll see and hear a lot more of Russell during the week and - no don't try and avoid him.
