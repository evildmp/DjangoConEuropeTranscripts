===================================
Kat Stevens: The Full Stack Octopus
===================================

Welcome back from lunch everyone, just a few quick reminders.  There will be a kind of gathering at about 2:00 o'clock during the lunch break tomorrow on one of the tables tomorrow, anybody interested in the Django formation for social good forum or platform or group or whatever we want to call it.

Speaking of social good, do you want to be responsible for making someone else go hungry?  Or do you want to be responsible for the unnecessary slaughter of an animal?

So, I think not.

So, would you visit a web page if you could help avoid that?  Okay.

Well you can.

All right.  Because and you need to.  Because this is our catering situation for the Thursday and Friday.  Those numbers still do not make sense.  Unless many people don't want to go to the party on Thursday evening?  Which you should not miss because there will be a lovely barbecue with plenty of food.  So, if you are coming to lunch on Thursday, staying for the sprints you must tell us, if you are coming to the party that night, tell us and the same for lunch on Friday.

This is how you do it, go to your e-mail and you find the message that is  -- hang on,  -- find the message that says your Djangocon ticket.  Edit details, it will take you the your ticket and then you fill in the details for us, please do it right now.

Thanks to AOTV busy filming these days, put the videos on the internet for us, once they finish the task of editing for us, thank you for your team and your work (APPLAUSE).

If you are interested in taking up the opportunity to visit a counsellor from the wellbeing support team, the appointment notes are there on the board at the back, pick some up.  There are some available for today and more available for Wednesday and Thursday.

Don't hesitate.  Even if you want to sit down and say, I am not really sure why I am here?  You might find that starts a conversation that leads somewhere.  So a lot of people have gone in for counselling sessions not really sure why or not even sure what is bothering them but the fact they start talking is what helps.

I would like to welcome our next speaker, Kat Stevens so if you want to come up Kat and plug yourself in.

Kat is going to be talking about Django development in a small business, under the title the full stack octopus.

KAT STEVENS:  Afternoon, I am Kat Stevens, the h web manager for, we are a fine wine and spirits merchant based in London,.

FROM THE FLOOR:  Yes!

KAT STEVENS:  Before, the question everyone asks me, is do I get to drink the wine, the answer is not as much as, the answer is not as much as I would like.  I am here to tell you about being a full stack developer and some of the challenges and the advantages.

Here is my octopus, and, there are plenty of legs going on here.  We have got all the Django side of things, on that side.  We have got content we have got a design and user experience.

Admin and all the management and project planning and don't worry, our octopus hasn't come across a nasty accident, he is fine, we will come on to that leg at the end.

Okay, so how am I going the fit all of this into a twenty minute talk?  Well, there is not as much code in this presentation as I would like but, that is the story of my life.  [screen].

So, where do we start?  When I was first joined the company, the company had did have an existing website and it was built in ".net" several years old, wasn't responsive this was 2010 didn't interact well with the companies CRM, so lots that needed improving for an expanding business, so I basically had a free slate to do whatever I wanted.  My manager was very trusting and said like, if you can prove to me that you know, Django work then great.  You know, you can go and ahead and do it.  I decided to go with Django, it is something completely different, different to ".net," but different to what I had done before, never programmed in Python before, I had only recently come across Django because some of my friends were using it.  I thought I would give it a go with a couple of small prototype projects my boss is keen on small events websites and things that would you know, branches of that business that were going the be temporary, this seemed perfect to try out Django, one of the prototypes I did was for Bordeaux enprimeur, every year around April, May, the wine industry goes crazy, everybody ships over to France for a couple of weeks and samples new wines out of the barrel.  Now this is basically wine futures, you get people investing in wine that doesn't exist yet.  Not going the be in a bottle for another two years, my challenge was to make a prototype site with a shopping cart and stock import for a product that didn't exist.

