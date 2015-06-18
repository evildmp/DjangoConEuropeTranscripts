============================================
Stefan Foulis: Local development with docker
============================================

Our next speaker is going the need internet access, we are having a few problems with connectivity today, so, unless you are doing something life or death right now on your phone or lap top, just close it for the next 20 minutes that will be greatly appreciated.

DANIELE PROCIDA:  I am specially pleased to introduce Stefan Foulis from DVO and it is I had the privilege of having him for a colleague at DVO, so a great pleasure to work with him and pleased to have him here speaking at Djangocon.

(APPLAUSE).

STEFAN FOULIS:  Thank you Daniele, so today I will be talking about local development and local Django development with docker, so I will briefly introduce what docker is and what the benefits are of using docker.  I will look at some basic docker concepts and then we are going to create a dockerised Django product.  Then use docker compose to define our stack, so run the stack locally, as a bonus, if we have time I will show you how to use nice urls's with a proxy and docker.

Most of this works without internet, I think just to make sure, I think we maybe sacrifice something to the demo gods, for that I have kittens (LAUGHTER).

So let's delete or sacrifice one or.  (APPLAUSE).

Hopefully that is enough!

(APPLAUSE).

I still have some kittens just in case, so, let's see if we can do this.

First of all, I am going the just want to show you a scenario, so got a new project just checked out the repository and you want to get this up and running.  You are go the docker directory, the docker composer comes up.  Start all the containers needed for the application, we are starting cob stainers and the web application, then the familiar run server.  So everything is running.  I can switch over to my web browser, open this IP and there we go.  That is the web app already running, in this case, just language containers running in, that is for debugging purposes and already using the cache, 3 second cache and a longer cache, so we see every 3 seconds it is updated so show you how the cache works.

I want to guide you through the way this.  I want to find my presentation again, dam kittens!

There we go.

So what is docker?  To make it really simple kind of like a virtual machine.  If you understand how to make virtual machines work to understand the analogy.  It is efficient, run them in a host.  Not the overheads, you can launch new containers within milliseconds, not in seconds and minutes like with a virtual machine.  The main selling point is the set of tools around it to build and share your applications with others and we will have a look at that with docker images.

The party between development and production.  Because you can really run the same code bit for code, the operating system, every library that is installed, the development and production.

So some of the common things you will hear, combination with docker, here is the image, this is you can think of a template.  To go back to the virtual machine analogy, a virtual machine, packages then make a snapshot then use it as a basis for a bunch of other machines you run, those will be containers in the docker world.

Then there is the registry, a useful place where you can share and distribute those images, those reusable images.

Here is some of the operations you can do in docker, at the right hand side the machine, you can docker pull an image which you would get from external registry for example, or build locally with the help of the docker file, once you have it you can run it.

On docker hub, there is ready to use images, like we are using in this example.  Django image in docker that is just insanely easy to use.  So, if you, images work in layers and that is how it does this with these different images so, there is for example, a debian8 docker image and then the Python image.  Then there is the Django image that builds on top and adds it stuff.  At the end your app which adds whatever is specific to your application and of course your source code.

A docker file to run a Django app is just this one line.  In this case it is using the own built trigger, automatically detect your ... copy your source code into the image, there is not more needed.  To see an example of how docker files work, I will make an example of using the Python ... so this is a docker file, start off using the Python image, install some packages, we want the mysql client, couple of things, create a directory, make this the default directory, copy in our requirements, install them.  Copy in the rest of the source code, tell docker we are expecting to expose part 8,000., requirements file is simple.  Just Django, now if you want to start a project from scrap, use docker build to build this docker file which is created dash T defines the tag, the name the image is going to have.  Then use start project which basically we do docker run, IT means run it interactivity, ...  -- V mounts your local source code into the container and user is needed for permission reasons for mounting that folder.  Then we run the general admin start project and you are all set.

We can run the container now with docker run, the same thing, the only thing is we tell it to map the port 8,000 on our local machine, to the port 8,000 on the local container.

... default command for this imam, but listed it here for completeness.

Docker compose, a command line tool that adds a yml file which describes the whole stack, a combination of multiple docker images and build them together to a whole stack.  So I will switch over to demo again and show you such a composed file.

