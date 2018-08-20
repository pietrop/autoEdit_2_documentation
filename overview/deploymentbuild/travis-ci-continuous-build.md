# Travis CI continuous build

  
There is no deployment as such as it's electron app, so the build described above serves as a packaging of the app for release.  
  
However As of version `1.0.8` support is added for Linux thanks to [@probonopd](https://github.com/probonopd), [\#36](https://github.com/OpenNewsLabs/autoEdit_2/issues/36).  
On commit to master there is a continuous built setup on Travis CI that builds and adds an up to date linux and mac os x release to the release section [under release section](https://github.com/OpenNewsLabs/autoEdit_2/releases).

Continuous integration service for 

* [x] Mac
* [x]  Linux
* [ ]  Windows 

More info on the implementation of this setup see the info in the [PR](https://github.com/OpenNewsLabs/autoEdit_2/issues/36) and `.travis.yml`

{% embed data="{\"url\":\"https://github.com/OpenNewsLabs/autoEdit\_2/blob/master/.travis.yml\",\"type\":\"link\",\"title\":\"OpenNewsLabs/autoEdit\_2\",\"description\":\"autoEdit\_2 - Fast text based video editing, node Electron Os X desktop app, with Backbone front end.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/1502863?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

