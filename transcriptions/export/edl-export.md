# EDL export

## Component/part description

Module: EDL Composer module in autoEdit 2.

{% embed url="https://trello.com/c/Eq6gAOYe" %}

Extrapolated as standalone module and published to npm.  minimal tests with jest.

Module figured out by reverse engineering export EDL from FCP7. supports limited amount of feature, eg only edit. No transitions.

![EDL.png](https://lh5.googleusercontent.com/JMaIWkgb8sbLSMRLCJS6LKvrFu9PC_GY6HwYywS-iJWPi6Vl4K64_OdKW1QWctZsapJomsKkEygOYGbaAUuNaLk_dMpaCpfxDd435uqqBFjcAGWJ5bpbG9ZRxDBaelLD-F7MY3Ly)

See this section for more details on the [EDL format](../../appendix/edl-format.md)

EDL specifications 

{% embed url="https://documentation.apple.com/en/finalcutpro/usermanual/index.html\#chapter=96%26section=1%26tasks=true" %}

{% embed url="http://www.edlmax.com/EdlMaxHelp/Edl/maxguide.html" %}

## Related projects

## Implementations Options considered

### XML

Limitations of EDL. not multi-track sequence. Only one video track. If given a multitrack EDL JSON, eg b-roll. \(currently not a use case/feature for autEdit 2 or 3\) could create multiple EDL for each track, with track name/number next to it. \(this might not be necessary, XML option might be better suited, see below\). 

Rationale is that for other use case, eg app for making video slideshow multi-track video is needed. Having a module that can tackle this could add more flexibility in those scenarios. Such as when combining with computational photography, eg programmatically matching transcription video interview track with B-roll of cutaways images.

Another edl limitation. No support for text titles, while xml does.

## Current implementation

{% embed url="https://www.npmjs.com/package/edl\_composer" %}

{% embed url="https://github.com/pietrop/edl\_composer" %}

## What needs refactoring

connected with spec of paper-edit json.



