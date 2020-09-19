---
title:  "Nice Weather Tizen Application"
date:   2017-02-16 9:08:23
categories: [Tizen]
tags: [tizen, tizen store, weather app, mobile app, nice weather, niceweather]
comments: true
---

**My first shot with Tizen Application development**

Some information and my experience in developing Nice Weather Tizen Web Application.

## Tizen Web Application
Develope a Tizen Web Application quite easy! You can use plain HTML, Javascript to make it work and combine it with Tizen Web library. Of course, you can use additional library or framework to support your development like, React, AngularJS, Angular2 or some HTML5/CSS mobile UI libraries like Kendo, Onsen, Framework7 etc...

The main thing here is choose your best framework and library and going with it.

## Build and Test in Emulator
You can use Tizen Studio for your development but in my experience with it in my Mac, Tizen Studio so bad. It will hold all your CPU and RAM, and especially always crash when you try to build the app or run in emulator.

After 2 days working with Tizen Studio I decide to play with Tizen command line and going to coding in Visual Studio Code. There are some command line I think will be useful with your development:
- To list all types of Tizen Web projects template.
```javascript
tizen list web-project
```
- That command will help you create a tizennews project base on WebBasicApplication template.
```javascript
tizen create web-project -p mobile-2.4 -t WebBasicApplication -n tznews -- ~/workspace/tizennews
```
- To build project you need to run command build-web.
```javascript
tizen build-web -- ~/workspace/tizennews
```
- Before running project in emulator you need to package it into .wgt file. (Remmember .buildResult is a hidden folder)
```javascript
tizen package --type wgt --sign MyProfile -- ~/workspace/tizennews/.buildResult
```
- To install app in emulator, you can use that command line. 
```javascript
tizen install --target M-2.4 --name tizennews.wgt -- ~/workspace/tizennews/.buildResult
```
(*) One important thing here is signature Profile. You will need to pay sometime with it to make it work in emulator, and it will still appear when you try to make available in Tizen Store. You can find more information to help you do that with command line [here][tizen-command-line].

This is the way I choose to develop Tizen Web App.

## Tizen Store
After development you will want to upload your app in Tizen Store. It's quite take time, especially for some country you do not have real device to play or test. My suggestion is please try to test it smoothly in your emulator. All functionals, how how to quit your app to make sure your app fault tolerant in some use cases. 

Prepair nice images and icon for your app to submit and wait. Be patient, Tizen Store test team will work on it about 3 or 4 business days. And send you a report with some errors or defects, you must work on it and repeat submit app process. After 3 or 4 times maybe your app will available in Tizen Store. With me I remember 4 times. 

If you have questions or suggestion, please leave me comments here:

### Some pictures of my app:

![splash-screen](/images/nice-weather-tizen-web-application/ads-screen01.jpg){:class="img-responsive"}{: height="300px"}
![main-screen](/images/nice-weather-tizen-web-application/ads-screen02.jpg){:class="img-responsive"}{: height="300px"}
![city-search-screen](/images/nice-weather-tizen-web-application/ads-screen05.jpg){:class="img-responsive"}{: height="300px"}
![settings-screen](/images/nice-weather-tizen-web-application/ads-screen04.jpg){:class="img-responsive"}{: height="300px"}
![themes-screen](/images/nice-weather-tizen-web-application/ads-screen06.jpg){:class="img-responsive"}{: height="300px"}


[tizen-command-line]: https://developer.tizen.org/dev-guide/web/2.3.0/org.tizen.mobile.web.appprogramming/html/ide_sdk_tools/command_line_interface.htm