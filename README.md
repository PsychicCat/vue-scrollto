# vue-scrollto

[![Vue 2.x](https://img.shields.io/badge/Vue-2.x-brightgreen.svg)](https://vuejs.org/v2/guide/)
[![npm](https://img.shields.io/npm/v/vue-scrollto.svg)](https://www.npmjs.com/package/vue-scrollto)
[![npm-downloades](https://img.shields.io/npm/dm/vue-scrollto.svg)](https://www.npmjs.com/package/vue-scrollto)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/rigor789/vue-scrollto/blob/master/LICENSE)

[DEMO](https://rigor789.github.io/vue-scrollto/#/examples)

Scrolling to elements was never this easy!

This is for `vue 2.x`

For `vue 1.x` use `vue-scrollTo@1.0.1` (note the capital T) but keep in mind that the old version depends on `jquery`.

## Under the hood

`vue-scrollto` uses `window.requestAnimationFrame` to perform the animations, thus giving the best performance.

Easing is done using [bezier-easing]() - A well tested easing micro-library.

<p class="tip">
It even knows when the user interrupts, and doesn't force scrolling that would result in bad UX.
</p>

## Installing

This package is available on npm.

<p class="warning">
    If you used this package before, please ensure you are using the right one, since it has been renamed from `vue-scrollTo` to `vue-scrollto`
</p>

Using npm:
```bash
npm install --save vue-scrollto
```

Using yarn:
```bash
yarn add vue-scrollto
```

Directly include it in html:
```html
<script src="https://unpkg.com/vue@2.2.4"></script>
<script src="https://unpkg.com/vue-scrollto"></script>
```
<p class="tip">
    When including it in html, it will automatically call `Vue.use` and also set a `VueScrollTo` variable that you can use!
</p>


## Usage

vue-scrollto can be used either as a vue directive, or programatically from your javascript.

### As a vue directive
```js
var Vue = require('vue');
var VueScrollTo = require('vue-scrollto');

Vue.use(VueScrollTo)
```

```html
<a href="#" v-scroll-to="'#element'">Scroll to #element</a>

<div id="element">
    Hi. I'm #element.
</div>
```

If you need to customize the scrolling options, you can pass in an object literal to the directive:

```html
<a href="#" v-scroll-to="{
     el: '#element',
     container: '#container',
     duration: 500,
     easing: 'linear',
     offset: -200,
     onDone: onDone,
     onCancel: onCancel
 }">
    Scroll to #element
</a>
```

<p class="tip">
    Check out the [Options Section](#options) for more details about the available options.
</p>

### Programatically

```js
var VueScrollTo = require('vue-scrollto');

var options = {
    container: '#container',
    easing: vueScrollto.easing['ease-in'],
    offset: -60,
    onDone: function() {
      // scrolling is done
    },
    onCancel: function() {
      // scrolling has been interrupted
    }
}

VueScrollTo.scrollTo(element, duration, options)
```

## Options

#### el / element 
The element you want to scroll to.

#### container
The container that has to be scrolled. 

*Default:* `body`

#### duration
The duration (in milliseconds) of the scrolling animation. 

*Default:* `1000` 

#### easing 
The easing to be used when animating. Read more in the [Easing section](#easing). 

*Default:* `ease`

#### offset 
The offset that should be applied when scrolling. 

*Default:* `0`

#### onDone 
A callback function that should be called when scrolling has ended. 

*Default:* `noop`

#### onCancel 
A callback function that should be called when scrolling has been aborted by the user (user scrolled, clicked etc.).
 
*Default:* `noop`


## Easing

Easing is calculated using [bezier-easing]() so you can pass your own values into `options.easing` in the form of an array with 4 values.

vue-scrollto defines the following easings that you can use:
```js
exports.easing = {
    'ease': [0.25, 0.1, 0.25, 1.0],
    'linear': [0.00, 0.0, 1.00, 1.0],
    'ease-in': [0.42, 0.0, 1.00, 1.0],
    'ease-out': [0.00, 0.0, 0.58, 1.0],
    'ease-in-out': [0.42, 0.0, 0.58, 1.0]
}
```

## License

MIT
