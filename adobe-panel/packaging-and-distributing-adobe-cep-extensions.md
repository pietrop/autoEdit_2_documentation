# Packaging and distributing Adobe CEP Extensions 🚧

## build the app in one folder

```bash
npm run adobe-panel-build
```

Packages all the parts needed for the extension to work in the `./adobe-panel-build` This directory is added to `.gitignore` to avoid merge conflicts.

## Download the ZXPSignCmd terminal utility 



> This SDK provides the low-level tools that you need to build extensions. Extensions that you build using these tools must be packaged as ZXP files in order to be seen and loaded by Extension Manager. You can offer extensions as free or paid products through our marketing portals \(Adobe Exchange, the Add-ins website, the Creative Cloud desktop app\). When you do this, you upload the extension to Adobe as a single ZXP file.
>
> Resources you will need include:
>
> * CEP JavaScript libraries for communicating with the operating system and Extension Manager and for communicating with the host application and other extensions.
> * Sample code for how to use these libraries
> * The ZXP packager, a command-line utility

_From_ [_Adobe docs_ ](https://github.com/Adobe-CEP/CEP-Resources/blob/master/README.md)\_\_

download the binary for `ZXPSignCmd`from the[ Adobe CEP Resources github repo](https://github.com/Adobe-CEP/CEP-Resources) see bewlo for direct. Downlaod as dmg and then move the binary where most suited in the project.

{% embed data="{\"url\":\"https://github.com/Adobe-CEP/CEP-Resources/blob/master/ZXPSignCMD/4.0.7/osx10/ZXPSignCmd.dmg\",\"type\":\"link\",\"title\":\"Adobe-CEP/CEP-Resources\",\"description\":\"CEP-Resources - Tools and documentation for building Creative Cloud app extensions with CEP\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars2.githubusercontent.com/u/7475984?s=400&v=4\",\"width\":396,\"height\":396,\"aspectRatio\":1}}" %}

## Creating a self signing certificate certificate

> So: fire the Terminal \(or the Win Command line\), get to the directory where you’ve moved the ZXPSignCmd file \(if you don’t know how to do this, just type “cd ” – mind you there’s a space – in the terminal and drag and drop the folder, then hit Enter\) and create a certificate using this pattern:

from 

```bash
ZXPSignCmd -selfSignedCert <countryCode> <stateOrProvince> <organization> <commonName> <password> <outputPath.p12>
```

dummy example for clarity 

```javascript
`./ZXPSignCmd -selfSignedCert IT BO DBCompany "Davide Barranca" OcaMorta selfDB.p12`
```

This command generate a certificate file `selfDB.p12`on your system, this certificate can be used in the next step to package the app.

## Package and sign the extension

Packaging and signing the extension happens in one step

> Let’s assume the extension you’ve made has the ID `com.example.helloworld` and it’s contained within a directory named accordingly.
>
> Gather together the Extension with the ZXPSignCmd and the selfDB.p12 in one folder, then build the ZXP using this pattern

from 

{% embed data="{\"url\":\"http://www.davidebarranca.com/2014/05/html-panels-tips-10-packaging-zxp-installers/\",\"type\":\"link\",\"title\":\"HTML Panels Tips: \#10 Packaging / ZXP Installers \| Photoshop, etc.\",\"description\":\"How to build customized ZXP installers for CC HTML Extensions \(standard, flash-compatible, hybrid\) using ZXPSignCmd, ucf.jar and MXI files.\",\"icon\":{\"type\":\"icon\",\"url\":\"http://www.davidebarranca.com/wp-content/uploads/2013/01/144.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"http://www.davidebarranca.com/wp-content/uploads/2014/05/mxi.png\",\"width\":150,\"height\":150,\"aspectRatio\":1}}" %}

eg in our case eg `com.autoedit2.it` as indicated in the adobe CEP manifest xml file

```javascript
ZXPSignCmd -sign <inputDirectory> <outputZxp> <p12> <p12Password> -tsa <timestampURL>
```

code example with dummy 

```javascript
./ZXPSignCmd -sign com.example.helloworld com.example.helloworld.zxp selfDB.p12 OcaMorta -tsa http://timestamp.digicert.com/
```

> If everything’s OK you should find a newly created `com.example.helloworld.zxp` file. That’s your self signed, timestamped installer; submit it to the Add Ons website and/or privately and enjoy.

from 

{% embed data="{\"url\":\"http://www.davidebarranca.com/2014/05/html-panels-tips-10-packaging-zxp-installers/\",\"type\":\"link\",\"title\":\"HTML Panels Tips: \#10 Packaging / ZXP Installers \| Photoshop, etc.\",\"description\":\"How to build customized ZXP installers for CC HTML Extensions \(standard, flash-compatible, hybrid\) using ZXPSignCmd, ucf.jar and MXI files.\",\"icon\":{\"type\":\"icon\",\"url\":\"http://www.davidebarranca.com/wp-content/uploads/2013/01/144.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"http://www.davidebarranca.com/wp-content/uploads/2014/05/mxi.png\",\"width\":150,\"height\":150,\"aspectRatio\":1}}" %}

## Submit to adobe 

Once you have a packaged and sign a Adobe CEP extension you can upload it to the Adobe Exchange marketplace.

Submit to[ **adobe exchange program**](https://partners.adobe.com/exchangeprogram/creativecloud/appslist.html)**,** click **create listing**.



## Other links

* [CEP Guide Part 7: Packaging and Distribution](http://aphall.com/2014/09/cep-5-distribution-en/), with bash script example to automate step.
* [HTML Panels Tips: \#10 Packaging / ZXP Installers](http://www.davidebarranca.com/2014/05/html-panels-tips-10-packaging-zxp-installers/)
* [Packaging and signing, more details in adobe's docs  ](http://wwwimages.adobe.com/www.adobe.com/content/dam/acom/en/devnet/creativesuite/pdfs/SigningTechNote_CC.pdf)
* There is also an npm tool [create-zxp](https://www.npmjs.com/package/create-zxp), but have not tried it.
  * If using the npm tool it also signs the extension so can skip next step about signing and go straight to upload to marketplace 
* [Extension Manager command-line basics](https://helpx.adobe.com/extension-manager/using/command-line.html)
* From ****Adobe-CEP/Samples: [**6. Package and deploy your panel**](https://github.com/Adobe-CEP/Samples/tree/master/PProPanel#6-package-and-deploy-your-panel)\*\*\*\*



{% embed data="{\"url\":\"https://partners.adobe.com/exchangeprogram/creativecloud.html\",\"type\":\"link\",\"title\":\"Exchange Program\",\"icon\":{\"type\":\"icon\",\"url\":\"https://partners.adobe.com/content/dam/adobeexchange/favicon.ico\",\"aspectRatio\":0}}" %}

{% embed data="{\"url\":\"https://helpx.adobe.com/extension-manager/using/packaging-submitting-extensions.html\",\"type\":\"link\",\"title\":\"Submitting extensions\",\"icon\":{\"type\":\"icon\",\"url\":\"https://helpx.adobe.com/include/img/favicon.ico\",\"aspectRatio\":0}}" %}

{% embed data="{\"url\":\"https://www.adobe.com/cy\_en/products/extendscript-toolkit.html\",\"type\":\"link\",\"title\":\"JavaScript development toolkit \| Download Adobe ExtendScript Toolkit CC\",\"description\":\"Download Adobe ExtendScript Toolkit CC to use directly with scriptable Adobe Creative Cloud desktop apps.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://wwwimages2.adobe.com/favicon.ico\",\"aspectRatio\":0}}" %}

