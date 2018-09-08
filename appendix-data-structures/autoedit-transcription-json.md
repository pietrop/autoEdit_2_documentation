# autoEdit transcription Json

This corresponds to the [backbone transcription model in autoEdit](https://github.com/OpenNewsLabs/autoEdit_2/blob/master/lib/app/models/transcription.js).

```javascript
// http://backbonejs.org/#Model
module.exports = Backbone.Model.extend({
  idAttribute: '_id',
  urlRoot: path.join(config.serverUrl, 'transcription'),
  defaults: {
    // title: 'Default Title ',
    // description: 'Default Description',
    // original file path
    // videoUrl: '/',
    // url:'/',
    // sttEngine: 'ibm',
    languageModel: 'en-US_BroadbandModel', // default is american US broadband model
    counterForPaperCuts: 0,
    audioFile: undefined,
    processedAudio: false,
    processedVideo: false,
    // status is marked as false by default and turned to true when transcription has been processed
    // could changed as status marked as null if there's an issue
    // so that can have 3 options. not set yet, gone wrong, success.
    status: false,
    highlights: [],
    // orderedPaperCuts:[],
    videoOgg: undefined,
    //TODO: get date from metadata of video
    metadata: undefined,
    text: undefined,
    //used for error handling when processing transcription
    error: undefined
  },
```

at the moment v`1.0.6` there are some redundant attributes, such as `counterForPaperCuts` that could be removed.

`highlights` is used to do selections in transcription show view.

`text` is the body of the transcription.

Here is an example of the json.

```javascript
{
    "languageModel": "en-US_BroadbandModel",
    "counterForPaperCuts": 7,
    "audioFile": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Jesselyn_Radack-Mobile.mp4.1486205670442.ogg",
    "processedAudio": true,
    "processedVideo": true,
    "status": true,
    "highlights": [
        {
            "id": 0,
            "paperCutOrder": 6,
            "startTime": 580.0699999999999,
            "endTime": 588.0899999999999,
            "reelName": "NA",
            "clipName": "Jesselyn Radack-Mobile.mp4",
            "speaker": "Jesselyn Radack",
            "transcriptionId": 78885461,
            "videoId": "videoId_78885461",
            "videoOgg": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Jesselyn_Radack-Mobile.mp4.1486205670442.webm",
            "audioFile": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Jesselyn_Radack-Mobile.mp4.1486205670442.ogg",
            "text": "I just said that I wrote more emails and that %HESITATION and I didn't quite know what to do but I knew I didn't want to be a part of this ",
            "offset": "NA",
            "words": [
                {
                    "id": 1116,
                    "text": "I",
                    "startTime": 580.0699999999999,
                    "endTime": 580.24
                },
                {
                    "id": 1117,
                    "text": "just",
                    "startTime": 580.24,
                    "endTime": 580.4300000000001
                },
                ...
            ]
        },

    ],
    "videoOgg": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Jesselyn_Radack-Mobile.mp4.1486205670442.webm",
    "metadata": {
        "filePathName": "/Users/pietropassarelli/Downloads/Jesselyn Radack-Mobile.mp4",
        "fileName": "Jesselyn Radack-Mobile.mp4",
        "date": "2016-02-29 12:52:17",
        "reelName": "NA",
        "timecode": "NA",
        "fps": "1/50",
        "duration": 1618.16
    },
    "text": [
        {
            "id": 0,
            "speaker": "Jesselyn Radack",
            "paragraph": [
                {
                    "line": [
                        {
                            "id": 0,
                            "text": "and",
                            "startTime": 12.09,
                            "endTime": 12.36
                        },
                        {
                            "id": 1,
                            "text": "like",
                            "startTime": 12.36,
                            "endTime": 12.53
                        },
                        ...
                    ],
                    "id": 0,
                    "startTime": 12.09,
                    "endTime": 19.92
                },


                .....
            ]
        }
    ],
    "title": "Jesselyn Radack-Mobile",
    "description": "",
    "videoUrl": "/Users/pietropassarelli/Downloads/Jesselyn Radack-Mobile.mp4",
    "sttEngine": "ibm",
    "_id": "78885461",
    "id": "78885461"
}
```

The part to consider when referring to as autoEdit transcription json is simply the content of text attribute tho:

```javascript
"text": [
        {
            "id": 0,
            "speaker": "Jesselyn Radack",
            "paragraph": [
                {
                    "line": [
                        {
                            "id": 0,
                            "text": "and",
                            "startTime": 12.09,
                            "endTime": 12.36
                        },
                        {
                            "id": 1,
                            "text": "like",
                            "startTime": 12.36,
                            "endTime": 12.53
                        },
                        ...
                    ],
                    "id": 0,
                    "startTime": 12.09,
                    "endTime": 19.92
                },


                .....
            ]
        }
    ],
```

