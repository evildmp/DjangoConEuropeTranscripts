===============================================================
Žan Anderle: Mistakes and lessons in developing user experience
===============================================================

Our next speaker is Žan.

I am pleased to welcome Žan Anderle who is going the be talking about mistakes and lessons learned, that is a common thing in our field.  So.  (APPLAUSE).

ŽAN ANDERLE:  Thank you for that.  So, hello everyone.  Before I start I would like to get a feel of who is in the room.  So, how many of you here are students?

Okay.  A couple.  How many of you do back end?

Okay most of you.  Front end?

... okay.

Also where you work, does user experience, is user experience something that is taking care of versus something that just happens on the way?  So who works in a company or a place where it is taken care of?

Okay some of you.  About half.

Okay thank you for that.

This talk is mainly about user experience, it is not specific to Django, where I work we use Django, will be happy to talk about that later but it is not going the be a part of this talk.

My name is Žan, I come from Slovenia, I studied maths science and Bachelor Degree in mechanical engineering, I currently work at datafy.it.  I am in charge of user experience.

I don't want to make assumption, let's get that out of the way.  One possible definition, it is basically how a person feels when they are interacting with the system.  In this talk I will be using the term broadly, like sometimes it is better to use usability or user friendliness but we are not going the dwell on that.

So, say you are a developer who has little to no knowledge about user experience or you work in a team where, a team that doesn't have money or time to devote to development of user experience.  What do you do about it?

That is basically what I am here to talk about.  It is what happened to us at datafy.it and it is a start-up.  We managed to do something about it.  Let's have a look at the mistakes made and the lessons learned along the way.

But first let's get some context.

So datafy.it is basically is search engine for business contacts.

You get the country, what you get in return is business contacts.  We are four developers and two sales people and because we are a start-up and a small team, this is what begs the talk rather than as we face this, this issues of not being able to devote a lot of resources to user experience.

So before we got the version of the app you saw on the slide before, we had bunch of versions before that.  We started with an app in command line and the first public interfacing app was this piece over here.  It was very complicated.  I had tonnes of features that shouldn't be there, yes, it was really complicated.  Complicated to maintain, difficult to explain how it works.  So needless to say, the user experience from that first version to today changed drastically.

Basically, at first it was a lot of users were using to ... because it was difficult.  For every new users the sales had to go through the process of how it works and explain everything which doesn't really scale because how are you going the sell to a lot of people if you have to explain it to every single one personally?

We got a lot of calls customer call related., we spent a lot of time to explain how everything is working.

Now fast forward to today, the one thing that people point out, time and again is the use of our app.  Basically, do no more teaching of how to use it, it is self-explanatory, yes.  Any calls or e-mails are just bug related and not user experience, that is good I guess.

Yes.  There is still a lot of, a lot of stuff to improve but, we have learned a lot on this way and we have messed up a lot of things and through messing up we have learned a lot of things and this is what I will talk about.

I mean, this talk comes from all the mistakes.  A quick think about user experience is, I notice it is, it gets ignored.  As developers we seem to forget we are developing for the users.  I don't know if that is us being lazy or ignorant but, it is not good because it matters.  Since even if your app has killer features, if it is unusable painful to use, people don't understand it, it doesn't matter.

Why is it that we tend to forget about it?  I think it comes down three reasons, lack of resources, lack of knowledge and ignorance.

Now through the mistakes and lessons I will talk about the first two, as someone coming from a small team, but just quickly about ignorance.  I feel that a lot of times developers see their users as like that.  [on screen].

Yes.

I think it is important to realise that when a user struggles with your app. It is your app's fault not user.  If you blame the user all the advice I will talk about now, they don't make any sense because, there is an issue elsewhere.

Also I think it is really important to realise that developing pretty good user experience is quite easy.  Now, getting to a phenomenal experience that is hard, that is not something we will talk about today.

So finally, this is the crux of the talk.  Let's go through the seven mistakes we have made and seven lessons we have learned.

Now some of these may seem obvious and they are after you have learned them but, until you have, they are not obvious.

So as I mentioned before, what happened to us was that as a start-up we have to focus on getting the product out there.  We have to focus on so many things and we don't have the time or money to have a single person work solely on user experience.  Because of that, what usually happens is, teams don't assign anyone to user experience at all.  Because someone can't be there 100% of the time.  The thing is, if this is the case, you can't expect results.

For us it was kind of by chance, I can't really retrace how it happened just one day I took over user experience and you should take that with a grain of salt because I still did, I still did and I still do front and back and full stack.  I just became the person to talk to about user experience.

Ideally someone would be assigned to user experience, focus all their time in reality there is no way usually and what we have learned is that you get great results regardless.  Even if I still worked on other stuff, this proved to be very helpful.

So, in our office when we discussed the features or stuff we want to work on, we have sales people, developers, CEO, there is no user involved in that, in that debate.  So when they talk, they talk about okay how we going to solve this from the technical side?  What it means about the big picture.  All that stuff yes, but no user.  That is not really good because users should always be involved in that, those debates.  Someone should represent them and someone should be there to defend their point of view.  So whatever you are considering a new, a new the feature, new feature, does this make sense for the user, is this user friendly?

This came as a second nature once we assigned someone to be in charge.

As developers I feel we are often content in our own little bubbles, and we don't talk to customers because it isn't our job.  Like the boss has moved, we don't talk to customers.  When it comes to user experience you need to have input from the actual users.  If you don't, you will just guessing and speculating what, what experience is for them.

