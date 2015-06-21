===================================================
Xavier Dutreilh: Web accessibility is not an option
===================================================

VINCE:	 Our next speaker is Xavier who started using Django 2 years ago {inaudible} opportunity to get involved with Django.  Talking about web accessibility.  {Applause}.

XAVIER DUTREILH:	 So, hi everybody.  My name is Xavier Dutreilh; I am going to talk about web accessibility during the next 30 minutes.  I would like to say 2 things before starting my talk.  The first one is I really appreciate different action on hearing are doing for the conference because otherwise I would not be able to understand anything of almost all talks.

The second thing I would like to ask you is much more a favour than anything else.  So at the end of the talk if you want to ask some questions, please, try to be clear and simple so I can read them here.  I am very sure that some of you have some questions to ask me.  Some of you have been very honest yesterday about issues in life.  And I think some of you may have some questions about accessibility.

Accessibility or web accessibility, we can ask both questions.

So, first of all I would like to clarify why web accessibility is not an option.

We are here at the conference on Django.  It's all related about the web.  So, is anyone in this room ever considered life without the web?  And all the smaller opportunities provided to you?

Before this talk I never really thought about this too so it's not surprising you may not have think about it.

But still even if you've never thought about what the web did for you and what happened in your life, it did, you may have obtained work, studied, you may have learned about it, maybe make friends, from what I see the Django community is very friendly so people make friends thanks to the web.

May be today you do not see any issue with the web, you use the web any day and it's fine and may be for you it's perfect but this issue exists for people and the issues are very real.  So I make this talk to explain to you what are these problems and what you can do to solve them.

One of the biggest reason why some people have real problems using web-site is because we do not design people for people in general - we design web-sites for non-disabled people.  So maybe you are shocked by such statement but it is what it is.  We do not include everyone when we design and build web-site and exclude a large part of our community and the world in general.

In particular, we exclude people with disabilities.  So, may be the world of disability is for you very fuzzy but with this talk I think you will get a clear idea of what it is.

So, let me tell you a few things about web accessibility.

So, it starts with an inclusive practice of removing barriers for people with disabilities.  In fact, we know that many web-site we'll be on every day may be difficult to use if we have some kind of impairment.  This issue, this kind of issue keep all people with disability apart, on the side and they cannot use it.  And such practice is very important because if you have some or no disability you get access to information on the web-sites and functionality.  It is not linked to the kind of disability you may have.

So, disability may be hard to understand if you never read something about it document yourself about or impairment or disability.

So disability is the consequence of an impairment.  And you may have one since your birth or you can get some disability later.

So if you get one from birth you can do anything but sometimes when it is acquired later, it, you can acquire the disability because of an accident, of genetic condition that start later in your live and affects your abilities.

Also can be progressive so it means that not all impairments have the same effect on you when you are five years old or ten or 20.  Sometimes in only a few weeks or a few months from being fully able to being disabled.

Often we split all this impairment in to four main categories we can see other categories but it is much more important to, to focus on this one to start.

So, visual impairment is what you see with your eyes, you can be blind, so have issues with light and perceiving, understanding what you see.  Blindness is not as we may think when we don't know what it is, blindness is not when you do not see at all.  It is when you cannot see in fact when you go to a doctor and you test your eyes and what you can see, if your view is rated below a certain threshold you are considered blind.  Even if you can still see something.

Low vision, or also called poor vision is something that a lot of you have in some way, if you wear glasses.  So a lot of this people in this room, never consider yourself being someone with disabilities?  Now you know you are.

Colour blindness is when you have some trouble making differences between colours, it is not always about making a difference between red and green colours, it is also an issue with blue colours sometimes, completely different.  It is not only about making difference between the red and green colour.  Sometimes a few people have issues with colour and they have issues with red and green colours and blue colours.

Impairment maybe also hearing and most of the time it falls under two categories; deafness and hard of hearing which is the category I am following.

When it comes to motor, I think most of you imagine someone in a wheelchair and that cannot move or walk by yourself, it is much more general, people with genetic condition that makes them having a lot of trouble to move or to coordinate the movement following this category, so that is why we call a limited dexterity.  It is also a loss of limbs when you have an accident and you lose your arm or two and you cannot use a computer as you used to before.