That meant I didn't have to worry about hooking up to any e-commerce, so it didn't need you know, a vast amount of security or a, it wasn't, we weren't dealing with purchases of fine wine that costs a thousand pounds, there was no money changing hands on here.  Payment providers get nervous if you try and sell wine, products that don't exist.  I think on-line selling regulations means you have to be able to return it within about six weeks and if it hasn't arrived yet then that is difficult.

It all worked pretty well.  I managed to reuse some of the modules as part of the main site which is great.

Yes, I proved to the company that Django was something that we could be using and he was happy, I was happy.  There was no one else to argue with, just me.  So, really straightforward.

Okay.  So on to the Django.  This is the fun bit.  My favourite part of the stack, this is why I am here.  I mean I love all this stuff and you know, creating like a nice database model that actually reflects all the complexities of the wine industry, it can, it is very complex trust me.

Even getting down into the nub of the Python coding and fixing bugs, I love all this stuff.  As you can see, I love writing stupid snippets of code.  I love the open-source nature of it.  So if something doesn't quite fit for my use, I can actually just, or even if I don't understand something, I can go in and look at the source code, that is something I could not do with.net, with Django, open up the file and say, great, here is a function, I can go in and see what it is doing.

Also custom template tags as well.  This is something I have picked out, out of the huge amount of the things that I like about Django.  Throughout the e-commerce site was having to use currency exchange rates because we sell wine all over the world and having to translate things into Hong Kong dollars, being able to use custom template tags and apply it to the exchange rates, it was so useful, adjust it to my needs.

I can lose track of things sometimes, I, it is a large complex site now and I really, it is really difficult.  It is hard trying to keep track of things when it is just on your own, I, I do run into trouble and thankfully, the debug tool bar come to my rescue.  One of the things about working on your own, you don't know that tools like this are out there half the time.  There is no one to tell you, oh great, if you are having trouble with knowing what template you are using, why not use the debug tool bar, you can just put it into your settings file and that is fine.  I didn't know it was there, until I was Googling trying to find out how do I know what template I am on?  The debug tool bar, when I first started to use it, it was difficult because I was new to Python and Django and it kept crashing.  There was some incompatibilities with some other plug ins I was using.  I almost put it to one side and then forgot about it almost.  Then again I came across a bit of code, a few months later.  I am stuck.  I can't understand why all these my queries are mounting up and up and I need to see what is going on under the hood.  I remembered the debug tool bar, there was a update and it stopped crashing, now I use it all the time.  Couldn't be without it.

Python code, I really get enthusiastic about writing a clean efficient views and queries.  I also like cleaning all the things in my forms.

Being a sole developer, only have to merge code with myself, if I am coming across code I wrote six months ago, it almost feels like I am a different person, so I write jokes to myself, so I can read them six months later.

Libraries I want, I don't have to worry, I can try it if I don't like it, I can get rid of it.  One thing I really did like was the tumbler, I know that the Django tutorial has a Blog and I did not use a Blog app in my website, even though we have a Blog.  I used the tumbler API because it was easier for our wines, our sales people, out in France tasting from the barrel, yes, this one tastes good, I will take a picture and put it on the Blog, easier for them to do that, rather than log into the Django site that I had created and mess around with the admin.  With tumbler, they could log in and up load the photo.  It worked really well for us.

So, as well as being enthusiastic, I can get carried away.  There is steam coming off the keyboard there.  That means sometimes I can reinvent the wheel, as a sole developer then I don't know sometimes that these libraries are out there.  Same with the debug tool bar, I just, there could be, I could be spending hours and hours on writing a piece of code.  Someone has already done it.  I never know.  Yes, I don't even realise the wheel exists, I have to say, I didn't even know that this conference existed until one direction had to make a move! (LAUGHTER).

One of my friends tweeted saying, friends tweeted saying, check out what one direction have done now, they are up to their own tricks.  Django! I work with Django! maybe I should go?  Say thank you to Daniele and all the organising team who encouraged people like me first time speakers to come and speak here, it has been great.  I really enjoyed myself.

