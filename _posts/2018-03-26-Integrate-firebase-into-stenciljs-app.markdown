---
title:  "Integrate Firebase Into Stenciljs App"
date:   2018-03-26 06:39:00
categories: [StencilJS, Ionic2, Ionic4]
tags: [Stencil, StencilJS, Web Component, Sass, Firebase]
comments: true
---

Hey, I'm back with one more StencilJS article. It's quite HOT now. In that article, I use our previous working so if you not familiar with StencilJS, please take a look these articles:

- [StencilJS and Ionic4 make easy][stenciljs-and-ionic4-make-easy]
- [Using SASS in your StencilJS App][using-sass-with-your-stenciljs]

Now, let's go ahead and see how we can integrate Firebase into our StencilJS App. The first step we need to install firebase into our app. 

```bash
npm i -S @firebase/app
```

Please remember `@firebase/app`, not `firebase`. Okay done! Go to **my-app** component .tsx file and then import firebase in the very top of your source code:

```typescript
import firebase from "@firebase/app";
```

And then in your MyApp class let working with **componentDidLoad()** event to config your firebase:

```typescript
componentDidLoad() {
    var config = {
      apiKey: "YOUR apiKey",
      authDomain: "YOUR authDomain",
      databaseURL: "YOUR databaseURL",
      projectId: "YOUR projectId",
      storageBucket: "YOUR storageBucket",
      messagingSenderId: "YOUR messagingSenderId"
    };
    firebase.initializeApp(config);
    console.log('Firebase configured! ', firebase);
}
```

Yes, now just test what we have:

```bash
npm start
```

Then open your Chrome or Safari console you can see something like that:

![StencilJS Ionic 4 - Firebase](https://www.xmobe.com/wp-content/uploads/2018/03/Screen-Shot-2018-03-26-at-10.56.31-AM-1024x371.png){:class="img-responsive"}{: height="206px"}

Thank for your reading. Hope it helps. See you in the next article with Firebase Authentication in StencilJS.

[using-sass-with-your-stenciljs]: https://www.xmobe.com/stenciljs/using-sass-in-your-stenciljs-app/
[stenciljs-and-ionic4-make-easy]: https://www.xmobe.com/ionic/stenciljs-and-ionic4-make-easy/