Cognitive.  It is not visible at first but some of us have issues about learning things.  For instance, remembering the things on websites.  This is two possibilities, this is category is very large and they cannot learn everything.

From there what can we do to make accessibility?

The first thing is simple.  Every time you put an image on the website try to describe it because for instance people who rely on screen readers to read a page, won't get any information.  The screen readers, scans the image up and then nobody might be able to understand what it is on it.

So, this example is very bad.  So, as you can see the name, it should be in front of me.  So, if we try to add a description or may use something like image of Xavier, which is also bad, better to produce this example, we add in description but it is bad because it is a lot of, a lot of redundant information, in fact, one way to describe as, there is an image, there is an image of Xavier, if you never use the screen reader on the website, you may not know, but every time you add a lot of text it becomes longer for people to read the page.

Before this talk I tried to do a screen, voice over which are still on macro six ...

To give you an idea of how long, if you put too much text on the website, it can make difficult for people to follow you and to browse your site.

So this one example is short.  It is clean but tells what it should be.

What I do on the photo is important.  You have to describe it.  Because otherwise it is, there is no possibility that these people, the people who use this screen reader can understand what is on it.  So only if it is important you have to specify the action on the photo.

The second, to use html but in a good way, so you have to stick with standards and structure your information.  So some of you write documentation on a daily basis, so they are used to a structure of writing but it is not always the case with the web.  To give you an example, this is an example from a oversimplified on the website.  You would use structure all your page as such.  So if you have header in the page and some part of the navigation you would use appropriate types like header and not choose what a lot of people use in their developments or in fact have no semantic at all.  So every time a screen reader it does not know if it is a header, navigation or the main content of the page.  It makes the things a lot harder.

If you write at all, you may try to use some kind of example.  You have a data which h1 a subtitle for h2 ... screen readers pay a lot overflow clone attention to this type of thing, every time on the list for instance they say, nine elements and element one and it is, element two reads the text and so on.

Advice and guideline, build proper tables, so often when we build tables, we put data without presentation to the name of the elements.  As you can see here, for screen readers it is very important because it helps when it reads the table to make the distinction between the header and the column in the table.

The fourth advice is about making proper validation from validation and error recovery.

Most of you use Django and most likely only Django, so this issue is not less, not sorry presented in our web apps, much more prevalent when we do a lot of java script in the front end, as you can see here, what is important is that we have a field name input and a label which is, which explains what it is to field before that.  The label is attached to the field by filling the attribute, the form attribute, so when you say name here it refers to the input with the right name.

At this level it helps a lot of assistive technologies to make a matching, allowing people to fill forms and it is also good practice to use all attributes you may have in html file because if the field is required and for some reason the person is not able to fill out the web browser will help the user to fill in properly and then instead if we do not make, if we do not fill the, we do not add the attribute, the user may submit the form and then get on without understanding what is, what.

Also this is very important, not also for accessibility but also for search engine optimisation, every time you put a link on any page, try to be sure it is clear.  If you have these kind of thing where you name, you name this link as clear, click here, it is very problematic because a lot of people may not understand what it does.  There are a lot of assistive technology which scan the page, extract all links and leads them to the user.  If you have a lot of click here link in your page, once they are presented to the user, which is any, no links, no links which are named, click here will be understandable by the user.

So if you are, the link which moves the user to the article page, just name it article.  But even better, something like see all articles.  So the user can understands where you want to move him.

This is guideline is offering ... I think it is just confirms what it means, you should have to every time you put some kind of audio or visual media on the website, you should put transcript.  Transcript is what is here on the screen, tells you what the speaker says and eventually some information you may have missed, if you have a hearing impairment like people when they laugh and when applause, caption is not about providing subtitles to the speaker and the subtitles are often displayed at the moment the speaker says the words.

So, I don't think you need a clear example since we have one from the very beginning of this conference, but if you want the slide of the talk or the video on-line, you may want to watch this talk from, this is one of the keynote and suddenly not so much talk from Py Con that contain subtitles, I hope following, the videos will contain everything.

After video and audio, you should ensure like I did for my slide to, if you are unsure, make sure that all of your binary files should be accessible, to do that, most of you probably use some kind of some kind of software like Office or ... to build binary files you just need to use the same guidelines, just need to structure everything, for titles and put things where it would be, it would make things a lot easier, but if you can use just the web for explaining yourself, use the web, because screen reader have made a lot of around the time with web pages not always the case that where all the binary files.