So, here at the top you see it is, we all our main container we call web, we tell it to, if we want to build it, build in the current directory, add this to your project.  We do the volumes like we defined before in the direct command as well.  Mount the directory for our up loaded media, so we don't lose that when we recreate and destroy the container.  Map the port again.

This is where it is interesting, link other containers into this one, take the container and map it in this container with the name postgres., this is straightforward, pulls it from the docker hub and you are good to go already, all we do is define the password.  The database here, the host is postgres.  ... Makes the host and matches that name to the IP address of the other container using postgres.

We have extracted the most important ones here, of course you will have to update your settings a little bit to follow this convention, so here, you see, we are setting secret key based on the environment and using some reusable tools like Django database and create settings out of it.

I got the docker file is a simple one, just the Django template we have built.  So basically we are ready to try this out.

This is the app I started previously, I will kill it.  So all containers are stopped again.  Actually completely delete those containers.  So this is now wiped postgres container, wiped the data, starting afresh.

This time, I am going the do compose up with no recreate and just a web container to show that it will automatically detect I need these other images because I need the links.  Start them up, no recreate, tells it not to rebuild the containers if not needed otherwise we will lose the postgres data every time we start.

So we have our up and running again.  You see, Django is already complaining oh, we forgot to migrate our migrations, this is pretty straightforward, so here is the command, docker compose run, which will with the web components tell it, well I want to run this in the context of the web component and run the command.  I will run, now I will end up in this container and I can run multiple commands so it is a bit faster than running, than less typing than always typing the whole thing, so I can just Python, manage, migrate.  Here.

There we go.

While we are at it, we will create a superuser.

Great.  So, let's switch back to the browser.  See if it is still working?  Yes, we are still up.  Now we can also log into admin, with our newly created user.

So, let's say we have this extra little application, myapp doesn't have any migrations, you go about this the same way, every time docker compose run, web, your commands or step into the container and just do them one by one, we will make the migrations for this app.

There we go.  And we will go ahead and run them as well.

So, another thing that is a bit different than when you normally develop in your machine, when you need to add dependencies, in order for dependencies be picked up by all of your containers you are running, add to requirements and rebuild the whole container, a trick there is you can also just add them.  If you have a single requirement and don't want to rebuild everything, you can use caching mechanism to your build.  Install that one package you need for experimenting but before committing this to code, you should probably put it in requirements.  Py.

Once you have rebuilt the container so the command to rebuild it with docker compose would be build then the name of the container.  To be really sure that it actually gets the new image, it's a good idea to delete the container and recreate it.  It's also good to do that when you change for example environment enables because it doesn't always pick those up automatically.

Another slightly different thing that you have to take care of if you want to use tools like PPB(?) with docker move up you won't have an interactive console it's just a log output but you can run data in another way that it's because to have an interactive console so run docker compose run instead of up and you tell it to service ports extracting which means also maps your port into a container like it would do when you normally do up and when you start the container like this you'll actually have an interactive console here and can do PDP debugging.

There is another neat way you can change stuff, for now every time we do docker compose run it creates a new isolated container that is not part of the web container already running but there is a command to step into, an existing container.  And that is docker exec.  So I can do docker exec IT for interactive, I choose a container, let's take our web container.  Run bin bash.  May be have to sacrifice some kittens.  No don't want to kill more kittens - what you do here is step into the processing space of existing running container then if you do PS for example you see the same processes running that you see when running the run server.

Another neat thing is a package called - or docker image called N gin X proxy.  We run this on our developer machines on port 80 and port 1 1 3 so does all the proxy for {inaudible} run locally and this is smart enough to watch docker and see any containers that get started up and if you have an container that has environment virtual set like this it will run any request for that virtual host to the correct container.

So what this gives you is that you can actually run your web-site like this which probably won't work now.  So you can have real URLs for your web-site.  This alleviates problems you might have with cookies when you run stuff on different ports, makes things way simpler in that regard.  It also has the functionality of doing SS L determination so for our older stack we have SS determination for older development as well and that allows us to really test the different services how they interact much better than if we have just http.

Okay I think I am running out of time.

Let's go to questions.  Thank you.  {Applause}.

NEW SPEAKER:	 How do you keep track packages installing your dock images and -

NEW SPEAKER:	 Can't hear you?

