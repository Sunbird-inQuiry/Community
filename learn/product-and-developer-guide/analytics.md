# Analytics

### Telemetry Events for QuML Player

Following is the list of telemetry events that are used to analyze the question sets to generate reports of the assessments and to calculate the attempts.

#### **START**

This will initialize the Player with content and user details

```json
{
  "eid": "START",
  "ets": 1647849981050,
  "ver": "3.0",
  "mid": "START:23dd18d1b3cb4f4f9649c4bed4da8c5c",
  "actor": {
    "id": "561c348e631fd225b46a5571cbd42ad1",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "preprod.diksha.portal",
      "ver": "3.3.0",
      "pid": "sunbird-portal.contentplayer"
    },
    "env": "contentplayer",
    "sid": "913b3c6c-2874-26dd-ed0c-c23ddc00b718",
    "did": "561c348e631fd225b46a5571cbd42ad1",
    "cdata": [
      {
        "id": "c0c9384a82a75f219468d363e1891963",
        "type": "ContentSession"
      },
      {
        "id": "a12f45a1d7078901adb27b48be4b428d",
        "type": "PlaySession"
      },
      {
        "id": "8XJCqu3HxZchf039369fHiGtAHFXvCch",
        "type": "ContentSession"
      },
      {
        "id": "dqYZxK1hUunrgJ9GcRKCHq1S2wc8GSnl",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      },
      {
        "id": "do_21348431528472576011",
        "type": "SectionId"
      }
    ],
    "uid": ""
  },
  "object": {
    "id": "do_213484313936035840138",
    "type": "Content"
  },
  "tags": [],
  "edata": {
    "type": "content",
    "mode": "play",
    "pageid": "",
    "duration": 0.01
  }
}
```

#### **INTERACT**

This method is used to capture user interactions on a page. For example, the next button click, option select, or keyboard actions such as enter key, move and resize

```json
{
  "eid": "INTERACT",
  "ets": 1647886019289,
  "ver": "3.0",
  "mid": "INTERACT:4dfa680648714137401a1104512d4526",
  "actor": {
    "id": "561c348e631fd225b46a5571cbd42ad1",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "preprod.diksha.portal",
      "ver": "3.3.0",
      "pid": "sunbird-portal.contentplayer"
    },
    "env": "contentplayer",
    "sid": "913b3c6c-2874-26dd-ed0c-c23ddc00b718",
    "did": "561c348e631fd225b46a5571cbd42ad1",
    "cdata": [
      {
        "id": "c0c9384a82a75f219468d363e1891963",
        "type": "ContentSession"
      },
      {
        "id": "a12f45a1d7078901adb27b48be4b428d",
        "type": "PlaySession"
      },
      {
        "id": "0A4fMmfb7WYZzAzYMTnc5kT5sqFM0XEk",
        "type": "ContentSession"
      },
      {
        "id": "MNNxc334B8GRey3tAXi8TAIYQwHxYU5K",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      },
      {
        "id": "do_21348431528472576011",
        "type": "SectionId"
      }
    ],
    "uid": ""
  },
  "object": {
    "id": "do_213484313936035840138",
    "type": "Content",
    "ver": ""
  },
  "tags": [],
  "edata": {
    "type": "TOUCH",
    "subtype": "",
    "id": "option_clicked",
    "pageid": "1"
  }
}
```

****

#### **IMPRESSION**

This method is used to capture telemetry for user visits to a specific page. In the case of QuML it gets generated when the user changes the question by clicking on the next or previous button, when a user visits the end page, or when a user visits the scoreboard.

```json
{
  "eid": "IMPRESSION",
  "ets": 1647886137586,
  "ver": "3.0",
  "mid": "IMPRESSION:653c50e4887b8db4bb397e0e4aaed242",
  "actor": {
    "id": "561c348e631fd225b46a5571cbd42ad1",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "preprod.diksha.portal",
      "ver": "3.3.0",
      "pid": "sunbird-portal.contentplayer"
    },
    "env": "contentplayer",
    "sid": "913b3c6c-2874-26dd-ed0c-c23ddc00b718",
    "did": "561c348e631fd225b46a5571cbd42ad1",
    "cdata": [
      {
        "id": "c0c9384a82a75f219468d363e1891963",
        "type": "ContentSession"
      },
      {
        "id": "a12f45a1d7078901adb27b48be4b428d",
        "type": "PlaySession"
      },
      {
        "id": "0A4fMmfb7WYZzAzYMTnc5kT5sqFM0XEk",
        "type": "ContentSession"
      },
      {
        "id": "MNNxc334B8GRey3tAXi8TAIYQwHxYU5K",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      },
      {
        "id": "do_21348431528472576011",
        "type": "SectionId"
      }
    ],
    "uid": ""
  },
  "object": {
    "id": "do_213484313936035840138",
    "type": "Content",
    "ver": ""
  },
  "tags": [],
  "edata": {
    "type": "workflow",
    "subtype": "",
    "pageid": "2",
    "uri": ""
  }
}
```

