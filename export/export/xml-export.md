# XML Export

## Component/part description 

---
## Related projects


---
## Implementations Options considered


---
## Current implementation


---
## What needs refactoring 

----


# XML (optional)
Module: XML FCP7 standard, compatible with Adobe Premiere.
Compatible with Avid? Advantage is can add multi track.

See srt to XML FCP7 module for more on building those kind of XMLs https://www.npmjs.com/package/srt2xmeml
https://github.com/woutervroege/node-srt2xmeml

Which converts srt file into text tracks in XML FCP7 specs.

![xml tool screenshot]() <!-- https://docs.google.com/document/d/12mUuXAtE65vhy5Sm0tmKRdgXGMn_Ob4RZEs9T5uDPkM/edit#heading=h.h9fmyw2nknlw-->

XML FCP7 specs
https://documentation.apple.com/en/finalcutpro/usermanual/index.html#chapter=97%26section=3%26tasks=true

Maybe make library that composes “EDL json” into XML FCP7.

Where “EDL JSON” refers to datastructrue of paper-edit in autoEdit 3, representing a video sequence.

From Storytellers united slack,

>Getting back to the “exporting from Final Cut, Premiere etc.” task @cubicgarden @cnorthwood @pietro - just stumbled upon bodymovin, an open source, actively developed After Effects plugin for exporting AE animations to open web formats: https://github.com/bodymovin/bodymovin . Maybe interesting? Didn’t try it yet, but if it does what it promises to do, it could be a helpful part of the workflow..
