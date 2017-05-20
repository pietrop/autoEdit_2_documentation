# QA Export EDL

## Item to test #9: export

### Steps:
- Click on export button.
- Click on`?.`
- Click on each export option button.
 
### Expected Results:
- Clicking export shows export menu modal.
- In export menu, see export options with text description.
- `?` takes you to appropriate section in guide manual help page.
- Each export options produces a valid file. 

<!-- example of valid files. eg how to test srt file, open in vlc with original see if words show up --> 

---- 

## Item to test #10: EDL file
### Steps:
- Open EDL file in premiere: https://youtu.be/4z143-nJlzs?t=58s. 
- Reconnect media. 
- Play sequence.
- Check against original text selection in autoEdit app. 

### Expected Results:
- EDL worth checking in premiere. (possibly fcp 7 and avid too)
- Expecting slightly different result wheather EDL Comes from Transcription or from Paperedit. 

_Note_: For EDL testing, its worth uploading a video file "from web" as well as a video file from camcorder, e.g. with and without metadata info associated with camera timecode offset and metadata reel/card name. This makes slightly different EDLs. Also worth trying with PAL and NTSC footage. 

<!-- TODO add sample footage for each 1.web video. 2.Camcorder video. 3. NTSC video. 4. PAL video with text to select for transcription and paper-edit text selections from transcriptions to make for paper-edit and expected text to check in playback in video editing softwar -->

Testing in one video editing software is fine. But ideally we'd like to test in the 3 major. 

- FCP7
- Adobe Premiere
- Avide Media Composer 
- Davinci resolve (Free verison) 