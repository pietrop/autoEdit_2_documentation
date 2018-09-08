# Selections

## Component/part description

Make text selection of transcription

To look into [https://github.com/timdown/rangy](https://github.com/timdown/rangy)  
[https://developer.mozilla.org/en-US/docs/Web/API/Selection](https://developer.mozilla.org/en-US/docs/Web/API/Selection)

## Related projects

Hyperaudio, palestinian remix

## Implementations Options considered

### Palestinaian remix drag and drop

Palestinaian remix drag and drop

### Other

How to do text selection for highlight paper cuts. Currently in transcription show it traverse the DOM to update those.

Eg see selecting words function. That recognises uses selection.

[https://github.com/OpenNewsLabs/autoEdit\_2/blob/paperedit/lib/app/views/transcription\_view.js\#L488](https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/views/transcription_view.js#L488)

And this function to update the dom with selections.

[https://github.com/OpenNewsLabs/autoEdit\_2/blob/paperedit/lib/app/views/transcription\_view.js\#L91](https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/views/transcription_view.js#L91)  
There might be a better way to do this? Using rangy ?  
****

## Current implementation

## What needs refactoring

