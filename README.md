# macaca-electron

[![Gitter Chat][gitter-image]][gitter-url]
[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][coveralls-image]][coveralls-url]
[![node version][node-image]][node-url]

[gitter-image]: https://img.shields.io/badge/GITTER-join%20chat-green.svg?style=flat-square
[gitter-url]: https://gitter.im/alibaba/macaca
[npm-image]: https://img.shields.io/npm/v/macaca-electron.svg?style=flat-square
[npm-url]: https://npmjs.org/package/macaca-electron
[travis-image]: https://img.shields.io/travis/macacajs/macaca-electron.svg?style=flat-square
[travis-url]: https://travis-ci.org/macacajs/macaca-electron
[coveralls-image]: https://img.shields.io/coveralls/macacajs/macaca-electron.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/macacajs/macaca-electron?branch=master
[node-image]: https://img.shields.io/badge/node.js-%3E=_7-green.svg?style=flat-square
[node-url]: http://nodejs.org/download/

> macaca electron driver

## Installment

```bash
$ npm i macaca-electron -g
```

## Notice

### window.alert

Macaca disables `window.alert`, `window.prompt`, `window.confirm` from popping up by default, and you can override by `execute`.

## Standalone usage

```javascript

const co = require('co');
const fs = require('fs');
const path = require('path');
const Electron = require('macaca-electron');

const electron = new Electron();

co(function *() {
  /**
    default options
    {
      show: true,
      alwaysOnTop: false,
      x: 0,
      y: 0,
      width: 800,
      height: 600,
      userAgent: 'userAgent string',
      webPreferences: {
        nodeIntegration: false
      }
    }
  */
  yield electron.startDevice({
    show: false // in silence
  });

  yield electron.maximize();
  yield electron.setWindowSize(null, 500, 500);
  yield electron.get('https://www.baidu.com');
  const imgData = yield electron.getScreenshot();
  const img = new Buffer(imgData, 'base64');
  const p = path.join(__dirname, '..', 'screenshot.png')
  fs.writeFileSync(p, img.toString('binary'), 'binary');
  console.log(`screenshot: ${p}`);

  yield electron.stopDevice();
});

```

- [sample macaca-electron-screenshot](//github.com/macaca-sample/macaca-electron-screenshot)
- [More API](//macacajs.github.io/macaca-electron/)

<!-- GITCONTRIBUTOR_START -->

## Contributors

|[<img src="https://avatars1.githubusercontent.com/u/1011681?v=4" width="100px;"/><br/><sub><b>xudafeng</b></sub>](https://github.com/xudafeng)<br/>|[<img src="https://avatars3.githubusercontent.com/u/4006436?v=4" width="100px;"/><br/><sub><b>meowtec</b></sub>](https://github.com/meowtec)<br/>|[<img src="https://avatars1.githubusercontent.com/u/1044425?v=4" width="100px;"/><br/><sub><b>ziczhu</b></sub>](https://github.com/ziczhu)<br/>|[<img src="https://avatars1.githubusercontent.com/u/4575751?v=4" width="100px;"/><br/><sub><b>jacksonlai</b></sub>](https://github.com/jacksonlai)<br/>
| :---: | :---: | :---: | :---: |


This project follows the git-contributor [spec](https://github.com/xudafeng/git-contributor), auto upated at `Sat Apr 21 2018 16:55:45 GMT+0800`.

<!-- GITCONTRIBUTOR_END -->

## License

The MIT License (MIT)