This one, again, it is very important for people who have a lot of issues, a lot of motor issues.  Sometimes we have very complex pages with a lot of stuff and we want to help people to move between part of the page really easily.  One example is from one link most of you never saw on any website but even though the, you have this like kind of link.  This is, it is this one.  In fact, at the very beginning of your document you have most of the time a non-visible link which allow you to skip to the main content of the page.  So you do not have to scroll to the page to go to where you need to go to get access.

You can do this kind of quick link for everything if your page, for instance, you want to switch directly to each part.

This one is about not relying on colour to convey information.  Most of the time since I started to work with back end developers they would use things like label to convey information but as with the classes imply, it is labels which should be boxed with a colour and not extend it.  So if you have issues to see the colour, you may not know and understand what it means.  A lot of e-mail clients a few years ago were doing that.  So labelling all the e-mails, if you cannot see the colour, you don't know what categories.

Simple information, put some label, so if you have trouble to see colours you may, you just may put the text in place.

This one is probably hardest guidelines to apply.  Because even if you master one language, if all of you, I assume all of you, as native language in which you can express yourself probably easily, but writing for the web is often very complicated.  Sometimes to explain things we use a lot of complex things and we often, sometimes people have to understand what we call nonliteral communication.  You have to be explicit about what you say and you will not have to expect people to have all the information we have to give you an easy example to understand this.

If you learn a new language and you talk to someone from the country that choose in language you may not understand the expression, you may not have the same culture in order to understand this.

Sometimes it is also good things if you cannot find someone around you or, I don't know, if you cannot find someone who has some with this issue, you maybe work with someone who is mastering the language, ask them for help.

One advice when you have to do this, you can also try to in fact a lot of this work, I don't know a lot of this word before making this talk, so you have to be explicit, clear, so if you think some of the talk you have heard in the past few days we are expressing and clear about what it is I want to tell you, it means a lot of people have spent a lot of time on it to make it clear.  It should be clear and positive, it means that, write explicit clear and positive, there is two way to have sentences, for instance, if I write a positive sentences I would say, I eat at, I ate at the city museum yesterday, it was really good.

So instead of if I will not choose a positive form I would say, yesterday, the city museum has offered me to eat free.

So this one connective issues, much more about visual issues, the first thing is to use clear fonts.  Some people for instance live with a dyslexia and much more the font we use on presentation website are not readable by some.

So, if you try to make your web-site accessible, you may want to of course build your pages with one set of fonts but also provide fall backs because there are fonts that have been made a long time for people with some issues with reading, a font we use most of the time.

Also use relative units.  If someone may have some issues accessing web-site need to zoom in most of the time if you use pixels to size everything when you zoom in it become a mess and when using relative units make sure when you zoom in on the page everything stay at the similar position.

And strong contrast, well you see the slide, you have to be sure the colour of the text is very different from the colour of the background and it's not magical and a lot of web-site have been made on this and if you need a tool to help you choose colours I will provide you with one at the end of the talk.

And this one is something that has been removed from HTML and it should of course - it's not about toning anything, it's much more about you don't want your friends if you develop a web-site - you don't want your friends to make some sort of epilepsy quizzes during the - but it happens.  Some of you are smiling but, yes, for instance we often say that sweep flushes in one second may start epileptic crisis so you don't want your user to have some kind of episode on viewing your web-site and also avoid to move things on the page here because if people who have some issues with co-ordination when things they move will have hard time on the web-site and will not spend a lot of time reading things.  But OK the thing was here, now it's here, and will spend much more time in other things.

This one is no simple thing to fix this issue.  Java script is accessible to almost all web browser, most work just above screen browser so if you think Java script does not work with a web browser or screen reader especially with a screen reader you are wrong.  10 years ago it was not the case but today it is.  I think 98 per cent in studies it has been shown 98 per cent of screen adjust users have Java script so you can make Java script application in top of your Django application.

The only thing you'll need to be careful is that not overlook people using keyboard over mouse.  So if you have motor disabilities or if you cannot use your arms or do not have hands at all, you won't use a mouse and most of the time people when they built Java script encryption over {inaudible} for instance they will pint all {inaudible} over mouse and they have no click so may be your app won't work at all.  You have to be careful about that much of the time the key board part is still supported so you can stick with key board.

