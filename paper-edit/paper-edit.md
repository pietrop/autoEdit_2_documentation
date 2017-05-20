# Paper-edit

<!--
- Component/part description 
- Related projects. Eg parts that look good, or previous implementations. But might not be considered for implementation options 
- Implementations Options considered
- Current implementation 
- What needs refactoring 
--> 

## Component/part description

### Paper-edit json schema specification
Connected to this is defining a schema for paper-edit, to make sure all components that work with this have a defined interface/specification.  This is same as a spec for “EDL JSON” which is used in the EDL composer module. 

<!-- link to appendix example -->

### component:Search and filter 

### component:Drag and Drop papercut 

### component:Video preview 

Components representation paper-edit view

![Components representation paper-edit view
](/assets/components_representation_paperedit_view.png)

<!-- google diagram
https://docs.google.com/document/d/12mUuXAtE65vhy5Sm0tmKRdgXGMn_Ob4RZEs9T5uDPkM/edit# 

https://docs.google.com/document/d/12mUuXAtE65vhy5Sm0tmKRdgXGMn_Ob4RZEs9T5uDPkM/edit#
-->



--
## Related projects.

NA

--
## Implementations Options considered

### component:Search and filter 

### component:Drag and Drop papercut 

### component:Video preview 

####  BBC Video context "EDL JSON"

BBC Video context previously video compositor. 

