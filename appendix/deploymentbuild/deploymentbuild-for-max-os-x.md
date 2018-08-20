# Deployment/build for Max OS X

From terminal from root of app, run the deployment script

```text
npm install
```

Then

```bash
npm run build:mac:dmg
```

It creates a `cache` and a `build` folder. `cache` is a folder used by deploy to keep the latest version needed to build and package the app, to avoid having to re-download it every time. While the packaged app ready for use can be found in the `build` folder.

This also packages the app as a `dmg` for distribution on os x.

Which uses [`appdmg`](https://www.npmjs.com/package/appdmg) to put the app from the build folder inside a `dmg` and save it on the `~/Desktop`.

Preferences for `appdmg` script are in `/appdmg.json`.

