# autoEdit 2 R&D Documentation for Developers

R&D Documentation for Developers for autoEdit2. [autoEdit.io](/www.autoEdit.io)

**TL;DR **: New version of autoEdit 2 `1.0.6` that does paper-editing.

## **Parts**

It's helpful to discuss the implementation of autoEdit by looking at the parts that make up the whole as stand alone overarching components, that are built of other smaller components and modules.

Tick \(✔\) for features implemented in `1.0.5`**      
**

1. **Transcriptions** ✔

   1. Transcriber

      1. STT✔

      2. Video preview conversion ✔

      3. Metadata info for EDL✔

   2. Hyper-Transcript ✔

      1. Representation video + transcript in sync

2. **Papercuts Selections** ✔

3. **Annotations Tags**

4. **Paper-edit**

   1. Search and filter paper-cuts and transcriptions

   2. D&D papercut in paper-edit

   3. Preview paper-edit

5. **Export**

   1. Paper-edit export to EDL

Main data structures in the project

* Transcription json 
* paper-cuts json 
* paper-edit json 

---

If you are not familiar with [Node](https://nodejs.org/en/), [NWJS](http://docs.nwjs.io/en/latest/For%20Users/Getting%20Started/), [backbone](http://backbonejs.org/) or not sure were to start to get an overview to familiarise yourself with this project, check out the [prerequisite section](/prerequisites.md) to get an overview of the stack and see the minimum you need to know to get up to speed with this project.

