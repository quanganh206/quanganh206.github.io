---
title:  "Hybrid App from Angular 5 and Cordova"
date:   2018-04-04 06:39:00
categories: [Angular5, Cordova]
tags: [Cordova, Angular5, Hybrid App]
comments: true
---

Today we come back to the old question: How to convert my current Angular 4 or 5 into a Hybrid Cordova App?

>Yes, it comes from my experience with [Ionic4 Angular 5 RC][experiencing-ionic4-angular5-project-rc]. I think Ionic Team going on the right way with that step. Angular Developers familiar with ng client can quickly adapt with Ionic4 Angular. And furthermore, in the same way, we can make Ionic 4 working like that with React or Vue. -- my point of view ![xMobe - Smile](https://s.w.org/images/core/emoji/2.4/svg/1f601.svg){:class="img-responsive"}{: width="20px"}  --

Okay, let's go.

First, make sure you are install ng cli and cordova yet. If not, follow here.

Then we create a new Angular Project name ngCordova by that command:

ng new ngCordova
Please wait, everything automatically for you. Now go inside your new project and make some small change.

Open .angular-cli.json and change the output directory to www:

```json
{
  "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
  "project": {
    "name": "ng-cordova"
  },
  "apps": [
    {
      "root": "src",
      "outDir": "www",
```

The next step you need to create a new **config.xml** file for your cordova app.

```xml
<?xml version='1.0' encoding='utf-8'?>
<widget id="com.xmobe.ngcordova" version="1.0.0" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
    <name>ngCordova</name>
    <description>
        A sample Apache Cordova application that responds to the deviceready event.
    </description>
    <author email="dev@cordova.apache.org" href="http://cordova.io">
        Apache Cordova Team
    </author>
    <content src="index.html" />
    <access origin="*" />
    <allow-intent href="http://*/*" />
    <allow-intent href="https://*/*" />
    <allow-intent href="tel:*" />
    <allow-intent href="sms:*" />
    <allow-intent href="mailto:*" />
    <allow-intent href="geo:*" />
    <platform name="android">
        <allow-intent href="market:*" />
    </platform>
    <platform name="ios">
        <allow-intent href="itms:*" />
        <allow-intent href="itms-apps:*" />
    </platform>
</widget>
```

For easier, I suggest you should create a Cordova project by Cordova command and then copy **config.xml** to your Angular project. You can use a command like that.

```bash
cordova create ngCordova com.yourcompany.ngcordova NgCordova
```

Now, back into your current Angular Project folder. Then please run the following command:

```bash
npm run build
```

(*) I omit to see what ng client generate here, you can see the result by running ng serve command.

You will get the resulting app built in the www folder. It provides material for our Cordova App in the next step.

In that step, we working with Cordova command. We need to add necessary platforms:

```bash
cordova platform add android --save
cordova platform add ios --save
```

The next step we need to build android & ios app by the following commands:

```bash
cordova build android
cordova build ios
```

After that, you can see your working by the following command in the emulators or real devices:

```bash
cordova run android
cordova run ios
```

![Angular5 Cordova - iPhone X](https://www.xmobe.com/assets/images/2018/04/Simulator-Screen-Shot-iPhone-X-2018-04-03-at-21.45.45_iphonexspacegrey_portrait-1024x1024.png){:class="img-responsive"}{: height="500px"}

**Note**: if you working with routing, please remember to change base tag in index.html to this <base href="./">.

![Angular5 Cordova - Pixel 2](https://www.xmobe.com/assets/images/2018/04/Screenshot_1522767718_pixel_really_blue_portrait-1022x1024.png){:class="img-responsive"}{: height="500px"}


[experiencing-ionic4-angular5-project-rc]: https://www.xmobe.com/ionic/experiencing-ionic4-angular5-project-rc/
