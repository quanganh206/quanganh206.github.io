---
title:  "StencilJS and Ionic4 make easy"
date:   2018-03-24 3:03:18
categories: [StencilJS, Ionic2, Ionic4]
tags: [Stencil, StencilJS, Web Component, Sass]
comments: true
---

As you know Ionic Team had done a great thing with Ionic Framework from version 1 to 3. All thing seems amazing! But how we can use that amazing thing in our new StencilJS app? Let's start to do it.

What'll we do in that article:
- StencilJS and @ionic/core library
- Styling with SASS (you can reference using SASS with StencilJS [here][using-sass-with-your-stenciljs])
- Simple routing to navigate through the app

## Starting with a new StencilJS App

```bash
git clone https://github.com/ionic-team/stencil-app-starter stencil-ionic4
cd stencil-ionic4
git remote rm origin
npm install
npm start
```

Because we want to start from the scratch so we will delete all components folder and recreate a new one in the ./src folder.

```bash
# in the src folder
rm -Rf components
mkdir components
```

## Install necessary libs
```bash
npm i -S @ionic/core @stencil/sass
```

Tips: I suggest you update the latest `@stencil/core`, in that article I use `@stencil/core@^0.7.7`. For config SASS to work with StencilJS you can follow that [article][using-sass-with-your-stenciljs].

## Our App's Component Structure
To make it easier and more familiar with the previous article. We will use the same components **my-app**, **app-home** and **app-profile** to describe how it works. Simple each component we will have 2 main file, one for style .scss file and one for .tsx file to render our component.

Let's look at first component *my-app*:

```typescript
import '@ionic/core';
import '@stencil/core';
import { Component } from '@stencil/core';


@Component({
  tag: 'my-app',
  styleUrl: 'my-app.scss'
})
export class MyApp {

  render() {
    return (
      <ion-app>
        <ion-router useHash={false}>
          <ion-route-redirect from="/" to="home" />

          <ion-route url='/home' component='app-home'></ion-route>
          <ion-route url='/profile/:profileName' component='app-profile'></ion-route>
        </ion-router>
        <ion-nav swipeBackEnabled={false} main></ion-nav>
      </ion-app>
    );
  }
}
```

You'll see it quite like your previous StencilJS App, just change the main tag to ion-app tag and stencil-route to **ion-route**. The second important thing here is ion-nav, it's the same with what you always see in previous Ionic2, 3 Apps.

```html
<ion-nav swipeBackEnabled={false} main></ion-nav>
```

All your pages navigation will be controlled by that component.

Now we move to app-home component:

```typescript
import { Component } from '@stencil/core';

@Component({
  tag: 'app-home',
  styleUrl: 'app-home.scss'
})
export class AppHome {

  render() {
    return [
        <ion-header>
          <ion-toolbar color='primary'>
            <ion-title>Stencil Ionic App</ion-title>
          </ion-toolbar>
        </ion-header>
        <ion-content padding>
          <p>
            Welcome to the Stencil App Starter.
            You can use this starter to build entire apps all with
            web components using Stencil!
            Check out our docs on <a href='https://stenciljs.com'>stenciljs.com</a> to get started.
          </p>

            <ion-button href="profile/stenciljs">
              Profile page
            </ion-button>
        </ion-content>
    ];
  }
}
```

Yes, amazing! The same with Ionic 2, 3 Page as we did. Here we have a `href="profile/stenciljs"` to navigate to app-profile page.

```typescript
import { Component, Prop } from '@stencil/core';

@Component({
  tag: 'app-profile',
  styleUrl: 'app-profile.scss'
})
export class AppProfile {

  @Prop() profileName: string;

  render() {
    return [
      <ion-header>
        <ion-toolbar color='primary'>
          <ion-title>Profile Page</ion-title>
        </ion-toolbar>
      </ion-header>,
      <ion-content padding>
        <p>
          Hello! My name is {this.profileName}.
          My name was passed in through a route param!
            </p>

        <ion-item>
          <ion-label>Notifications</ion-label>
          <ion-toggle checked={false}></ion-toggle>
        </ion-item>
      </ion-content>
    ];
  }
}
```

Still the same Ionic 2, 3 page content, maybe you can reuse some of your previous UIs. And one more magic here, you can easily get passing value from profile route with StencilJS `@Prop() profileName: string`.

Now we can take a look with what we did here:

```bash
npm start
```

And you can get the app working as below.

![StencilJS Ionic 4 - 01](https://www.xmobe.com/wp-content/uploads/2018/03/stenciljs-ionic4-01.png){:class="img-responsive"}{: height="360px"}
![StencilJS Ionic 4 - 02](https://www.xmobe.com/wp-content/uploads/2018/03/stenciljs-ionic4-02.png){:class="img-responsive"}{: height="360px"}
						 						
Next articles we will try to work with Menu and Tabs in StencilJS and Ionic4. See you soon!

Tips: if you boring with creating components you can use my small tool here to save your typing time.

```bash
# install my small generator
npm install -g generator-stencil-component

# then free to use it
yo stencil-component YourComponentName

# eg.
yo stencil-component app-home
```

## Update 26th of Mar 2018
You can use Stencil component creator supported by Ionic Team. First installation

```bash
npm i -g st-cc
```

Then you can use it some thing like as following:
```bash
npx st-cc
Stencil component creator
? What is name of the component you want to create? test-app
? Is shadow component? No
? What type of style file? scss
? Create test file? Yes
🚀 Stencil component test-app created!
```

Note: npx is a new utility available in npm 5 or above that executes local binaries/scripts to avoid global installs.

[using-sass-with-your-stenciljs]: https://www.xmobe.com/stenciljs/using-sass-in-your-stenciljs-app/