And the last one, guidelines.  It's very similar to the guidelines about tutoring content.  If you use HTML 5 do not put HTML 4 element into HTML 5 because you'll have deprecated tax and it will be a complete mess.  Avoid in line styles, put your access into complete files.  Do not miss some attributes for example images, the other attribute is not an issue - {inaudible} it makes your pages very inaccessible.

So, from there, if you at least implement those guidelines on the web-site most of the people will be able to board the web-site you will just start to exclude a large part of our community and people in general.  And after that I would like you to spend sometime to first document yourself about impairment and disability.  If you're not very - I think for a lot of you it's not very clear what it means in reality so you have to document yourself.  I can't talk about it during presentation but you have to document yourself.  This subject is very, very broad so you have to spend some time.

You also have to talk with people who have some kind of disabilities.  You cannot just talk to one person.  You have to talk do lot to understand what it means.  Because not only one way to live with disabilities and if you want to improve your web-site you have to talk them and listen to them.  It's very frequent in our community to hear from people who have no disabilities and asking people with disability to making more effort include themselves.

They do they already do, so may be at the moment, maybe you should be.

Once you get a lot more fine and comfortable with the disabilities you should also read some guidelines like WC AG, but if you understood some of the things I said you are done with WCAG, the other ones the 2 other ones ATAG and UUAG are about software that allows you to write a page.  And there we are come up last once you must ARIA and it's very useful if you build {inaudible} - {inaudible} WCAG is sufficient.

Also I think a lot of you haven't tried, haven't yet any kind of accessibility tools and most of you have a smart phone or computer at your disposal day or night so if you have some recent computer with windows or I don't know 1, 2, any other Linux application activate things like the screen reader the colour blind tools and everything else, it's very important that you try them, may be at some point it will disturb you because it will change how you look at web-site and how you use them to interact with them.

But you should have to try them because if you never try one you may not fully understand what it means to design accessibilities on your web-site.

To get things here a lot of people have started organisation like web aim and they build a web-site which can call your web-site and make you some things that tell you which things work and what things do not work so we can tell you if you use tone contrast and if you have issues with contrast it can tell you why and pose some solution.  It applies to the same thing for the links and in fact most of the guidelines I gave earlier is covered by this application.  So, just try it.  It's wonderful.

And you can try it on the Django web-site.

Also if you don't like using web-site and prefer some kind of extension for your web browser you can use this accessibility tools.  Google provide a lot of tools including this one to help you in this.

I don't know if that is something similar to fire fox but my view you should try this one with chrome.

And finally once you master everything or at least a bit of it you should provide your skills to any accessibility organisation that you may have met before or you may meet today because most of the time they like the technical skills need to make great application and you can provide them with these kind of skills.

So in conclusion, web accessibility is not an option.  We may think so but it's not.  And none of us are optional.  So we should get back to work and fix this.

{Applause}.

VINCE:	 Thank you Xavier.  If we have any questions could you make your way to the microphone please.

RUSSELL KEITH-MAGEE:	 Thank you Xavier.  Just something you said at the end there.  Did you say that the Django web-site does not have good accessibility at the moment?

XAVIER DUTREILH:	 In general if you use screen reader for instance not that bad, some areas for improvement and if you want we can talk about that after that but for screen reader it is really good.  It is longer to pass and to read so maybe there is some areas for improvement there because some pages were really long, but I think, yes, on the colours, yes, the colours are really - you may not see the issue between the text in white and the green for instance but - so, maybe you do not need to make, to rebuild all the web-site in fact, you can keep your current CSS on the web-site and provide a link which - off CSS which applies some kind of stronger contrast.  This is something we can do.

RUSSELL KEITH-MAGEE:	 Absolutely.  If you are here for the sprints we'd love as much assistance as possible to improve any accessibility problem.

XAVIER DUTREILH:	 We should do it.

NEW SPEAKER:	 Fantastic talk so thank you very much.  I just had a quick add on actually as a person with a visual impairment myself, I don't use any specific tools, but what I find sometimes is the most useful thing is for developers and designers to get out of my way.  The best example I have of that is using meta tags to lock the zoom on the view port because that means that when you are trying to pinch and zoom on a web page in order to read text, that optional setting that designers like to set means that you can't zoom in any more.  So I think there is a lot that you've said which is fantastic about using tools that are available, but also some of it is about not setting options which get in peoples way so I just had that to add but thank you very much.