#### **ERROR**

This method is used to capture the errors with stacktrace, for example when content fails to load when the internet is not available, or when corrupted ECAR opened.

```json
{
  "eid": "ERROR",
  "ets": 1647886200908,
  "ver": "3.0",
  "mid": "ERROR:93bce8052268b09ab9e41024d371de8a",
  "actor": {
    "id": "561c348e631fd225b46a5571cbd42ad1",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "preprod.diksha.portal",
      "ver": "3.3.0",
      "pid": "sunbird-portal.contentplayer"
    },
    "env": "contentplayer",
    "sid": "913b3c6c-2874-26dd-ed0c-c23ddc00b718",
    "did": "561c348e631fd225b46a5571cbd42ad1",
    "cdata": [
      {
        "id": "c0c9384a82a75f219468d363e1891963",
        "type": "ContentSession"
      },
      {
        "id": "a12f45a1d7078901adb27b48be4b428d",
        "type": "PlaySession"
      },
      {
        "id": "j7qS353smUdovr8o9OrmMfOTKDycZobW",
        "type": "ContentSession"
      },
      {
        "id": "lcThEjeBDEGuQsDAus7jxgQXlWgZtdxo",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      },
      {
        "id": "do_21348431657166438417",
        "type": "SectionId"
      }
    ],
    "uid": ""
  },
  "object": {
    "id": "do_213484313936035840138",
    "type": "Content",
    "ver": ""
  },
  "tags": [],
  "edata": {
    "err": "LOAD",
    "errtype": "content",
    "stacktrace": "Error: content failed to load , No Internet Available"
  }
}
```

#### **ASSESS**

This method is used to capture user assessments that happen while playing content. Which includes the options with correct answer value and selected option. This event is used to calculate the score.

```json
{
  "eid": "ASSESS",
  "ets": 1647850263832,
  "ver": "3.0",
  "mid": "ASSESS:8e936a7fc0f51f75217d559b0b6eb308",
  "actor": {
    "id": "561c348e631fd225b46a5571cbd42ad1",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "preprod.diksha.portal",
      "ver": "3.3.0",
      "pid": "sunbird-portal.contentplayer"
    },
    "env": "contentplayer",
    "sid": "913b3c6c-2874-26dd-ed0c-c23ddc00b718",
    "did": "561c348e631fd225b46a5571cbd42ad1",
    "cdata": [
      {
        "id": "c0c9384a82a75f219468d363e1891963",
        "type": "ContentSession"
      },
      {
        "id": "a12f45a1d7078901adb27b48be4b428d",
        "type": "PlaySession"
      },
      {
        "id": "TWyTb82FPy9W79ayWaFhmitEfecaPUb9",
        "type": "ContentSession"
      },
      {
        "id": "Peu3ndqo4ILAFaJj1M2oIBvdyvzNXGp8",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      },
      {
        "id": "do_21348431528472576011",
        "type": "SectionId"
      }
    ],
    "rollup": {
      "l1": "string",
      "l2": "string",
      "l3": "string",
      "l4": "string"
    },
    "uid": ""
  },
  "object": {
    "id": "do_213484313936035840138",
    "type": "Content",
    "ver": "",
    "rollup": {
      "l1": "string",
      "l2": "string",
      "l3": "string",
      "l4": "string"
    }
  },
  "tags": [],
  "edata": {
    "item": {
      "id": "do_21348431640099225615",
      "title": "q2",
      "type": "mcq",
      "maxscore": 1,
      "params": [
        {
          "answer": true,
          "value": {
            "body": "<p>Jeff Bezos</p>",
            "value": 0
          }
        },
        {
          "answer": false,
          "value": {
            "body": "<p><span style=\"background-color:rgb(255,255,255);color:rgb(32,33,36);\">Bill Gates</span></p>",
            "value": 1
          }
        }
      ],
      "sectionId": "do_21348431528472576011"
    },
    "index": 2,
    "pass": "Yes",
    "score": 1,
    "resvalues": [
      {
        "label": "<p>Jeff Bezos</p>",
        "value": 0,
        "selected": true
      }
    ],
    "duration": 3
  }
}JSO
```

#### RESPONSE

This method is used to capture user responses. For example; response to a question.

