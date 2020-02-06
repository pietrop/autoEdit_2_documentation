---
description: Simple automated route
---

# Packaging and distributing Adobe CEP Extensions

{% hint style="info" %}
There is a more [in depth explanation of the steps involved here](packaging-signing-adobe-cep-panel-in-details.md).  
Otherwise if you just want to run the automated script continue on this page.
{% endhint %}

## Build, package and sign the app

### Addd a config file

Create a `.env` file in the root of the repository, here's an example

```text
ZXPSignCmd_PATH="./ccextensionsmac/ZXPSignCmd"
COUNTRY_CODE=US
STATE_OR_PROVINCE="New York"
ORGANIZATION=""
COMMON_NAME=""
CERTIFICATE_PASSWORD=""
CERTIFICATE_OUTPUT_PATH="./ccextensionsmac/certificate.p12"
INPUT_DIRECTORY="./adobe-panel-build"
OUTPUT_ZXP="./dist/com.autoedit2.it.zxp"
TIMESTAMPS_URL="http://timestamp.digicert.com/"
```

### Run script

The command below

```bash
npm run adobe-panel-package-sign-buil
```

It uses this script, `sign-and-package-adobe-panel.js`  to 

*  package all files and folders needed for Adobe CEP panel inside `./adobe-panel-build` folder  \(in `.gitignore`\)
* creates a self signed, time stamped, certificate `./ccextensionsmac/certificate.p12`  \(in `.gitignore`\)
*  pack and sign the extension, can find it in `./dist/com.autoedit2.it.zxp` \(in `.gitignore`\)

## Distribution 

See [submit to adobe section](submit-to-adobe.md) for how to distribute that way.

or some more instruction on how to install third party extensions

{% embed url="https://helpx.adobe.com/creative-cloud/kb/installingextensionsandaddons.html\#Install\_third\_party\_extensions" %}





