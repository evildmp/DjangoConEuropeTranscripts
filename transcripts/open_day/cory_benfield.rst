=============================================================
Cory Benfield: Security Vulnerabilities - A Story About Panic
=============================================================

DANIELE.  Okay just about ready to kick off.  So, someone knows how to dim the lights so just to let you know, that lunch today is going to run between twelve thirty and two thirty at Aberdare hall it is on the website.  I have mentioned it in the Djangocon twitter account as well.  There is a map to get there.  Go out of the back of the building, that side.  Then you walk up the avenue until you get to the very end ... and then Aberdare Hall is in front of you.  Check what times you are supposed to be in a tutorial or workshop, go at the appropriate time.  The talks break will be as close as we can get it to between 1 and 2 I think is what is said in the programme?  Is that correct?

Yes, the talks break will be between one and two, no talks between one and two, if you want to stay in the talks all day, that is a good time to go, if you want to go earlier or later that is helpful for the crowds.

If you have special dietary requirements if you have a vegan or if you have serious allergies, tell the staff there because some of the meals are being kept back for you, so nobody else takes your vegan lunch for example.

And that is all I have to say I think actually.  So, we will David?

Yes, when you come in and introduce Cory while he sets up.

NEW SPEAKER:  So he is going to tell us about a security nightmare discovered in the open-source product.  Good.

(APPLAUSE).

CORY BENFIELD:  I am using about eight devices.  A quick warping I too too fast I have way too much material.  I will have questions at the end.

You can find me at places, feel free to ask me questions at these places, if you can't grab me at the talk.  I am kind of what you would call, an open-source software medium shop.  I piggy back on other peoples work, I am a core maintainer on the requests project.

I am also on the ... three project and it is the most important project you have ever heard of.  Maintain a few projects of my own that you don't care about, I maintain hyper, Python's only http2.  I have done various bits of open-source, landed patches in open-source projects, some of them Python and some of them not.

I am going the tell you a story this is a story about one of my experiences with handing a critical vulnerability ... it is called requests.  Little, it is kind of a big deal.

Anyway, like (INAUDIBLE) title it is catchy that is CVE 2015-2296 this will be a blockbuster with rights at end of the month.

2014, a long time ago, the world was a different place, we were in London, where it rained as much as here.  The world was wonderful, the requests project, we had butterflies and bunnies cavorting; do bunnies cavort?  Yes.  Cool, I am worried they might frolic.  They are bunnies, they hop around.

Everything was all right with the world, more importantly the requests project by this point still a fairly notable, had not had a single security vulnerability, we were feeling super-cocky, then we discovered that if you configured requests to website A, which we will call good site, that website redirect to another one Chaplaincy we will we all evil.inc., we will send your password to there as well as good.org.

So, we felt (INAUDIBLE).

So, yes, we leapt into action, a well drilled project and so we filed for two CVE numbers, CVE common vulnerabilities and exposures, a formalised number for keeping tracks.

So we filed two of them.

At the same time decided we should probably have a protest for these, this is a good thing to have.  This is a list to look at to work out what to do.  We had no idea what we were doing, we are idiots we don't deal with this stuff.

So, we kind of just made this stuff up.  This is the crux of this story is, this was the error we made, we didn't talk to anyone about what we do.  The first thing we did right, put up contact e-mail addresses, if you don't put up contact e-mail addresses, people will report vulnerabilities in the public bug tracker.  Anyone can read them., this means the evil happens can read them and say hey, that might be a problem, I should do something with that, then exploit the users, get into trouble and then get fired.  Put out a public e-mail address, let someone contact you, could be a personal, doesn't need to be anything fancy.

Along with it, if you are sufficiently technically savvy, put up a gpg keys., who knows, that is less than half the room if you don't know anything about GPG it is probably not the end of the world.  If you can have them, do, that is my GPG fingerprint.

