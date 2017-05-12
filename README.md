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

![](https://docs.google.com/drawings/d/slSCkfwYW5hCSyJSEP8ggjg/image?w=624&h=221&rev=90&ac=1)

