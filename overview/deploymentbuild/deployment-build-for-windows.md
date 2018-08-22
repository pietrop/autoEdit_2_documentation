# Deployment / Build for Windows

From terminal from root of app, run the deployment script

```text
npm install
```

Then

```bash
npm run build:win
```

It creates a `cache` and a `build` folder. `cache` is a folder used by deploy to keep the latest version needed to build and package the app, to avoid having to re-download it every time. While the packaged app ready for use can be found in the `build` folder.

It packages the app as a `.exe` file.

## Note

If you are deploying/building from a Mac OSX computer for a windows machine as your target you might run into a compatibility issue.

You'll need to follow [this tutorial](https://www.davidbaumgold.com/tutorials/wine-mac/) to get your mac setup with `wine` in order to be able to package the app for windows while on Mac.

Key steps are.

Install \`brew if you don't have it already, skip if you do.

```text
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Note: If Homebrew tells you that you need to agree to the Xcode license, you can do that by running:

```text
sudo xcodebuild -license
```

Install `xquartz`

```text
brew cask install xquartz
```

install `wine`

```text
brew install wine
```

You should then be able to run to package the app.

```bash
npm run build:win
```

### uninstalling `wine`

if you ever need to uninstal wine

```text
brew uninstall wine
```

