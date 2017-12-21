[![Npm Package](https://img.shields.io/npm/v/pure-svg-code.svg?style=flat-square)](https://www.npmjs.com/package/pure-svg-code)
[![Build Status](https://img.shields.io/travis/gwuhaolin/pure-svg-code.svg?style=flat-square)](https://travis-ci.org/gwuhaolin/pure-svg-code)
[![Npm Downloads](http://img.shields.io/npm/dm/pure-svg-code.svg?style=flat-square)](https://www.npmjs.com/package/pure-svg-code)


# pure-svg-code
Generate qrcode & barcode to svg in pure javascript, can be used in browser & Node.js & 小程序, small no dependency.

## Install
Install from npm:
```bash
npm i pure-svg-code
```
Import it:
```js
// import both
const {barcode,qrcode} = require('pure-svg-code');

// import as you need
const barcode = require('pure-svg-code/barcode');
const qrcode = require('pure-svg-code/qrcode');
```

## qrcode
```js
const svgString = qrcode({
  content: "http://github.com/",
  padding: 4,
  width: 256,
  height: 256,
  color: "#000000",
  background: "#ffffff",
  ecl: "M"    
})
```

#### List of options:
- `content` - QR Code content, required
- `padding` - white space padding, `4` modules by default, `0` for no border
- `width` - QR Code width in pixels
- `height` - QR Code height in pixels
- `color` - color of modules, color name or hex string, e.g. `#000000`
- `background` - color of background, color name or hex string, e.g. `white`
- `ecl` - error correction level: `L`, `M`, `H`, `Q`

## barcode
Set it up and specify your type and options. The following 3 are the only
required ones.

```javascript
var svgString = barcode("9234567890128", "ean13", {width:'50', barWidth:1, barHeight:50});
```

#### Support types:
- codabar
- code11 (code 11)
- code39 (code 39)
- code93 (code 93)
- code128 (code 128)
- ean8 (ean 8)
- ean13 (ean 13)
- std25 (standard 2 of 5 - industrial 2 of 5)
- int25 (interleaved 2 of 5)

#### Support options:
- `barHeight` (number) -height of svg (default: 30);
- `width` (number) -width of svg (default: 100);
- `bgColor` (string) -background color css like (default: 'transparent');
- `color` (string) -barcode color (default: '#000000');


## Use it with <img> tag
```js
const {qrcode,svg2Url} = require('pure-svg-code');
const svgString = qrcode('data');
const url = svg2Url(svgString);

// set img element's src to url
imgEle.src = url;
```
This way can be used for browser & 小程序。

## Use it in Node.js server
```js
const {qrcode} = require('pure-svg-code');

app.get('/',function(req, res) {
    const svgString = qrcode('data');
    res.send(svgString)
})
```