[Preview/ BBC Video compositor](https://github.com/bbc/html5-video-compositor)

This is the sequence taken in by tge BBC video compositor to be able to render a video preview in canvas. 
It takes two tracks, but for our porpuses we can just pass one track. 
Needs adding type “video”, change startTime to start. 
And add duration instead of endTime. 

```js
var playlist = {
    "tracks":[
        [{type:"image", src:"assets/aston.png", start:0, duration:10, id:"aston"}],
        [{type:"video", src:"assets/title.mp4", start:0, duration:2, id:"title"},
  	{type:"video", src:"assets/title.mp4", start:2, duration:8, id:"clip1"}]
  ]
}
```

<!-- add link to issue raise when asked about json EDL input in video context. + add json example -->

#### Popcorn js 

<!-- JS fiddle example -->

#### Vanilla js 

<!-- JS fiddle example -->

#### Two players 

<!-- Hyperaudio implementation to remove gap in between load time -->


--
## Current implementation

### component:Search and filter 

### component:Drag and Drop papercut 

### component:Video preview 

Data structures in view components.

![Data structures in paper-edit view components](/assets/Data structures in paperedit view components.png)

<!-- put the json examples here -->

#### Hypertranscript / autoEdit Json
This is the autoEdit json for a transcription. It models the structure of a transciptions text. 
With paragraphs, lines, and words. 

```js
"text": [
	{
	 "id": 0,
	"speaker": "Unnamed Speaker",
	"paragraph": [
			{
			  "line": [								
                      {
				"id": 0,
				"text": "oh",
				"startTime": 0.06,
                        "endTime": 1.65					                      
				},
```

#### Papercuts 
This is a papercut json extracted from the dom view. 
Inside events. Contains either headings / titles or actual “papercuts” video segments.
Events is sinonimum with papercuts. In edl format they are called events. 
It is missing words and text. So it’s hard to parse it back into the view once that is saved into the model/db.
→ ideally would want to change this to accomodate words, and have one papercut template for both scenarios. 

```js
{
	"title": "Paperedit 2",
	"events": [
		{
			"title": "Introduction",
			"id": 1
		},
		{
			"startTime": "16",
			"endTime": "22.64",
			"transcriptionId": "24dcd88b",
			"reelName": "NA",
			"clipName": "Ian Perkin-Mobile.mp4",
			"videoId": "videoId_24dcd88b",
			"speaker": "Unnamed Speaker",
			"src": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Ian_Perkin-Mobile.mp4.1486169904445.webm",
			"audioFile": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Ian_Perkin-Mobile.mp4.1486169904445.ogg",
			"offset": "NA",
			"id": 2
		},
```

### Papercut in view
Data structure used in `papercut.html.ejs` to make a paper-edit when selecting words in transcription side. (hypertranscript).
 
It is an array of words, and It has redundant informations. To make it easier for the extraction. 

```js
{
    "papercut": [
        {
            "text": "but ",
            "clipName": "Ian Perkin-Mobile.mp4",
            "reelName": "NA",
            "startTime": "92.35",
            "endTime": "92.47",
            "speaker": "Unnamed Speaker",
            "audioFile": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Ian_Perkin-Mobile.mp4.1486169904445.ogg",
            "src": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Ian_Perkin-Mobile.mp4.1486169904445.webm",
            "transcriptionId": "24dcd88b",
            "videoId": "videoId_24dcd88b",
            "offset": "NA"
        },
        {
            "text": "it ",
            "clipName": "Ian Perkin-Mobile.mp4",
            "reelName": "NA",
            "startTime": "92.47",
            "endTime": "92.76",
            "speaker": "Unnamed Speaker",
            "audioFile": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Ian_Perkin-Mobile.mp4.1486169904445.ogg",
            "src": "/Users/pietropassarelli/Library/Application Support/autoEdit2/media/Ian_Perkin-Mobile.mp4.1486169904445.webm",
            "transcriptionId": "24dcd88b",
            "videoId": "videoId_24dcd88b",
            "offset": "NA"
        },
   
    ]
}
```

#### ejs
This is done so that there can be an interactive transcript this side as well using ejs 

```
<dl class="dl-horizontal">
		<dt><%= papercut[0].speaker %></dt> 
		<dt>
	  		<a data-start-time="<%= papercut[0].startTime %>" data-video-id="<%= papercut[0].videoId %>" class="timecodes"><%= fromSeconds(papercut[0].startTime) %></a>
		</dt>
		<dd>
			<% for(var i=0; i<papercut.length; i++){%>
			 	<span contenteditable="false" class="words text-muted papereditWords" 
			 	data-transcription-id="<%= papercut[i].transcriptionId %>" 
			 	data-reel-name="<%= papercut[i].reelName %>" 
			 	data-clip-name="<%= papercut[i].clipName %>" 
			 	data-video-id="<%= papercut[i].videoId %>" 
			 	data-speaker="<%= papercut[i].speaker %>" 
			 	data-src="<%= papercut[i].src %>" 
			 	data-audio-file="<%= papercut[i].audioFile %>" 
			 	data-start-time="<%= papercut[i].startTime %>" 
			 	data-text="<%= papercut[i].text %>" 
			 	data-end-time="<%= papercut[i].endTime %>"><%= papercut[i].text %> </span>
	 		<% } %>
	 	</dd>
	</dl>
```

#### EDL JSON/EDL export module - transcription
At the moment as as the papercut EDL json in autoEdit but with fields less, as it doesn’t need a lot of the once in the autoEdit one, to be able to make an .edl file. 

```
var edlSqDemo = {
    "title": "Demo Title of project",
    //offset is optional default is "00:00:00:00"
    "events":  [
      { "id":1,
        "startTime": 10,
        "endTime": 20,
        "reelName":"SomeReelName",
        "clipName":"Something.mov"
        "offset": "00:00:28:08"
      },
      { "id":2,
        "startTime": 45,
        "endTime": 55,
        "reelName":"SomeOtherReelName",
        "clipName":"SomethingElse.mov",
        "offset": "00:00:28:08"
      },
        { "id":2,
        "startTime": 45,
        "endTime": 55,
        "reelName":"NA",
        "clipName":"SomethingElse.mov"
        "offset": "00:00:28:08"
      }
    ]
}
```

#### EDL JSON/EDL export module - paper-edit

<!-- TODO: export paperedit and put json here as example -->

--
## What needs refactoring

### component:Search and filter 

### component:Drag and Drop papercut 

### component:Video preview 

The flow and consistency between the different components json is not great, needs to be revisited.

#### Paper-edit/EDL export json
Paper-edit and transcription EDL export should have consistent schema. at the moment they are different. 
