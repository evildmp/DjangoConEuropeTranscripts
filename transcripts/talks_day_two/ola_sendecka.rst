==================================
Ola Sendecka: Into the rabbit hole
==================================

OLA:  It is good to welcome Ola today, she organised Djangocon Europe, in Warsaw together with me, also Django core developer, started Django girls, a huge organisation that is now changing the way this kind of conference is being run.  So, she is going the give a wonderful talk about getting into rabbit holes and it is wonderful story and how to get out of the rabbit hole which is probably the most important part.  So yes without further ado, please give a warm welcome to the sweetest person I know, Ola Sendecka.

(APPLAUSE).

OLA SENDECKA:  Good morning everyone.  Do you hear me well?  Okay.

Amazing.  I am extremely happy to be here, I really appreciate that so many of you came, it is like the second day of talk and there was a party yesterday, so it is really amazing so many of you are here.  I really want to first thank Djangocon organisers, especially Daniele who convinced me to give a talk, turns out it is a keynote, I am extremely excited about it.  You can hear that in my voice, I am superhappy to tell you my story; I have so much stuff to say to you.  So.  Yes.  It is Tuesday morning you probably had a great time yesterday.  You are probably sleepy; some of you have coffee and some of you not.  So, the good news is that I will start with a story.

This story will be about Alice in Djangoland obviously.  Little disclaimer, if you don't follow all the code examples, please don't worry, because they are not the most important part of this talk.  So, if you are lost then it is fine.  Actually there are a lot of bad code here, so maybe it is even better if you don't follow it.

So are you ready?

Alice was beginning to get tired of sitting by her sister on the bank and having nothing to do.

I am bored, I want to do something interested, everybody is occupied, I half hour and I have nothing to do.

She was having this little project and tempted to start coding even though she was visiting her family, she felt a little bit guilty about it because yes, she was not visiting her family too often wanted to spend some time with her sister.

But she had this free half an hour and her project that was not finished, so, she decided to herself that, well, nobody will really notice and she will be done before afternoon tea.

She was working on this project for some time already.  It was quite big, tightly coupled, lot of legacy code, she felt very confident about the code.  She knew that quite a lot so she knew that she can do everything very quickly.

One part of the project was basically tracking time so she could have some projects and then she could lock time, how much time she spent working on the project.

The project and many, many other models were very special.  They were special because you could archive them.  So, by default, you just work with active instances but the archived ones are still there and you can still in some scenarios see them.

And it was done like this.  It was not maybe the best way to do that but it was already there implemented so she had the class, the class called archive bubble that was saying if they had the flak saying if something is active or not.  Then all the models she wanted to archive inherited from it and override the objects manager and filtering out archived model instances.

She could track time, logged the time, how much hours spent on which project and after the project was done, she could archive it.  So later on when she entered new time, she didn't show the first project with the list at all.

She had this list where she could look what she did last month or last year.  Recently she looked at the list and she saw this line.  Maybe you haven't noticed what is wrong with this line?  But Alice noticed this very quickly because she hate typos, there was typo in the description.  So she clicked the edit button, this is what she saw, where is my project she asked?

What is wrong?  She felt a little bit and she realised that the model form she used is just taking active objects active instances so obviously it does not show up in this select.  Because she edit something that is pointing to the archived model, archived instance.

So now editing that was not possible and she really wanted to edit this.  Alice started to think what she really wants and what she defined it this way, that if she wanted to by default work with active instances, so wherever she had the form with the select, she wanted to have list of active instances and the current one.  So if the current ones was archivable she wanted to save anything in the form and save it.  She didn't want to change many, many forms she had.  She started to think about it and decided she will create this function outside of any forms and she will call it preserve existing choices that will take a form and she will iterate over all the fields and do some magic, so no matter what is the field, no matter what is the projects, is it a project or something else inheritable from archivable, it will do it for her.

She thought about query sets well, most of her forms were model forms and Django is doing all the magic for herself so, she felt yes, what I want is to have current query set plus the current value of the instance.

So, she started to draft in there that and she decided that in her function she will just take the field and override the query set with extended query set that is taking current query set plus current value.

She started coding hoping that she will be done very, very soon.  After a while, she had her first sketch ready.  This is how it looked like, extended query set inherited from Django query set.  Passed the value to the init and then saved it, then after iterator and then after returning everything that is there, yielded the value.  Didn't check if the current value is not already returned but just wanted to check if it works.

Yes, she was happy with that.  She was yes, convinced that she will just go to her sister and speak with her and very soon.  But she refreshed the browser and this is what she saw.

