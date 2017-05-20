# QA Transcriptions

## Item to test #2: Adding transcription

### Steps:
- Click “new” in nav bar. 
- Add transcription details. 

### Expected Results:
- `?` http://www.autoedit.io/user_manual/setup.html#gentle-stt-open-source-free-and-offline. Page opens in a default browser. 
- After adding transcription details, you are sent to transcription list. See transcription with name and description.
- After saving transcription, new links in list disabled. See spinning wheel symbol next to title for about 5 min processing time. 


![Screenshot of spinning transcription waiting 5min process time]()

- After 5 min from saving transcription, disabled links to become available.


## Item to test #3: Deleting a transcription

### Steps:
- Click red delete button in transcription list. 

### Expected Results:
- Clicking delete for that transcription removes it from the list. 
- After clicking new, list should be consistent with the previously deleted transcription. 

## Item to test #4: Show transcription
### Steps:
- Click on transcription (anywhere but the delete button).
### Expected Results:
- You are taken to a transcription show page.

![Transcription show page]()

_Known issue_: When video is done processing, it does not self-update the preview if on show page. You need to go back to list and then back to show to get an updated video preview. 

## Item to test #5: Show transcription - playback

### Steps:
- Click on word in transcription. 

### Expected Results:
- In highlight mode, default, you click on word and are taken to corresponding part of the video. Video starts playing. 

## Item to test #6: Show transcription - text position indication

### Steps:
- Click on video player play button or click on text of transcription.

### Expected Results:
- While video is playing, text changes color (grey to black up to current point) to signal corresponding part.

_Known bug_: If you start playing video from the video player it does not do text color change. If you start the video by clicking on a word, then it works. 

## Item to test #7: Show transcription - highlighting 

### Steps:
- Highlight transcription text with mouse (push click, hold, then release).

### Expected Results:
- You should be able to select text and have the blue highlight underline appear under the text.
- You should be able to unselect text by highlighting the previous selection. 

_Known behavior_: When selecting both previously selected and not, it inverts selection. The desired behaviour is to remove selection.

## Item to test #8: Show transcription - Edit text

### Steps:
- Click on Edit mode in transcription show page
- Click on a word
- Edit the text 
- Click on tab to move to next word. 

### Expected Results:
- Expect clicked word to auto select word, and make word text editable 
- Expect editing of words to auto save. To test this navigate out of transcription show page and back in, changes should have persisted.


[_see QA Export section to complete_](/qa/qa-export.md)
