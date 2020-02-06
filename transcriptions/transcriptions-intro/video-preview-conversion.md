# Video preview conversion

## Component/part description

Convert input video into lower res video preview. For hypertranscript view.

Uses ffmpeg. Fluent ffmpeg.

## Related projects

NA

## Implementations Options considered

initially converted to `ogg` video. Quality was very poor, so moved to webm.

Then in previous implementation using NWJS this needs to be `webm` coz `mp4` not supported. Issue is making it cross browser compatible. `webm` not supported by safari and iOS.

## Current implementation

However with the recent move to Electron, was able to refactor and add support for `mp4`.

ffmpeg command 

```bash
ffmpeg -i inputfile -vf "scale=-1:360" -c:v libx264 -preset ultrafast -crf 40 output.mp4
```

see component 

{% embed url="https://github.com/OpenNewsLabs/autoEdit\_2/blob/master/lib/interactive\_transcription\_generator/video\_to\_html5/index.js" %}

 

{% embed url="https://trello.com/c/IPZ8mKhL" caption="in textAV components" %}

## What needs refactoring

Seems quiet fast now. 

