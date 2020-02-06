---
description: "work in progress \U0001F6A7"
---

# autoEdit Adobe CEP Panel dev setup

Thanks to [@bfasenfest](https://github.com/bfasenfest) help in figuring out adobe CEP there is now support for an adobe panel version of autoEdit under development.

CEP stands for [`Common Extensibility Platform`](https://www.adobe.io/apis/creativecloud/cep.html) and it's an SDK by Adobe to create panels for the Adobe suite.

It is now possible to run autoEdit as an Adobe panel. The idea is that when run inside of adobe as a CEP panel, autoEdit, will have access to same local databse as the desktop application, to allow maximum portability, and have extra acess to features to integrate with adobe premiere, such as sync play with clips in source monitor from transcriptions etc..

Also [see autoEdit Adobe Panel user manual](https://autoedit.gitbook.io/user-manual/autoedit-adobe-panel/transcription-to-source-monitor) for user facing functionalities.

![Example autoEdit CEP](https://pbs.twimg.com/media/Dkg0waTW4AALCCM.jpg)

### electron vs adobe panel \(vs nwjs\)

It seems like adobe panel CEP and and Electron use slightly different setup of `chromium`.

> The downside is, Chromium is a very large codebase and requires very powerful machines to build. For normal laptops, that can take more than 5 hours. So this greatly impacts the number of developers that can contribute to the project, and it also makes development slower.
>
> In order to avoid the complexity of building all of Chromium, Electron uses libchromiumcontent to access Chromium's Content API.

[from electron's docs](https://electronjs.org/blog/electron-internals-building-chromium-as-a-library) and [here](https://electronjs.org/docs/development/atom-shell-vs-node-webkit)

The main difference is noticeable when calling `window.process.versions` in the console for CEP and for electron.

Due to some of these differences the code base for autoEdit has been adjusted to accomodate and target for the two enviroments.

### Dev enviroment needed for CEP

* node
* npm 
* You need to have recent version of [Adobe Premiere](https://www.adobe.com/products/premiere.html) on your system. Version `12.11` to ensure compatibility with all features.
* Chrome browser to view the dev tools for the CEP panel 
* [See here fore more details on JSX language](https://jsx.github.io/doc/tutorial.html) used to interact with Adobe Premiere API and [here](https://jsx.github.io/)
* _optional_ but highly reccomended to use the [Property Explorer](https://www.adobeexchange.com/creativecloud.details.1170.html) extension in Premiere. \(to install follow their instruction if you sing into adobe creative cloud it should auto install and be available in the window -&gt;  extensions list in Premiere \)

### setup

The main code for the adobe panel is in [`adobe-panel-src`](https://github.com/pietrop/autoEdit_2_documentation/tree/d35184bd7887535034333e2604a3128b5ec288e7/adobe-panel/adobe-panel-src/README.md) folder.

At a mimum the files needed in that folder for the CEP panel are

* The `.debug` file is necessary to get the chrome dev tools
* the `manifest.xml` is really the important part, its what loads the `index.html` and `jsx` file
* `index.html` entry point into the app
  * We use autoEdit's `electron/index.html` for this
* `jsx/Premiere.jsx` contains APIs to communicate to Adobe Premiere 

However will see section below for an automated build development step to achieve this programmatically

#### 1. allow un-signed extension

Since Premiere only accepts signed extension, [you should tell it to accept unsigned extensions like this as well](https://github.com/Adobe-CEP/CEP-Resources/blob/master/CEP_8.x/Documentation/CEP%208.0%20HTML%20Extension%20Cookbook.md#debugging-unsigned-extensions)

But you can skip to [Debugging Unsigned Extensions](https://github.com/Adobe-CEP/CEP-Resources/blob/master/CEP_8.x/Documentation/CEP%208.0%20HTML%20Extension%20Cookbook.md#debugging-unsigned-extensions) and do the following terminal comand on a mac.

```text
defaults write com.adobe.CSXS.8 PlayerDebugMode 1
```

You might need to potentially cover 5 to 8 depending on which CSXS version you have. eg

```text
defaults write com.adobe.CSXS.5 PlayerDebugMode 1
defaults write com.adobe.CSXS.6 PlayerDebugMode 1
defaults write com.adobe.CSXS.7 PlayerDebugMode 1
defaults write com.adobe.CSXS.8 PlayerDebugMode 1
```

You might need to re-start your computer

#### 2. CEP development in autoEdit

[Fork branch `autoedit-panel-refactor`](https://github.com/OpenNewsLabs/autoEdit_2/tree/autoedit-panel-refactor)

git clone locally, so that you are setup to do a PR with any changes.

Then run `npm install`.

a series of npm scripts in [`package.json`](https://github.com/pietrop/autoEdit_2_documentation/tree/d35184bd7887535034333e2604a3128b5ec288e7/adobe-panel/package.json) with ndoe module [`sync-files`](https://www.npmjs.com/package/sync-files) are used to copy the relevant files across from [`adobe-panel-src`](https://github.com/pietrop/autoEdit_2_documentation/tree/d35184bd7887535034333e2604a3128b5ec288e7/adobe-panel/adobe-panel-src/README.md) and the rest of the relevant parts of the electron app into the CEP Adobe Premiere extension folder.

The extension folders are

* For Win: `C:\<username>\AppData\Roaming\Adobe\CEP\extensions`  
* For Mac: `~/Library/Application Support/Adobe/CEP/extensions`  

For one off development builds in local adobe extension folder do

```text
npm run adobe-panel-dev
```

For development with watch

```text
npm run adobe-panel-dev:watch
```

With this last comand everytime you save it automatically copies changes over.

#### 3. open CEP panel in Adobe Premiere

Last but not Launch Premiere Pro and open this Panel under

```text
Window > Extensions > autoEdit
```

Everytime you want to update changes in the panel you need to close and reopen it.

#### 3. CEP local server

Local server for adobe panel is at [http://localhost:8099/](http://localhost:8099/), there you can see the dev tools inspector and console."

### autoEdit adobe JSX integration

* [List of features here organised by autoEdit views](../autoedit-adobe-cep-panel-integration-overview.md).
* [See this section for adobe JSX functions useful for autoEdit Panel](../adobe-cep-jsx-functions-for-autoedit-adobe-panel.md).

### Packaging and distributing extension

* [see this section for more details on packaging, signing and distributing Adobe CEP extensions.](../packaging-and-distributing-adobe-cep-extensions/)

### some more docs for Adobe dev documentation

* [Official Adobe Sample Panel](https://github.com/Adobe-CEP/Samples/tree/master/PProPanel)
* [Semi Official API Docs](http://ppro.aenhancers.com/)
* [Non Official but very nice API Docs](http://www.brysonmichael.com/premiereapi-home)

For a more comprehensive unofficial guide of Adobe CEP see this series of blog posts, highly recommended if you want to understand the overall setup and inner workings.

{% embed data="{\"url\":\"http://aphall.com/2014/08/cep-mega-guide-en/\",\"type\":\"link\",\"title\":\"CEP 5 Super mega guide: Extending Adobe apps with HTML5+Node.js \| aphall.com\",\"description\":\"Andy Hall is a developer in Tokyo, working on a game.\"}" %}



### 

