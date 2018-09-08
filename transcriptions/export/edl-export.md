# EDL export

## Component/part description

Module: EDL Composer module in autoEdit 2.

{% embed data="{\"url\":\"https://trello.com/c/Eq6gAOYe\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/Eq6gAOYe\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

Extrapolated as standalone module and published to npm.  minimal tests with jest.

Module figured out by reverse engineering export EDL from FCP7. supports limited amount of feature, eg only edit. No transitions.

![EDL.png](https://lh5.googleusercontent.com/JMaIWkgb8sbLSMRLCJS6LKvrFu9PC_GY6HwYywS-iJWPi6Vl4K64_OdKW1QWctZsapJomsKkEygOYGbaAUuNaLk_dMpaCpfxDd435uqqBFjcAGWJ5bpbG9ZRxDBaelLD-F7MY3Ly)

See this section for more details on the [EDL format](../../appendix/edl-format.md)

EDL specifications 

{% embed data="{\"url\":\"https://documentation.apple.com/en/finalcutpro/usermanual/index.html\#chapter=96%26section=1%26tasks=true\",\"type\":\"link\",\"title\":\"Final Cut Pro 7 User Manual\",\"description\":\"Comprehensive Apple documentation for Final Cut Pro 7 User Manual\"}" %}

{% embed data="{\"url\":\"http://www.edlmax.com/EdlMaxHelp/Edl/maxguide.html\",\"type\":\"link\",\"title\":\"Guide to EDL Management\"}" %}

## Related projects

## Implementations Options considered

### XML

Limitations of EDL. not multi-track sequence. Only one video track. If given a multitrack EDL JSON, eg b-roll. \(currently not a use case/feature for autEdit 2 or 3\) could create multiple EDL for each track, with track name/number next to it. \(this might not be necessary, XML option might be better suited, see below\). 

Rationale is that for other use case, eg app for making video slideshow multi-track video is needed. Having a module that can tackle this could add more flexibility in those scenarios. Such as when combining with computational photography, eg programmatically matching transcription video interview track with B-roll of cutaways images.

Another edl limitation. No support for text titles, while xml does.

## Current implementation

{% embed data="{\"url\":\"https://www.npmjs.com/package/edl\_composer\",\"type\":\"link\",\"title\":\"edl\_composer\",\"description\":\"ELD composer can be used to create Edit Decision List. EDL, Edit Decision List, is a plain text format that describes a video sequence. It can be opened in a video editing software to reconnect media to assemble a video sequence\",\"icon\":{\"type\":\"icon\",\"url\":\"https://static.npmjs.com/1996fcfdf7ca81ea795f67f093d7f449.png\",\"width\":230,\"height\":230,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://static.npmjs.com/338e4905a2684ca96e08c7780fc68412.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

{% embed data="{\"url\":\"https://github.com/pietrop/edl\_composer\",\"type\":\"link\",\"title\":\"pietrop/edl\_composer\",\"description\":\"edl\_composer -  EDL composer can be used to create Edit Decision List. EDL, Edit Decision List, is a plain text format that describes a video sequence. It can be opened in a video editing software ...\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars3.githubusercontent.com/u/4661975?s=400&v=4\",\"width\":372,\"height\":372,\"aspectRatio\":1}}" %}

## What needs refactoring

connected with spec of paper-edit json.