XAVIER DUTREILH:	 Thank you.

NEW SPEAKER:	 Thanks for the very informative talk I was wondering could you recommend a command line that we could run like unit tests that would validate accessibility.  Could you recommend one?

XAVIER DUTREILH:	 I do not know any kind of tool.  I think may be there would be something to build - in fact maybe we can have some library built up on top of, - for instance if we want to make some Django forms more accessible and may be build something above the Django forms to apply accessibility more easily but at this moment, no, I do not know any kind of tools you can run from the common line -

NEW SPEAKER:	 May be a good sprint project?  OK thanks.

NEW SPEAKER:	 Thank you for your talk.  A quick question, from your experience do you think building 2 versions of the web-site one with accessibility and one for normal viewing is better than having the same like version of the web-site respond depending on the accessibility of the user accessing the web-site?

XAVIER DUTREILH:	 From my own experience and a lot of organisations - accessibility organisation - I think you should deal with the same version and should not put too much like just stick to what I said to Russell before I think one version in fact, yes, and not building 2 version because you want to provide the same kind of information, sometimes you may want to mark some information on the page as optional so it may be skipped by some for instance screen reader but no it is easier and from a dev viewpoint it is important not to have 2 version to maintain.  But this one is acceptable because there is no value added to provide 2 version, 2 different version.

NEW SPEAKER:	 Thank you.

NEW SPEAKER:	 Thank you.  I have inherited a design have you project and I have 2 questions.  Where does the responsibility of the designer come in in designing and picking up proper colour scheme?  How would you work in accessibility features in a legacy project or in a legacy code base?

XAVIER DUTREILH:	 So the designer is really responsible.  In fact most of the time most designer I worked with in the past are not trained in accessibility so they use funny colours because they like contrasting of colours.  There are a lot of tools like wave I suggested before that can help you to, well, you choose one colour or a set of colour that you like and you want to use for design and then after that you can just check that for instance if it's about contrast that the whole contrast are still varied.  After that if your question about colours is about dealing with colour blindness, I think you should make your colours optional. In fact you can still use red or blue or whatever colour you want but it should not be important to use your web-site so I don't know what kind of computer you use or operating system you have on it but most operating systems allow you to switch to a grain mode to see how your design your web-site will look like: about the second question which -

NEW SPEAKER:	 Legacy code basis, working in it -

XAVIER DUTREILH:	 Oh yes so on new project it's very easy because you can just - at the moment you design your web-site, includes all this stuff and all guidelines.  On existing code base it's very hard.  I suggest you may be to start using one or 2 guidelines for instance describing non text content may be in {inaudible} for instance using retinue needs things like that may be hard because your designers not been designed for that.  I would suggest to take one guideline at a time and apply to your web-site. It is really hard because most websites when they have not been designed for accessibility are hard to integrate.

FROM THE FLOOR:  Thank you.

FROM THE FLOOR:  Question on colour blindness, could you recommend specific tools for validating our presentation slides web based or pdf's, so validate them on colour blindness, on all the types that exist?

XAVIER DUTREILH:  I mentioned a few slides ago.  This is this slide, mention WAVE and mention colour contrast checker, wrote a few years ago and you can, you can use it in fact to validate your presentation.  Before this presentations on some of my slide I was used to use some different colours like on ... because of this tools I make some adjustment to ensure that if some people in this room had some issues with colour, they wouldn't be able to read.  So.

FROM THE FLOOR:  I have just tried ...

XAVIER DUTREILH:  If you have sometimes ...

FROM THE FLOOR:  I think WAVE is really good if you have web based slides, what about pdf's and images?

XAVIER DUTREILH:  If it is just about colour, if it is just about colour, you can use WAVE and because you can provide a colour, in fact there is a colours as specified in the tool I use for building my slide can be taken and injected into.  Because you have fields to type, colour code you use and assert you can still validate.  It is still a lot manual, you can have to take the colours from the tools and import to the tools but yes.  It is yes, about colours it is very complicated.

FROM THE FLOOR:  Thank you.

(APPLAUSE).
