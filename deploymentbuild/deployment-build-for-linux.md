# Deployment / Build Linux

From terminal from root of app, run the deployment script

```
npm install
```

Then

```bash
npm run build:linux
```

It creates a `cache` and a `build` folder. `cache` is a folder used by deploy to keep the latest version needed to build and package the app, to avoid having to re-download it every time. While the packaged app ready for use can be found in the `build` folder.

It packages the app as a [`AppImages`](https://appimage.org)

>Download an application, make it executable, and run! No need to install. No system libraries or system preferences are altered.

>Distribute your desktop Linux application in the AppImage format and win users running all common Linux distributions. Package once and run everywhere. Reach users on all major desktop distributions.


[Fore more details on how to run in Linux after download this see below](https://askubuntu.com/questions/774490/what-is-an-appimage-how-do-i-install-it)

>AppImages can be downloaded and run without installation or the need for root rights.
>
>Making it executable
>You can make the appImage executable as follows:
>
>chmod a+x exampleName.AppImage
>Executing it
>You can execute an appImage as follows:
>
>./exampleName.AppImage
