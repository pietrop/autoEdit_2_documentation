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

### Gentle - json 

[See appendix for json](/gentle-json-transcription-specs.md) example.

<!-- link to appendix -->


### IBM - Json  

[See appendix for json](/ibm-watson-json-specs.md) example. As well as their [stt api reference](https://www.ibm.com/watson/developercloud/speech-to-text/api/v1/) and documentation.

<!-- TODO: update in appendix -->

### Pocketsphinx  - plain text

[See appendix for example](/pocketsphinx-results.md) pocketsphinx plain text.

<!-- TODO: link to appendix -->

---

## Implementations Options considered

<!-- 
### quickQuote transcription modelling 

see dissertation chapter, perhaps add in appendix, or add that diss on gitbook.or just get relevant summary.

initially modelled the srt file, coz was parsing the srt file. saved that in db. however that was restrictive. ?
-->

### Other

An array of words object, to represent lines this could also be a nested array of word objects. 

Where the word object at a minimum as a start, end time and text attribute.

---

## Current implementation 

### Transcription domain
<!-- google drawings diagram of transcription components https://docs.google.com/drawings/d/1PzZw3Zu5BkT6Y-JM7Ox4OTBpaWxRvyjnh4UMxHIe8rs/edit
-->

autoEdit JSON Transcription schema at a high level it models the objects present in a transcription.

![Transcription modelling diagram](/assets/Transcription modelling.png)

In this representation:

- Transcription 
  - Paragraphs  ← speaker 
    - Lines 
      - Words 

Speakers are associated to paragraphs. Paragraphs are treated as sections of lines.

A list of speakers can also be kept separate, similarly to how IBM Watson stt API returns the results of speaker diarization.

<!-- TODO: add link to api reference/documetnation ibm spekaer diarization json --> 

[See Appendix for autoEdit json schema example](/autoedit-transcription-json.md).

---

## What needs refactoring 

Name of `paragraph` and `line` attribute are ambiguos. 
It should be `lines` and `words` instead(?).



### replace array with hash
This is a bigger refactoring but instead of array data structure, could use hash/dictionary.

This way id is the key. and can make use of `key` `value` methods available in js. 
Lookup speed would improve(?) and could easily get array of values using js method. 
<!-- example -->







