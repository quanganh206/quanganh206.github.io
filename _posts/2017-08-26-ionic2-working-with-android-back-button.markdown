---
title:  "Ionic2 - Working with Android Back Button"
date:   2017-08-26 9:08:23
categories: [Ionic2]
tags: [ionic2, android, back button, native plugin, cordova]
comments: true
---

This snippet help you working with Android Back Button in your Ionic 2 & 3 app. Hope this help. Happy coding.

- To list all types of Tizen Web projects template.

```javascript
// app.component.ts
if (this.platform.is('android')) {
    this.platform.registerBackButtonAction(() => {
        if (this.menu.isOpen()) {
            this.menu.close();
        } else {
            switch (this.nav.getActive().name) {
                case 'WelcomePage':
                case 'RegisterPage':
                    // silent
                    break;
                case 'HomePage':
                    // exit App
                    this.platform.exitApp();
                    break;
            }
        }
    });
}
```