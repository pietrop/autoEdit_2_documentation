# audio to video

## Component/part description

This module is used to convert audio or video file ingested in autoEdit to meet the specs needed by the speech to text api that it is being used.

Unfortunately each has it's preferred encoding/settings. Eg you can't send the same audio file spec to IBM and pocketsphinx coz it wouldn't work for one or ther other.

## Related projects

First started looking into this when working on a refactor of [quickQuote](http://pietropassarelli.com/quickQuote.html), into a [quickQuote node version](https://github.com/pietrop/quickQuoteNode) making a [twitter export module](https://github.com/pietrop/quickQuoteNode/tree/master/lib/interactive_video_components/export/twitter_video).

## Implementations Options considered

You could also use `spawn` to fork a new ffmpeg process.

## Current implementation

Used fluent ffmpeg, passed ffmpeg as binary option to make it easier to package inside of autoEdit.

## What needs refactoring

At the moment there are two audio converter modules, one for IBM specs, and one for pocketsphinx specs. It be good to unify this code, perhaps pass in configuration variable with audio specs. Perhaps strategy pattern?

