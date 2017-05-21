# Hypertranscript - Draft

<!--
- Component/part description 
- Related projects. Eg parts that look good, or previous implementations. But might not be considered for implementation options 
- Implementations Options considered
- Current implementation 
- What needs refactoring 
--> 

## Component/part description 

Best described by functionality 
- click on word, play video at corresponding part
- video plays, words change color to show you were it's at. 
- sync scroll (optional)
- search text (optional) 

It’s a view. It’s extensible. Eg need to be able to add other components, for text selections, annotations, tags, search, etc to the view.


---
## Related projects

### What is an `hypertranscript`?

[HyperTranscript representation as described in hyperaudio](http://hyperaud.io/blog/hypertranscripts) `==` Clickable transcript in sync with video. 


--
## Implementations Options considered

in quickQuote, made hypertranscript using rails and erb.

--
## Current implementation 
Using backbone and browserify, with ejs templating. 

--
## What needs refactoring 

Reusable front end client side components. 

At the moment the views are one block, it could be smaller views combined together, with defined interfaces, to make it more reusable. 

Eg the hypertranscript "component" in transcript show and in paper edit is repeated.
See view components for paper-edit

Eg in branch paper-edit (which is an attempt to implement “v3”) I have tried to put hypertranscript template as a separate view. 
https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/templates/hypertranscript.html.ejs 

Which extracts it from transcription show template. 
https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/templates/transcription_show.html.ejs 

Paper-edit show and transcription show could be made of components.


Entertaining the idea of using [vuejs]() to help with this. Or to do more research on how to best use backbone views in a more modular way. 


