# ffmpeg and ffprobe in electron

using modified version of static ffmpeg /ffprobe lib.

* github.com:pietrop/ffmpeg-static

  -github.com:pietrop/ffprobe-static

require in config.js and make them avaible to rest of app from there. eg require config to get the path.

static ff has advantage that packages cross platform bin of ffmpeg. which means you could be developeing this app on mac, linux and windows, without ffmpeg on your machine and could still be developing for autoEdit.

in production, we want to remove the versions we don't need. we use the files notation for electron-builder to specify in package.json

that all apps need to have these files. \(this might not be needed tho as they are added by default?\) Making use of `${os}` and `${arch}` var provided.

```javascript
"node_modules/ffmpeg-static/bin/${os}/${arch}/ffmpeg",
"node_modules/ffmpeg-static/index.js",
"node_modules/ffmpeg-static/package.json",
"node_modules/ffprobe-static/bin/${os}/${arch}/ffmpeg",
"node_modules/ffprobe-static/index.js",
"node_modules/ffprobe-static/package.json"
```

then for each os specific settings, eg for mac we do this, remove the folders for the opposite os.

```javascript
"mac": {
      "category": "public.app-category.productivity",
      "files": [
        "!node_modules/ffmpeg-static/bin/win${/*}",
        "!node_modules/ffmpeg-static/bin/linux${/*}",
        "!node_modules/ffprobe-static/bin/win${/*}",
        "!node_modules/ffprobe-static/bin/linux${/*}"
      ]
    },
```

To make use of use of `${os}` and `${arch}` var provided by electron-builder, we modified the ff github package

* renames `win32` to `win`. win32 is how the `os` module detects it, but for the folder structure to be inferable programmaticly by electron-builder files settings, we need to change the name.
* Similarly for os x, change folder to `mac` rather then `darwin`.

Then in `index.js` we adjust the output of `os` module to meet electron-builder needs

```javascript
if(platform == "darwin"){
    platform = "mac";
}else if(platform == "win32"){
    platform = "win";
}
```

and change rest of code accordingly.

Unrelated, but also added `browser` in list of platform, because when config, that requries ff path is loaded, if it is detected in browser mode. TODO: test not requirins config.js in browserify, removing this `!==browser` and see what happens.

