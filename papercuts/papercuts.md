# Papercuts 

<!--
- Component/part description 
- Related projects. Eg parts that look good, or previous implementations. But might not be considered for implementation options 
- Implementations Options considered
- Current implementation 
- What needs refactoring 
--> 



## Component/part description 


![selection annotation balsamiq mockup in transcription view]()

Semanticly papercuts can be selections, hilights, annotations when found in a transcription but is only as the building block of a paper-edit that we refer to them as paper-cuts.

### Selections component 
A component that can make a selection of word objects from a transcription/hypertranscript.

### Annotations
Associate a selection with a tag, a tag description and a comment.

### Tags
Tags to group annotations. 


--
## Related projects.

### Annotations 
Need Annotation schema specification
Check out recent annotation spec by W3C https://www.w3.org/annotation/ 

Combine, selection, annotation, tag, and event info/papercut for paper edit/“JSON EDL” when multiple annotations combined. With some as optional fields. Eg tags, etc..

Could use http://tether.io to keep annotation close to selection in trascription .
And coul use bootstrap popovers https://getbootstrap.com/javascript/#popovers 


--
## Implementations Options considered

### Selections
Selections 
Make text selection of transcription 

To look into https://github.com/timdown/rangy 

https://developer.mozilla.org/en-US/docs/Web/API/Selection 


--
## Current implementation 

Paper-edit json schema specification
Connected to this is defining a schema for paper-edit, to make sure all components that work with this have a defined interface/specification. 
Same as EDL papercut/”event” object in “EDL JSON: schema  from EDL composer component module from autoEdit2.

<!-- more on current implementation -->

### Selection 
ended up using intermediate data structure. 
Data is stored in html in data attribute for ease of retrieval at word level.


--
## What needs refactoring 

### → Refactoring: Words Selections

How to do text selection for highlight paper cuts. Currently in transcription show it traverse the DOM to update those. 
Eg see selecting words function. That recognises uses selection. 
https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/views/transcription_view.js#L488 

And this function to update the dom with selections. 
https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/views/transcription_view.js#L91

There might be a better way to do this? Using rangy ?


### refactoring words data
Data is stored in html in data attribute for ease of retrieval at word level. this is very bulky. There might be more elegant options, using listeners and events(?) or other(?).

