# Packaging and distributing Adobe CEP Extensions 🚧

## Package extension as a ZXP file 

Add quote 

> This SDK provides the low-level tools that you need to build extensions. Extensions that you build using these tools must be packaged as ZXP files in order to be seen and loaded by Extension Manager. You can offer extensions as free or paid products through our marketing portals \(Adobe Exchange, the Add-ins website, the Creative Cloud desktop app\). When you do this, you upload the extension to Adobe as a single ZXP file.
>
> Resources you will need include:
>
> * CEP JavaScript libraries for communicating with the operating system and Extension Manager and for communicating with the host application and other extensions.
> * Sample code for how to use these libraries
> * The ZXP packager, a command-line utility

_From Adobe docs_ [_https://github.com/Adobe-CEP/CEP-Resources/blob/master/README.md_](https://github.com/Adobe-CEP/CEP-Resources/blob/master/README.md)\_\_

There is also an npm tool [https://www.npmjs.com/package/create-zxp](https://www.npmjs.com/package/create-zxp)

If using the npm tool it also signs the extension so can skip next step about signing and go straight to upload to marketplace 

## Adobe Extension Manager



{% embed data="{\"url\":\"https://www.adobe.com/exchange/em\_download/\",\"type\":\"link\",\"title\":\"Adobe - Exchange : Download the Adobe Extension Manager\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.adobe.com/favicon.ico\",\"aspectRatio\":0}}" %}

## Getting a certificate

{% embed data="{\"url\":\"https://www.thesslstore.com/knowledgebase/code-signing-collecting-export/download-export-firefox/\",\"type\":\"link\",\"title\":\"How to Download or Export a Code Signing Certificate in Firefox - The SSL Store™\",\"description\":\"A complete step-by-step guide to downloading or exporting a Code Signing Certificate in Firefox.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.thesslstore.com/knowledgebase/wp-content/uploads/2017/02/cropped-favicon-192x192.png?x65967\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://www.thesslstore.com/knowledgebase/wp-content/uploads/2017/03/firefox-step2.png\",\"width\":309,\"height\":565,\"aspectRatio\":1.8284789644012944}}" %}

## Sign the extension 

{% hint style="info" %}
You need a certificate 
{% endhint %}

Packaging and signing, more details in adobe's docs  [http://wwwimages.adobe.com/www.adobe.com/content/dam/acom/en/devnet/creativesuite/pdfs/SigningTechNote\_CC.pdf](http://wwwimages.adobe.com/www.adobe.com/content/dam/acom/en/devnet/creativesuite/pdfs/SigningTechNote_CC.pdf)

There's also a command line utility for signing. 

## Upload to exchange marketplace 

Once you have a packaged and sign a Adobe CEP extension you can upload it to the Adobe Exchange marketplace.

