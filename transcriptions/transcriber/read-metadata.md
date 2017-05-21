# Transcriber: Read Metadata

## Component/part description 

Read metadata info from input video or audio file, minimum required.

* Card name
* Timecode offset
* File name

Altho card name seems to be optional in Adobe Premiere.

<!-- Added fps. to the mix, explain how this is calculated -->


<!-- link to EDL format, and to edl composer module, for attributes needed-->


---
## Related projects

NA

---
## Implementations Options considered

NA


---
## Current implementation

Uses `ffprobe`, through fluent-ffmpeg.

---
## What needs refactoring 

<!-- need to figure out what is the fps ? -->