---
description: current travis setup
---

# Travis CI continuous build

There is no deployment as such as it's electron app, so the build described above serves as a packaging of the app for release.

However As of version `1.0.8` support is added for Linux thanks to [@probonopd](https://github.com/probonopd), [\#36](https://github.com/OpenNewsLabs/autoEdit_2/issues/36).  
On commit to master there is a continuous built setup on Travis CI that builds and adds an up to date linux and mac os x release to the release section [under release section](https://github.com/OpenNewsLabs/autoEdit_2/releases).

Inspired by this [issue](https://github.com/electron-userland/electron-builder/issues/1751) In the latest iteration it use `electron-builder -mwl --publish always`on Travis CI  `Mac OSX` instance to package for these platforms,

* [x] Mac
* [x] Linux
* [x] Windows 

This is an attempt to capture some notes on the steps of setting up travis CI integration in the current implementation

## github + Travis CI

### Travis CI Integration

1 - enable Travis CI for your repository as [described here](https://travis-ci.org/getting_started)

2 - Set up `GITHUB_TOKEN` in Travis CI for this to work. as [described here](https://github.com/probonopd/uploadtool#usage)

\(Direct link to [Github token here](https://github.com/settings/tokens)\)

#### Add a `.travis.yml` file to your repository

```yaml
os: osx
osx_image: xcode9.4
language: node_js
node_js: "8"
sudo: required

env:
  global:
    - ELECTRON_CACHE=$HOME/.cache/electron
    - ELECTRON_BUILDER_CACHE=$HOME/.cache/electron-builder

# specifying npm version as
# by default travis seemed to sue 4.2.0
# https://docs.travis-ci.com/user/languages/javascript-with-nodejs/#using-a-specific-npm-version

install:
  - node --version
  - npm i -g npm@5
  - npm --version
  - npm install
  - npm run make_js

script:
  - npm run build:mwl:publish:always;
  - ls ./dist;
  - find . | grep mac.zip;
  - find . | grep x86_64.AppImage;
  - find . | grep .exe;

branches:
  except:
    - # Do not build tags that we create when we upload to GitHub Releases
    - /^(?i:continuous)/
```

#### `package.json`

added to the the npm scripts 

```javascript
"scripts": {
  ...
    "build:mwl:publish:always": "electron-builder -mwl --publish always",
...
}
"build": {
    "publish": {
      "provider": "github",
      "releaseType": "prerelease",
      "vPrefixedTagName": false
    },
    ....
```

## Electron builder documentation 

more on electron builder here

* github repo [electron-userland/electron-builder](https://github.com/electron-userland/electron-builder)
* [publishing artifacts](https://www.electron.build/configuration/publish)
* [configuration](https://www.electron.build/configuration/configuration#Configuration-publish)

