====================================================
Theofanis Despoudis: Django aggregations demystified
====================================================

NEW SPEAKER:  Just a brief announcement we are going the take a group photo before lunch in the lecture theatre here, if you want to be on the photo, please stay here for a minute or two, if you don't want to be on the photo, you can go straight to lunch.

Thank you.

VINCE:  Next speaker is Theofanis talking about aggregations.

THEOFANIS DESPOUDIS:  Look it is the guy with the windows!

So, thanks for having me today.  My name is Theo, I am a Greek man, I am living in Cyprus for now.  Today we are going to talk about like one thing that, for you, for the developers is a set of tools for doing aggregation, and annotations on your data.  So, a little bit of thing about me, I used to be the PHP developer, a pretty horrible pages developer I think a lot of people so you started.

I recently, I mean about six months ago starting programming with Python.  I have this you know, sound that the snakes do ssss and I work at social airways which is a platform for managing your flights, you can set flights and you can have friends on the flight and you can also do a lot of things with your account and stuff.

So, we can, it is going to be a small talk, not a big one, we are going the talk about aggregations.  Then we are going to continue with annotations and then they complement the aggregations notion and then we are going the maybe say a tips and tricks about this and then we are going the answer some questions.

So what are they?  What are the aggregations?  Basically, database functions, they are functions of the database.  Django has a nice layer on top of it.  You only have to deal with the effect you know.  You just call the method aggregate or annotate.  If your parameters are okay, it will return the result for you.  So it is useful for producing summaries and collections of objects.  You will have a look at collections of objects.  It will produce something you say that you need to produce.  So, we are going to see some examples later.

It is similar to the reduce function, you have a collection and then it applies the function and then it returns the results for you.

As a single volume.  These are some of the functions, that is, those are all supported in Django.  They are probably more in the database level but that is, the database limitations specific, some database support, some database don't support.  But the average marks means, in this, on the right hand side is the return value.  Return the float or the same field or any, or you know.

So we are going to just for this purpose of this demonstration, I have devised like a small database which is we have like this company so this company has like a mini games, on-line games.  It has this you know, database schema, then we have gamers, the gamer may like have a gender or a name or whatever he has.  We have a game, let's say the game is like on-line risk or on-line strategy game or whatever which is like strategy or an action, whatever we need to categorise it.

We have a game server, where the gamers register themselves.  Might be the chance that the gamer registers in multiple servers that is why we have the field here.

The game station, records the games played.  We have the game, when it is started, ended, linker to the server and then this mainly we save the result of the game.  Then we make sure that the session and the users is unique, so we have this session, this user has won or lost and these, he has accumulated like some points.  They might be a chance that we have like a game with like ten users, ten gamers?  Maybe some of them have lost, some of them have won and they will just record the result.

Just for a simple minimal database for we need to work on.

Then say let's say okay, how do you use this?  So let's say we need to count how many unique this is probably, how does it work?  We generate the query that is we apply the function and then we return the result.  It is 55 mate.

That is probably the yes.  So let's say we need to filter the results so we can apply filtering on the query sets and any kind of filtering, all the tricks and the things you know.  You can apply the filters about the user or find the user one or whatever.  Then we need to find the number of wins.  So, we remove the you know, the losses and we need to count only the wins.

This is the actually, query in the database.  So you want to do it by hand you probably do something like this.  But the nice thing is, that Django for this functionality for you, you don't have to do this, the other parts.  So left to use the API, the interface and then it will, it will help you build the query and look at the results.  That is a bonus for Django.

Also you can do like, you also have a standard deviation and variance, they have a lot of functions so you can while you are there, just compute the average of the scores and the session, then you can also add multiple you know, multiple results so you can have the average standard variation, with the sample and the variance.

All comes one the single results for its function you asked for.  So, let's continue with annotations.  So annotations helps you also, it is another way to have a summary.  This is a method that maps the differences, the aggregations aggregate, but these maps a summary value for each object.  So, any query set equates it.

So let's say, want to find the sum of all scores by each user, so we need to go for each user and find all the collective summary of all of these scores.  So how do we do this?  We just annotate the sum and nothing would do here, we just the ... we find the score.  So now, every scores, every gamer this score is a gamer object of course will have in addition a field game session result, because I didn't name it, it will give it to this name and then we will have this score, maybe the second will have another score.  This really great tool to just helps you know, collect all of those results in your, in the same place.

So let's say, min, max, sum.  Find the score of the session with the most scores accumulated.  So what we can do here.  We can annotate of course over the game session objects now.  We calculate all the sum of each game session object across the relationship then we can aggregate and we can continue with aggregation and we can use the sum of course and apply the Max function on it.  While we are there, you can also add all this game, access the free things because when we are over there, we can ask another thing.

The result is of course, the game with the maximum sum of scores, that is, it show it is result and the oldest game is like a daytime object.

Then what we can do is also slice and order our you know, annotations, so let's say you have, you want to ask what is the top five players by awarded points?  So annotate the gamer object.  You want to find his score, the sum of his score of all his games.  We want to filter some because they will appear in our as a result.  Then we need to apply ordering.  Descending, so the first one will be the highest score, the second the next highest score etc. We also slice the first five.

Then we can see that you know, the first gamer is like this guy and his points are like in these extra field.  Because we specified on the annotate you know, function that method.