Something was wrong, yes, that was for sure.  She started the bugging.  She looked back; she went deep into Django, step by step, PDP and printing different kind of things.  The things didn't work as she supposed they will.  Alice tried to override different parts of query set but it was retrieval.  Fixed one place and another thing was broken.  After a while she knew that it is not the way to go.

This slide is very Polish!

(LAUGHTER).

During her trials she noticed the error happens someone in model toys iterator, what if I, if I override model choice iterator.  Why not?  Had this idea that she wanted to try but in this very moment her sister came asking Alice do you want to have tea with me?  Alice said, I need to try one thing, I will be done in 10 minute cans you wait for me?  Yes sure.  Sister left, Alice started to code and minutes passed and after some time it was ready.

This is how it looks like; it is very similar to the query set.  She passed the value to the init and then after everything was done yielded the choice that was, that was the current choice, once again she didn't bother to check if it is actually active or not.  Just wanted to check if it works.

Then in her preserved existing choices function took the field and changed choices and create extended model choice iterator.  She refreshed and superhappy.  Now it works.  Her project appeared here and she was supersure she can go to her sister and have nice evening with her family.

But then she tried to save the form.  She realised she was wrong.  There is a validation error.  No! She cried.

She felt frustrated, angry, and her sister came again asking Alice, can you just come?  The tea is already cold.  Alice was really irritated and she really wanted to fix that.  So she said, just give me some more time.  I will be soon.

So her sister went away once again and Alice started to think and debug again.

She finally reached a definition of model choice field.  She decided that the error must be somewhere there and without even thinking she decided okay, I will override the model choice field too, I can do that, I already override the iterator, why not do it with the model choice field?

She did.  This is how it looks like.  At this point she didn't even bother to change, to make something smart just copy pasted Django code to model choice field, she checked the value is the current value of the instance and if so, she returned that.

Then in her function preserve existing choices one she extended, basically, she created a field and put that inside the form.

Now, Alice said, it must work! She refreshed the page with the form, save it.  It worked.  Alice felt it is over now.  There she had overridden the choice field, iterator and model choice field.  Kind of ugly but it works, she tried to convince herself and she is sure she is done.

But then, she notice another thing, she wanted to change one of the fields pointing out to the archive bubble object and instead of this; she ended up with this thing.  Oh no, no, no! Alice started to tear her hair out of her head! What now! On top of that her sister came, she was annoyed, you came here to visit, why you code and code all the time?

Alice just she was superfrustrated and superangry, said, just go away, I need to fix that, it is very important.  Her sister left angry.  Alice felt pressure and she felt very, very guilty.  But she continued.  She looked into the code again and she understood that yes, creating a new field it is not the way to go.  Because she was trying to do that outside of the form and she had no idea what was the widget used or any other thing.  When she looked into definition of model choice field and in it, she was thinking maybe I can pass it somehow, take it from the old field and put that into the new one?  Well it was not way to go, so many things were there.

I can do that.  I can, Alice was sure, there must be a way, I need to fix that somehow.

So she thought a little bit and started to think in a weird way and decided what she wanted was different to Python not the whole field.  If she could just take the different implementation and inject it into the existing field that was created by Django, yes, I can do that.  So she did.

So she took the whole Python method from her old extended model choice field and she put that into function custom to Python.  Then in preserve existing choices she did this, so she took field and put the new cast into Python, using partial to Python.

At this stage it finally worked.  Alice decided to leave it as it is.  She couldn't spot anymore errors and felted really frustrated and angry and her family was angry.  Spent hours and hours of her free time looking at that.  She was sure that it was supereasy at the beginning like, half an hour job.

The code was ugly, weird, confusing and partly working, just like a house of cards, have fragile and ready to collapse any time.

She committed that repository and felt superashamed every time when she looked back and others could see that too.

She was not even sure what she tried during this way everything was blurred, had weird errors and felt frustrated so much, every step, so many unexpected things happen.  In the end she spent hours making something that was not working.  It was, it seemed easy at the beginning but, in the end, it was band of horrible code through repository.

What happened?  Asked Alice.

How I end up doing all, all this horrible things?

Exactly.  What happened?  This is very good question and yes.  Rabbit, Alice was in the rabbit hole and I know that many of you have intuition about what rabbit hole is, but let me rephrase it for you, or define it.  If you are not familiar with it.  So, the rabbit hole is the act of getting so caught up in what you are doing that you spend precious minutes, hours, or even days on doing that and it negatively impacts your overall productivity.

When you fall down into rabbit hole with the certain goal in mind, you get side-tracked by various events and you change direction many times along the way and eventually you end up somewhere unexpected and very often without satisfied the original goal.

