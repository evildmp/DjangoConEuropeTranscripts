=====================
Shai Berger: Lispisms
=====================

DANIELE PROCIDA:  ... I am very pleased to introduce Shai, Shai is one of my colleagues in the Django team and he will be talking about lispisms.

Thank you Shai.

SHAI BERGER:  Okay.  Hi there.  I am going the talk about things that Python in general in Django in particular could take from lisp and how we could do this and also introducing here a library at a time I have been developing.

The first question that you could be asking is, why lisp?  What is so special about lisp?  What is interesting about it?

It is not a very new language.  It is, it doesn't look very nice.  It is hard to read if you are not used to weird things.  Yet, it gets people very excited about it.  You probably don't know Erik Raymond, like fifteen, twenty years ago, he was an important voice and an earlier adopter of Python.

What really is interesting.  So, lisp actually pioneered many things that we take today for granted.  Recursion, dynamic typing was first seen in lisp, garbage collection was first seen in lisp.  So the question is, basically, are we done pulling things out of lisp or are there still things we could find interesting there?

Or, rather, did these things come first out of lisp just because it happened to be there first, or are there things in lisp that help foster innovation and allow us to and then give reason to their being more things that we should pick up.

People who know lisp usually when you say, let's take a feature from lisp to another language usually the thing that comes to mind is macros, lisp macros are powerful.  People start adding similar features to Python, perhaps ... does that and it was rejected.  There is libraries that does that, similar, sorry, does limited macros in Python.

But, actually that is not what I want to talk about here.  I will have more about it if there is time later.

I want to talk about dynamically scoped variables.

So, what is the problem that dynamically scoped variables solve?

People everywhere for years have wanted access global access to request.  Also to other of things it was just last weekend I think someone asked on the developers list for the current app to be available globally.  Sorry.  Whenever people make those requests on the developers list, it usually get the same answer:  No.  Globals are evil.

Why are globals evil?

Globals are evil because when you use globals in your code your piece of code is tied down to a specific system and you can't pull it out and reuse it.  Because, when you are using globals and you call out to other code that other code can change it under your feet and it is hard to reason about the behaviour of your code.

All that is only, if you use thread locals, you can use those and things like thread safety to worry about.

Yet, evil is more than about being bad.  You don't hear six hundred line functions being described as evil.  Don't hear spaghetti code being defined as evil.  Why are we saying globals are evil?

Because they are mighty convenient!

We like it that we can make ORM queries without passing the connections explicitly, we like to have access to settings whenever we like.  In normal Python not related to Django, we like to have the STD out available by default for print and available not by default if we needed to press it.

So, globals are evil because it is hard to control them.

But what if you could have globals that do behave?

Globals were the values can only change down the call chain, so they can change from under your feet.  Like a "with" statement where everybody change to the global would be like a "with" statement.  Then each piece of code makes sense in isolation, you don't need to know what all your calls do to realise what your globals do.

You can set up local environments, so you can reuse codes that reuse the globals.

So, back to lisp.  Lisp local change is the norm.  Use let for assignments.  What let does is not what assignment do in Python, but introduces a new binding, when ... disappears and then all bindings come back.  After the inner let is finished, that is returned is the a from the external let and its values.

Equivalent in Python, you into deuce that shed all the old bindings, this is the equivalent Python to the previous lisp.

Let's keep this because it is not really important and we are short on time.

So, for Python, you still have the "with" statement in mind right?  The thing is for Python it is not enough to introduce those bindings with "with," because Python likes objects and mutables with lisp with the examples we have seen before, all the values for atomic.  With Python you can change parts of the variable without changing the variable.  So, that would not be enough.

Then the obvious problem with the code, you give it a global, it changes its inner parts, you are back to where we were before.  So, we need to make the objects immutable if we wanted to do this.

Slightly less obvious problem.  Sometimes we do want it to change even in a restorable way we do want to change just part of the object and then changing bindings will again not be a good solution.  So, we'll use something special for attribute change.

What we do and now I'm introducing the solution.  Library called lispism which explores a special object called D and its attributes are the dynamically scoped variables and this way we have them marked specifically so you don't mistake them for normal variables.  And for atomic values this looks exactly like the equivalent lisp.  You do with D let and then you have the values for the variables.  And then this prints first 1 when the value is 1, then 3 in the inner with and then goes back to 1.  .  And once you are out of the external with, you get a name error.

For containers, we do special frozen containers so after this, after the first let, you see that A has turned from a list to a topple which is immutable but the thing is they're deeply immutable, they're containers that also freeze their contents so if you access - so B is itself a topple but if you access its members in the originals they were lists.

And if I have a user defined type, with its own attributes, and its own - sorry some of them are just normal, some of them are containers themself, there are 2, one can only read and the other changes state of the object.

