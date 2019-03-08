---
title:  "A city tour with Capacitor from Ionic Team"
date:   2018-04-06 00:08:00
categories: [Capacitor, Native Web Apps, Hybrid App]
tags: [Capacitor, Angular5, Hybrid App, Native Web Apps, Ionic Framework]
comments: true
---

Hello everyone! Welcome to xMobe technology jungle ![xMobe - Smoke](https://s.w.org/images/core/emoji/2.4/svg/1f912.svg){:class="img-responsive"}{: width="20px"}. In this article, we are going on an **"Indiana Jones Journey"** with Capacitor.

### What Capacitor is?
Let's see the definition in [https://capacitor.ionicframework.com/docs/][https://capacitor.ionicframework.com/docs/]

>Capacitor is a cross-platform app runtime that makes it easy to build web apps that run natively on iOS, Android, Electron, and the web. We call these apps "Native Progressive Web Apps" and they represent the next evolution beyond Hybrid apps.

Yes, it is! Understand??? Just a little bit ![xMobe - Cry Smile](https://s.w.org/images/core/emoji/2.4/svg/1f602.svg){:class="img-responsive"}{: width="20px"} !!! The best way to get more understand with Capacitor is dig into it.

Before the start, please make sure you had install **npm 5** or above.

### Play with your Angular 5 project!
Yes, no Ionic 2&3 test as in the example, we one something different as Capacitor said in the definition. I'm going to create a new Angular 5 app with ng cli. Our app call **ngCap**:

```bash
ng new ngCap
```

Okay, done! Go inside the **ngCap** folder and now we need to install capacitor libs to start:

```bash
npm install --save @capacitor/core @capacitor/cli
```

The next step is telling Capacitor to init the necessary native platforms:

```bash
npx cap init
```

Please remember **npx** not npm, it's come from **npm version >= 5**. And follow the Capacitor guide you will get something like the following:

```bash
npx cap init
? App name ngCap
? App Package ID (must be a valid Java package) com.xmobe.ngcap
 Initializing Capacitor project in ~/capacitor/ngCap in 2.53ms


   Your Capacitor project is ready to go!  

Add platforms using "npx cap add":

  npx cap add android
  npx cap add ios
  npx cap add electron

Follow the Developer Workflow guide to get building:
https://capacitor.ionicframework.com/docs/basics/workflow
```

Now we have all thing to add platform? No, not yet. Like Cordova, Capacitor need a **www** folder to work. Like my previous article "[Angular 5 & Cordova][Angular 5 & Cordova]" and "[Angular 5 and Ionic 4][Angular 5 and Ionic 4]", we need to change ourDir in .angular-cli.json to www and build to make **www** available with Capacitor:

```json
"apps": [
    {
      "root": "src",
      "outDir": "www",
```

Then you can add Android and iOS platform by the following commands:

```bash
npx cap add android
npx cap add ios
```

Wait a few seconds to lets Capacitor make a great work for you.

```bash
npx cap add android
 Installing android dependencies in 10.75s
 Adding native android project in: /Users/anhlq/working/capacitor/ngCap/android in 97.10ms
 Syncing Gradle in 1.08s
 add in 11.93s
 Copying web assets from www to android/app/src/main/assets/public in 18.17ms
 Copying native bridge in 1.33ms
 Copying capacitor.config.json in 857.82μp
 copy in 45.42ms
 Fetching plugins in 3.21ms
Found 0 Capacitor plugin(s):

 update android in 7.80ms
```

and

```bash
npx cap add ios
 Installing iOS dependencies in 11.77s
 Adding native xcode project in: /Users/anhlq/working/capacitor/ngCap/ios in 71.25ms
 add in 11.84s
 Copying web assets from www to ios/App/public in 22.60ms
 Copying native bridge in 1.58ms
 Copying capacitor.config.json in 1.14ms
 copy in 33.39ms
 Fetching installed plugins in 3.97ms
[info] No Capacitor plugins found. That's ok, you can add more plugins later by npm installing them.
 Updating iOS native dependencies in 31.71s
 update ios in 31.71s
```

For iOS please remember you had to install CocoaPods. You can do it by the following command:

```bash
sudo gem install cocoapods
```

The last step quite easy, you just open Android or iOS project and test your result in emulators or real devices to test.

```bash
npx cap open android
npx cap open ios
```

![Capacitor - xCode](https://www.xmobe.com/assets/images/2018/04/Screen-Shot-2018-04-05-at-3.51.09-PM-1024x669.png){:class="img-responsive"}{: width="600px"}
![Capacitor - Android Studio](https://www.xmobe.com/assets/images/2018/04/Screen-Shot-2018-04-05-at-3.50.43-PM-1024x725.png){:class="img-responsive"}{: width="600px"}

If you need to make it work with Vue Project, no problem try with it but need some change that you can find in my other article with [Vue and Ionic 4][Vue and Ionic 4] to make Vue build in www folder. Yes, go ahead.

[Angular 5 & Cordova]: https://www.xmobe.com/angular/hybrid-app-from-angular-5-and-cordova/
[Angular 5 and Ionic 4]: https://www.xmobe.com/ionic/experiencing-ionic4-angular5-project-rc/
[Vue and Ionic 4]: https://www.xmobe.com/vue/vue-ionic-4-cordova-hybrid-lover/
[CocoaPods]: https://cocoapods.org/
[https://capacitor.ionicframework.com/docs/]: https://capacitor.ionicframework.com/docs/