So the rabbit hole is kind of metaphor of entering, disorientating, confusing land and a moment ago you could follow the Alice steps following the rabbit into this strange world of query set, model choice field, and the strange thing is nothing seems to work as expected and he got more and more confused and more and more frustrated.

Some can argue that rabbit hole could be a good thing, that you are in a flow and you discover many unexpected things and you can learn from that.

It's true, but it's very individual.  And I must confess that every time I end up in a rabbit hole I end up feeling frustrated, angry, helpless, and stupid.

Next time I look into the code I know I would do that differently, like I have no idea how I end up doing all of this horrible stuff, like it was wrong at the very, very beginning.  And I know that many of you already have some cool ideas on which Alice went wrong and how she could do that better but really it's not the part, like it's not the main thing in this talk because believe me I really - yeah I had so much stops and it pained me when I wrote this presentation and wrote this horrible code for you.

But this is the point.  Once you are in a rabbit hole you don't really think and you're so confused and so frustrated that you don't see obvious things at all.  And for Alice it was model forms.  But for you it could be different library, something that you don't know yet, or maybe you have hard problem to solve and you have the worst day.

To understand the rabbit hole, I tried to read things and, yeah, I wanted to somehow deal with it much, much better, and there are 2 things I want to discuss with you briefly and I believe it will give you a better understanding what's going on when you are in your rabbit hole.

The first thing is Zeigarnik effect.  I don't know if I pronounce that correctly.  According to Balmeister and Bushman, the Zeigarnik effect is the tendency to experience intrusive thoughts about something that was once started and never finished.  So even though you try to pursue new goal you cannot stop thinking about what you left behind something unfinished.  In a way it's reassuring because it kind of means we are built to finish things but how many times you end up abandoning your project and not finishing something and you feel guilty and you keep thinking about it and you feel bad about yourself. Experiments in this area suggest people remember unfinished tasks and puzzles much better tan solved ones so we can say people are built to finish things.

However there are times we need to realise that we have invested too much.  It's very, very hard to objectively judge it use especially when we feel responsible for the project.  And this brings us to the second phenomenon which explains rabbit hole which is sunk cost fallacy.  I expect some of you know the term but if you are not familiar with it it's a phenomenon that your decision or you are influenced by the emotional investment you already accumulate.  And the more you invest in something, the more time, money or resources, the harder it becomes to abandon it.

So, if you work on a project and you go nowhere and like Alice you spend a lot of time that you should do something totally different you just feel you cannot abandon it because then everything you invested, the time you sacrifice it's not always your time only but time of your family.  It would be like sacrifice for nothing so you don't want to waste it and you keep going, keep going and the damage is bigger and bigger.

One of the features of sunk cost fallacy is that it's connected to personal responsibility and it appears to operate mainly on people who are personally responsible for investing the resources money or time.  And this irrational escalation of commitment is a very dangerous thing and it can make you miserable.  You will end up doing unwise things and you invest more and more resources on something that has no chance to succeed.  And you will feel worse and worse about yourself.

So, being in a rabbit hole is possibly very, very dangerous and you waste your time, effort and wellbeing for it.

So, let's talk a little bit how Alice end up in a rabbit hole in the first place?

First of all, she assumed the problem she's fixing is very easy and because Django was doing everything for her magically she assumed that this must be easy, she expect easy solution and therefore she did not see all the implications at all.

She was also fixing symptoms and she didn't look at the problem as something bigger.  She had no bigger picture of the problem.

She also continues even though she failed so many times, she tried override query set and failed, tried override model choice field and failed and then override model choice field and failed.  She should have realised something is not right much, much quicker.

And all this time she was super, super sure she will be done in 5 minutes, just give me 10 minutes I'll be done and she was sure solution is one step away and she had something else she didn't expect and she was confused again.

Finally, she couldn't give up.  She was very persistent and she really want to solve the problem.  It is possible that Alice didn't want to admit that she cannot solve it on her own.  She was too proud or she want to prove that to herself.  But rabbit hole is very dangerous place and maybe it's fine when you do that, like that you are in a rabbit hole working on your side project to discover different things, but if you work for your client or you work on open source and then you commit something that is horrible and people see that then, yeah, I'm not sure if you'll be very happy to see that out there, people commenting, so I think rabbit holes can make people not contribute to open source that much.

So, how one can fight with rabbit holes.

First thing is to realise that you are in one and believe me it is not very easy.  So many times I'm asked are you stuck are you in a rabbit hole?  I said no, no I will be done in 5 minutes; I just need to fix the error.  I was in rabbit hole obviously.

