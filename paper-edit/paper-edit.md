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

Identify JS search library and structure  to use in hypertranscript and paper-edit view to search transcriptions, annotations, filter by tags etc..

eg http://fusejs.io ?

### component:Drag and Drop papercut 

#### sortable 
Eg use js library  https://github.com/RubaXa/Sortable 

#### vuejs
Or if using veu js https://github.com/SortableJS/Vue.Draggable 

#### dragula 
Or use https://github.com/bevacqua/dragula js 
To figure out in dragula is how to integrate with selections. Eg make a selection draggable. 
Coz I think dragula needs draggable items to be wrapped in a div with a certail class (?) 

Could wrap selection/annotations/tags in a div with that class to make this possible.

in autoEdit Comes from a problem is of representation of highlight for drag and drop.
Hilight is a class added to a word.

https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/views/transcription_view.js#L34


It be good to figure this out as a component.

![TBVE mobile screenshot]()

JSffidle high fidelity mockup example: https://jsfiddle.net/pietrops/Lufaerr2/1/
For simplicity the words are plain text and not wrapped in span tag, as they would be in an proper hyper transcript. 

This makes the whole line / paragraph draggable. 

Making words as draggable and having multi selection is outside of the scope of dragula (read that in the issues section of github repo). 

Adding sortable  with dragula gives this error `TypeError: Cannot read property 'pointerEnabled' of undefined `
There might be a problem with dragula and browserify?


#### Option: Jquery UI multisortable

![auotoEdit express node versions screenshot with jquery multisortable]()

<!-- https://docs.google.com/document/d/12mUuXAtE65vhy5Sm0tmKRdgXGMn_Ob4RZEs9T5uDPkM/edit#heading=h.50858w4z2grk-->


Other option is JQuery UI multisortable previous version of autoEdit in node. A bit fiddly to make a selection.

Github repo: https://github.com/shvetsgroup/jquery.multisortable 
JS fiddle example: https://jsfiddle.net/neochief/KWeMM/ 

In previous version we used jqueryUI.
https://github.com/pietrop/autoEdit_nwjs_alpha_RandD 

https://github.com/pietrop/autoEdit_nwjs_alpha_RandD/blob/master/views/template/paperedit.html 

Abstracted example with jquery multi sortable  https://jsfiddle.net/pietrops/eo4najce/  

Main issue with this is that you need to click to select. And do click shift to select from one word to the other. 

An option could be to add slected class to words span contigues to clicked selected?


#### Jquery Sortable
https://johnny.github.io/jquery-sortable/ 
Nice coz it has nested ul/li which would allow to move all sections of paragraphs all togethere.


#### Palestinian remix / hyperaudio - Laurian 
Also review Palestinian remix (trello/slack) D&D by Laurian, example code. 

https://github.com/hyperaudio/hyperaudio-experimental 

From Laurian: 

>the drag and drop was made with rangy and tether.js (http://tether.io/) , basically using tether to replicate the selection and have it html5 draggable

http://popcorn.gridinoc.com/ 

![img example of laurian drag and drop hyperaudio- shakespeare]()

#### listener + data layer // Andrea's option <-- current implemtation 
Listener on user text  selection on transcription 
Grab info
Create div 
Add and div to the paperedit side at the end. 

Div on paper-edit side can then be sortable.

DataLayer

Spec of the EDL sequence. 
http://www.autoedit.io/jsdoc_docs/module-edl_composer.html 

https://github.com/andrixb/texthighliter 

https://jsfiddle.net/andrixb/9cnp4rgL/56/ 

http://farhadi.ir/projects/html5sortable/ 

https://www.html5rocks.com/en/tutorials/dnd/basics/ 

https://github.com/andrixb/v-textselector 


Not using drag and drop. But using data layer.
User selects words in transcriptions. 
Data structure is created with those info.
Papercut ejd template is populated 
And is added at the end of paper edit
With mouse down listener 

With html5 drag and drop added sortable 
To allow to be able to rearrange order of papercuts.
Can drag a piece and then copy and append after element you drop on. And remove original piece.

Subsequent improvement 
If click on papercut then can add selection after that one rather then at the end.
Todo: find away to signal that in CSS.



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

Not implemented yet. 

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

<!-- TODO: export paperedit and put json here as example, is the below one correct? -->

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
			"id": 2,

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
	        	...
	        ]
		},
		...
	]
}
```

--
## What needs refactoring

### component:Search and filter 

### component:Drag and Drop papercut 




### component:Video preview 

The flow and consistency between the different components json is not great, needs to be revisited.

#### Paper-edit/EDL export json
Paper-edit and transcription EDL export should have consistent schema. at the moment they are different. 
