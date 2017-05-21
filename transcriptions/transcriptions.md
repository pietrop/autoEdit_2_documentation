# Transcriptions - Draft

<!--
- Component/part description
- Related projects. Eg parts that look good, or previous implementations. But might not be considered for implementation options 
- Implementations Options considered
- Current implementation
- What needs refactoring
-->

---

## Component/part description 

In this section we are looking at the Transcription JSON schema used in autoEdit. 


---

## Related projects.

Connected to this is defining a schema for transcription, to make sure all components that work with this have a defined interface/specification. Eg  [BBC Transcript model](https://github.com/bbc/transcript-model)
 



<!--### starTime

 I used start time coz some other project was using htat-->

### Gentle json 

[See appendix for json](/gentle-json-transcription-specs.md) example.

<!-- link to appendix -->


### IBM Json  

[See appendix for json](/ibm-watson-json-specs.md) example.

<!-- TODO: update in appendix -->

### Video grep json 

See appendix for json example.

<!-- TODO: link to appendix -->

---

## Implementations Options considered


### quickQuote transcription modelling 

<!-- see dissertation chapter, perhaps add in appendix, or add that diss on gitbook.or just get relevant summary -->


### Other

An array of words object, to represent lines this could also be a nested array of word objects. 

Where the word object at a minimum as a start, end time and text attribute.

---

## Current implementation 

### Transcription domain
<!-- TODO: google drawings diagram of transcription components
-->

autoEdit JSON Transcription schema at a high level it models the objects present in a transcription.

- Transcription 
  - Paragraph 
    - Line 
      - Word 
        - Speaker



<!-- TODO: Link to appendix data structure autoEdit transcription json --> 

---

## What needs refactoring 

Name of `paragraph` and `line` attribute are ambiguos. 
It should be `lines` and `words` instead(?).



### replace array with hash
This is a bigger refactoring but instead of array data structure, could use hash/dictionary.

This way id is the key. and can make use of `key` `value` methods available in js. 
Lookup speed would improve(?) and could easily get array of values using js method. 
<!-- example -->







