# B-roll computational photography

For now, just adding interviews in autoEdit. What if could add also b-rolls/cutaways or obs doc scenes. and it recognises, objects, people etc.. computational photography capabilities. 

Could add new column to paper-edit for visuals to go along side audio (transcription). 

However not hat export would need to be as XML as EDL only supports one track. or could do 1 EDL per track. Which means two files. One for interview track and the other for video track.

----

For example here are some notes from the Watson conf 2016, but same could be done with Open source tech. 

## Visual recognition in video -draft notes
API key in process env variable

Ffmpeg select='not (mod 30 Every Number of frames Collect files as glob (node globe library) Spawn sync process node
Loop through images Load image and send to visual recognition classifier
Node A sync, img sent all at same time Code available on blog bluechasm
Outliers generally 1 result only.
-vsync cutting video without transcoding it.

Ffmpeg can pull out time stamp robert@bluechasm.com or tweet @RobertFromBC

http://blog.bluechasm.com/post/152964631846/turning-visual-recognition-into-video-recognition 
code example from blog:

```js
//Included libraries
var glob = require('glob');
var watson = require('watson-developer-cloud');
var fs = require('fs-extra');
var sync = require('child_process').spawnSync;

//Visual Recognition API key setup
var visual_recognition = watson.visual_recognition({
  api_key: [YOUR API KEY HERE], // Demo Credentials.
  version: 'v3',
  version_date: '2016-05-20'
});

//Cut the video into frames: One every 30 frames
const procVid = sync('ffmpeg', ["-i" ,"video2.mp4","-vsync" ,"0", "-vf","select='not(mod(n,30))'","image_%d.jpg"]);

//Initialize the arrays and lists
var files= glob.sync('*.jpg' );
var x = files.length;
var j =0;
tags = []

//Tally up the results
function count(tags){
    var counts = {};
    for(var k = 0;k<tags.length;k++){
        counts[tags[k]] = (counts[tags[k]] || 0)+1;
        if(k==tags.length-1){
            console.log(counts)
        }
    }
}

//Iterate over the list of images
for(var i =0;i<x;i++){
    //Build request with the image you want to tag
    var params = {
        images_file: fs.createReadStream(files[i])
    };

    //Send image to tag to the Classify endpoint
    visual_recognition.classify(params, function(err, res) {
        if (err){
            console.log(err);
        }

        //Error Checking
        if(res.images[0].hasOwnProperty('error')||res.images[0]['classifiers'][0]['classes'].length ==0){
                    tags.push("NA");
                    j+=1
        }
        //No errors: continue with storing tags
        else {
            tags.push(res.images[0]['classifiers'][0]['classes'][0]['class']);
            console.log("Done Getting tags for: "+res.images[0].image);
            j+=1;
        }
        //Once you're done with the tags, count them up
        if(j==x){count(tags)}
    });
} 
```