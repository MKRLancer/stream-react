<p align="center">
  <a href="https://recruit.moneyforward.com/" target="blank"><img src="https://storage.googleapis.com/studio-design-asset-files/projects/Z9qp7A67OP/s-247x44_392d9252-7133-4aa7-907e-861a536cd5ab.svg" width="200" alt="Nest Logo" /></a>
</p>

<br>

<p align="center">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQyZYyI_kksy6bkPp1nImZa44ehobfKmxMBiw&usqp=CAU" width="200" alt="Nest Logo" />
</p>
<br>

<p align="center">
  <img src="https://camo.githubusercontent.com/44ef4570e0663cb66576ea1a816223ff22d8493f29ba16ed054fad13d71f1222/68747470733a2f2f696d616765732e6374666173736574732e6e65742f7834776536356271693435712f3739636c5a585a6d745077577a5475783259496c676e2f61373863306635346537653633363932373565616163376530343933333833352f315f485369734c7569664d4f364b624c66504f4b744c6f772e6a706567" alt="" />
</p>
<br>

<h1 align="center">
  <img src="https://zhstatic.zhihu.com/cfe/griffith/griffith-banner.png" height="200" width="200"/>
  <p align="center" style="font-size: 0.5em">A React-based Web video player</p>
</h1>

[![License](https://img.shields.io/npm/l/griffith.svg)](https://github.com/zhihu/griffith/blob/master/LICENSE)
[![npm package](https://img.shields.io/npm/v/griffith/latest.svg)](https://www.npmjs.com/package/griffith)
![](https://badgen.net/npm/types/griffith)
[![Coverage Status](https://coveralls.io/repos/github/zhihu/griffith/badge.svg?branch=master)](https://coveralls.io/github/zhihu/griffith?branch=master)
![Code style](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/zhihu/griffith/blob/master/CONTRIBUTING.md)

[English](./README.md) | [简体中文](./README-zh-Hans.md) | [日本語](./README-ja.md)

# Introduction


- **Streaming:** Griffith makes streaming easy. Whether your video format is mp4 or hls, Griffith can use Media Source Extension (MSE) for segment loading.
- **Extensibility:** Griffith makes it simple to support video features in React apps. It also supports the UMD (Universal Module Definition) patterns for direct use in the browser if your application is not based on React.
- **Reliability:** Griffith has been widely used in the web and mobile web of Zhihu.

## Usage

### React application

```bash
yarn add griffith
```

```js
import Player from 'griffith'

const sources = {
  hd: {
    play_url: 'https://zhstatic.zhihu.com/cfe/griffith/zhihu2018_hd.mp4',
  },
  sd: {
    play_url: 'https://zhstatic.zhihu.com/cfe/griffith/zhihu2018_sd.mp4',
  },
}

render(<Player sources={sources} />)
```

[Detailed usage](./packages/griffith/README.md)

**Note: Griffith is not supporting SSR application**

### non-React application

```html
<script src="https://unpkg.com/griffith-standalone/dist/index.umd.min.js"></script>
```

```js
const sources = {
  hd: {
    play_url: 'https://zhstatic.zhihu.com/cfe/griffith/zhihu2018_hd.mp4',
  },
  sd: {
    play_url: 'https://zhstatic.zhihu.com/cfe/griffith/zhihu2018_sd.mp4',
  },
}

Griffith.createPlayer(element).render({sources})
```

[Standalone mode detailed usage](./packages/griffith-standalone/README.md)

## Project Structure

Griffith is a Monorepo and uses [Yarn workspace](https://yarnpkg.com/lang/en/docs/workspaces/) and [Lerna](https://github.com/lerna/lerna).

### Core

- `packages/griffith`: The core library

### Utilities

- `packages/griffith-message`: Helpers for cross-window message
- `packages/griffith-utils`: Utilities

### Plugins

- `packages/griffith-mp4`: MP4 plugin powered by [MediaSource API](https://developer.mozilla.org/en-US/docs/Web/API/MediaSource)
- `packages/griffith-hls`: [HLS](https://developer.apple.com/streaming/) plugin powered by [hls.js](https://github.com/video-dev/hls.js)

### Others

- `example`: example and demos
- `packages/griffith-standalone`: A UMD build that can be used without React or Webpack

## Custom Build

Build tools like webpack include `griffith-mp4` and `griffith-hls` by default. You can make your bundle smaller by injecting aliases at build-time.

If you use webpack, do so with [resolve.alias](https://webpack.js.org/configuration/resolve/#resolvealias):

```javascript
// webpack v5+
module.exports = {
  resolve: {
    alias: {
      'griffith-hls': false,
      'griffith-mp4': false,
    },
  },
}

// webpack v4
module.exports = {
  resolve: {
    alias: {
      'griffith-hls': 'griffith/null',
      'griffith-mp4': 'griffith/null',
    },
  },
}
```

Note that without `griffith-mp4` / `griffith-hls` Griffith can no longer play MP4 / HLS media unless the browser supports it natively.

## Contributing

Read below to learn how you can take part in improving Griffith.

### Contributing Guide

Read our [contributing guide](./CONTRIBUTING.md) to learn about our development process, how to propose bugfixes and improvements, and how to build and test your changes to Griffith.

### Contributor

- [Cheng Wang](https://github.com/wangcheng678)
- [Wuhao Liu](https://github.com/liuwuhaoo)
- [Xiaoyan Li](https://github.com/lixiaoyan)
- [Tianxiao Wang](https://github.com/xiaoyuhen)
- [Xiaoshuang Bai (Designer)](https://www.behance.net/shawnpai)

## LICENSE

MIT
