---
description: In more details
---

# Packaging signing Adobe CEP Panel in details

{% hint style="info" %}
[simplified automated steps see here](./)
{% endhint %}

## Build the app in one folder

if you only want to build the app without packaging as `zxp` or signing then use this command.

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

{% embed url="https://github.com/Adobe-CEP/CEP-Resources/blob/master/ZXPSignCMD/4.0.7/osx10/ZXPSignCmd.dmg" %}

## Creating a self signing certificate certificate

{% hint style="info" %}
You need to use the `ZXPSignCmd` to generate your self signed certificate. See below for how
{% endhint %}

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

{% embed url="http://www.davidebarranca.com/2014/05/html-panels-tips-10-packaging-zxp-installers/" %}

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

{% embed url="http://www.davidebarranca.com/2014/05/html-panels-tips-10-packaging-zxp-installers/" %}



## Other links

* [CEP Guide Part 7: Packaging and Distribution](http://aphall.com/2014/09/cep-5-distribution-en/), with bash script example to automate step.
* [HTML Panels Tips: \#10 Packaging / ZXP Installers](http://www.davidebarranca.com/2014/05/html-panels-tips-10-packaging-zxp-installers/)
* [Packaging and signing, more details in adobe's docs  ](http://wwwimages.adobe.com/www.adobe.com/content/dam/acom/en/devnet/creativesuite/pdfs/SigningTechNote_CC.pdf)
* There is also an npm tool [create-zxp](https://www.npmjs.com/package/create-zxp), but have not tried it.
  * If using the npm tool it also signs the extension so can skip next step about signing and go straight to upload to marketplace 
* [Extension Manager command-line basics](https://helpx.adobe.com/extension-manager/using/command-line.html)
* From ****Adobe-CEP/Samples: [**6. Package and deploy your panel**](https://github.com/Adobe-CEP/Samples/tree/master/PProPanel#6-package-and-deploy-your-panel)\*\*\*\*



{% embed url="https://partners.adobe.com/exchangeprogram/creativecloud.html" %}

{% embed url="https://helpx.adobe.com/extension-manager/using/packaging-submitting-extensions.html" %}

{% embed url="https://www.adobe.com/cy\_en/products/extendscript-toolkit.html" %}

{% embed url="https://www.adobe.com/cy\_en/products/extendscript-toolkit.html" %}