So, as long as I have tried to just read the object I get that I can access the attributes and that's OK.

If I try to modify an attribute I get a type error because it's a frozen object.

And attributes are controlled inside methods.  I can call the reader and get the frozen attributes.  If I call the rider I get a type error.

And I use ORM inspired syntax for changing specific attributes of objects.

Limitations of what I've done here.  First of all, the whole freezing thing is a consenting adults API.  That means that there are ways to go around it if you really want to.  The intention behind it is to prevent values from being changed by mistake, not to force them to be frozen.  That's one way you could just change attributes on a dynamically scoped variable without using let.

This a good thing because if anyone actually went to the trouble of writing something like this I suppose they know what they're doing.

And this is not as I said, not designed with security in mind, just with engineering.

I can't control extension models.  If anything is written in seasonally it's not really controlled by the pattern library that I wrote.

I can and do try to make sure that values returned from extension methods even though they - sorry, if - dynamically scoped variable holds an object with extension methods and they return objects I make sure those are frozen but I can't enforce that they don't change the variable.

There is this annoying quality of generators that if you write a generator using a dynamically coped variable you change with let and under that you do yield and the variable is changed so that doesn't work yet.  I have some things to do about it in mind but not done yet.

Dict access is currently a problem but again this will be handled.

And the future directions to go with this.  The library is currently public, you can't pip install it yet.  The repository is public.  And the next places I'm going to go is, 1, handling threading, if you have a set of dynamically scoped variables and I open a thread they should be inherited but currently they just use thread local storage so they are not inherited by new threads.

Macro py the library I alluded to earlier, I could use that to make better sub object control.  And it intend to do that.  I could do things like here, to do things like, for example, for I can access not just attribute access.

And another thing that is interesting and dynamically scoped variables enable is something called restarts which is an error mechanism which is in lisp, has not been adapted by any other language I'm aware of and I want to talk about restarts a little.

The idea behind restarts is that when you try to handle errors you're basically in a conflict.  The code protecting the error may be in the best position to do something about it, but it is not in the best position to make decisions.  Code higher up knows the big picture, knows what needs to be done, but has no access to details to actually do it.  So, when you try to catch an exception higher up most of the thing that caused the exceptions to be strong, to be raised are already gone because the stack was unwound.

So, the idea here is basically that the inner code instead of actually defining what to do defines options, it defines the different restart and each restart - the example is reading a set of a log file or a set of rows trying to pass each row, and recover when things go wrong.  And there are 3 options for recovery.  You could return a special record indicating error, you could return a default record saying this is OK, and you could drop in a debugger. But the decision of what is the right choice is not made my read rows by the function at the top, it's made by the function at the bottom which is the one calling things, and test parsers defines how to handle each of the errors that could come about, it maps exceptions to selection of restarts.

So, with the setting as it is here, if a record shows and the parser decides it's out of date then it returns an error record, but if it calls a parsing error it drops into the bug because it's still in development what we wanted at the moment.

And another important point about it is that the function in the middle, read file, knows nothing of this.  It just goes over rows and return - and read each row and collects - sorry just the function just holds opening the file, it doesn't need to know anything about the specifics of - neither of policy nor of details of error correction.  And that is only enabled by dynamically scope variables.

This is like research for the future project.  This is like - of course not valid python code just pseudo code.

There is a great paper explaining this in detail how it works in lisp not in Python.

So, that's pretty much what I have to say today.  Library will be released on PY PI soon but for now it's just a public repository.  I think greenspun's 10th rule of programming does not apply as strongly to Python programmes but it does in some degree.

That's all I have.  {Applause}.

DANIELE PROCIDA:	 Thank you very much.  We've got time for 2 quick questions.

NEW SPEAKER:	 Thanks it looks awesome and clever and dangerous I don't know.  I was wondering, is there any library that provides immutable that has structures for Python?

SHAI BERGER:	 Not that I'm aware of.

NEW SPEAKER:	 And have you heard about HY?

SHAI BERGER:	 Implementation in Python yes.

NEW SPEAKER:	 Thanks.

NEW SPEAKER:	 Thanks that was great so the question is yes have you used it for anything apart from like hey this will be cool?  Is it in use for like a real production system for doing that and what is that and why was that a good idea?

SHAI BERGER:	 Well, this is not yet in production for anything.  This is just something I thought would be cool at this point.  But, thought it would be call cool is the applications I have in mind for it are in Django.  I think doing this sort of making things globally available because most of the things that people want globally available they want usually for read only access -

NEW SPEAKER:	 Request object -

SHAI BERGER:	 Like the request object.  People want mostly read only access so we could give it to them with acceptable guarantees that they're not going to make too much trouble.  And I think that the thing with restarts would be very valuable for error ending an URL(?) for example.
