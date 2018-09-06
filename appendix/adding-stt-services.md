# Adding STT services

Can use the Pr [Added support for AssemblyAI \#70](https://github.com/OpenNewsLabs/autoEdit_2/pull/70) as an example.

Generally adding a new STT service to autoEdit will entail: 

#### 1. Credentials part 1

1. Adding module to handle credentilas [electron/assemblyai\_keys.js](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-461f90f13050a27a2315277b2090433e)
2. add support for keys in db.js [electron/db.js](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-82b9f8ce52da2a672645e08248bf129d)
3. expose getters and setters in [electron/index.html](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-e038f54f0fe0c4453b5b5f93c4ee487f)

#### 2. credentials part 2

1. Pass data for settings view through the router [lib/app/router.js](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-59ad222f8ee232953bb031df0989874c)
2. add credentials field in settings template [settings\_template.html.ejs](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-cf6867d7a32733ed4c10d35620891ef2)
3. integrate with settings view [lib/app/views/settings\_view.js](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-75c925345257c9200d05aae742b3bb25) 

#### 3. Transcription form 

1. Add option in transcription form template [/transcription\_form\_template.html.ejs](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-e16b377f919aec1676289959229568e2)
   1. optional list of languages, if model supports multiple language models.
2. Integrate with transcription form view [lib/app/views/transcription\_form\_view.js](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-033f58af7e1a6d85bbe6d2dae9e1089f)

#### 4. Backend 

1. Add backend option for that stt service in transcriber module [lib/interactive\_transcription\_generator/transcriber/index.js](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-c90aa252ef7bc87ad573376b620c4c87)
2. The module to call the STT API and convert to json might more or less involved depending on the STT SDK provided by the STT service.
3. Then a module adapter to convert the STT API output into autoEdit Json [lib/interactive\_transcription\_generator/transcriber/assemblyai/convert\_to\_json.js](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-c404a2506a23b882467f8c331161f40a)
   1. sometimes to build the adapter, it's easier to get some sample json from the STT API Service, or from a sample response and use that to create the parser.  eg [lib/interactive\_transcription\_generator/transcriber/assemblyai/sample-assemblyai.json](https://github.com/OpenNewsLabs/autoEdit_2/pull/70/commits/05a72e95daf3278404641cd79065986323686405#diff-a9ee80506b1b4ccd121256b5f2e4c5e7)

A bit involved, but for now that's it, `npm start`, to test it out.

