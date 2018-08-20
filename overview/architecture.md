# Architecture Overview - draft

## High level Overview

1.  autoEdit uses Speech to text services to create automatic transcription from a video or audio file
2.  the user can make text selections
3. export those selections as a video sequence in the editing software of choice

### `docs` Project page

Contains a jeckyll site for the [project page, hosted on github pages](https://opennewslabs.github.io/autoEdit_2/).

Uses this template for the Landing page [pratt-app-landing-page](http://blacktie.co/2013/10/pratt-app-landing-page/) [demo](http://blacktie.co/demo/pratt)

While the [user manual has been moved on gitbooks](https://pietropassarelli.gitbooks.io/autoedit2-user-manual/content)

#### Documentaiton

Was initially Using [jsdoc](http://usejsdoc.org/) and \[docco\]\[docco\] for automatic documentation generated. See [updating documentation ](../appendix/updating-automated-documentation.md)section for more on how to update [jsdoc](http://usejsdoc.org/) and \[docco\]\[docco\]. But have decided to [move the documentation gitbooks](https://pietropassarelli.gitbooks.io/autoedit-2-r-d-documentation-for-developers/content/) \(which is what you are most likely reading now\). And still need to decide what is the place, if any for automated generated documentation.

### `spec`

Test suite `npm run test`. [Uses jasmine for testing](https://jasmine.github.io/). Testes are setup to be all in one place rather then divided with their respective components, for ease of use. Altho test coverage is far from complete and could do with some attention, s[ee supporting the project](support-the-project.md) if that's something you'd be interested getting involved with.

### `Electron`

Is the front end of the project.



###  `Backbone.sync` 

`db.js` overrides `backbone.sync` method to provide a backend for the app and persistent storage using linvodb3, which uses `medeadown` to storing db on the user file system. [See current db setup tutorial for more info](../appendix/current-db-setup.md).

in `index.html` the window object is used to provide an interface between the [nwjs mixed contexts](http://docs.nwjs.io/en/latest/For%20Users/Advanced/JavaScript%20Contexts%20in%20NW.js/#mixed-context-mode)

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



### `edl_composer` module

See [EDL format](../appendix/edl-format.md), and [Export section](../export/export/) as well as [EDL composer module](https://github.com/OpenNewsLabs/autoEdit_2/tree/master/lib/edl_composer).

### `lib/interactive_transcription_generator`

After the user uploads a video or audio file the backbone app override default [`backbone.sync`](http://backbonejs.org/#Sync) and calls the `nwjs/db.js` which after saving the transcription model in db, triggers this module to get stt transcription, video preivew, and metadata info.

At a hight level this module:

* converts the file to an audio file meet the IBM Watson STT Specs, using the submodule `transcriber`. 
* if greater then 5 min long it splits it into 5 min chunk.
* It keeps tracks of the time offset of each clip. 
* It sends audio files to IBM STT API. 
* If submitted file was greater then 5 min.
* When results starts to come back as json after about 5 min or less results are re-interpolated into one json file. 
* The json returned by IBM is converted into json meeting autoEdit2 specs and saved in db. 
* User can now view interactive an transcription.

`interactive_transcription_generator`. On top of prepping the audio or video file to get a transcription from IBM, it also generates a webm html5 video preview and reads the metadata, which is something needed make an [EDL](https://github.com/pietrop/autoEdit_2_documentation/tree/6a02a8d72f177e127c3fe0b3c3959dbc6f737f13/jsdoc_docs/tutorial-EDL_format.html).

The `transcriber` module used by `interactive_transcription_generator` can also chose between using Gentle open source STT, Pocketsphinx or IBM to generate the transcription depending on what was specified by the user.

`interactive_transcription_generator`:

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

The `pocketsphinx` module was originally extracted from the Video grep project.

The implementation of this module is discussed in more details in subsequent sections.

### `srt`module

[srt module](https://github.com/OpenNewsLabs/autoEdit_2/blob/master/lib/srt/index.js) is a simplified version of [srt parse composer module](https://github.com/pietrop/srtParserComposer) also [npm](https://www.npmjs.com/package/srt_parser_composer).



