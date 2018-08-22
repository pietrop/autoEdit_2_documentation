# Travis CI continuous build

There is no deployment as such as it's electron app, so the build described above serves as a packaging of the app for release.

However As of version `1.0.8` support is added for Linux thanks to [@probonopd](https://github.com/probonopd), [\#36](https://github.com/OpenNewsLabs/autoEdit_2/issues/36).  
On commit to master there is a continuous built setup on Travis CI that builds and adds an up to date linux and mac os x release to the release section [under release section](https://github.com/OpenNewsLabs/autoEdit_2/releases).

Continuous integration service for

* [x] Mac
* [x] Linux
* [ ] Windows 

More info on the implementation of this setup see the info in the [PR](https://github.com/OpenNewsLabs/autoEdit_2/issues/36) and `.travis.yml`

{% embed data="{\"url\":\"https://github.com/OpenNewsLabs/autoEdit\_2/blob/master/.travis.yml\",\"type\":\"link\",\"title\":\"OpenNewsLabs/autoEdit\_2\",\"description\":\"autoEdit\_2 - Fast text based video editing, node Electron Os X desktop app, with Backbone front end.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/1502863?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

This is an attempt to capture some notes on the steps of setting up travis CI integration.

## github + Travis CI

### Travis CI Integration

1 - enable Travis CI for your repository as [described here](https://travis-ci.org/getting_started)

2 - Set up `GITHUB_TOKEN` in Travis CI for this to work. as [described here](https://github.com/probonopd/uploadtool#usage)

\(Direct link to [Github token here](https://github.com/settings/tokens)\)

#### Add a `.travis.yml` file to your repository

See [exampe in README of `probonopd/uploadtool`](https://github.com/probonopd/uploadtool#usage) as well as example below from [autoEdit `.travis.yml`](https://github.com/OpenNewsLabs/autoEdit_2/blob/master/.travis.yml) or from [subtitlesComposer-app `.travis.yml`](https://github.com/pietrop/subtitlesComposer-app/blob/master/.travis.yml).

#### `package.json`

To add linux see example

* [autoEdit `package.json`](https://github.com/OpenNewsLabs/autoEdit_2/blob/master/package.json)
* [subtitlesComposer-app `package.json`](https://github.com/pietrop/subtitlesComposer-app/blob/master/package.json)

