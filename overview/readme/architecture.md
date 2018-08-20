# Architecture Overview

## High level Overview

1. autoEdit uses Speech to text services to create automatic transcription from a video or audio file
2. The user can make text selections 
3. Export those selections as a video sequence in the editing software of choice

See [See user manual ](https://autoedit.gitbook.io/user-manual) for more details. And project [README](https://github.com/OpenNewsLabs/autoEdit_2) on github.

## Stack

It is built using `node` `electron` and `backbone`.

### electron

Code of the electron app is in the `./electron` folder. The backbone app is added to `./electron/index.html` with browserify using npm scripts.

### Backbone app

The backbone app is in `lib/app` folder. For troubleshooting you can use `cmd`+ `alt` +`i` to get the electron developer console. There you have `appTranscription` and `appPaperedit` two backbone routers in the global `window` scope that give you access to getting to individual backbone models and collections for transcriptions and paper-edit.

### `Backbone.sync`

Is designed so that the front end in backbone can be used as standalone static site. Which is how [the demo](https://opennewslabs.github.io/autoEdit_2/demo/index.html) is run, with an hard coded sample data in `backbone.sync`.

`db.js` overrides `backbone.sync` method to provide a backend for the app and persistent storage using linvodb3, which uses `medeadown` to storing db on the user file system. [See current db setup tutorial for more info](../../appendix/current-db-setup.md).

in `index.html` the window object is used to provide an interface between the electron client side code code packaged with browserify and the 'backend' that can make the file system calls in node.

If you use `require` in the html file, then you are in node context, and can use module like `fs` but if you use a script tag, then you are in js client side code and don't have access to thos function.

The downside of being in node context on the client side, without using a bundle like browserify and requring modules directly is that the front end is no longer portable as standalone client side web app if needed, eg for the demo page.

```javascript
// if require is not undefined then we are in node context in `index.html` , and therefore using 
if (typeof require !== 'undefined') {
    // other code here..
    window.DB = require('./db.js');
    //...
```

in `lib/app/app.js` the choice between the demo db and the production db is made.

```javascript
// Connect up the backend for backbone
if (typeof window.DB !== 'undefined') {
  Backbone.sync = window.DB;
} else {
  Backbone.sync = require('./demo_db');
}
```

`demo_paperedit.json` and`demo_transcription.json` provide the data for the demo when `index.html` is run in client side mode in the browser. and `lib/app/demo_db.js` provides the logic for the demo db.

`DB` in `./electron/db.js` allows to connect the backbone front to the `medeadown`/ `linvodb3` databse locally. As well as trigger `./lib/interactive_transcription_generator` component to at a high level

* read metadata of the media file, for the EDL sequence
* create video preview
* create audio version to send to STT APIs

### `lib/interactive_transcription_generator`

To re-cap After the user uploads a video or audio file the backbone app override default [`backbone.sync`](http://backbonejs.org/#Sync) and calls the `electron/db.js` which after saving the transcription model in db, triggers this module to get stt transcription, video preivew, and metadata info.

At a hight level this module:

* converts the file to an audio file meet the STT Specs, eg for IBM Watson, using the submodule `transcriber`. 
* _for IBM Watson only_ if greater then 5 min long it splits it into 5 min chunk.
  * It keeps tracks of the time offset of each clip. 
* It sends audio files to STT API. 
  * _for IBM Watson only_ If submitted file was greater then 5 min.
  * _for IBM Watson only_ When results starts to come back as json after about 5 min or less results are re-interpolated into one json file. 
* The json returned by STT Service API is converted into json meeting autoEdit2 specs and saved in db. 
* User can now view interactive an transcription.

`interactive_transcription_generator`. On top of prepping the audio or video file to get a transcription from IBM, it also generates a webm html5 video preview and reads the metadata, which is something needed to make an [EDL](https://github.com/pietrop/autoEdit_2_documentation/tree/6a02a8d72f177e127c3fe0b3c3959dbc6f737f13/jsdoc_docs/tutorial-EDL_format.html).

The `transcriber` module used by `interactive_transcription_generator` can also chose between using Gentle open source STT, Pocketsphinx or IBM to generate the transcription depending on what was specified by the user.

`interactive_transcription_generator` folder structure overview:

```javascript
.
├── README.md
├── index.js
├── transcriber
│   ├── convert_to_audio.js
│   ├── gentle_stt_node
│   │   ├── gentle_stt.js
│   │   ├── index.js
│   │   └── parse_gentle_stt.js
│   ├── ibm_stt_node
│   │   ├── parse.js
│   │   ├── sam_transcriber_json_convert.js
│   │   ├── send_to_watson.js
│   │   └── write_out.js
│   ├── index.js
│   ├── pocketsphinx
│   │   ├── README.md
│   │   ├── index.js
// pocketsphinx binaries 
│   │   ├── pocketsphinx
│   │   ├── pocketsphinx.js
│   │   ├── pocketsphinx_converter.js
// pocketsphinx binaries 
│   │   ├── sphinxbase
│   │   └── video_to_audio_for_pocketsphinx.js
│   ├── split.js
│   └── trimmer.js
├── video_metadata_reader
│   └── index.js
└── video_to_html5_webm
    └── index.js
```

The `pocketsphinx` module was originally extracted from the [electron version of the Video grep project](https://github.com/antiboredom/videogrep). The implementation of this module is discussed in more details in subsequent sections.

### `edl_composer` module

See [EDL format](../../appendix/edl-format.md), and [Export section](../../export/export/) as well as [EDL composer module](https://github.com/OpenNewsLabs/autoEdit_2/tree/master/lib/edl_composer).

This module as also been abstracted as separate [npm module](https://www.npmjs.com/package/edl_composer) and [github repository](https://github.com/pietrop/edl_composer#readme)

### `ffmpeg` and `electron`

autoEdit uses `ffmpeg` under the hood, and getting `ffmpeg` and `electron` to work can sometimes be problematic when setting up a new app, so [I wrote here](http://pietropassarelli.com/ffmpeg-electron.html) about how this setup works in autoEdit, with simplified example.

I've since abstracted and published these two forks as npm packages

* [ffmpeg-static-electron](https://www.npmjs.com/package/ffmpeg-static-electron)
* [ffprobe-static-electron](https://www.npmjs.com/package/ffprobe-static-electron)

### STT

The app uses the following Speech To Text systems to generate transcription

1. [x] IBM watson\(free trial + paid\), 
2. [x] Speechmatics\(free trial + paid\), 
3. [x] Gentle\(open source\) 
4. [x]  pocketsphinx \(open source\) 
5. [x] Rev.com \(human transcriptions\)
6. [ ] Google 

The user can then select text and export a video sequence to the video editing software of choice.

### `srt`module

The module used to export transcriptions as captions file [srt module](https://github.com/OpenNewsLabs/autoEdit_2/blob/master/lib/srt/index.js) is a simplified version of [srt parse composer module](https://github.com/pietrop/srtParserComposer) also [npm](https://www.npmjs.com/package/srt_parser_composer).

## Tests folder

Tests are in the `spec` folder, to run the test suite `npm run test`. [Uses jasmine for testing](https://jasmine.github.io/). Testes are setup to be all in one place rather then divided with their respective components, for ease of use. Altho test coverage is far from complete and could do with some attention, s[ee supporting the project](../support-the-project.md) if that's something you'd be interested getting involved with.

Future plans include refactoring, and separate tests to be closer to their components, as well as migrate from jasmine to jest.

## Other docs

There is also a google doc for a ["QA Test Plan autoEdit 2"](https://docs.google.com/document/d/18hqjb5K7owSV6HJ-uqgeFwxicRUvf-nYsdpJiBkF-BU/edit?usp=sharing), which was original used with Vox Media QA team. It is now not up to date to the paper-editing features, but is comprehensive enough for the test. And a great starting point to make a new one.

There is also an ["R&D planning google doc"](https://docs.google.com/document/d/12mUuXAtE65vhy5Sm0tmKRdgXGMn_Ob4RZEs9T5uDPkM/edit?usp=sharing) that was used for version `1.0.6` to add the paper-editing functionality.