So, finally with the on the Python side of things, I don't get any technical feedback, I have no idea whether I am programming well.  My code could be amazing, could be awesome but I have got no idea, I know one of the talks on Sunday was about imposter syndrome, overcoming the feeling that you don't know what you are doing, that everyone else knows what they are doing a lot better than you do.  I really don't know, I mean, not only do I work on my own at the moment.  I have always developed on my own, never worked in a team of developers.  It has been really a real challenge to actually try and be confident in my code and make sure that the company is confident in me and I am happy to deploy this code and make sure that our website is going to run okay.  Yes, I think we have done all right so it has been a learning process.

So, I am going the quickly run through my advantages and disadvantages with testing and bug fixing.  If I don't like something, I can ditch it or better yet, convince my boss we didn't need the feature in the first place.

There is no need for a complex ticketing system, people can shout across the office to me and say it is not working or better send me an e-mail.  Everyone knows to report the bug to me.  Things don't usually get messed because I can keep them in one place, I can decide whether something is important and how to prioritise it.

I can actually deploy small fixes quickly, if I know it is a typo in a template, I know it is not dependent on other things, I can get in there and do it in half an hour, I don't have to worry about the complex methods you are doing, when you have to make sure that everyone on the team is okay.

But, testing.  I don't do enough of it.  I am sure no one does enough of it but, we work in a high pressure company.  Things need to be done yesterday and when I have to turn around a fix in twenty minutes that means that testing is going to suffer and it always does.  I need it more than ever though, if I am trying to deploy something quickly, then it is going to you know, I need a robust testing system to make sure that you know, I can be confident in that deploy.

I keep, definitely don't have any of these in my code at all.  Comments saying to do, fix this later.

I am sure none of you do either?  But yes, moving swiftly on.

Thinking out loud as well.  When I am trying to solve a bug, then I try to think out loud at people and try and put the problem into a sentence and see if that makes anymore sense to me, my poor nontechnical colleagues have been on the receiving end of this and nodding and smiling.  Yes, I lost you at Django, sorry, but it helps me to even say it out loud.

But, sometimes I just get really stuck.  So stuck overflow it is.

Obviously it is very frustrating when I am sure again, most of you have this problem where you type in the exact question and only it is there but no one has answered it.  Or you find it is actually you that answer that question, that ask the question six months ago and still no one answered it.

So I will move on to another leg now.  That was my Django bit mostly done.

In terms of design and user experience that is where my background really is.  I have been designed websites since the late 90's, lots of marquee text, terrible under construction gif's, you get the idea, having the front end experience helped me in terms of saving time.  I know what works and doesn't work in terms of html and J query and, so I didn't have to learn new things, obviously I did learn new things but didn't have to start from scratch there.

And one aspect of working for a small company, we really have a good idea of who our client base is.  We know that well, they are fine wine lovers, usually male, over 40 and a large proportion in China and Hong Kong, so we know they are quite tech savvy, we don't have to support IE seven I was pleased when I learned that.  I do have to support mobile responsiveness.  All the time I was saving not having to worry about IE seven I put into making sure that it works on tablet and mobile.

So all those, trying to save time, on the design side of things.  It is completely scuppered if you are having to use photo shop.  If you have got your development server, men cached, four different browsers Skype, Spotify and photo shop running on one poor little lap top things start grinding to a halt.  I have wasted more time rebooting to try and get photo shop to work, than I have fixing bugs I think.  So the solution I found to this is to make friends with your Mac using print designer and be able to be able to send files home and hopefully they can sort it out.  I am sure some of you are thinking, why use photo shop?  I don't know, never used gimp, been using it for the last ten years and I know I can use it quickly and well, hopefully quickly, I know where all the commands are, I know what I can and can't do.  Whereas gimp I would have to start again and learn those things, I don't have time to do it.  It will be great to use all these nifty bits of software, but this is what I have got and this is the tool I am using, and everyone has to deal with it.

Okay so my other leg is content.  There is no point in having an empty website.  So, one of the main challenges I had to deal with, importing our stock data, all of our wines from our CRM built in MS windows sequel server, I was running my sequel and I had to support ETFA characters, wine names have circumflexes and accents in them.  Translated into Chinese as well for our Asian market.

