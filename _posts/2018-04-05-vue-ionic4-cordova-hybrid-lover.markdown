---
title:  "Vue + Ionic 4 + Cordova = Hybrid Lover"
date:   2018-04-05 06:39:00
categories: [Ionic2, Ionic4, Vue]
tags: [Ionic4, Vue, Ionic Framework]
comments: true
---

Hey, as I talk in the previous article, today we are going to create a Hybrid Cordova App with Ionic 4 and Vue. Let's see how easy it is with Ionic 4.

Not like what we do with [Angular 5 & Ionic 4][experiencing-ionic4-angular5-project-rc], Vue Client quite smart to help us create a hybrid app more easier and faster.

The first step we play with Cordova command, here we create a new project in ion4vue, with the package name is com.your-company.ion4vue and Display Name is Ion4Vue.

cordova create ion4vue com.your-company.ion4vue Ion4Vue
Then the next step we push Vue Client into its job. Let's create a Vue project inside the same folder ion4vue by the following command:

```bash
vue init webpack ion4vue
```

Remember to answer YES to the question: Target directory exists. Continue? Then following Vue Client's guide, you can complete the initiation Vue's project.

```bash
vue init webpack ion4vue

? Target directory exists. Continue? Yes
? Project name ion4vue
? Project description A Vue.js project
? Author Quang Anh <quanganh@aiti.com.vn>
? Vue build standalone
? Install vue-router? Yes
? Use ESLint to lint your code? No
? Set up unit tests No
? Setup e2e tests with Nightwatch? No
? Should we run `npm install` for you after the project has been created? (recommended) npm
```

Congratulation, you've done the first step of our great app. Let's go inside Vue's project folder ion4vue and open it with your favorite IDE to look around.

![Vue Ionic4 Cordova Hybrid App - Visual Studio Code](https://www.xmobe.com/wp-content/uploads/2018/04/Screen-Shot-2018-04-04-at-4.39.45-PM-1024x686.png){:class="img-responsive"}{: height="500px"}

Now it's time the Ionic4 come & take the ball. Please open your index.html file and add the following line to it.

```html
<script src="https://unpkg.com/@ionic/core@0.1.5/dist/ionic.js"></script>
```
Your index.html will look like that:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>vue-ionic</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script src="https://unpkg.com/@ionic/core@0.1.5/dist/ionic.js"></script>
  </head>
  <body>
    <div id="app"></div>
    <script src="/dist/build.js"></script>
    <script type="text/javascript" src="cordova.js"></script>
  </body>
</html>
```

Okay, Ionic4 integration with Vue done! Go ahead, let make some change in your App.vue to see how nice it is?

```javascript
<template>
  <ion-app>
    <ion-header>
      <ion-toolbar class="primary">
        <ion-title>Ionic 4 Vue</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content padding>
      <h3>This is an Ionic 4 & Vue Hybrid App</h3>
      <p>
        We have some nice products in our <a href="https://xMobe.com">https://xMobe.com</a>, please take look.
      </p>
    </ion-content>
  </ion-app>
</template>
```

I push some traditional Ionic tags... One thing to remember here is you need to include **<ion-app>** tags. 

Now you can test with what you did in the browser with command:

```bash
npm run start
```

and you can see the result like that:

![Vue Ionic4 Cordova Hybrid App - Google Chrome](https://www.xmobe.com/wp-content/uploads/2018/04/Screen-Shot-2018-04-04-at-4.56.23-PM-950x1024.png){:class="img-responsive"}{: height="500px"}

Great! Now you can testing with Cordova, but please wait. Vue build process will generate your app content into dist folder. But Cordova just accepts www folder. We need some small config here to make it work with Cordova. 

Let's look at the index.js in the config folder. And change the follow lines:

```js
build: {
    // Template for index.html
    index: path.resolve(__dirname, '../dist/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../dist'),
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
```

to

```js
build: {
    // Template for index.html
    index: path.resolve(__dirname, '../www/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../www'),
    assetsSubDirectory: 'static',
    assetsPublicPath: './',
```

Yes, done! Now we can play with Cordova command to build and run our Ion4Vue app in emulators or devices.

```bash
cordova build android | ios
cordova run android | ios
```

And please remember to add your desired platform before doing like that. Especially you can change the running scripts in package.json to help you integrate Vue build process with Cordova Build/Run process to make it work together in just one command.

Yeah, happy coding!!!

[experiencing-ionic4-angular5-project-rc]: https://www.xmobe.com/ionic/experiencing-ionic4-angular5-project-rc/