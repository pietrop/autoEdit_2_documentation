# Jsx functions for Adobe CEP autoEdit adobe Panel

_Can use the_ [_Property explorer_](https://www.adobeexchange.com/creativecloud.details.1170.html#.WRQJd-V96bg) _extension to figure out what methods and properties are available. Installing with creative clouds, it becomes available under window, extensions, in Premiere._

## **Node path issue in adobe CEP**

As explained here

{% embed url="https://forums.adobe.com/thread/2387875" %}

  
****Adobe CEP  requires absolute path for nodejs, this is a problem when requiring modules, as you can no longer use relative path eg

```javascript
require( "./js/lib/jquery.js");
```

But you need to use  
****

```javascript
require(__dirname + "/js/lib/jquery.js");
```

This does not seem like much of a change, but if you have code where you want to keep you modules portables, and/or perhaps you are porting an application into the adobe CEP environment \(eg like from electron in the case of [autoEdit.io](www.autoEdit.io)\) then it involves a fair bit of tedious refactoring.

This solution of setting the process `cwd()` using `chdir()` seems to have work fine on mac.  
****

```javascript
try {
   process.chdir(__dirname);
   console.log('New directory: ' + process.cwd());
}
catch (err) {
   console.log('chdir: ' + err);
}
```

However need to test if this works on windows, or if need to use the path node module to adjust for osx vs win path slashes differences.  
****

## Adobe Functions

![Adobe Premiere Parts diagram for integration with CEP panel.](https://docs.google.com/drawings/d/sTNVABxrqA__jPP4mnfyCgA/image?w=624&h=411&rev=150&ac=1&parent=1PCivPisinsoIOh7NnceuXgh0ks5h_vwLLFX6gKRW0LM)

### **✅Project Panel: Get information of selected media in premiere project panel**

Returns project item object \(?\) with information of what file you have selected -- useful for automatic transcription or any other functionality where you want to operate on premiere clip source files.

[**Code from sample app**](https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx#L1633)

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L1633" %}

```javascript
var viewIDs = app.getProjectViewIDs(); 
// sample code optimized for a single open project
viewSelection = app.getProjectViewSelection(viewIDs[0]);
// get string with absolute path to media file
viewSelection[0].getMediaPath();
// eg "/Users/pietropassarelli/Desktop/Demo_media/wetransfer-f13849/Goldsmith for Transcription.mp4"	
```

also relevant thread 

{% embed url="https://forums.adobe.com/message/10194319\#10194319" %}

Only available in Premiere `12.1`  
****

### **✅Source monitor: Load external file into source monitor**

A function to load a media file into the source viewer programmatically.  
  
For example connected with one above, once it know what click is selected in source project panel can load media into source monitor viewer,  
****

From sample app

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L249" %}

```javascript
openInSource : function() {
	var fileToOpen = File.openDialog ("Choose file to open.", 0, false);
	if (fileToOpen) {
	// This is the function to load a file into source monitor from path
		app.sourceMonitor.openFilePath(fileToOpen.fsName);
        // playback speed as float, 1.0 = normal speed forward
		app.sourceMonitor.play(1.73);			
		fileToOpen.close(); 
	} else {
		$._PPP_.updateEventPanel("No file chosen.");		
	}
},
```

### **✅Project Panel: Search/find clip using file name or path in project panel**

a function to be able to find clip using file name or path in project panel eg to see if they have been added to the project

Here is some code [from adobe Bruce](https://forums.adobe.com/message/10193352#10193352) about finding the clip with the same path in project panel:

```javascript
var ignoreSubClips = 1;

var arrayOfProjectItemsReferencingSomePath = app.project.rootItem.findItemsMatchingMediaPath(path, ignoreSubClips);
```

```javascript
// get clip from Project panel 
var first = app.project.rootItem.children[0];

```

### **✅Source Monitor: Load media into source monitor**

a function to be able to load media into source monitor viewer programmatically.

Is there a direct way to do this? Or need to get the media eg from project panel and then get the file path eg using `.getMediaPath();` ?

Which could then be used with the code from the `openInSource` function example above.

```javascript
// gets the clip being selected by the user. Returns a path to the file
var selectionFilePath = viewSelection[0].getMediaPath();
// open that clips in the source monitor 
app.sourceMonitor.openFilePath(selectionFilePath);
// this means you can open clips in the source monitor even if they are not in adobe project panel as long as you have the path to them
```

### **❓Source Monitor: Get information of current clip in monitor**

Seems like this might not be possible?

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L1466" caption=undefined %}

```javascript
// closeFrontSourceClip
app.sourceMonitor.closeClip()
```

```javascript
// closeAllClipsInSourceMonitor
app.sourceMonitor.closeAllClips(); 
```

### **✅Source Monitor: Set in and out points**

Set in and out point for clip in source monitor programmatically  
Seems like you set the in and out on the clip in project panel and then that is also show in the source monitor\(?\)  
See below.

### **✅Project panel: Set in and out point of file**

I.e. set in points on a particular project item that is only in the project panel, not in the source monitor. I think in the end what we will have to do is set the in and out here \(as I think that is possible but it is not in the source as far as I can tell\). So the workflow would be you open the transcript in autoedit -- it opens the correct file in the source monitor, when you make an edit it finds the clip with the same path in the project panel, sets in and out points, and then brings it into the sequence.  
****

```javascript
var first = app.project.rootItem.children[0];
first.setStartTime(20);
first.setInPoint(30);
first.setOutPoint(45);

var seq = app.project.activeSequence;
var vTrack1 = seq.videoTracks[0]; morning 

vTrack1.insertClip(first, '00;00;00;00');
```

inPoint and outPoint seems to set them in ource monitor!  
Unclear whether setStartTime changes the timecode metadata for the clip. Eg instead of starting at zero, you can add an offset. Think rec un, freerun, time of the day timecodes for timecodes generates by camcorders.

### **✅ Project panel: Import clip from Project Panel into sequence**

Code for bringing into sequence can be found in the sample panel JSX under the insert or append and overwrite functions

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L1415" caption=undefined %}

```javascript
// insert clip in sequence 
// get clip from Project panel 
var first = app.project.rootItem.children[0];
var seq = app.project.activeSequence; 
var vTrack1 = seq.videoTracks[0];
// insert in sequence at position (?) 
vTrack1.insertClip(first, '00;00;00;00'); 
```

```javascript
// append to last element in sequence
vTrack1.insertClip(first, lastClip.end.seconds);
if (vTrack1.clips.numItems > 0){
   var lastClip = vTrack1.clips[(vTrack1.clips.numItems - 1)];
  if (lastClip){
    vTrack1.insertClip(first, lastClip.end.seconds);
  }
}
```

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L1446" %}

```javascript
// overWrite
var seq = app.project.activeSequence;
var first = app.project.rootItem.children[0]; 
var vTrack1 = seq.videoTracks[0];
var now = seq.getPlayerPosition();
vTrack1.overwriteClip(first, now.seconds);
```

### **✅create sequence programmatically from list of clips**

Provided a list of clips, with in and out points for each segment, would want to create a sequence from it.

Is there a way to do this or do we have to combine previous insert/append function to achieve same result?  
****

From sample app, here is how to create a sequence

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L441" %}

```javascript
createSequence : function(name) {
		var someID	= "xyz123";
		var seqName = prompt('Name of sequence?',	 'Some Descriptive Name', 'Sequence Naming Prompt');
		app.project.createNewSequence(seqName, someID);
},
```

Get active sequence

```javascript
getActiveSequenceName : function() {
	if (app.project.activeSequence) {
		return app.project.activeSequence.name;
	} else {
		return "No active sequence.";
	}
},
```

From sample app

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L100" %}

See autoEdit jsx file \`create\_sequence\_from\_paper\_edit\` for how to iterate over a sequence as described in the autoEdit edl composer component.

Below how you’d add one clip, then, you’d need to iterate and change the insert timecode.

### **✅ Sequence: Import clip from source monitor into sequence**

```javascript
// get the active sequence 
var seq = app.project.activeSequence;

// or create a new one 
// var seq = app.project.createNewSequence(sequenceName, someID);

// get the track in the sequence
var vTrack1 = seq.videoTracks[0];

// find the clip in project panel, it returns a list of matches
var arrayOfProjectItemsReferencingSomePath = app.project.rootItem.findItemsMatchingMediaPath( 'someFileName.mov', 1);
// get the clip
var clipInProjectPanel = arrayOfProjectItemsReferencingSomePath[0];

// set in and out point in seconds
clipInProjectPanel.setInPoint(300); 
clipInProjectPanel.setOutPoint(600);

// add to track , can be timeocde ; separate notation or seconds.
vTrack1.insertClip(clipInProjectPanel, '00;00;00;00');
```

### **✅sequence: Adjust timings of clips in sequence**

From Adobe's Forum this seems to trim clips in the sequence;

{% embed url="https://forums.adobe.com/thread/2313445" %}

But not sure exactly what the code does.

```javascript
var clip1 = app.project.activeSequence.videoTracks[0].clips[0];
var endTime = clip1.end;
endTime.seconds = 50;
var startTime = clip1.start;
startTime.seconds = 10;
clip1.start = startTime;
clip1.end = endTime;
```

### **✅Sequence: Replace media for sequence clip**

Exists in pond5 panel -- can be used to replace low quality footage with higher quality or replace placeholders with real footage

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L351" %}

### **✅Source monitor: scrub to position and play**

```javascript
var pos = '10.5';
// pos is in the format of seconds.frames (e.g. 10.5 is 10 seconds, 5 frames) or in timecode ('00;00;10;05')
// This might be a useful reference: https://forums.adobe.com/thread/2420603 

// enable the undocumented QE DOM which is necessary to control program monitor playback
app.enableQE();
qe.source.player.startScrubbing();
qe.source.player.scrubTo(String(pos));
qe.source.player.endScrubbing();
app.sourceMonitor.play(1.0)
```

We are using a  js function to convert from seconds to seconds.frames format:

```javascript
function secondsToFrames(time){
    var buffer = 3 // amount of frames to jump before the start of the word to make it a little less abrupt
    let fps = 25;
    var base = Math.floor(time)
    var fraction = time - base
    var frames = Math.floor(fps * fraction) - buffer
    if (frames < 1){
        frames = fps + frames 
        base -= 1; 
    }
    return String(base) + '.' + String(frames)
}
```

### **✅Active Sequence/Program: scrub to position**

```javascript
var activeSequence = qe.project.getActiveSequence(); 
	
// note: make sure a sequence is active in PPro UI
if (activeSequence) {
  activeSequence.player.startScrubbing();

  activeSequence.player.scrubTo(String(pos));
  activeSequence.player.endScrubbing();
}

// Alternate
// would not be able to use the same pos without parsing as this will assume its a float vs the seconds.frames format
app.project.activeSequence.setPlayerPosition(pos * 254016000000) 
```

### **✅Import files into bin**

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L278" %}

```javascript
importFiles : function() {
	if (app.project) {
		var fileOrFilesToImport	= File.openDialog ("Choose files to import", // title
		0, // filter available files? 							true);// allow multiple?
		if (fileOrFilesToImport) {
			// We have an array of File objects; importFiles() takes an array of paths.
		 	var importThese = [];
		 	if (importThese){
				for (var i = 0; i < fileOrFilesToImport.length; i++) {
					importThese[i] = fileOrFilesToImport[i].fsName;
				}
			 	// this is the function 
				app.project.importFiles(importThese, 
				1,// suppress warnings 
				app.project.getInsertionBin(),
				0); // import as numbered stills
			}
		}
	}
}
```

### **✅Export as FCP XML**

From sample app:

{% embed url="https://github.com/Adobe-CEP/Samples/blob/master/PProPanel/jsx/PPRO/Premiere.jsx\#L234" caption=undefined %}

```javascript
// completeOutputPath == path to save fcp xml
// 1 == suppress UI 
app.project.activeSequence.exportAsFinalCutProXML(completeOutputPath, 1); 

```

