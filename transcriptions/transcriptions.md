# Transcriptions - Draft

<!--
- Component/part description
- Related projects. Eg parts that look good, or previous implementations. But might not be considered for implementation options 
- Implementations Options considered
- Current implementation
- What needs refactoring
-->


## Component/part description 

Transcription JSON schema. 


## Related projects.

Connected to this is defining a schema for transcription, to make sure all components that work with this have a defined interface/specification. 
Eg review BBC Transcript model https://github.com/bbc/transcript-model 

## Implementations Options considered

### Transcription domain
<!-- TODO: google drawings diagram of transcription components
-->

autoEdit JSON Transcription schema at a high level it models the objects present in a transcription.

- Transcription 
  - Paragraph 
    - Line 
      - Word 
        - Speaker

### Other

<!-- array of words, nested array --> 


## Current implementation 

<!-- TODO: Link to appendix data structure autoEdit transcription json --> 


## What needs refactoring 

Name of `paragraph` and `line` attribute are ambiguos. 
It should be `lines` and `words` instead(?).

### replace array with hash
This is a bigger refactoring but instead of array data structure, could use hash/dictionary.

This way id is the key. and can make use of `key` `value` methods available in js. 
Lookup speed would improve(?) and could easily get array of values using js method. 
<!-- example -->







