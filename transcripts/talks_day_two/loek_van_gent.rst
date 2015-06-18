==================================================================
Loek Van Gent: True beauty is on the inside, but users are shallow
==================================================================

I think we're back on time now so here is Loek Van Gent from the one per cent club.

LOEK VAN GENT:	 We'll be talking about some of the things you heard earlier today just in Aaron's talk and David's talk but hopefully I can be of service to the ones that were thinking that's really cool stuff, but that's not for me.  Hopefully I can convince you that part of things they were talking about can apply to any of you.  I don't know, I reckon most of you would be back end developers.  Oh, a first.  Are you still awake?  Who is asleep?  Hi, quite some, who is awake, 2 hands yeah that's better!

The last talk but we should get pumped up for the lightening talks after right?

So, I'm going to be talking about and the title is true beauty is on the inside but your users are shallow.  That should be a familiar - should sound familiar.

I want to tell you something about writing about front end code.  So first about me this is me away from key board, I have done PHP for many, many years before as have others of you I think so too.  3 years I been riding ponies.  Proper multi-Dutch Django association.  If you are not a member yet and are from the Netherlands they just lowered the annual membership fee by 10 euros and it's free now so you should sign up.  {Laughter}.

And I work for 1 per cent club.  1 per cent club has been remembered several times yesterday.  We're not the richest people in America.  We do run a platform for small projects that have a social impact.  So far we're 800 - close to 900 successful projects, very small, couple of a thousand euros just to start for instance to buy solar lights for a village in Nigeria so kids can study when the sun goes down and very small, smart changes that have huge impact.

So, we're doing quite well.  We are changing lots of lives, and doing projects with social impact that's something that also big corporates are interested in doing now and mainly as a corporate social responsibility programme, so now we're selling our web-site to them too and then we can earn some money because from do good crowd filling that we do you can't take money from that.

And so one day our product manager came and say, listen up guys, we've got a really cool idea, let's make a multi-tenant and a white label web-site out of the web-site we have.  At that point, we were running our own web-site and not a web-site for a big company.  And they said 2 web-sites should merge into one and make a multi-tenant.  Interesting stuff of course.  I won't tell too much about it but it was a big refactor we had to do and I only want to show the changes we did - oh no - it's too many changes to talk about it right now.  But I can show you - you can imagine we went from multiple databases to one database with different schemas in it and it worked all very well.  This is what overview with the project looked like.  Then we changed it to look like this.  Minor changes but the good thing is everything worked, people could still do their nations and do wall posts on the project site and even the project manager was really impressed and in big swirling letters he said wow this amazing guys we really love that new design!  Yeah,, {laughter} and that was only 2 per cent of the time we spent on that.  So true beauty is on the inside but your product manager is shallow {laughter} sounds familiar?

So what's all this fuzz about front end?

We have to go a little back in time.  Second reference to that movie I think.  OK.

Web-sites something like this.  This is the first web-site.  You all should recognise that right?

Anyone could put a year on this?

NEW SPEAKER:	 1996, 7 ... {applause}.

LOEK VAN GENT:	 That's almost good.  This is when the screen shot was taken.  Before that they didn't take a screen shot it's from 1989 but good enough.

So this is what web-site used to look like and this is how mobile phones what mobile phones looked like.

And of course, mobile phones have taken a rise and we're not texting like this anymore we're swiping away and playing games and using the apps and in fact phone cells the interface to mobile apps are so - come so naturally, that they are more easy to use than most web-sites, they're intuitive, they know what the user wants.

And web-sites are starting to lag behind, the traditional web-sites.  Of course you have things like Gmail.  Anyone has this mail in their in box by Baptiste that you really should start filling in your dates for the menus that you want to have?  ... Of course you can't call this a web-site any more.  It's an application.  So, that is clear.

Web-sites, the front end for a web-site is the user facing part of your web-site is very important, but how can we write better front end codes?

