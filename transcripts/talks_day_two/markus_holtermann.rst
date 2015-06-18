=====================================================
Markus Holtermann: Forms are static - no, they aren't
=====================================================

DANIELE PROCIDA:	 Thank you very much.  {Applause} I am really pleased to introduce Markus Holtermann who is another colleague in the Django core team.  There are tens of people in this room with whom I've shared meals and drinks and quite a few with whom I've shared a hotel room or someone's spare room, but there is only one person with whom I've actually shared a bed.  {Laughter}.  And so that's what we do {laughter} - I was going to finish my sentence and say that's what we in the Django core team do for you when we go to sprints!  Thank you Markus.  {Applause}.

MARKUS HOLTERMANN:	 Hi, thank you for being here, thank you for having me here.  Today I want to talk to you about how you probably use forms and how you could actually use them in a quite different way so might be different, might be similar way.  And the way forms can, what forms can actually do beyond what most of you use them for.

But first let me introduce you to - let me introduce myself.  I'm Markus Holtermann a master of science student at technical university of Berlin and I'm also a member of the Django core team since the beginning of this year and some of you might have seen me running around at euro Python 2014 fixing internet and Wi-Fi and being pretty busy the first days but conference was cool so I was relaxed the next days.

So, referring back to the title of my talk, forms are static, no they're not.  I'm actually talking about the stuff in Django dot forms just to be clear.  Before I go into any details I'm going to talk to you about what forms are and what basically you use them in general for and the most important use of forms is basically input validation then you have a user that goes to your web-site, enters some data and you want the data the user enters to be somehow validated against some rules and Django does a pretty fine job at that.

Some of you might not use it for end user direct user interaction but also to validate data that comes from API similar to what serialisers do in Django framework but yeah they are basically input validation.

The other thing is forms are static.  But when I talk about static, what does it even mean?

Well, first and foremost forms do not change when you run your web application.  More precisely, the {inaudible} layout does not really change.  So what does change when I talk about forms?  Well, actually the content user types into forms but, well, that's just per request and that doesn't really make any difference to the forms, it's just some data is validated.

So, the question arises why are forms static at all?

And static I define as you have to actually change code, you have to test and modify code, you have to probably run some testing staging environments and test your bundle release and deploy it and, well, this is pretty much the way how forms are used and how Django is a good idea how to use them, but sometimes you want forms to be more dynamic in terms of I have for example a user who whose locked in and I don't want him to have a catch up field he has to fill out when requesting data but on the other hand you want the page or form for anonymous to post data as well and there you have to have a mechanism for be a to prevent {inaudible} from spanning your site so there you have some kind of dynamic form, form feed allocation, the allocation you meant remove forms from fears from the form or you add them depending on what you actually do.

But what also changes in those kinds of situations is what Ola talked about in her keynote about - in the {inaudible} talk - you can have permissions on objects and you want to do filtering on objects you have in model choice spheres and depending on what's in your data basis you have different data for {inaudible} data in the fields which is pretty much obvious.

So I honestly have to disappoint you at this point because those forms are still static because you still have to modify code if you want to make them behave slightly different.  You still need to test them on the {inaudible} and deploy them.

So, you might argue now that this is actually the right way to do and yes, I pretty much agree with you.  Yes, I think almost all cases but, they are situations where it does not apply.

what are nonstatic forms then, they are forms that can change the lay out, the field that is are there.  The fields that are not there, the order of the fields as well and practically, this, the dynamic forms are forms that don't need to be modified on a code level.  Therefore, are without necessity to deploy them again.

Well, now you might ask, why do you need them?  This is actually a brief story I have had a very, a company I have worked for, for a couple of years and we had a rather small client not that, not that much, not a large, they didn't have that large budget and the only thing they pretty much did for organising events throughout the year and the event organisation or event registrations was more or less the same each time but they all of those found forms had different additional fields they had to provide.  Be it a birthday, e-mail address or whatever.  So we would have ended up with coding every week, another form for the entire year which is not really code base you want to maintain after some time.

So, I came up with okay, let's do something else.  Let's do, let's be smarter at that.  What I later realised is that the application I came up with allows you to do even way more complex things.  Before I actually talk about the application itself I want to talk about you, what I am doing there at all.  In the end, I create classes dynamically.  So, what of you used or are uses model forms?

Yes.  Pretty much everybody.  Which is what I actually expected.  But, model forms are not that quite static.  This is actually a pretty simplified version of what Django does when creating a model form.  I hope you can read it.  Can you see my laser pointer in the end?  In the back?  You Django first takes all the model fields from the model, creates the class matter, you design on the form, and then sets the model on this matter class and creates the actual class, we have dynamic class construction, which something that Python lets you do.

Then Django lets you create the model form putting the class on there, and you have the model form class you can use that is in somehow from the form and pretty much lets you save in model instance.

But, wait.  They are not really static, they are not real, they are static, they are not really dynamic, why?  Because the form that is constructed is constructed from the models from the models fields and for the sake of your health I hope nobody of you actually modifies models during the run time of the application.  It is, might work but you probably don't want to do that.  So, this forms this model forms are still static because if you want change, you actually have to deploy the code of the modification you do to the models and then release and deploy.