```json
{
  "eid": "RESPONSE",
  "ets": 1647850364447,
  "ver": "3.0",
  "mid": "RESPONSE:369882d4d4db9a4eb972d1f0de61ca02",
  "actor": {
    "id": "561c348e631fd225b46a5571cbd42ad1",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "preprod.diksha.portal",
      "ver": "3.3.0",
      "pid": "sunbird-portal.contentplayer"
    },
    "env": "contentplayer",
    "sid": "913b3c6c-2874-26dd-ed0c-c23ddc00b718",
    "did": "561c348e631fd225b46a5571cbd42ad1",
    "cdata": [
      {
        "id": "c0c9384a82a75f219468d363e1891963",
        "type": "ContentSession"
      },
      {
        "id": "a12f45a1d7078901adb27b48be4b428d",
        "type": "PlaySession"
      },
      {
        "id": "TWyTb82FPy9W79ayWaFhmitEfecaPUb9",
        "type": "ContentSession"
      },
      {
        "id": "Peu3ndqo4ILAFaJj1M2oIBvdyvzNXGp8",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      },
      {
        "id": "do_21348431528472576011",
        "type": "SectionId"
      }
    ],
    "uid": ""
  },
  "object": {
    "id": "do_213484313936035840138",
    "type": "Content",
    "ver": ""
  },
  "tags": [],
  "edata": {
    "target": {
      "id": "do_21348431640099225615",
      "ver": "1.0",
      "type": "MCQ"
    },
    "type": "CHOOSE",
    "values": [
      {
        "option": {
          "label": "<p>Jeff Bezos</p>",
          "value": 0,
          "selected": true
        }
      }
    ]
  }
}
```

#### SUMMARY

This method is used to log telemetry summary events, which includes the progress of the question set, duration to complete the question set, and a number of questions answer correctly, wrongly, or skipped.&#x20;

```json
{
  "eid": "SUMMARY",
  "ets": 1647850446006,
  "ver": "3.0",
  "mid": "SUMMARY:1d26c7ed1b59a70c4b88b44ad29c0c3e",
  "actor": {
    "id": "561c348e631fd225b46a5571cbd42ad1",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "preprod.diksha.portal",
      "ver": "3.3.0",
      "pid": "sunbird-portal.contentplayer"
    },
    "env": "contentplayer",
    "sid": "913b3c6c-2874-26dd-ed0c-c23ddc00b718",
    "did": "561c348e631fd225b46a5571cbd42ad1",
    "cdata": [
      {
        "id": "c0c9384a82a75f219468d363e1891963",
        "type": "ContentSession"
      },
      {
        "id": "a12f45a1d7078901adb27b48be4b428d",
        "type": "PlaySession"
      },
      {
        "id": "OgOdqEX6q2n0dT48D76Qb5hqETsqnMAx",
        "type": "ContentSession"
      },
      {
        "id": "oSNXAvhqp0ydXlOfaJUEMVV7nAcxvN2h",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      },
      {
        "id": "do_21348431657166438417",
        "type": "SectionId"
      }
    ],
    "uid": ""
  },
  "object": {
    "id": "do_213484313936035840138",
    "type": "Content",
    "ver": ""
  },
  "tags": [],
  "edata": {
    "type": "content",
    "mode": "play",
    "starttime": 1647850442442,
    "endtime": 1647850446004,
    "timespent": 3.56,
    "pageviews": 4,
    "interactions": 2,
    "extra": [
      {
        "id": "progress",
        "value": "100"
      },
      {
        "id": "endpageseen",
        "value": "true"
      },
      {
        "id": "score",
        "value": "2"
      },
      {
        "id": "correct",
        "value": "2"
      },
      {
        "id": "incorrect",
        "value": "0"
      },
      {
        "id": "partial",
        "value": "0"
      },
      {
        "id": "skipped",
        "value": "2"
      }
    ]
  }
}

```

#### END

This method is used to capture closure after all the activities are completed which includes the summary object and duration to complete the question **** set

```json
{
  "eid": "END",
  "ets": 1647850446016,
  "ver": "3.0",
  "mid": "END:a6be05876355d991674433b627b57a0d",
  "actor": {
    "id": "561c348e631fd225b46a5571cbd42ad1",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "preprod.diksha.portal",
      "ver": "3.3.0",
      "pid": "sunbird-portal.contentplayer"
    },
    "env": "contentplayer",
    "sid": "913b3c6c-2874-26dd-ed0c-c23ddc00b718",
    "did": "561c348e631fd225b46a5571cbd42ad1",
    "cdata": [
      {
        "id": "c0c9384a82a75f219468d363e1891963",
        "type": "ContentSession"
      },
      {
        "id": "a12f45a1d7078901adb27b48be4b428d",
        "type": "PlaySession"
      },
      {
        "id": "OgOdqEX6q2n0dT48D76Qb5hqETsqnMAx",
        "type": "ContentSession"
      },
      {
        "id": "oSNXAvhqp0ydXlOfaJUEMVV7nAcxvN2h",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      },
      {
        "id": "do_21348431657166438417",
        "type": "SectionId"
      }
    ],
    "uid": ""
  },
  "object": {
    "id": "do_213484313936035840138",
    "type": "Content",
    "ver": ""
  },
  "tags": [],
  "edata": {
    "type": "content",
    "mode": "play",
    "pageid": "sunbird-player-Endpage",
    "summary": [
      {
        "progress": 100
      },
      {
        "totalNoofQuestions": 4
      },
      {
        "visitedQuestions": 4
      },
      {
        "endpageseen": true
      },
      {
        "score": 2
      }
    ],
    "duration": 464.966
  }
}
```