This for us, this was, I remember one day, I heard my boss talking on a phone with a customer.  I heard some complaints.  Just by hearing that, I immediately got, I immediately realised, that is not okay, we should change that.  It was 5 minutes work, if I didn't hear the input I wouldn't know that.  He didn't think of passing that on to the developer’s team.  So, I think it is really important to, to include developers to customer support.  So a really good advice I have is that all, any feedback you get from customers which is usually forwarded to sales or other, or what is the word?  Other parts of the office, developers should be included in that too.  What we do is, whenever we get feedback, they toward it to me, so, they forward to me, so I can see if the feedback they gave and what they are struggling with is part of a bigger problem.

This was one of the most beneficial things we did.  Through that, realised, error messages were worded in a way that confused the users.  We had for example, when you wanted to export the search results you would get a comma separated value format.  Which made perfect sense to us as developers like you can import it to anywhere., to every customer that was painful.  Didn't know how to convert it to Microsoft excel.

Also we realised for every single user, they have to like as I said, at first we had to explain how to, how to get started with the app.  I simply created an intro to our app, which took less than a day, now everyone just gets it which is awesome.

Now, complicating is always an issue because especially for the developers I think we always have, we are working on something and we always have ten different ideas what else we could, ten new features, ten more ways how to improve something.

That is not always good because then you end up with, with so many features that it is difficult for users.  It is difficult for you as a developer to maintain everything, basically nobody has a good time.

For example, we had a really complicated export which contained all of the data we could get.  Which sounds like a good idea right?  Just give them everything but, in the end it just confused the users.

Also we would offer pausing and stopping of the searching and scheduling and all kinds of stuff which you don't really need for a search engine.

So, simplify.

You have to be very critical of what features you are going the add and keep.  Basically, in the office we have a rule that we are not going, we are always going the assume that no one is going the need a certain feature and move forward only if we have evidence that it is something that is going the, some kind of use to someone.

Now this one is tricky.  Use of technical language.  We don't even, we are not even aware that we are doing it but let's, I will just give you an example.  So, we are doing a search engine and at first when the button or like start search we call it "start query," when we mentioned a search, we said query.  Of course it is a query, why would that be complicated?  Almost no one understood what we meant by a query.  So simply by changing that to search, it made things a lot easier for everyone.

So yes, try to use plain English, it is so hard, since we are involved in that language, we are deaf to it, we don't realise the word might not be natural to someone else.

Yes.  So, not listening to users.  Listening to users means many different things and it means listening to them when they give feedback but also means testing new features with actual users.  Sitting down them next to a computer, seeing how they interact with what you design.  In ideal world you would do user testing but this would be very extensive you would have to get different people in the office and in reality you can't always do that, but we have learned that if you bring someone from the next office or someone from just the different person doesn't have to be an actual person and get them to use your app and observe it, you get so much information from it, it is incredible.  I am surprised every time.

So always test new features with actual users.  With actual people.

Finally, sometimes it is just failing to adopt basic principles.  So, in user experience there are like ten basic principles if you follow just two and follow them consistently, you can get better user experience of the app than most other apps.

It is kind of surprising how easy it is to ignore this or forget about this.  But yes, consistency and feedback meaning consistency, do your buttons in your web app always represent the same thing?  Is a link that is pointed out wards, is it always styled the same way?  Whatever action a user might take, do they get a feedback for it?

So on.

For example, with us, it was the first version was when they started the search it took like a minute to get started and in that minute nothing happened so usually just I mean obviously like, if I was there, I would do the same, click until something happens right?

It is really frustrating but, just a simple tweak was that, so yes.  This was what happened after you read a search.  Nothing.  Even like, even after a, it went after last ten searches it was easy to miss.

Okay.  Now you get a notification and it is separated from last searches so it is clear you started a search.  It is a simple thing but so easy to miss.

So basically starting taking care of user experience because it is not that hard.  Regardless of your knowledge, it is simple things you just have to be consistent and critical of yourself.

As I said.  That is it.  Thank you.

(APPLAUSE).

DANIELE PROCIDA:  Thank you very much.  We have got time for a couple of pretty short questions and short answers I guess.

FROM THE FLOOR:  Hi, you mentioned that you assumed that you don't need new features or your users doesn't need new features unless you got evidence.  What evidence do you need?

ŽAN ANDERLE:  It can be many things for example, getting a person to request it.  So getting a person to request it and say they are willing to pay for it.  So sometimes you often like we will create a landing page, selling something, and we haven't even developed yet, but to see if there is any interest, if there is, we will develop it and otherwise probably not.

NEW SPEAKER:	 My question is what about why first and did technology you use have or doesn't have to do {inaudible}.

ŽAN ANDERLE:  Sorry can you repeat that?

NEW SPEAKER:	 My question was about the mobile first applicability to such experience and if the general technology you use helps or make it more difficult to implement mobile first.



ŽAN ANDERLE:  Yes from mobile first design we use boot strap from everything we doth if you use boot strap properly it kind of forces you to do mobile first.  That's been working great for us.

NEW SPEAKER:	 One more up there.

NEW SPEAKER:	 How do you measure good user experience like for instance if you are a data driven team and implemented something and wanted to measure the effect you have any advice on that?

ŽAN ANDERLE:  I think that is one of the controversial topics when it comes to user experience because it is very hard to measure.  For us it was very obvious by the amount of user support related questions we got.  So before even though we had a lot less customers we were dealing with customer support, support all the time, things they didn't understand, things we had to explain, that kind of stuff, and now we have a lot more customers and that just simply does not come up and that can be one indicator that user experience is better but other than that it's, yes, through user testing so when you sit down with a user to see how they use your app you get to see where they struggle and that can also be one way to tell if it's good or not.