How did I fix it?  I can't remember.

I don't know, I can't remember, something to do with OCDV drivers, I don't know, it was two years, I know where the file is I can't keep all the things in my head, in doing the full stack, I don't know.  I mean I spend most of my time concentrating on Django, that is the bit I love most.

I do not enjoy dealing with ODBC drivers so I just write myself a note, I know where the note is.  If I need to change it I have to look it up so this will remain a mystery to you for ever I'm afraid.

As well as the actual typing of data BTFA and things it's the actual wine data itself causes massive problems.

OK burgundy, any burgundy fans? if you are a burgundy fan you will be able to see that 3 of these are actually referred to the same wine but one of them costs half the price of the others.  So who thinks it is A?  Hands up if you think A is the different one the cheap one?  OK how about B?  Yes, some hands of course.  C?  Yes and more people there and D?  OK most people going for D.

It's actually B because it doesn't have the Chaumes vineyard there, my knowledge was nowhere near enough good enough to deal with this information and I basically had to get some help.

So these dogs do not have burgundy in their barrels but basically I didn't have time to learn a vast amount of wine knowledge so I got some help, I got an assistant who had some wine knowledge.  While they weren't very technical, they could use the Django CMS.  So I used, customised the admin as much as I could to try and help them out.

Also with the Chinese translations, my Chinese is worse than my Welsh so I could outsource those and I made use of Django's i18n ...

NEW SPEAKER:	 Internationalisation.

KAT STEVENS:	 OK.  As well as the fun stuff I have to do boring things, reporting, analytics, invoices, where are the customers coming from, is the site making a profit, is it paying for itself.  I have to do all this custom management as well as super tedium stuff renewing domain names, liaising with ad agencies, terms and conditions, being on hold to Barclays trying to explain to them no we're not going to sell wine futures, you don't have to Murray about these 6 week on-line selling regulations, I had to sign a bit of paper promising I would not sell {inaudible} premier on free web-sites and SYS admin my least favourite aspect terrifying for me I would have outsourced it if I could have done.  It is something that fills me with horror because I just don't know enough to really be confident in what I'm doing here so I just have to do my best.  In terms of security, well there is just me really so I don't have to worry about complex user permissions.  And I could do a quick response when the heart bleed bug came up.  I saw it come up on twitter and raced into fix it to try and figure out what was going wrong and then 24 hours later my hosting company sent me a nice email saying you should really fix heart bleed yeah.  And a week later my boss comes racing through the door saying have you done anything about heart bleed?  !  Yeah don't worry it's fine ...

Some problems are just beyond me and we are going to get some help try and outsource this and make sure everything is up-to-date and secure.

So our octopus sushi leg.  Basically working in a small company, you know there is so much unpredictability that goes on, for example I've had to proof a 70 page cook book with matching luxury wines as a gift for our client base.  I had a 6 month secondment where one of my colleagues left the company and I had to do email marketing for 6 month's that was fun.  I am at the mercy of third parties especially when Barclays are hanging around for 6 months putting a block on our development time line.  I also made an HTML 5 roulette wheel for my boss with wine names and things on for an event he wanted to do and unfortunately I don't think this is going to rotate very well - hang on is it going to go?  No, that's it, it keeps landing on drunk so there we are {laughter}.

So to summarise, I have learned so much doing this project over the last 4 years or so especially how to research stuff how to look up things on stack overflow and make sure using the right name for everything and I discovered I really love Django and it's something I really want to do more of in the future.  Definitely put jokes to yourself in your comment.  I recommend that rather than song lyrics because it's what is this?  I didn't remember at all.  And if there is a problem I'm working on my own so I can reprioritise very quickly and easily.

However, things do get missed especially testing, it's definitely something I need to work on but it's always going to be difficult.