Now it's not a live demo but it's a console screen.

Let's create a Django project.  We can use Django admin for that.  Probably everyone did at once when they did the manual or the tutorial and after that narrow down but let's try it.  We're going to create a project named true beauty.  We're going to add an app called heart and a app called spirit.

Let's look at the project layout.

You'll have the main project and your 2 apps down; that's all good.  The templates and the front end doesn't have those bits yet but normally you would place those inside the heart and in the spirit.

Because they're portable and you can take them out and copy and paste them somewhere else, that's traditional may how we Django go noughts think but let's ask Danny and Audrey what they think about it and they say you have to really group your front end code, at least I have to look it up in their newest 2 groups book, 2 scoops has been mentioned before and it has been said you should own that book so that's all clear.  So they say group your front end code, group it in a typical project Django project layout.  You should put your templates and your static files, your Java scripts inside your main project folder.

This is where you are.  This bit is for the front end guys.  That's it right.  But I don't know, how many do full stack or - full stack?  Most of you right?  So, if you have a bigger company then you would hand that over to the front end guys and when we first did this in our company to start a grouping, our front end guys were really happy because they turned crazy every time we did changes in our template and had to {inaudible} all their app folders.

Let's look at how we can further improve that little bit that's really the main front end.

I'm going to just shout out some tools.  Hopefully most of you are already using them or similar one we can discuss about it later if these are the best ones or the other.

So, take Bower, it's very useful to do your requirements instead of having just a base HML where you specify all the Java script you want to include like J query and J query UI, you have dependencies like you have in your Django folder with your requirements file.

If you've ever tried to do CSS coming from the back end you would, yeah, it would still be spaghetti code, you switch to Django from PHP and really happy, but with something like sas or las you can really structure your code that would in the end generate CSS and you would use something like Grunt to run those tasks to create your sas file or minify some templates and you can use NPM tool to install all that so if you do deploy NPM will ensure everyone is in power and run Bower and suddenly everything is magically done.

When I first started with projects, running Django I would just include my J query in my repository which is a bad thing, I hope you all agree.  Yes so you have all these tools to get your front end in shape but it's starting to look like an entire app in your Django project right?

Now you're getting it!

So you have this back end and this front end.  The back end is probably has to deal with some file storage and the database and there is probably a user talking to your front end hopefully.  You need some back and forth communication.

Django server can talk, can perfectly have that data, talk to your front end using Django Rest Framework in Json, that has been - it was in error sock as well of course.  In front end you'll use full tack framework like Ember or Angular or React.

The good thing about splitting those is if you have an API in your server, if your server is just talking API, then you can easily test that and have an integration test.  Of course you can have your unit test on a low level, but you can start writing your back end and you don't have to wait for all those front end as they are tweaking their pixels and can just run off if the functional design is clear, you know what the API should be able to spew out and accept back then you can easily write your test and your back end is done.

And the other way round is the same.  You can start creating your front end, you just use a mock API, and you don't have to wait for all those back enders over complicating things.  You can easily run a demo if they suggest new designs, it's very easy to just change the styles, and you can even deploy the front end separately from the back end unless you have API schema changes of course.

So, what we use it's not our hit thing Aaron was trying to think of.  We use Ember CLI, for our front end, it's just an example how you can use it.  And I'll leave enough time so we can argue if Ember or Angular is better.

Back to your console.  All you do is ember - no we want to create a new application.  It's called good looks because it's on the outside.  Let's go into good looks.  We generate the route that will - Ember starts with the route and then your MPC(?) pattern backing that up and create a smile, that's the 2 apps to talk in Django terms and it would look something like this.  You have your app JS that will spin up your ember server and then all the components that will give you the eyes and the smile and will make your user happy.

If you want to really go wild, you can also use ember serve that will spin up a web server and you can proxy your own API after that and then you - then the API calls will be proxy to your Django server.  And then you have a fully independent front end just like a web app, just like a mobile app, but backed up by your API.