Which brings me basically back to the idea of the, to the function that is Django users in this code type.  Which is a Python bid in that let's you create classes dynamically, so takes the name of the class, created the base classes it should inherit from the attributes so Django is a framework and pretty much what you do with web frameworks and Django, is always interact with the database, this is pretty much what I did.  I put all the information I need for form into the database.  So, I have a form instance that is an entry in a database table that has some attributes and I have couple of fields that belong to a specific form and they are at rows or entry in a different table but belong to the field and when you open a view, or when you open the actual view, this application Django takes the database and creates the form dynamically, you don't have any culture changed there.

This is the basic lay out of the application, which I explained.  You have the form model which gives you the instance of the form or the form class, it has a name, it has actions and I am going to, to that in a second.

It has urls where the form should be able on and where it should redirect you.

The other thing our form fields which basically wrap the Django form fields into usable interface for this application.  They are instances you can bind them to a specific form and then the, the app constructs the forms with those fields.

Talking about the actions, this is the layout of the function base idea of the, that is going the be in the next release, you are pretty much get the form model which is the instance of the form in the, from the database.  You get the form that is the form, the instance of the form and you get to the current request.  With that, you can actually go and create model, you can actually do and create basically any kind of interaction you want to do with the data the users submitted.

You can interact with the form instance, take the data, the users submitted and do whatever you want with it.  In this case, I am sending the data to the administrators of your page, this admin settings.

There are two actions which let you send e-mails to the specifiable e-mail address, or list of e-mail addresses, the presentation to store the information in the database.  Right now it is just text field that wraps, that is contains some Json and uses that.  Then the next release, the Json field couple of days ago this is going to be Json field for 1.9 so you can later query on the data inside the Json field which is pretty cool.  Well the action in the next release gets also the request, which allows you to access the current user in the form, so you can actually create a profile form with dynamic form fields and when and let the user modify their profile with this application.  If you want to have a new field you just add it in the admin or the, yourself this field will show up in the user profile.

The other form are the form fields, these are the wrapper, you decorate them, to the application again, they have to inherit from this base dynamic form field and of course needs to read, imported at some point which basically do that in your ep config, it defines which form field it should bundle or relate to.  The name how it should show up in select fields and some attributes you want to define.  So the type, if ... the field that is used in the admin after all.

Well, and this is basically how it looks like.  You have a form that has the name, it has two urls, the urls where you submit it to where it is shown on and submitted to.  The success url define in the generic class based views.  You have the actions which appear, you have which I added a few versions ago.

Different templates for different forms you will see in a second, one default template for a form, html without any (INAUDIBLE).

There is an option to allow the user to visit a previously entered data item and with that, they can well, review what they entered before.  There is an option to for recipients, so if you want to send the form by mail it goes there.

These are pretty much the fields you can enter and just the admin inline, not that much magic there.  The attributes you find here show up here and this is basically what it looks like, there is a form that is rendered when you access the url, there is the success page that is, that you get shown when the user, when the user gets shown when you successfully submitted something and this is actually the detail of you when you visit this enter again.

There.  This is the application I have developed as part of those, this client project.  The original code was I created during a train ride throughout Germany which was, which is, which was pretty much work running in production for a couple of months until I decided okay, this is something I want to release as a third party app.  Might be helpful for others, yes, that is pretty much it thank you.  (APPLAUSE).

NEW SPEAKER:  Thank you, got time for maybe two questions or so, if anyone wants to come up?  One question.  One of the things if you have, when you are on dynamic forms much of the data series is common throughout all the different forms, the dynamic part is where you would like to have extra fields to add in.  Would there be any way to keep your, the same tables for the static data but the common data and then use the dynamic storage to store it into extra tables somewhere.  Otherwise if you store all your data in Json it is difficult to query.  Particularly if it is common data.

MARKUS HOLTERMANN:  I am not sure I understood.  The forms inherited from a normal form class, could override the, class based view that is shown up here in the first screen shot?  So you could hook up in there and define your custom form it should inherit it from.

The other thing of starting a database, since you have the instance of a user for example, in this particular case, you could actually update user item based on some investigation so you verify that the users, verify the idea and then update the, update the, in respect of the user profile item for example.

FROM THE FLOOR:  Hi, how do you manage internationalisation of ... name.

MARKUS HOLTERMANN:  I don't.  This is pretty much mono content translation which is something I briefly mentioned in the and hash Django thing, you could probably come up with something like, with an idea of Django parlour or something?

It was never used for the cases where I used the application.

FROM THE FLOOR:  Okay thank you.

RUSSELL KEITH-MAGEE:  Okay, so that all hinges on some Meta programming and sort of self-reflective code, code that is reflective on itself to build the forms.  Given that that is a feature that one of the reasons why we formalise the Meta interface in 1.8, how difficult that is to try and let everyone else know, how easy or difficult it is to build something that is reflective or self-reflective?

MARKUS HOLTERMANN:  I don't use the Meta ...

RUSSELL KEITH-MAGEE:  I know you are not using it in that case, but the same sort of tricks would be involved?  So the Meta programming idea you were using?

MARKUS HOLTERMANN:  So the actually the most creative stuff and I am not really proud of it honestly is the generation of those option fields here.  It involves some really hacky Django admin things, if anyone else comes up with a better code, I am happy to ... the other one is straightforward I think.

NEW SPEAKER:  Thank you very much.

(APPLAUSE).