So I wrote down some symptoms that I have, so it's not very extensive list and I believe you could have different symptoms too.  But here is the list:

You don't know when time flies.  2 or 3 hours feels like 5 minutes.  You are always almost done.  And you are hungry and thirsty because you forget to eat anything.  You are so fixed on solving the problem you ignore everything around including your body and its needs.  And when you finally try to make a break because you are starving or you really need an extra coffee you cannot stop thinking about it you go to the coffee machine, starting to make it and you think, what if I do ... if I check his barrier, or maybe this is wrong?  And you do this debarking session in your head and cannot stop thinking about it and then you go with your coffee and try to see if you are right.

If you haven't spoken with everyone for a longer while you can be in a rabbit hole.  It is tricky though if you are a remote worker as I was for a long time but yeah if you haven't even chat with anyone, yes it's one of the symptoms.

And finally, you feel extremely unhappy when anyone dare to interrupt you.  A colleague, your boss, neighbour, or even a food delivery.  You are cranky and very, very irritated and you want to kill them.

So if you suspect that you are in a rabbit hole what can you do?  And getting out is not easy.  Once again it's not trivial.

And this list is also not very long and I still try to find the better ways to get out of the rabbit hole but here are some of my tips.

Ask yourself how much time you need for fixing the next problem you face and be honest and say, if you don't know, if you don't understand what's going on just try to think how much time you would like to spend maximum and just set the timer and be very strict about it.  If the timer - if {inaudible} just make a break.

Make a list is a good idea because it force you to think what could be wrong and to think about it not as a solving error you face but to think what you try to achieve?

So you will have a bigger picture and you will not go in obvious bad direction like Alice did a couple of times.

Obviously rubber duck works too so if you say to somebody or rubber duck, you can also paint rubber duck in paint if you don't own one, so if you try to describe what's going on and try to explain to yourself what you try to achieve and what's happening may be you'll notice something more.

If it's still not working take longer break.  But make sure that you are not doing the bugging session in your head so, yes, an hour swimming, or I know climbing, or just meeting with friends, going to the cinema, making a longer break like one or 2 days, it is really, really helpful.

And finally and I think this one works the best for me, is asking for help.  You might be proud and you would not like to show to somebody that you spend hours on fixing something weird and not understanding what's going on.  Honestly, being in a rabbit hole is potentially much, much more dangerous and it will undermine yourself confidence a lot.  So it's better to ask for help as soon as you feel that you are stuck.

And if you don't work with people who willing to help you or will judge you because you do weird stuff sometimes in new code you probably should change your employer.  If you don't have colleagues because many of you are self-employed or freelancers you can ask your friends or ask on internet.  Sometimes even explaining things to somebody who is not a programmer is very, very good idea.

One more tip is to have somebody who is not doing their own debugging sessions in their head so they are not in rabbit hole because you can end up convincing them that you are doing something smart.  It happened to me.

Rabbit holes are scary but there is one positive thing and good news for you if you ever found yourself in a rabbit hole.  It means you are very, very curious and very persistent and really want to finish what you started and it's a good thing, but being in rabbit hole is something really, really horrible and it can impact you in many different ways and make more damage than you expect.  It can make you feel bad about your code about your skills, you can feel dumb and worse than everyone else and just because you have the worst day and had nobody to ask for help you are just fixer and you are in this strange confusing world.  So don't be afraid to ask for help when you're in a rabbit hole.

I'm Ola Sendecka; I am Django girl founder, Django cofounder.  Many years’ experience; I work for amazing company called Potato but still I find myself in a rabbit hole from time to time.  ; They make me feel bad about my skills and undermine myself confidence.  That's why I am super happy to hear about your tips and tricks, how to become unstuck when you are in this horrible funnel with only one way out through the rabbit hole.

I would be glad to hear about your stories and your ways of avoiding noticing and getting out of the rabbit holes.

Thank you.  {Applause}.

NEW SPEAKER:	 So if anyone has any questions or suggestions there is a microphone in the middle of the room.  I can start.  So you said you are working remotely for a long time so where are tips for remote workers and how they can make sure they don't fall into that?

OLA SENDECKA:	 What worked for me is to communicate with a team very often and if you cannot have hang out open all the time with your team you can try chatting with them a lot.  It's tricky though when your time zones are different.  In his scenario I think like taking longer breaks here and there and having something that distracts you and you cannot just put that away helps.  It's very tricky though and I am not sure I am doing that very well so that's why I'm talking here so I hope you have some amazing ideas and I can learn from you.  But yeah taking breaks and asking for help, writing an email sometimes helps so if you have somebody in your team in a different time zone and you try to write in the email what's going on what's not working for you then you can during writing the email you can realise what you are doing and that it's insane basically.

