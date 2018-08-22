# Paper-edit

## Component/part description

### Paper-edit json schema specification

Connected to this is defining a schema for paper-edit, to make sure all components that work with this have a defined interface/specification. This is same as a spec for “EDL JSON” which is used in the EDL composer module.

* [component:Search and filter ](paper-editsearch-filter.md)
* [component:Drag and Drop papercut ](paper-editdrag-and-drop.md)
* [component:Video preview ](paper-editvideo-preview.md)

Components representation paper-edit view

![Components representation paper-edit view ](../../.gitbook/assets/components_representation_paperedit_view.png)

--

## Related projects.

NA

--

## Implementations Options considered

--

## Current implementation

--

## What needs refactoring

The flow and consistency of json data representation between the different components json is not great, needs to be revisited.

For instance Paper-edit and transcription EDL export should have consistent schema. at the moment they are different.

