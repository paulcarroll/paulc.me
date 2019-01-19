---
title: Rethinking NodeJS
date: 2017-08-04 08:17:41
tags:
---

> Javascript on the server? Are you mad??!

That was my take on NodeJS for a long time, but now I quite like it.. in it's place.

I've read post after post expounding the virtues of the non-blocking technology but a few nagging thoughts lingered:

> How the hell the hell can you refactor an enterprise grade application without static type checking?

My opinion on that hasn't changed either, it's crazy. Tools like [WebStorm](https://www.jetbrains.com/webstorm/) are great for Javascript development, but even it will make mistakes when refactoring a variable, especially if it's a rather common word. That isn't a failing of the technology, it's a failing of the language; more over it's a failing of how the language is being used.

> How does `One language to rule them all` actually help my developers?

It doesn't. 

Programmers should be polyglots. Once they have an understanding of imperative programming, OOP or functional programming they should be able to pick another language that slight syntactic differences and be productive relatively quickly.

Domain specific langauges exist to help solve the problems of the domain, simple. Using javascript or Kotlin to query a SQL database is crazy because a well established language exists for that already (and has done so for over 40 years).

The other issue is switching between ES6 and client javascript with all the subtle differences between them and forgetting which version of javascript you're using. 

> Why isn't NodeJS multithreaded?

Is this still the case? I don't know and I'm not much bothered... architecture can make up that loss now; but more about that in another post.

## What's good then?

So I've not said anything positive yet, so here goes...

> NodeJS is great for microservices, especially looser services or sites that need to be fault tolerant. 

Take C# for instance. Great language, but eternally frustrating because one field not mapping (depending on your code base) can bring down the entire service request. 

Having the environment slap you in the face when you make a mistake is good, but it's terrible for the user. In this case it's much more desirable (generally) to keep working and miss that piece of information.

Clearly that logic doesn't work if you're a large bank, that's a different application and has to be precise. I'm talking about the soft services where you can get away with it and QC/users will find the missing information or unit tests will provide coverage. Things like:

* Messaging: Yes, not including the middle name or message title that was added last week might not be the best thing for a user, but it's better than the user picking pieces of monitor out of their face when it blows up.
* Search results: Ok, a few new things are missing, maybe highlighting breaks, better than a 500 error!
* Profile image resizing: So you image library cakes itself, I bet the user would rather a broken image than the whole page dying!

Another aspect is that NodeJS is so stupidly simple to get up and running it's criminal. 

It's fast too, super fast. Spinning up Java on Tomcat or C# (local IIS, Kestrel or IIS Express) seems like it takes an age. Not only that but the memory footprint for what you want to be a small little service is minimum in the region of 100mb. NodeJS instances spring to life with hardly any effort making development a breeze.
