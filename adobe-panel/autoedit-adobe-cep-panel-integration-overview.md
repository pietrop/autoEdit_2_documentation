---
description: >-
  Describe the desired behaviour for the integration of autoEdit as a CEP panel
  with adobe.
---

# autoEdit Adobe CEP Panel integration overview

Organised by main autoEdit views.

Symbols legend: ✅done,  𝥷 todo , 𐄂 out of scope for this version

![diagram showing naming of various parts of adobe premiere that integrate with the autoEdit CEP panel.](https://docs.google.com/drawings/d/snAH8rGwT5UU_JN-0RAfOTQ/image?w=624&h=411&rev=1&ac=1&parent=1NTQvPj6UOD6QLPQUworz0JN4vH31tCvT6ML1Ne6BLfE)



## **View: New Transcript**

See user manual for refresher of what this view looks like

{% embed data="{\"url\":\"https://autoedit.gitbook.io/user-manual/transcribing\",\"type\":\"link\",\"title\":\"Transcriptions - autoEdit 2 User Manual\",\"icon\":{\"type\":\"icon\",\"url\":\"https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/spaces%2F-LKETZisqiBNpYXfFMzt%2Favatar.png?generation=1534636740751094&alt=media\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://www.gitbook.com/share/space/thumbnail/-LKETZisqiBNpYXfFMzt.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

Or even the interactive demo [http://www.autoedit.io/demo/\#transcriptions/new](http://www.autoedit.io/demo/#transcriptions/new)

### ✅Import video/audio in autoEdit

For importing video or audio for transcriptions

* Select a video or audio file in project panel
* Click on choose file
* File path is loaded in autoEdit

### ✅**Import srt caption in autoEdit**

For importing captions

* Same as above +
* For caption option Select a srt file in project panel
* chose caption file radio button
* Click chose caption button,
* Srt File path is loaded in autoEdit

## **View: Transcript show**

**See user manual for refresher od what this view looks like**  

{% embed data="{\"url\":\"https://autoedit.gitbook.io/user-manual/transcribing\#selecting-text-from-a-transcription\",\"type\":\"link\",\"title\":\"Transcriptions - autoEdit 2 User Manual\",\"icon\":{\"type\":\"icon\",\"url\":\"https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/spaces%2F-LKETZisqiBNpYXfFMzt%2Favatar.png?generation=1534636740751094&alt=media\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://www.gitbook.com/share/space/thumbnail/-LKETZisqiBNpYXfFMzt.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}



### **✅Navigation**

* ✅When you navigate to an interview it loads the clip associated into the source monitor \(user can replace the clip with a sequence or the correct project item manually if desired\)
* ✅ If on 12.1 highlight the appropriate project item in the browser by selecting programmatically if possible
* ✅ When user clicks a word:
  * ✅ Moves playhead in source monitor to that point
  * 𐄂 and starts playing
* 𐄂 Option: stop playing after \(x\) seconds \(if checked will activate a setTimeout to do the scrub method of stopping playback -- can perhaps do programmatically to automatically end at end of nearest paragraph, or allow user to input a setting\)

### **✅ add highlights selection from autoEdit to premiere**

The highlights for a transcription can be added to a new premiere video sequence programmatically.

### **𐄂 add selection from autoEdit to premiere \(with in and out points\)**

in transcription view set inPoint + outPoint on selection or on word click.

Eg When you make new hilight it could set in and out on source monitor.

Or just Out of scope for this version, to be revisited in subsequent versions.

Coz once the clip is loaded in source monitor and the playhead moved to current time on word click. The user can do cmd + i and cmd + o to set the desired outpoint, and then there’s also a video editor short cut to insert \(with different type of inserts cmd +  , and cmd + .\) segment in between in and out into the active sequence  
or as a workaround for now can use  add highlights selection from autoEdit to premiere and clear highlights to make new selections etc..



## **View: Paper Edit Show**

See user manual for refresher of what this view looks like   ****

{% embed data="{\"url\":\"https://autoedit.gitbook.io/user-manual/paperediting\",\"type\":\"link\",\"title\":\"Paperediting - autoEdit 2 User Manual\",\"icon\":{\"type\":\"icon\",\"url\":\"https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/spaces%2F-LKETZisqiBNpYXfFMzt%2Favatar.png?generation=1534636740751094&alt=media\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://www.gitbook.com/share/space/thumbnail/-LKETZisqiBNpYXfFMzt.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

### **✅Export paper-edit as premiere sequence**

\*\*\*\*

## **𝥷 Clean up**

* save file from panel in export view or hide

