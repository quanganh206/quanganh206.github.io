---
title:  "Firebase Authentication with StencilJS – Google"
date:   2018-03-27 09:39:00
categories: [StencilJS, Ionic2, Ionic4]
tags: [Stencil, StencilJS, Web Component, Sass, Firebase, Firebase Authentication, Google Authentication, Authentication]
comments: true
---

Today we will pay a litter attention to our StencilJS App security. This article will try to push Google Authentication to work in our previous app.

This article assumes that you can create your own StencilJS App, integrate SASS, Ionic 4 and Firebase into your App. If you not familiar with it please recheck my previous articles here:

- [Starting with StencilJS Web Components Compiler][starting-with-stenciljs-web-components-compiler]
- [StencilJS and Ionic4 make easy][stenciljs-and-ionic4-make-easy]
- [Using SASS in your StencilJS App][using-sass-with-your-stenciljs]
- [Integrate Firebase into StencilJS App][integrate-firebase-into-stenciljs-app]

Let’s install @firebase/auth lib to your StencilJS App.

```bash
npm i -S @firebase/auth
```

Now we make some change in our **my-app** component. Of course, we need to **import @firebase/auth**. And we need some **@State** to control my-app component state.

```typescript
import '@firebase/auth';
import { Component, State } from '@stencil/core';
...
export class MyApp {
  @State() loading: boolean = true;
  @State() user;
  ...
}
```

In my previous app my-app component had import firebase yet with import firebase from `@firebase/app1`; now we will use it to detect firebase authentication state. Please push the following code after firebase config:

```typescript
componentDidLoad() {
  ...
  firebase.auth().onAuthStateChanged(user => {
      this.user = user ? user : null;
      this.loading = false;
      console.log("user authed", user);
  });
}
```

Next step we need to add a new component app-login and update our router to make it work with Firebase Authentication:

```shell
yo stencil-component app-login
```

Leave an empty path, that generator will help you create a new component in components folders. And you will have **app-login.scss** and **app-login.tsx** files in **src/components/app-login** folder.

Let’s take a look at our new router config:

```typescript
render() {
    return (
      <ion-app>
        <ion-router useHash={false}>
          <ion-route 
            url='/' component='app-home'
            componentProps={{ firebase: firebase, user: this.user }}
          />
          
          <ion-route
            url="/login"
            component="app-login"
            componentProps={{ firebase: firebase }}
          />
          <ion-route url='/profile/:profileName' component='app-profile'/>
          <ion-route-redirect from="/*" to={this.user ? undefined : "/login"} />
          <ion-route-redirect from="/login" to={this.user ? "/" : undefined} />
        </ion-router>
        <ion-nav swipeBackEnabled={false} main></ion-nav>
      </ion-app>
    );
}
```

Just look like the previous Route config, URL path and specify the component. One more thing you can see here is `componentProps`, it does the magic thing that helps us passing data between components. Thanks, Ionic Team for that magic feature.

The rest redirect just have some small confuse code with `this.user ? undefined : “/login”`. It’s just conditional Ternary Operator if you can not recognize it.

Now we jump into the app-login component:

```typescript
import { Component, Prop } from '@stencil/core';
@Component({
  tag: 'app-login',
  styleUrl: 'app-login.scss',
})
export class AppLogin {
  @Prop() firebase;
  googleLogin() {
    console.log("google login");
    let provider = new this.firebase.auth.GoogleAuthProvider();
    provider.addScope('profile');
    this.firebase
      .auth()
      .signInWithRedirect(provider)
      .then(result => {
        console.log('result', result);
      });
  }
  render() {
    return [
      <ion-header>
        <ion-toolbar>
          <ion-buttons slot="start">
            <ion-menu-button></ion-menu-button>
          </ion-buttons>
          <ion-title>Login Page</ion-title>
        </ion-toolbar>
      </ion-header>,
      <ion-content padding>
        <ion-button onClick={() => this.googleLogin()}>Google Login</ion-button>
      </ion-content>
    ];
  }
}
```

Okay continue with the componentProps in my-app component pass to app-login. We need to import Prop decorator and then using it with `@Prop() firebase;` to get firebase passing from my-app component.

The second thing inside app-login component is calling `signInWithRedirect` with Google Auth Provider to make a login with Google Authentication. Yes that allllll, that’s easy huh?

I make a small change to home to show the result

```typescript
import { Component, Prop } from '@stencil/core';
@Component({
  tag: 'app-home',
  styleUrl: 'app-home.scss'
})
export class AppHome {
  @Prop() firebase;
  @Prop() user;
  render() {
    return [
        <ion-header>
          <ion-toolbar color='primary'>
            <ion-title>Stencil Ionic App</ion-title>
          </ion-toolbar>
        </ion-header>,
        <ion-content padding>
          <p>
            Welcome to the Stencil App Starter.
            You can use this starter to build entire apps all with
            web components using Stencil!
            Check out our docs on <a href='https://stenciljs.com'>stenciljs.com</a> to get started.
          </p>
          <p>
          {this.user.displayName}: {this.user.email}
          </p>
            <ion-button href="profile/stenciljs">
              Profile page
            </ion-button>
        </ion-content>
    ];
  }
}
```

Now it’s time to test:

```bash
npm start
```

Then open your Chrome or Safari console you can see something like that:

![Firebase Authentication with StencilJS – Google - 01](https://www.xmobe.com/wp-content/uploads/2018/03/Firebase-Authentication-with-StencilJS-02.png){:class="img-responsive"}{: height="206px"}
![Firebase Authentication with StencilJS – Google - 02](https://www.xmobe.com/wp-content/uploads/2018/03/Firebase-Authentication-with-StencilJS-03.png){:class="img-responsive"}{: height="206px"}
![Firebase Authentication with StencilJS – Google - 03](https://www.xmobe.com/wp-content/uploads/2018/03/Firebase-Authentication-with-StencilJS-01.png){:class="img-responsive"}{: height="206px"}

Hope it helps to save time in development. Happy coding!!!

[starting-with-stenciljs-web-components-compiler]: https://www.xmobe.com/stenciljs/starting-with-stenciljs-web-components-compiler/
[using-sass-with-your-stenciljs]: https://www.xmobe.com/stenciljs/using-sass-in-your-stenciljs-app/
[stenciljs-and-ionic4-make-easy]: https://www.xmobe.com/ionic/stenciljs-and-ionic4-make-easy/
[integrate-firebase-into-stenciljs-app]: https://www.xmobe.com/ionic/integrate-firebase-into-stenciljs-app/