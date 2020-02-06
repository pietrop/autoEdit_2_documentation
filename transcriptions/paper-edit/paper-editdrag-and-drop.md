# drag-and-drop

## Component/part description

## Related projects.

## Implementations Options considered

### sortable

Eg use js library [https://github.com/RubaXa/Sortable](https://github.com/RubaXa/Sortable)

### vuejs

Or if using veu js [https://github.com/SortableJS/Vue.Draggable](https://github.com/SortableJS/Vue.Draggable)

### dragula

Or use [https://github.com/bevacqua/dragula](https://github.com/bevacqua/dragula) js To figure out in dragula is how to integrate with selections. Eg make a selection draggable. Coz I think dragula needs draggable items to be wrapped in a div with a certail class \(?\)

Could wrap selection/annotations/tags in a div with that class to make this possible.

in autoEdit Comes from a problem is of representation of highlight for drag and drop. Hilight is a class added to a word.

[https://github.com/OpenNewsLabs/autoEdit\_2/blob/paperedit/lib/app/views/transcription\_view.js\#L34](https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/views/transcription_view.js#L34)

It be good to figure this out as a component.

JSffidle high fidelity mockup example: [https://jsfiddle.net/pietrops/Lufaerr2/1/](https://jsfiddle.net/pietrops/Lufaerr2/1/) For simplicity the words are plain text and not wrapped in span tag, as they would be in an proper hyper transcript.

![Screen Shot 2017-04-19 at 15.12.04.png](https://lh6.googleusercontent.com/VI0mT7f6yiTz_DRbEhcDppEmq3qRQfN5XEelu3lxHXZVhiRww44FRrbWdn_6lFFWIoCvDLbPa2qWyO-phE4DvheeXeaOVFViMjHdbhKU-QhNQNRBMMgVW0GsnfOMZXlEJqC9ovqa)

{% embed data="{\"url\":\"https://jsfiddle.net/pietrops/Lufaerr2/1/\",\"type\":\"rich\",\"title\":\"Paperedit - dragula - JSFiddle\",\"description\":\"Test your JavaScript, CSS, HTML or CoffeeScript online with JSFiddle code editor.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://jsfiddle.net/img/favicon.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"app\",\"url\":\"https://jsfiddle.net/pietrops/Lufaerr2/embedded/\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.25%;\\\"><iframe src=\\\"https://jsfiddle.net/pietrops/Lufaerr2/embedded/\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":0}}" %}



This makes the whole line / paragraph draggable.

Making words as draggable and having multi selection is outside of the scope of dragula \(read that in the issues section of github repo\).

Adding sortable with dragula gives this error `TypeError: Cannot read property 'pointerEnabled' of undefined` There might be a problem with dragula and browserify?

### Option: Jquery UI multisortable

Other option is JQuery UI multisortable previous version of autoEdit in node. A bit fiddly to make a selection.

Github repo: [https://github.com/shvetsgroup/jquery.multisortable](https://github.com/shvetsgroup/jquery.multisortable) JS fiddle example: [https://jsfiddle.net/neochief/KWeMM/](https://jsfiddle.net/neochief/KWeMM/)

In previous version we used jqueryUI. [https://github.com/pietrop/autoEdit\_nwjs\_alpha\_RandD](https://github.com/pietrop/autoEdit_nwjs_alpha_RandD)

[see vide demo of previous version](https://pietro-passarelli.wistia.com/medias/rmur7siumj)

using express, jquery multisortable for D&D, bbc video compositor for preview. issues:

* lack of data structure for selection to -&gt; papercut-&gt;to paperedit made it hard to add text in a reliable way. 
* jquery ui multisortable selection not natural, click then `shift` + `click` to select range of text.

[https://github.com/pietrop/autoEdit\_nwjs\_alpha\_RandD/blob/master/views/template/paperedit.html](https://github.com/pietrop/autoEdit_nwjs_alpha_RandD/blob/master/views/template/paperedit.html)

![Screen Shot 2017-04-19 at 19.17.07.png](https://lh3.googleusercontent.com/AByDvF7-eci9joyF3-OkNM_j40OBpdefk1xeJ4alcXpFRLdlxX0gpso1Op6Ac59AeOUOBfMc5I_CyvO2Sl4LryYy_4Md8bT5EFJuALVEHShp3ZknZbzJQzcAcQOgH0Zb_rYU1HFW)

Abstracted example with jquery multi sortable [https://jsfiddle.net/pietrops/eo4najce/](https://jsfiddle.net/pietrops/eo4najce/)

{% embed data="{\"url\":\"https://jsfiddle.net/pietrops/eo4najce/\",\"type\":\"rich\",\"title\":\"jquery.multisortable - Working - JSFiddle\",\"description\":\"Test your JavaScript, CSS, HTML or CoffeeScript online with JSFiddle code editor.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://jsfiddle.net/img/favicon.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"app\",\"url\":\"https://jsfiddle.net/pietrops/eo4najce/embedded/\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.25%;\\\"><iframe src=\\\"https://jsfiddle.net/pietrops/eo4najce/embedded/\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":0}}" %}

Main issue with this is that you need to click to select. And do click shift to select from one word to the other.

An option could be to add slected class to words span contigues to clicked selected?



### **Option: Sortable**

Another option is to use sortable [https://rubaxa.github.io/Sortable/](https://rubaxa.github.io/Sortable/)

### Jquery Sortable

[https://johnny.github.io/jquery-sortable/](https://johnny.github.io/jquery-sortable/) Nice coz it has nested ul/li which would allow to move all sections of paragraphs all togethere.

### Palestinian remix / hyperaudio - Laurian

Also review Palestinian remix \(trello/slack\) D&D by Laurian, example code.

[https://github.com/hyperaudio/hyperaudio-experimental](https://github.com/hyperaudio/hyperaudio-experimental)

From Laurian:

> the drag and drop was made with rangy and tether.js \([http://tether.io/](http://tether.io/)\) , basically using tether to replicate the selection and have it html5 draggable

{% embed data="{\"url\":\"http://popcorn.gridinoc.com/\",\"type\":\"link\",\"title\":\"Hyperaudio Experimental\",\"icon\":{\"type\":\"icon\",\"url\":\"http://popcorn.gridinoc.com/media/favicon.ico\",\"aspectRatio\":0}}" %}

![Screen Shot 2017-04-10 at 19.23.59.png](https://lh4.googleusercontent.com/pCA-mdvlWqcdKdgTLJ7kNq0QOuDZf-7Yk22EXscnbkbVjPSIPUoe5TN_zFPW7IazAQgAxBM4CxyE7_TYhTyl0rgu9MpfxB6ww-R7oIqwzUgW40hZhQaM16DrcYCs4xgexvghCSs1)

### listener + data layer // Andrea's option &lt;-- current implemtation

Listener on user text selection on transcription Grab info Create div Add and div to the paperedit side at the end.

Div on paper-edit side can then be sortable.

DataLayer

Spec of the EDL sequence. [http://www.autoedit.io/jsdoc\_docs/module-edl\_composer.html](http://www.autoedit.io/jsdoc_docs/module-edl_composer.html)

[https://github.com/andrixb/texthighliter](https://github.com/andrixb/texthighliter)

{% embed data="{\"url\":\"https://jsfiddle.net/andrixb/9cnp4rgL/56/\",\"type\":\"rich\",\"title\":\"Edit fiddle - JSFiddle\",\"description\":\"Test your JavaScript, CSS, HTML or CoffeeScript online with JSFiddle code editor.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://jsfiddle.net/img/favicon.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"app\",\"url\":\"https://jsfiddle.net/andrixb/9cnp4rgL/embedded/\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.25%;\\\"><iframe src=\\\"https://jsfiddle.net/andrixb/9cnp4rgL/embedded/\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":0}}" %}

[http://farhadi.ir/projects/html5sortable/](http://farhadi.ir/projects/html5sortable/)

[https://www.html5rocks.com/en/tutorials/dnd/basics/](https://www.html5rocks.com/en/tutorials/dnd/basics/)

[https://github.com/andrixb/v-textselector](https://github.com/andrixb/v-textselector)

Not using drag and drop. But using data layer. User selects words in transcriptions. Data structure is created with those info. Papercut ejd template is populated And is added at the end of paper edit With mouse down listener

With html5 drag and drop added sortable To allow to be able to rearrange order of papercuts. Can drag a piece and then copy and append after element you drop on. And remove original piece.

Subsequent improvement If click on papercut then can add selection after that one rather then at the end. Todo: find away to signal that in CSS.

## Current implementation

Not actually drag and drop but intermediate data structure implementation.

## What needs refactoring