NEW SPEAKER:	 Is that on?  Good.  Thank you for your beautiful talk and beautiful storytelling as well.  I appreciate the artistry in telling a good story.

I am not really - I feel a bit of a fraud being here because I'm a research astronomer and I consider my code to be hacky and really like tinkering, but I am a remote worker as an astronomer and I have to interface with a lot of professional software engineers and I feel like a bit of a fraud, so I don't ask questions when I probably should.  But also a lot of them are Java programmers and can't help my Django questions so because I feel a bit of a fraud asking them for help and they can't help, I don't really know where to look for other help, so I write even hackier code.  Do you have any questions that will help me stop going down the rabbit hole?

OLA SENDECKA:	 I am not sure if I understand correctly because I'm stressed - no sorry I'm excited.  This is my trick I'm excited not stressed!  So you ask where to find help if you don't know where to find, ask to help.

NEW SPEAKER:	 It's knowing what questions to ask so you don't -

OLA SENDECKA:	 Yeah so I think like asking the internet is a good way to start or starting to explain things to even to someone who is not in the field.  So, it's good to have a mentor or a colleague even if that's like remotely so make connections with somebody and have a network of people who are willing to help you.  I know it's not a perfect solution if you don't have anyone to speak right now, but yeah.  It's hard and I still struggle with that.  So I would suggest trying to find somebody in the internet even.  Try to find person who is doing something similar and try to contact them and I don't think a lot of people will bother if they don't want to talk with you, they will just not respond to your email, but maybe you'll have, yes, end up having nice mentor or nice peer to talk about things, even the emails or something like that.     NEW SPEAKER:  How would you suggest finding those people?  Just by looking at this sort of community and - people don't have little like floating bubbles with their contact details but I try to talk as many people as possible but it's always tough.

OLA SENDECKA:	 So I didn't hear that well but about finding people I think it's very nice to go to the conference and meet ups and be part of the community so if you do something and you are alone with that you are like - it's very possible that you end up in the rabbit hole more and more likely.  If there are any meet ups and or forums or mailing list, just be active, if it is like, if you don't have a question now, maybe you will have in the future, if you are active and try to help others, it is likely they will help you once you are in a rabbit hole.  It is nice to have a network of supporting people, I encourage you to speak with people at the conferences and meet ups.  Write to the people who are your role models, like make your community bigger.

FROM THE FLOOR:  This might just be me, I don't particularly mind the rabbit hole thing, when I am in the middle of it, I am not happy about it.  I find at the end of it I have learned something, do you ever think you have learned something from the whole process, dug into model forms code, otherwise would never have looked at and understood how it worked.

OLA SENDECKA:  It is not that the rabbit hole is bad, but if you are wasting time like you wanted to spend with your family or do something else or you are working on the task that your clients want to have something done, but, you estimated that for one hour work but then you spend one day and you wasted clients’ money or you wasted your money if you are a freelancer, it starts to be not worth it.  So it is about the balance and it is, I think it is very important to know that you are stuck and you are in a rabbit hole, then decide, is it really worth to dig in and to find the solution?  Or to like experience all this unexpected things in wonder land?  Or are you have no time and you don't want to follow that.  In case of Alice she was frustrated not in the flow, not happy with what she is doing but felt guilty there is pressure and she didn't want to be there.  So, I think it is, it is important to realise that you are in one and to consciously decide if I want to follow this path or not.

FROM THE FLOOR:  It is as much about time management type of thing?

OLA SENDECKA:  Kind of.  But also, it is like you are, in your project in your life, I think that often it is that you are not realising that you are doing something bad; you are just fixed to do something, to finish the task.  You don't really pay attention to anything else, so then in tend you have something that you are ashamed of and you feel bad about it yourself and it undermines your self-confidence and then you think you are stupid but you are not, you are just following the wrong path and you are superconfused in the way.

FROM THE FLOOR:  Thank you.

FROM THE FLOOR:  Okay, all right okay, so I have got one thing I was going to say, more a comment than a question which is that for anyone here who is as old as me, and used to programming in CVS back in those days in the rabbit hole, made 15 commits, it was difficult to come out of it.  With the horrible things you have done and put that in there and start again from the beginning of the problem you were supposed to be solving in the first place, quite often forget that the other branch was there at all.  Sorry that is not really a question.

OLA SENDECKA:  So we are running out of time.  Thank you, that was amazing.

(APPLAUSE).
