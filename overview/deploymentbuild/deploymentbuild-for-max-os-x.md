# Deployment/build for Max OS X

From terminal from root of app, run the deployment script

```text
npm install
```

Then

```bash
npm run build:mac
```

It creates a `cache` and a `dist` folder. `cache` is a folder used by deploy to keep the latest version needed to build and package the app, to avoid having to re-download it every time. While the packaged app ready for use can be found in the `dist` folder.

The `build` folder contains info needed for the packaging, such as background image for the dmg and logos.

 This also packages the app as a `dmg` for distribution on os x.

Which uses [`appdmg`](https://www.npmjs.com/package/appdmg) to put the app from the build folder inside a `dmg` and save it on the `~/Desktop`.

Preferences for `appdmg` script are in `/appdmg.json`.

can also package the app without the `dmg`and `zip` file.

```bash
npm run pack:mac
```

