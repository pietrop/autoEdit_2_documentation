# IBM Watson json specs

* [API reference](https://www.ibm.com/watson/developercloud/speech-to-text/api/v1/)
* [IBM API reference](https://www.ibm.com/watson/developercloud/speech-to-text/api/v1/#recognize_sessionless_nonmp12)
* [IBM speech to text in documentation](https://www.ibm.com/watson/developercloud/doc/speech-to-text/output.html)

```javascript
{
  "results": [
    {
      "alternatives": [
        {
          "word_confidence": [
            [
              "good",
              0.52266540965618
            ],
            [
              "sign",
              0.89689802653416
            ],
            [
              "that's",
              0.33068099683986
            ],
            [
              "a",
              0.50049249829394
            ],
            [
              "really",
              0.92257759174313
            ],
            [
              "big",
              0.3309017279039
            ],
            [
              "deal",
              0.060633448667329
            ],
            [
              "Lenormand",
              0.27524941044761
            ],
            [
              "door",
              0.55675870253254
            ],
            [
              "is",
              0.99999999999996
            ],
            [
              "one",
              0.99999999999995
            ],
            [
              "with",
              0.82833913604084
            ],
            [
              "a",
              0.54441580608657
            ],
            [
              "design",
              0.95057876073007
            ],
            [
              "told",
              0.43942960858989
            ]
          ],
          "confidence": 0.621,
          "transcript": "good sign that's a really big deal Lenormand door is one with a design told ",
          "timestamps": [
            [
              "good",
              0.13,
              0.33
            ],
            [
              "sign",
              0.33,
              0.68
            ],
            [
              "that's",
              0.68,
              0.95
            ],
            [
              "a",
              0.95,
              1
            ],
            [
              "really",
              1,
              1.49
            ],
            [
              "big",
              1.52,
              1.81
            ],
            [
              "deal",
              1.81,
              2.12
            ],
            [
              "Lenormand",
              2.59,
              3.07
            ],
            [
              "door",
              3.07,
              3.32
            ],
            [
              "is",
              3.32,
              3.5
            ],
            [
              "one",
              3.5,
              3.75
            ],
            [
              "with",
              3.75,
              3.9
            ],
            [
              "a",
              3.9,
              3.93
            ],
            [
              "design",
              3.93,
              4.41
            ],
            [
              "told",
              4.41,
              4.68
            ]
          ]
        }
      ],
      "final": true
    }
  ],
  "result_index": 0
}
```

see also [example in api reference](https://www.ibm.com/watson/developercloud/speech-to-text/api/v1/#recognize_sessionless_nonmp12) under response.