NEW SPEAKER:	 How do you try stacker images make sure all your images are to date with all the latest secret batches?

STEFAN FOULIS:	 Updated images on docker hub and make sure you get those locally?

NEW SPEAKER:	 Yeah or that images on docker hub web are updated with latest open SSL or mercury or ability -

STEFAN FOULIS:	 Basically it's to you if there is a dependent image you are using that has a bug you have to rebuild your application based on that.  There are tools on docker that make this easier so if you have docker hub build your image as well a service they have you can have build triggers that will automatically rebuild your image if one of your dependent images changes which means you always have up-to-date version in that cases you still have to remember to employ that to your live system but that alleviates it a bit.

NEW SPEAKER:	 Hi there.  Why should I move from vagrant to docker as a sort of development environment?

STEFAN FOULIS:	 Well you think it's a good idea or?

NEW SPEAKER:	 No - I never heard of docker much and I just wondered.

STEFAN FOULIS:	 It's much more light weight specially if you have a lot services that are different, if you have one part it's only a no dap or Django app and have different dependencies what they need on the system.  It's easier to spend up 10 docker systems with different operating systems than 10 vagrant systems with different operating systems.

NEW SPEAKER:	 Thank you.

NEW SPEAKER:	 Thank you very much.  Do you think there is any benefit of using Ansible with docker?

STEFAN FOULIS:	 You mean use Ansible to build docker images or -

NEW SPEAKER:	 Yes -

STEFAN FOULIS:	 I don't think so because the nice thing about the docker files is basically you don't have to maintain your image over time because whenever there is any change you just rebuild the whole thing and you redeploy a whole new artefact so what Ansible is strong on I think is keeping servers up-to-date with what you've defined to be your stack over time which isn't really needed with docker any more so the docker file I think is perfectly enough to build those docker images.

DANIELE PROCIDA:	 2 very quick ones.

NEW SPEAKER:	 First question.  Do you use docker in production.  If yes how do you manage to keep user data and put database on this containers if you need to rebuild them?  If not why not?

STEFAN FOULIS:	 OK so we do use docker in production.  We make sure toe that the containers are state less so any up loaded files for example on the sites me host go into a shared storage back hand.  The postgres database is running in docker but not running in those containers, it's running separately as a service and we're using that and with postgres for example if you want to get your data outside of the container you mount the directory and have the data part outside the container so you reconstruct them.

NEW SPEAKER:	 If I may, how do you manage different versions if you have to all {inaudible} container NEW SPEAKER: SF of the what?

NEW SPEAKER:	 For example postgres data 3, and 4, have to change data of underlying files -

STEFAN FOULIS:	 It's the same process you do traditionally with a server so make sure you migrate the data when you upgrade.

NEW SPEAKER:	 OK thanks for your talk.  Say you have your own project and have gone down a rabbit hole writing your 5,000 line bash script to build everything up and only just heard of docker, do you have any advice for converting your existing projects over to docker?

STEFAN FOULIS:	 Really depends if you're having problems with your current set up.  If you're not having any specific problems for them I don't see a good reason there but of course it's useful for new developers starting on a project because the only dependency they need to install is docker so if you have a lot of new developers working on your project probably until they have that set up it will take a long time if you don't have a good reproducible set up.

DANIELE PROCIDA:	 Thank you very much Stephan.  I won't keep you but I've got an important announcement before we go into our break.  Let me just quickly do this.  OK so I'm about to put through the order for the sprints catering on Thursday and Friday.  According to this, we have got 248 people coming to lunch on Thursday.  199 on Friday.  But only 137 are coming to the sprints party on the evening of Thursday in-between.  So, this is why we need you to give us accurate information because we don't want to have a party expecting 137 people then have 248 turn up because some of you will go hungry and go home disappointed so what you need to do is go to your teeto ticket.  You have one of these on every single email message that came to you from teeto practically and just answer the questions.  Hit change to do that and say yes I will be coming to this meal or that meal.  This will be on your individual or corporate or sponsor ticket the one for the whole event the first ticket you bought.  If you can do that straight away we'd be very grateful.

I'll let you get your coffee now.  Be back promptly at 5 past, an extra 5 minutes because we have a special announcement for you of something that's been kept secret until now.

(Break)
