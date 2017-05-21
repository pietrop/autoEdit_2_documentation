# EDL export - draft

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

## Module: EDL Composer module in autoEdit 2. 
To extrapolate as standalone module and publish to npm. Add tests. Decide on test suite for these modules. 
http://www.autoedit.io/jsdoc_docs/module-edl_composer.html 

Module figured out by reverse engineering export EDL from FCP7. supports limited amount of feature, eg only edit. No transitions.

![Chris bbc img EDL explanation]()

connected with spec of paper-edit json. 

<!-- example or link to appendix example -->
 

[EDL tutorial](/edl-format.md)

EDL specifications 
https://documentation.apple.com/en/finalcutpro/usermanual/index.html#chapter=96%26section=1%26tasks=true 

http://www.edlmax.com/EdlMaxHelp/Edl/maxguide.html 
 
 

Limitations of EDL. not multi-track sequence. Only one video track. If given a multitrack EDL JSON, eg b-roll. (currently not a use case/feature  for autEdit 2 or 3) could create multiple EDL for each track, with track name/number next to it. (this might not be necessary, XML option might be better suited, see below).
Rationale is that for other use case, eg app for making video slideshow multi-track video is needed. Having a module that can tackle this could add more flexibility in those scenarios. 
Such as when combining with computational photography, eg programmatically matching transcription video interview track with B-roll of cutaways images.

Another edl limitation. 
No support for text titles, while xml does.