Holiday I haven't had a proper holiday in about 2 years.  Generally being not on call but if the web-site does go down any time of day then I'm going to get a text message from somebody.  And I've got no time to really get an in depth knowledge.  I've got a broad overview but apart from Django I've been really trying hard to learn more about it, I don't consider myself an expert in anything.

Also I've got poor attention span, having to flit between all these aspects of my job so it's amazing I'm still here rather than wondered off out the door somewhere.  Also the Barclays hold music is one of the worst things I've ever encountered!  {Laughter}.

So I would like to give a big thanks to my friend Pippa who drew the octopus for me and she's at Pippa Alice Art.  Anyone have any questions?  {Applause}.

DANIELE PROCIDA:	 Thank you, that was absolutely brilliant and if I'm allowed first go at the questions I just want to say even down to the dates your career path seems to have mirrored mine yet you got away more lightly because I had to support 6 up until a few months ago at Cardiff university, that's not a question but thank you and I hope we see more of you in the community because we need people like you - any more questions?

NEW SPEAKER:	 That all sounded very familiar.  Just one question, how do you make your boss less worried about you being run over by the proverbial bus.

KAT STEVENS:	 I have very good disaster recovery plan in place which involves hiring my identical twin.  Yep ... {laughter}.  No, it is a problem, and basically this is a problem I encounter right now because I'm going to leave the company and start a new job in a couple of weeks and they've been desperately trying to hire someone to replace me and instead they've actually decided to outsource the entire thing to an agency who's got a couple of members of the team who can take on the different roles.

NEW SPEAKER:	 2 questions.  One, you said you were working on a template tag that does dynamic pricing based on world markets and stuff and I'm wondering if you ever open source these kinds of fringe bits you write and could you put it on get up so the rest of us could check it out?

KAT STEVENS:	 I'd love to I'd have to run it by my legal team at the company to make sure it's not covered by -

NEW SPEAKER:	 Don't tell them just put it out!

KAT STEVENS:	 It's definitely something I'd look at because it was a lot of fun to do and would love to contribute something like that.

NEW SPEAKER:	 There was a couple of times in your talk where you explained something you had a tough time and I was like oh I know how she could work on that but you don't have your fitter up there so I can't tweet you.

KAT STEVENS:	 It's on the first slide, Kat Stevens.

NEW SPEAKER:	 Hi, thanks a lot for your talk a lot of that sounded familiar.  I didn't have so much a question as a sort of a feedback on some of the things you touched on.  Personally I'm in a very similar situation where it's very much a one person show and I'd really encourage you to invest interesting because that is sort of what's kept me sane for the past 2 years knowing I can roll-out something in production and it's not all going to explode in my face.

KAT STEVENS:	 Absolutely, I mean testing is something I've definitely done more and more as the years have gone, as the project has progressed just because the project has become more and more unruly and like I said I have a poor memory and I can't remember what affects everything else so having like a strong testing framework is essential.

NEW SPEAKER:	 Hi, that was a great talk.  My question is your job sounds incredibly stressful and you said yourself that you are scared of the whole SYS admin thing.  And I just wondered what was your background and what made you think when you applied for the job, oh, this is something I can actually do?

KAT STEVENS:	 Well I looked at the job spec and it said we're looking for a web designer for a wine company so I thought internet and booze those are my 2 favourite things {laughter} and I didn't really spec out what it was and I wasn't working at the time so I thought I'll go for it and see what it is and the company was really exciting and the people were really great so I thought well, it seems like a really good opportunity for me to explore this and be able to see, do the full stack and see what I enjoyed doing, find out what my strengths and weaknesses were.  In terms of background I have a computer science degree but I stopped programming pretty much as soon after I finished it because I got disillusioned with the whole theoretical side of it and wanted to do something practical and doing web-sites was much more appealing to me than writing furrier transforms and things like that so as you are doing web design and have a chance to have a free rein to do whatever I want was a great opportunity.  I want to say thanks to my boss for being so supportive for the last 4 years.

DANIELE PROCIDA:	 Thank you very much Kat.  {Applause}.
