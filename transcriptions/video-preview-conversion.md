# Video preview converter - draft

## Component/part description 

Convert input video into lower res video preview. For hypertranscript view. 

---
## Related projects

NA

---
## Implementations Options considered

initially converted to `ogg` video. Quality was very poor, so moved to webm.

<!-- link to module converts to ogg in quickQuote node? or video components github repo-->

---
## Current implementation

Uses ffmpeg. Fluent, ffmpeg.

Eg using NWJS this needs to be webm coz mp4 not supported. Issue is making it cross browser compatible. Webm not supported by safari and iOS.



---
## What needs refactoring 

Not very fast, it be great to find a way to speed up the conversion in some way. 

Perhaps test against `ogg`?