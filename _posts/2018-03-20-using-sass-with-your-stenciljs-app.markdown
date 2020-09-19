---
title:  "Using SASS in your StencilJS App"
date:   2018-03-20 18:03:18
categories: [StencilJS]
tags: [Stencil, StencilJS, Web Component, Sass]
comments: true
---

To make SASS with your StencilJS app quite easy. Thanks, Ionic Team! They'd supported an npm package call `@stencil/sass` to make your like easier.

In your project root folder, run that command:

```shell
npm install -S @stencil/sass
```

The next step is working with stencil config file:

```javascript
// stencil.config.js
// add this on top of the file
const sass = require('@stencil/sass');
...
exports.config = {
  ...
  plugins: [
    sass()
  ] 
}
```

And the last step using it with your component. If you not familiar with StencilJS component go to that article to read more. For example, using it with your first-comp component in first-comp.tsx component file.

```javascript
@Component({
  tag: 'first-comp',
  styleUrl: 'first-comp.scss'
})
export class MyApp {
  ...
}
```

and your first-comp.scss file:

```scss
.some-sass-class {
  background: #5851ff;
  color: white;
  height: 56px;
  display: flex;
  align-items: center;
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.26);
}
```

See you in the next article.