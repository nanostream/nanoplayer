# nanoplayer-vue

nanoStream H5Live Player Samples

(c) 2018-2026, nanocosmos gmbh http://www.nanocosmos.net support@nanocosmos.net

LEGAL NOTICE: This material is subject to the terms and conditions defined in separate license conditions ('LICENSE.txt') All information contained herein is, and remains the property of nanocosmos GmbH and its suppliers if any. The intellectual and technical concepts contained herein are proprietary to nanocosmos GmbH, and are protected by trade secret or copyright law. Dissemination of this information or reproduction of this material is strictly forbidden unless prior written permission is obtained from nanocosmos. All modifications will remain property of nanocosmos.

## Purpose

This template should help get you started with developing nanoStream with Vue 3 in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Recommended Browser Setup

- Chromium-based browsers (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd) 
  - [Turn on Custom Object Formatter in Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Turn on Custom Object Formatter in Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Configuring the player

Edit nanoPlayer.vue and change the config.js

```
const config = {
  source: {
    bintu: {
      // Enter your bintu streamid here
      // for more information on how to setup check our API documentation
      // https://docs.nanocosmos.de/docs/nanoplayer/nanoplayer_api/
      streamid: "859b1a11-5458-404a-bd10-5fcd5a9228f1",
    },
  },
  // ...
  ```

