# vue2-leaflet-draw-toolbar

<a href="https://www.npmjs.com/package/vue2-leaflet-draw-toolbar.svg">
  <img src="https://img.shields.io/npm/dw/vue2-leaflet-draw-toolbar.svg" alt="Downloads">
</a>
<a href="https://www.npmjs.com/package/vue2-leaflet-draw-toolbar.svg">
  <img src="https://img.shields.io/npm/v/vue2-leaflet-draw-toolbar.svg" alt="Version">
</a>
<a href="https://www.npmjs.com/package/vue2-leaflet-draw-toolbar.svg">
  <img src="https://img.shields.io/npm/l/vue2-leaflet-draw-toolbar.svg" alt="License">
</a>

This is a [Vue2Leaflet](https://github.com/KoRiGaN/Vue2Leaflet) plugin port to provide the
[leaflet-draw-toolbar](https://github.com/justinmanley/leaflet-draw-toolbar) control
on [Leaflet](https://leafletjs.com/) maps in [Vue](https://vuejs.org/) applications.


## Installation
```bash
npm install --save vue2-leaflet-draw-toolbar
```


## Usage

### Adding the component to a map

With the `LDrawToolbar` component loaded into Vue (see below), simply add the
`l-draw-toolbar` element inside an `l-map`, optionally providing it with an
`position` prop to specify any the location of Toolbar.

For example,
```html
<l-map>
  <l-draw-toolbar position="topright"/>
  <!-- other map components -->
</l-map>
```


### Loading the Vue component

You can either install the control globally within your application at the point where you initially
configure Vue, or import the control only within the components that require it.


#### Option 1: Global install

Where you load and configure your Vue environment,
```js
import Vue from 'vue';
import LDrawToolbar from 'vue2-leaflet-draw-toolbar';
// ...
Vue.component('l-draw-toolbar', LDrawToolbar);
// ...
```


#### Option 2: Local import

In the `<script>` of a Vue component,
```js
import LDrawToolbar from 'vue2-leaflet-draw-toolbar';
// ...
export default {
  // ...
  components: {
    LDrawToolbar,
    // ...
  },
  // ...
};
```


## Credit

The majority of the credit for this plugin goes to the author and contributors of the underlying
[leaflet-draw-toolbar toolbar](https://github.com/justinmanley/leaflet-draw-toolbar), and of course
the plugin wouldn't be possible without Vue, Leaflet, and Vue2Leaflet.


### Plugin author

Huberto Kaiser Filho


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
