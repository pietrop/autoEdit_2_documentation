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

## Sign the extension 

Packaging and signing, more details in adobe's docs  [http://wwwimages.adobe.com/www.adobe.com/content/dam/acom/en/devnet/creativesuite/pdfs/SigningTechNote\_CC.pdf](http://wwwimages.adobe.com/www.adobe.com/content/dam/acom/en/devnet/creativesuite/pdfs/SigningTechNote_CC.pdf)

There's also a command line utility for signing. 

{% hint style="info" %}
But you need a certificate 
{% endhint %}

## Upload to exchange marketplace 

Once you have a packaged and sign a Adobe CEP extension you can upload it to the Adobe Exchange marketplace.