We can do this quite right like even for fairly technical project, one GPG key per developer.  Rather than having a central.

Reporting a bug, either pick the one that will respond quickly or send one mail to every developer, not the ebbed of the world, it is not great, we do plan to having a project GPG key at some point in time.  Those two steps fantastic, hard core, everyone can securely report bugs to us, nothing can go wrong.

All right so we fast forward, early 2015, doesn't count as now anymore, but it is no ... set the scene, the morning of Saturday 14th March, weather nothing like this.  There are no wading birds here.  I woke up around 7:30 a.m., I rolled over, grab my phone and read all the e-mails.  Sitting at the top of the inbox, was this.  So ...

Coffee has got nothing on that subjects like for waking you up in the morning.  That is way, way worse, so I am panicked then I noticed the time stamp.  I was already 8 hours behind, no one in the team got the this yet.  I was the first person to see it 8 hours after reported.  I freaked out a little bit.  Started my week end a little differently to the way I wanted it.  Trying to read the e-mail on a device that was good at reading e-mail.

So, reporter did something right.  I want to credit Matthew for this, he produced a tarred of detail, it was probably two pages long and can take a thorough description of what the bug was, why it was a problem, and reproducible working code F. you run this, you will see the bug and in fact because it is request he went so far as to write a web server that would reproduce the problem. If you report a vulnerability, I reported one recently, found the bug via code read, I spent hours writing ... so this was great.

One caveat there, our bug was a security leakage vulnerability, so leak information to other people, if your vulnerability is code execution, don't run reproduction code that is an obvious way for someone to take over your machine, so I wouldn't do that if I were you.  I mean feel free! Just don't hold my liable.

Matthew was right, this bug definitely did exist and like most relatively experienced programmers at this point, I didn't stop to think about it.  I just immediately charged into trying to find the bug.  So, quickly jumped into the Python debugger, within 5 minutes narrowed down the problem.  I will have an interlude, I don't want to go into too much detail.  I want to say what it was, if you don't care, there is an okay to put on the screen, octopus, talk to her while I explained the bug.

If you set, if a website set a http cookie, at the same time as it redistributes to the website, we will assume it is belongs to the website that redirected to.  It is made worse, that some frameworks will set cookies on every request sent.  We would happily send your session to wherever flask sends you, the specks say you shouldn't do that.

Right fine good, so I worked it out.  Didn't tell me long to work out what the fix was, it was a simple one.  There is a take away, we hear in the news, hot lead or log jam or insert vulnerability here, there are weird overflows that you can't have in Python, so easy to thing these vulnerabilities don't happen and they do.  But they happen because of simple logical errors this bug here would not have been caught by any type checker that is available in Python, both objects of the same type and passed into the function, we were passing the wrong one of two.

There is nothing you can do about this, code review, this function is a hundred lines long, didn't get effectively coded.  We would have been extremely lucky.  That is mostly where you get the errors from.

I found the bug, prepare a fix, ship it in the next release, great.  The answer is no, the second you push a patch for a vulnerability you should assume that it is public knowledge, pain in the ass to look for vulnerabilities but quick to check a log.

The news is contained I know about it, Matthew knows about Is, Ian probably knows about it.  He is in America.

But, for us to find out, order our code base.  The second I push this they know and can start exploiting the users.  So remain calm and level headed.

I am not good at calm and level headed at the best of times, this is not one of the times.  Up until this point I did everything right, I could have pat t myself on the bag, given a most mortem.  I said don't do any of this, I am terrible.

Don't let panic overcome you and don't move really fast.  We prepared a patch, pushed it, cut the zero relux, pushed it to PIPI and contacted ... there is a stream on the, you will want to update your stuff.

That kind of feels like a success because we are like yeah, went from a report to a fix in twelve hours, eight of which I was asleep for, soy feel pretty good about myself.  This was so quick we didn't have a CVE number for this.  We said security vulnerability, CVE pending.  I did it the next day.

