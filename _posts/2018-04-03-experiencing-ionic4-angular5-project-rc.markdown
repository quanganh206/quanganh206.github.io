---
title:  "Experiencing Ionic4 Angular5 Project (RC)"
date:   2018-04-03 08:39:00
categories: [Ionic2, Ionic4, Angular5]
tags: [Ionic4, Angular5, Ionic Framework]
comments: true
---

Ionic 4 promises a bright future. A few days ago Ionic team drop an Ionic4 RC version. As a fan of Ionic Team many years I try to experience with Ionic4 Angular5 RC version. Yes, if you like it follow me!

First, we need to update our ionic cli:

```bash
npm i -g ionic@rc
ionic config set -g features.project-angular true
ionic start
```

The second command set the Angular project to true is necessary for our start. Then we going with ionic start command to start a new project. Then we follow Ionic client guide to go ahead. Give it a name, here is **ion4angular**.

```bash
[INFO] Every great app needs a name! 

       We will use this name for the project's folder name and package name. You can change this at any time. To bypass 
       this prompt next time, supply name, the first argument to ionic start.

? Project name: ion4angular
[INFO] What type of project would you like to create?

       We recommend angular. To learn more about project types, see the CLI documentation[1]. To bypass this prompt 
       next time, supply the --type option.
       
       [1]: https://ionicframework.com/docs/cli/starters.html

? Project type: (Use arrow keys)
❯ angular (recommended) | Ionic Angular v4+ 
  ionic-angular         | Ionic Angular v2/v3 
  ionic1                | Ionic 1 
```

Please choose **angular (recommended) | Ionic Angular v4+**. After that, we have no choice with a blank project 

```bash
? Project type: angular
[INFO] Let's pick the perfect starter template! 

       Starter templates are ready-to-go Ionic apps that come packed with everything you need to build your app. To 
       bypass this prompt next time, supply template, the second argument to ionic start.

? Starter template: (Use arrow keys)
❯ blank | A blank starter project
```

And then you will be asked to add Cordova or not and Ionic Client will auto install necessary libraries for you.

I assume you finish the rest steps and have to go to your ion4angular folder. Open it with your best IDE and take a look.

![Ionic4 Angular RC - Angular Cli](https://www.xmobe.com/assets/images/2018/04/Screen-Shot-2018-04-03-at-4.01.32-PM-1024x683.png){:class="img-responsive"}{: height="500px"}

Ooh, surprise? Yes! It's look like an Angular Client project!!! For the rest of thing, you will see it quite the same with your old Ionic 3 project.

Dig more into package.json you will see some new: **@ionic/core**, **@ionic/angular** etc.

Let's see the Home Page, no special syntax here:

```html
<ion-header>
  <ion-toolbar>
    <ion-title>
      Ionic Blank
    </ion-title>
  </ion-toolbar>
</ion-header>

<ion-content padding>
  The world is your oyster.
  <p>If you get lost, the <a target="_blank" href="https://ionicframework.com/docs">docs</a> will be your guide.</p>
</ion-content>
```

Now it's time going to running ionic serve to see our result.

```bash
ionic serve
> ng serve --host=0.0.0.0 --port=8100 --progress=false
[ng] 
[ng] @angular/compiler-cli@5.2.9 requires typescript@'>=2.4.2 <2.7.0' but 2.7.2 was found instead.
[ng] Using this version can result in undefined behaviour and difficult to debug problems.
[ng] 
[ng] Please run the following command to install a compatible version of TypeScript.
[ng] 
[ng]     npm install typescript@'>=2.4.2 <2.7.0'
[ng] 
[ng] To disable this warning run "ng set warnings.typescriptMismatch=false".
[ng] 

[OK] Development server running!

     Local: http://localhost:8100
     External: http://10.245.190.125:8100
     DevApp: ion4angular@8100 on deepthought.lan

[INFO] Browser window opened to http://localhost:8100!

[ng] webpack: wait until bundle finished: /
```

Exactly, it's just run ng serve.

Furthermore, we should try with emulators and real devices.

```bash
ionic cordova platform add android
ionic cordova platform add ios

ionic cordova run android | ios
```

Ohh Huuu! It's not working, just a blank page!!!

Now let's go to your index.html page and change the base tag to:

```html
<base href="./" />
```

And retest with ionic cordova run android | ios. Ohh, it's working my friends! And here is the result

![Ionic4 Angular RC - iPhone X](https://www.xmobe.com/assets/images/2018/04/Simulator-Screen-Shot-iPhone-X-2018-04-03-at-15.13.06_iphonexspacegrey_portrait-1024x1024.png){:class="img-responsive"}{: height="500px"}

Now, maybe you want to see more example code. Please go to new ionic conference app here: [https://github.com/ionic-team/ionic-conference-app/tree/core-update][https://github.com/ionic-team/ionic-conference-app/tree/core-update].

If you need more articles or think it helpful, please leave me comments here.

Hope it helps to save time in development. Happy coding!!!

[https://github.com/ionic-team/ionic-conference-app/tree/core-update]: https://github.com/ionic-team/ionic-conference-app/tree/core-update