So, summing it up in a few easy steps to hopefully give you a hand to changing your full stack Django web-site into 2 things back in the front end, first thing is love your front end.  It's the only thing you use they get to see.  You don't see the marvellous thing you've done on the back end and the marvellous ways you manage your database and stuff like that.  Group your front end, if you are the only container, Kat where are you?  Then still it is good to have it in clustered in one place.

Use tools to help structure your front end code, if you are not using barrow or NPN or something like that, try it, the same goes for, for instance Ember start using it, try a demo organisers use Angular or React, but forget about Backbone, it used to be popular among the Django developers but that is not the way to go to build it all yourselves.

So that is all from me.

If there is any questions or suggestions please, be welcome.

(APPLAUSE).

FROM THE FLOOR:  Thank you for your talk, that was a really good talk.  I did look into Bower and Grunt and all those lovely looking tools, all my colleagues, I was on a didn't have the internet and the project I am on, the client didn't have the internet on the network we are going to deliver on.  Any advice for trying to use the tools without access to the repositories they will pull from?

LOEK VAN GENT:  So you are talking about an intranet.

FROM THE FLOOR:  Essentially.

LOEK VAN GENT:  I would reckon you could do a stage deploy, so first, make sure step one, build it as you would in a normal life in the world website and then deploy that.  But yes, I am not sure.

FROM THE FLOOR:  Okay thanks.

FROM THE FLOOR:  Hi there, you mentioned about multi-tenanting bit, what package did you use and what problems did you have with it?

LOEK VAN GENT:  Were you we were, we were using Django tenant schema.

FROM THE FLOOR:  I patched that,.

LOEK VAN GENT:  We did the same thing, extended it with useful stuff.  I did send one pull request that I didn't get on.

FROM THE FLOOR:  Maybe I will have a chat with you, thanks.

FROM THE FLOOR:  Thank you very much.  I would like to know if you did try to implement some life with load, so every time you changed your SASS files or java script files automatically the ...

LOEK VAN GENT:  Ember does ... I don't know if you mean that.

FROM THE FLOOR:  You don't use a grant for that?

LOEK VAN GENT:  No, so if you use embassy live, use that as the web server for the front end, that fires up live reloads if you are coding it will reload like the Django server run server can do right?  Is that what you were looking for?

FROM THE FLOOR:  Yes, the way to implement it, Django server with this life will load methodology.

LOEK VAN GENT:  Ember will do the same and I think Angular has started shipping a CLI as well I think.

FROM THE FLOOR:  Thanks.

FROM THE FLOOR:  Hello.  What would you recommend if I would, were to, if I would like to recycle one of the apps in another project?  With front end and all?

LOEK VAN GENT:  Sorry?

FROM THE FLOOR:  If I have Django app and the java and I would like to use it in another project, how would you do that if you can't group it all into one project?

LOEK VAN GENT:  Yes I think it shouldn't be in your projects from the start.  It should be separated out but I think the question you want to ask is, you have this lovely app that is we all use, all these libraries and they do also have templates in them right?  And if you split it yes, then you have this, that Django template stuff going on and you have to rewrite that in your Ember or Angular application right?  Yes.  I don't know.

I understand the problem.  But, yes, the main thing is, how, how can we continue using Django in, now I think we all sense this is happening that we, that web servers will be mainly to pride data and that representation will happen in the browsers.  But, yes, I am, I don't know.  So you can really use your app up and until the API so the API framework.  I think.

FROM THE FLOOR:  Thank you.

FROM THE FLOOR:  It is going to be really quick, I just want to answer the question that has just been asked.

If Ember is your plus Django is your regular stack, ember is component if you want to do an app in Django, you can usually map it to your component in Ember, when you want to have your template with your reusable app, you can pack it as a component and put it in there.

LOEK VAN GENT:  True.

DANIELE PROCIDA:  Thank you very much Loek.

(APPLAUSE).