So here is the problem, that is wrong, we did a number of things wrong we should have done better.  So, thing one, released on a Sunday.  Don't release on weekends it is a terrible idea.  Firstly, lots of your users will be businesses, most businesses don't work weekends and they are not paying attention.  Attackers do not work nine until five  -- they live in basements with plenty of hours and ... releases patches on weekends gives attackers a day or two of head start on your vulnerable users who are businesses who don't know what they are doing., businesses are (INAUDIBLE) and those require that pretty much the second someone becomes aware of vulnerable they have to assess who is at risk, I have people following us on twitter.  Forcing people to work on a Sunday doesn't enforce ... release on weekdays, preferably Tuesdays.

Don't release before you have a CVE number, this gets into the same concerns of businesses and complaints, CVE's are how businesses track vulnerabilities, whether they are exposed to them.  If you don't know how to get them, Google "how to get a CVE number and great."

I did that, it is fine, super-easy to get, not that hard, make sure you get one.

If you have downstream redistributors, warn them ahead of time.  This admittedly might have been a privilege for larger projects, you might have surprised how much have got them ... if you have them, find them out, form a relationship with them and make sure you can warn them ahead of time.  If possible, and you are GPG savvy, have a conference, so you can definitely contact them and only them.  That way you can coordinate a release over all the channels, minimise the risk to the users ... they are people too.

Also, if you put ... (NAME - INAUDIBLE) users to hate you, ... they write nasty e-mails.

Right, we will speed through.  Clear what versions of software are affected and how to fix them.  Just upgrade.  We had to request all the back verses so people know, most importantly have a public policy about the stuff, have a document, here is who you contact, how you do it.  Request, promises to get back to you within twenty four hours we will acknowledge the e-mail, then a separate time how to push for it.  If you don't know how to write one, steal ours, look for the vulnerability section, steal it, maybe change the keys in the GPG keys.

Number one tip show, scar, this is good, be prepared for this sort of thing, it can happen to you, you want to know, hey, I saw a talk and maybe there was some good advice in there.  Cool, I am done.  Thank you very much.  (APPLAUSE).

NEW SPEAKER:  Thank you, sorry to cut you short.

Whilst Amit comes to set up, many a couple of questions?

Anybody?

FROM THE FLOOR:  I have got one.

RUSSELL KEITH-MAGEE:  Fantastic, thanks very much for that, by the way Django has one of the policies in Wales, I would be interested.  Any comment how it changes in?

CORY BENFIELD:  It was, vulnerability is not disclosed to you, you have become aware of it, already exploited.  Everything moves much faster, my ... it was entirely inappropriate in the case of a well disclosed vulnerability, again, Alex has a really good log post on this, I recommend you read, I steal most of my good ideas from this.  This is one of those, get ready to check it out.

There was another question?

FROM THE FLOOR:  So first off thank you for riding requests or.  Have you had a chance to put your new improved process into action?

CORY BENFIELD:  We have not, I think the best kind of work is work that I do, that I don't have to use, I am happy to waste the 8 hours.

NEW SPEAKER:  Any other questions for Cory?

Thank you very much.  (APPLAUSE).

Amit is going the set up for the next talk, while he is setting up.  I would like to mention two people who are doing a really great job for us here today, Sheryll and Hilary, here at the front from Action on Hearing Loss who are providing the speech to text transcription, so thank you very much.

(APPLAUSE).

Is this more difficult than most jobs?

Yes, it is.

So, they are doing a really valiant job and it is fantastic, if you know, if English is not your first language, if it benefits you to see this, make your way over here so you can see the screen, I hope that it is proving useful to people.

If it is proving useful to you, mention it next time you go to a conference, there are people with hearing impairments who don't go to conferences because they feel they don't hear things.  So, thank you very much once again, they will be here with us for the next 4 days, I hope we don't wear you out completely.  So thanks.  (APPLAUSE.).
