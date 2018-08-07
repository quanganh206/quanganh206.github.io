---
title:  "NestJS as an Ionic 4 Backend"
date:   2018-08-08 09:01:00 +0700
categories: [Ionic 4, NestJS]
tags: [Ionic Framework, Ionic 4, NestJS, NodeJS, Typescript]
comments: true
---

Back to my blog for a long time. Now take a small touch to NestJS. Yes, if you familiar with Ionic 2, 3 (and now Ionic 4 for Angular) you should take a look at NestJS, I think it’s a cool thing for Angular’s man.

Thought out the dumb question “What is NestJS?“, you can find something like this in [https://docs.nestjs.com][https://docs.nestjs.com]

>“Nest is a framework for building efficient, scalable Node.js server-side applications. It uses progressive JavaScript, is built with TypeScript (preserves compatibility with pure JavaScript) and combines elements of OOP (Object Oriented Programming), FP (Functional Programming), and FRP (Functional Reactive Programming).”

I just want to show some quick and cool thing that you can do with NestJS to create a Backend for your mobile app build by Ionic 4. So let’s concentrate in the below list:
- Create your API in super time
- Call your new API in Ionic 4
- Easy get CORS done with NestJS

First, let’s make sure you have done all necessary installation that makes NestJS work in your machine. Remember to install @nestjs/schematics too.

Now we should start with:

```bash
nest new nest5api
cd nest5api
```

Yes you can “hot reload” your api in development with npm run start:dev.

Now create your first API endpoint. In NestJS, controllers are used to mapping endpoints to functionalities. So let create it by the command below:

```bash
nest generate controller items controllers
```

That command creates an Item Controller within the controllers folder. And then push some line of code like what you see:

![Items - Controller](https://www.xmobe.com/wp-content/uploads/2018/08/carbon-1.png){:class="img-responsive"}

Now test your API, I use Postman to call get with localhost:3000/items, and get something like that.

![Items - API Call](https://i0.wp.com/www.xmobe.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-07-at-10.33.45-AM.png?w=1960&ssl=1){:class="img-responsive"}

Okay, quite a good start. Now we jump into Ionic 4. Assume you start with an Ionic 4 project yet. If not here you go:

```bash
ionic start app4 sidemenu --type=angular
```

We going to create a Service with Angular Cli command:

```bash
ng g service items/item
```

![Items - Service](https://i1.wp.com/www.xmobe.com/wp-content/uploads/2018/08/carbon-1-1.png?w=1060&ssl=1){:class="img-responsive"} 

And add a minimum code like you see. And then try to use this in List Page.

![Items - List Page](https://i1.wp.com/www.xmobe.com/wp-content/uploads/2018/08/carbon-2.png?w=1480&ssl=1){:class="img-responsive"} 

Everything nice, but when I try to run with our new Backend, one thing happend.

![Cors - API Items](https://i2.wp.com/www.xmobe.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-07-at-10.46.48-AM.png?w=1402&ssl=1){:class="img-responsive"} 

NestJS have a nice way to do with CORS you can find it here https://docs.nestjs.com/techniques/cors

For our quick development you can have a simple change in your main.ts

![Cors - Main.ts](https://i0.wp.com/www.xmobe.com/wp-content/uploads/2018/08/carbon-3.png?w=1328&ssl=1){:class="img-responsive"}  

Then retest with what you have you can see your new List Page like below.

![Items - Page](https://i2.wp.com/www.xmobe.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-07-at-10.47.18-AM.png?w=598&ssl=1){:class="img-responsive"}  

Happy coding!!!

[https://docs.nestjs.com]: https://docs.nestjs.com