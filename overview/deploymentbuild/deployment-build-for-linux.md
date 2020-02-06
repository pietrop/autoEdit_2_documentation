# Deployment / Build for Linux

From terminal from root of app, run the deployment script

```text
npm install
```

Then

```bash
npm run build:linux
```

It creates a `cache` and a `build` folder. `cache` is a folder used by deploy to keep the latest version needed to build and package the app, to avoid having to re-download it every time. While the packaged app ready for use can be found in the `build` folder.

It packages the app as a [`AppImages`](https://appimage.org) that works across linux distribution see deployment section and this [issue](https://github.com/OpenNewsLabs/autoEdit_2/issues/36) and corresponding [PR](https://github.com/OpenNewsLabs/autoEdit_2/pull/45) for more details.

{% embed data="{\"url\":\"https://github.com/OpenNewsLabs/autoEdit\_2/issues/36\",\"type\":\"link\",\"title\":\"Linux version · Issue \#36 · OpenNewsLabs/autoEdit\_2\",\"description\":\"Is there any reason not to publish a Linux version?\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars0.githubusercontent.com/u/2480569?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

{% embed data="{\"url\":\"https://github.com/OpenNewsLabs/autoEdit\_2/pull/45\",\"type\":\"link\",\"title\":\"AppImage by probonopd · Pull Request \#45 · OpenNewsLabs/autoEdit\_2\",\"description\":\"This PR, when merged, will compile this application on Travis CI upon each git push, and upload an AppImage to your GitHub Releases page. Providing an AppImage would have, among others, these advan...\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars0.githubusercontent.com/u/2480569?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

> Download an application, make it executable, and run! No need to install. No system libraries or system preferences are altered.
>
> Distribute your desktop Linux application in the AppImage format and win users running all common Linux distributions. Package once and run everywhere. Reach users on all major desktop distributions.

[Fore more details on how to run in Linux after download this see below](https://askubuntu.com/questions/774490/what-is-an-appimage-how-do-i-install-it)

> AppImages can be downloaded and run without installation or the need for root rights.
>
> Making it executable You can make the appImage executable as follows:
>
> chmod a+x exampleName.AppImage Executing it You can execute an appImage as follows:
>
> ./exampleName.AppImage

## What is an AppImage

AppImages can be downloaded and run without installation or the need for root rights.

### Making it executable

You can make the appImage executable as follows:

`chmod a+x` exampleName.AppImage

Or [see also how to make an AppImage executable for easier users instructions using GUI](https://discourse.appimage.org/t/how-to-make-an-appimage-executable/80)

### Executing it

You can execute an appImage as follows:

`./exampleName.AppImage`

### AppImage advantages

Providing an [AppImage](http://appimage.org/) would have, among others, these advantages:

* Applications packaged as an AppImage can run on many distributions \(including Ubuntu, Fedora, openSUSE, CentOS, elementaryOS, Linux Mint, and others\)
* One app = one file = super simple for users: just download one AppImage file, [make it executable](http://discourse.appimage.org/t/how-to-make-an-appimage-executable/80), and run
* No unpacking or installation necessary
* No root needed
* No system libraries changed
* Works out of the box, no installation of runtimes needed
* Optional desktop integration with `appimaged`
* Optional binary delta updates, e.g., for continuous builds \(only download the binary diff\) using AppImageUpdate
* Can optionally GPG2-sign your AppImages \(inside the file\)
* Works on Live ISOs
* Can use the same AppImages when dual-booting multiple distributions
* Can be listed in the [AppImageHub](https://appimage.github.io/apps) central directory of available AppImages
* Can double as a self-extracting compressed archive with the `--appimage-extract` parameter

[Here is an overview](https://appimage.github.io/apps) of projects that are already distributing upstream-provided, official AppImages.

If you have questions, AppImage developers are on \#AppImage on irc.freenode.net.

## 