So what else we can do?  We can group that is a really cool thing because grouping is a really nice thing to do.  You can use the values method of the related manager and if you do that it will just transform itself and it will group according to the fields specified.  What I mean by that, see in the example the results can be used later on for annotated or aggregated queries and then we will be merged into the common groups.  What I mean by that?  So let's say we have like three servers.  So we have, we can get the values and then we can annotate the count of the number of gamers.  So the servers in the US, have users registered, the Asia and the Europe.  If you want to group some of those results you could, you could make the reads the same for two values, that is probably the best way to do it but again for the demonstration, you could group the values for the Asia and the US and now if you go to the same, you can call the same method again it will merge the results so we have like six users from US and four from Asia, total ten from Asia, then the other one.  So it is really, if you are into the sequel, you know what grouping means, groups the values into the common group parameter, so in practice you should always check the generator query, you can do this with, like from the Django tool bar or you can use the you know, the go I, you can easily see what is being generated over the request or you can simply print the query set query class, which holds the generated query.

So this links to another presentation, if you can do it in this sequel, try to do it in Python.  If you have the option to do it in sequel, just do it in sequel.  Apply the function where the data is you can do it as Python but, I mean, it doesn't look good sometimes.

It can be aggregated.

So what I, this also linkers to another yesterday you know, and to another presentation, how do we use a proxy?  Maybe you can use it like this?  Maybe collect all your queries related to this what you want to do, what you want to achieve, it may be applied different ordering, maybe you want to display another page with another statistics, so you can put the proxy class and apply different ordering.  It maybe you can also create your own manager and then you can do all sorts of things as long as you stay with the boundaries of the proxy you know, proxy class.

So this is the last did for me, try to keep it simple.  You can get easily into you need to think of what is your problem basically because you can easily get, you know, you cannot easily get away with a lot of things.  You need to find what the problem is, what you are trying to achieve, how Django can help you solve that problem.  For us, for developers really easy, because we have a vast library of tools to use and so we have to think about what we are doing every time.  So, so all that the results, you need to think about if the result is actually worth it.  I mean, can we count it?  Cannot it be counted, I mean, what is the point?  You have to think about what you are doing so any questions?

(APPLAUSE).

VINCE:  First questions, come to the mic.

FROM THE FLOOR:  Can you hear me?  Thanks for the talk, so, you mentioned that we shouldn't do something in Python, if it can be done in SQL, I agree with that., we have a situation where we need to fetch the objects anyway?  We need to list them somewhere.  So is it better to do another SQL query, where we have to aggregate, or to use the same queries we fetch to do the?

THEOFANIS DESPOUDIS:  If you have the results in hand you can use it.  It is better if you reuse those capabilities so if you have like a function with, you have this aggregated function okay, if you use it one way, which will only one way, use it only once that is okay.  But if you want to use it many times maybe later on in your code, you might be putting it in the function, maybe in the aggregated query, to reuse it, so you don't have to deal with the situation of how do I filter?  How do I aggregate the result again?  Om have to call the mb, only have to call the manager and it will take care of the results for you.

FROM THE FLOOR:  Okay just another question, that is probably a question that is all over the internet, I didn't find the answer.

Can you filter the objects that you are annotating on?

THEOFANIS DESPOUDIS:  I think so, you can, because it is a query set it is, you can filter the query set.

FROM THE FLOOR:  I think it is an F object, it is not a query search.  I mean if you want to annotate for example, only.

THEOFANIS DESPOUDIS:  Because if you see the SQL generated it is a new field that gets applied so it is just like alliance, so you get this field back, so if it is like an F field you can, I think you can filter it.

FROM THE FLOOR:  For example, your example if I want to see how many won games for each user was, not all the games, only the ones that you won?

THEOFANIS DESPOUDIS:  If you want to find all the won games for each user, you have to count them first.  Then put them in an annotated you know, field.  So you have to annotate the count and find the, for each user, what is his number of wins.  Or maybe if you think about what the problem S you need to find the count of the wins for each user.

FROM THE FLOOR:  Okay thank you.

NEW SPEAKER:	 Hello thank you for your talk.  I am wondering if we can use annotation with some simple mathematical operations like if you want to subscribe to 2 fields?

THEOFANIS DESPOUDIS:	 Well, that where it gets really complicated because you can do things but cannot over exaggerate over things because there are probably more ways to do mathematics in Python than SQL.

NEW SPEAKER:	 For instance if you want to calculate the distance of the object -

THEOFANIS DESPOUDIS:	 You can do it but it's really tricky and it's gets into the rabbit hole experience, you're trying to find something that it might be easier to solve with another method.  So that's how you have to poor prioritise and say OK what is the data, what do I have in my disposal, what tools do I have and what's the end result?  So, you can try a lot of things but you may be - it may be not worth it sometimes so you may have to just use Python.

NEW SPEAKER:	 Of course thanks.

NEW SPEAKER:	 One very quick last question.

NEW SPEAKER:	 Direct response on that.  I'm not completely sure it's 1.8 or 1.9 and there will be some statistic functions in Django {inaudible} that have been launched a couple of weeks ago, at least there is something in that area going to happen.

VINCE:	 Thank you very much.  {Applause}.
