---
title:  "Starting with StencilJS Web Components Compiler"
date:   2018-03-18 6:20:18
categories: [StencilJS]
tags: [Ionic2, Stencil, Stenciljs, Web Component]
comments: true
---

Before talking about StencilJS, and what it is we just take a look back to Web Components and it's basic.

## What are web components?
From webcomponent.org you can see a definition:

>"Web components are a set of web platform APIs that allow you to create new custom, reusable, encapsulated HTML tags to use in web pages and web apps. Custom components and widgets build on the Web Component standards, will work across modern browsers, and can be used with any JavaScript library or framework that works with HTML."

Web components are based on four main specifications: Custom Elements, Shadow DOM, HTML imports, and HTML Template. Using a Web Component very simple, you just import into your to your system and using it with HTML Custom Tags like the original HTML Tags

```html
<link rel="import" href="../a-web-component/a-web-component.js">

<a-web-component cool-attr="Arkay Lee"></a-web-component>
```

## How about StencilJS?
Stencil combines the best concepts of the most popular frameworks into a simple build-time tool.

Stencil takes features such as
- Virtual DOM
- Async rendering (inspired by React Fiber)
- Reactive data-binding
- TypeScript
- JSX
and then generates standards-based Web Components with these features baked in. More than that StencilJS also support some features on top of Web Components like Server Side Rendering (SSR), pre-rendering, and objects-as-properties etc.

## Getting Start with StencilJS
Let's open a terminal window and clone Starter Stencil App to start. Please make sure you had installed NodeJS over 8.0. The following commands create a new project app of Stencil in folder first-app.

```shell
git clone https://github.com/ionic-team/stencil-app-starter first-app
cd first-app
git remote rm origin
npm install
npm start
Your app will be up and running on localhost port 3333.
```
![StencilJS Start App](https://i0.wp.com/www.xmobe.com/assets/images/2018/03/start_with_stencil_01.png?resize=768%2C576&ssl=1){:class="img-responsive"}{: height="200px"}

Okay, you have a running StencilJS app now! Let's go ahead with more detail inside.

## StencilJS Starter App Structure
The StencilJS App Structure quite simple. You will see a clear structure look like the image below:

![StencilJS App Structure](https://i1.wp.com/www.xmobe.com/assets/images/2018/03/Screen-Shot-2018-03-23-at-3.26.10-PM.png?resize=1024%2C745&ssl=1){:class="img-responsive"}

The main entry point is in src/index.html

```html
<!DOCTYPE html>
<html dir="ltr" lang="en">
<head>
  <meta charset="utf-8">
  <title>Stencil Starter App</title>
  <meta name="Description" content="Welcome to the Stencil App Starter. You can use this starter to build entire apps all with web components using Stencil!">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=5.0">
  <meta name="theme-color" content="#16161d">
  <meta name="apple-mobile-web-app-capable" content="yes">

  <meta http-equiv="x-ua-compatible" content="IE=Edge"/>

  <script src="/build/app.js"></script>

  <link rel="apple-touch-icon" href="/assets/icon/icon.png">
  <link rel="icon" type="image/x-icon" href="/assets/icon/favicon.ico">
  <link rel="manifest" href="/manifest.json">
</head>
<body>

  <my-app></my-app>

  <style>
    body {
      margin: 0px;
      padding: 0px;
      font-family: sans-serif;
    }
  </style>
</body>
</html>
```

The most important line is `<my-app></my-app>`, it looks the same with the way we use a Web Component above. And it brings us to jump into components folder.

The **components** folder keep all of your app's components, as you can see here we have **my-app**, **app-profile**, and **app-home** components. Each component has 3 files, one file with .tsx extension, one file with the .css extension, and the last family one with .spec.ts extension for testing purpose.

Another thing related to components is components.d.ts file. So much of code on it but no worries, it is an auto-generated file, Stencil Compiler will take care of it for you.

It's a short start with StencilJS Web Component Compiler. The next future posts I will try to push more thing about StencilJS and it's power to make great Web Components that all frameworks could use

