# react-cropperjs

[cropperjs](https://github.com/fengyuanchen/cropperjs) as a React component.

[![NPM](https://nodei.co/npm/react-cropper.png)](https://www.npmjs.com/package/react-cropper)


## Docs
* [Image Cropper](https://github.com/tapp-tv/react-cropperjs)

## Installation

Install via [npm](https://www.npmjs.com/package/react-cropperjs)

```shell
npm install --save react-cropperjs
```

### Webpack User

You also need a couple of loaders for webpack

```shell
npm install style-loader css-loader
```

### Browserify User

https://github.com/cheton/browserify-css

```shell
npm i --save-dev browserify-css
```

Compile your project with command line like

```shell
 browserify -t reactify -g browserify-css index.jsx > bundle.js
```

If you are using `gulp`, `browserify` or other build tools, make sure you enable `global` option `true`

For example in `gulp` you should do

```js
b.transform(browserifycss, {global: true});
```

## Todo
* Unit test
* Put demo in [http://roadmanfong.github.io/react-cropper/](http://roadmanfong.github.io/react-cropper/)

## Quick Example
```js
var Cropper = require('react-cropper');
var Demo = React.createClass({
  _crop: function(){
    // image in dataUrl
    console.log(this.refs.cropper.getCroppedCanvas().toDataURL());
  },

  render: function() {
    return (
      <CropperJS
        ref='cropper'
        src='http://fengyuanchen.github.io/cropper/img/picture.jpg'
        style={{height: 400, width: '100%'}}
        // Cropper.js options
        aspectRatio={16 / 9}
        guides={false}
        crop={this._crop} />
    );
  }
});

```

## Options

### src
* Type: `string`
* Default: `null`

```js
  <CropperJS src='http://fengyuanchen.github.io/cropper/img/picture.jpg' />
```

### Other options

Accept all options in the [docs](https://github.com/fengyuanchen/cropper#options) as attributes.

```js
  <CropperJS
    src='http://fengyuanchen.github.io/cropper/img/picture.jpg'
    aspectRatio={16 / 9} 
    guides={false} 
    crop={this._crop} />
```

## Methods
Assign a `ref` attribute to use [methods](https://github.com/fengyuanchen/cropper#methods)

```js
var Demo = React.createClass({

  _crop: function(){
    var dataUrl = this.refs.cropper.getCroppedCanvas().toDataURL();
    console.log(dataUrl);
  },

  render: function() {
    return (
      <CropperJS
        ref='cropper'
        crop={this._crop} />
    );
  }
})
```

## Events

Assign [Events](https://github.com/fengyuanchen/cropper#events) handler with `.on(eventname, callback)` and `ref`.

```js

componentDidMount: function(){
  this.refs.cropper.on('dragstart.cropper', function (e) {
    console.log(e.type); // dragstart
    console.log(e.namespace); // cropper
    console.log(e.dragType); // ...
  });
},

```

## Build

```
npm run build
```

## Author
Fong Kuanghuei(waneblade@gmail.com)

## License
MIT
