# ProPresenter Websocket API Documentation

## Description
Based on [jeffmikels repository](https://github.com/jeffmikels/ProPresenter-API), I created (and went a bit further) on creating a documentation for the undocumented ProPresenter6 Websocket API. I am currently working on a generic Python API Client that I will be uploading soon, so it is easier to build apps based on it. These are not all the possible commands, but the ones that are used by the ProPresenter Remote app.
If anyone find any other new commands and want to collaborate, you are welcome to create Pull Requests.

## Index

* [Actions](#actions)
    * [authenticate](#authenticate)
    * [clockRequest](#clockRequest)
    * [messageRequest](#messageRequest)
    * [libraryRequest](#libraryRequest)
    * [playRequestAll](#playRequestAll)
    * [audioRequest](#audioRequest)
    * [audioCurrentSong](#audioCurrentSong)
    * [audioStartCue](#audioStartCue)
    * [audioPlayPause](#audioPlayPause)
    * [telestratorSettings](#telestratorSettings)
    * [presentationRequest](#presentationRequest)
    * [presentationTriggerIndex](#presentationTriggerIndex)
    * [presentationTriggerNext](#presentationTriggerNext)
    * [presentationTriggerPrevious](#presentationTriggerPrevious)
    * [presentationSlideIndex](#presentationSlideIndex)
    * [presentationCurrent](#presentationCurrent)
    * [clearAll](#clearAll)
    * [clearVideo](#clearVideo)
    * [clearAudio](#clearAudio)
    * [clearText](#clearText)
    * [clearProps](#clearProps)
    * [clearToLogo](#clearToLogo)
    * [clockUpdate](#clockUpdate)
    * [clockStart](#clockStart)
    * [clockStop](#clockStop)
    * [clockReset](#clockReset)
    * [clockStartAll](#clockStartAll)
    * [clockStopAll](#clockStopAll)
    * [clockResetAll](#clockResetAll)
    * [messageSend](#messageSend)
    * [stageDisplaySets](#stageDisplaySets)
    * [stageDisplaySendMessage](#stageDisplaySendMessage)
    * [stageDisplayHideMessage](#stageDisplayHideMessage)
    * [stageDisplaySetIndex](#stageDisplaySetIndex)
* [Sent from server](#sent-from-server)
    * [clockNameChanged](#clockNameChanged)
    * [clockStopAll](#clockStopAll)
    * [audioTriggered](#audioTriggered)

## Actions

### authenticate
#### Description
Authentication
#### Paremeters
* _protocol_: int (default: 600)
* _password_: string
#### Request
```
{
    "protocol": 600,
    "action": "authenticate",
    "password": "password"
}
```
#### Response
```
{
    "controller": 1,
    "authenticated": 1,
    "error": "",
    "action": "authenticate"
}
```

### clockRequest
#### Description
Returns clock information
#### Request
```
{
    "action": "clockRequest"
}
```
#### Response
```
{
    "action": "clockRequest",
    "clockInfo": [
        {
            "clockDuration": "0:00:00",
            "clockEndTime": "0:00:00",
            "clockIsPM": 0,
            "clockName": "Countdown 1",
            "clockOverrun": true,
            "clockState": true,
            "clockTime": "0:02:13",
            "clockType": 0
        },
        {
            "clockDuration": "7:00:00",
            "clockEndTime": "--:--:--",
            "clockIsPM": 1,
            "clockName": "Countdown 2",
            "clockOverrun": false,
            "clockState": false,
            "clockTime": "--:--:--",
            "clockType": 1
        },
        {
            "clockDuration": "0:00:00",
            "clockEndTime": "--:--:--",
            "clockIsPM": 0,
            "clockName": "Elapsed Time",
            "clockOverrun": false,
            "clockState": false,
            "clockTime": "--:--:--",
            "clockType": 2
        }
    ]
}
```

### messageRequest
#### Description
Returns messages information
#### Request
```
{
    "action": "messageRequest"
}
```
#### Response
```
{
   "action": "messageRequest",
   "messages": [
      {
         "messageComponents": [
            "${Message}"
         ],
         "messageTitle": "Message"
      },
      {
         "messageComponents": [
            "Session will start in:  ",
            "${Countdown 1: H:MM:SS}"
         ],
         "messageTitle": "Countdown"
      }
   ]
}
```

### libraryRequest
#### Description
Returns library information
#### Request
```
{
    "action": "libraryRequest"
}
```
#### Response
```
{
   "library": [
      "\/path\/to\/library\/Welcome To ProPresenter 6.pro6",
      "\/path\/to\/library\/Untitled.pro6"
   ],
   "action": "libraryRequest"
}
```

### playRequestAll
#### Description
Returns playlists information
#### Request
```
{
    "action": "playRequestAll"
}
```
#### Response
```
{
    "playlistAll": [
        {
            "playlistLocation": "0",
            "playlistType": "playlistTypePlaylist",
            "playlistName": "Default",
            "playlist": [
                {
                    "playlistItemName": "Untitled",
                    "playlistItemLocation": "0:0",
                    "playlistItemType": "playlistItemTypePresentation"
                }
            ]
        }
    ],
    "action": "playlistRequestAll"
}
```

### audioRequest
#### Description
Returns audio information
#### Request
```
{
    "action": "audioRequest"
}
```
#### Response
```
{
    "action": "audioRequest",
    "audioPlaylist": [
        {
            "playlistLocation": "0",
            "playlistType": "playlistTypePlaylist",
            "playlistName": "Default",
            "playlist": []
        }
    ]
}
```

### audioCurrentSong
#### Description
???
#### Request
```
{
    "action": "audioCurrentSong"
}
```
#### Response
No response

### audioStartCue
#### Description
Start playing audio
#### Parameters
* _audioChildPath_ (): ???
* _audioPath_ (int): ???
#### Request
```
{
    "audioChildPath": "0:0",
    "action": "audioStartCue",
    "audioPath":"0"
}
```
#### Response
```
{
    "action": "audioPlayPause",
    "audioPlayPause": "Play"
}
```

### audioPlayPause
#### Description
Play/Pause current audio
#### Parameters
#### Request
```
{
    "action": "audioPlayPause"
}
```
#### Response
No response

### telestratorSettings
#### Description
Returns telestrator settings
#### Request
```
{
    "action": "telestratorSettings"
}
```
#### Response
```
{
    "telestratorToolweight": 0.5,
    "telestratorToolcolor": "0.135296 1.000000 0.024919 0.750000",
    "telestratorOutputsize": "{1680, 1050}",
    "telestratorTooltype": 1,
    "action": "telestratorSettings"
}
```

### presentationRequest
#### Description
#### Parameters
* _presentationPath_: string
* _presentationName_: string
* _presentationSlideQuality_: int
#### Request
```
{
    "action": "presentationRequest",
    "presentationPath": "\/path\/to\/library\/Untitled.pro6",
    "presentationName": "\/path\/to\/library\/Untitled.pro6",
    "presentationSlideQuality": "400"
}
```
#### Response
No response

### presentationTriggerIndex
#### Description
Switch to slide with index _n_
#### Parameters
* _presentationPath_ (string): Path to presentation file
* _slideIndex_ (int): Index of the slide
Index of the slide
#### Request
```
{
    "action": "presentationTriggerIndex",
    "presentationPath": "\/path\/to\/library\/Untitled.pro6",
    "slideIndex": "1"
}
```
#### Response
```
{
    "action": "presentationTriggerIndex",
    "presentationPath": "Untitled.pro6",
    "slideIndex": 1
}
```

### presentationTriggerNext
#### Description
Go to next slide
#### Parameters
#### Request
```
{
    "action": "presentationTriggerNext"
}
```
#### Response


### presentationTriggerPrevious
#### Description
Go to previous slide
#### Parameters
#### Request
```
{
    "action": "presentationTriggerPrevious"
}
```
#### Response
```
{
    "slideIndex": 2,
    "action": "presentationTriggerIndex",
    "presentationPath": "Untitled.pro6"
}
```

### presentationSlideIndex
#### Description
#### Parameters
#### Request
```
{
    "action": "presentationSlideIndex"
}
```
#### Response
```
{
    "action": "presentationSlideIndex",
    "slideIndex": "1"
}
```

### presentationCurrent
#### Description
#### Parameters
* _presentationSlideQuality_ (int): Quality of the presentation to be shown in the app
#### Request
```
{
    "action": "presentationCurrent",
    "presentationSlideQuality": "400"
}
```
#### Response
```
{
    "action": "presentationCurrent",
    "presentation": {
        "presentationSlideGroups": [
            {
                "groupName": "Group",
                "groupColor": "0.2637968361377716 0.2637968361377716 0.2637968361377716 1",
                "groupSlides": [
                    {
                        "slideEnabled": true,
                        "slideNotes": "",
                        "slideAttachmentMask": 0,
                        "slideText": "Some text",
                        "slideImage": ". . .",
                        "slideIndex": "0",
                        "slideTransitionType": -1,
                        "slideLabel": "",
                        "slideColor": ""
                    },
                    {
                        "slideEnabled": true,
                        "slideNotes": "",
                        "slideAttachmentMask": 0,
                        "slideText": "Some other text",
                        "slideImage": ". . .",
                        "slideIndex": "0",
                        "slideTransitionType": -1,
                        "slideLabel": "",
                        "slideColor": ""
                    }
                ]
            }
        ],
        "presentationName": "Untitled",
        "presentationHasTimeline": 0,
        "presentationCurrentLocation": "\/path\/to\/library\/Untitled.pro6"
    }
}
```

### clearAll
#### Description
Clear all (background and slides)
#### Parameters
#### Request
```
{
    "action": "clearAll"
}
```
#### Response
```
{
    "action": "clearAll"
}
```

### clearVideo
#### Description
Clear background only
#### Parameters
#### Request
```
{
    "action": "clearVideo"
}
```
#### Response
No response

### clearAudio
#### Description
Clear audio
#### Parameters
#### Request
```
{
    "action": "clearAudio"
}
```
#### Response
```
{
    "action": "clearAudio"
}
```

### clearText
#### Description
Clear slide text only
#### Parameters
#### Request
```
{
    "action": "clearText"
}
```
#### Response
```
{
    "action": "clearText"
}
```

### clearProps
#### Description
Clear props
#### Parameters
#### Request
```
{
    "action": "clearProps"
}
```
#### Response
No response

### clearToLogo
#### Description
Clear all and go to logo
#### Parameters
#### Request
```
{
    "action": "clearToLogo"
}
```
#### Responses (2)
```
{
    "action": "clearAll"
}
{
    "action": "clearAudio"
}
```

### clockUpdate
#### Description
Updates the settings of the Stage Display clock
#### Parameters
* _clockTime_ (time): Time set
* _clockIsPm_ (int): 0 (AM) | 1 (PM) | 2 (24h)
* _clockOverrun_ (boolean): Countdown finishes on 00:00 or keeps running on negative time
* _clockName_ (string): Clock name
* _clockIndex_ (int): Index of the clock being updated. There are 3 clocks, so it may be: 0, 1 or 2.
* _clockType_ (int): 0 (Countdown timer) | 1 (Countdown to time) | 2 (Elapsed time)
* _clockElapsedtime_ (time): Elapsed time
#### Request
```
{
    "clockTime": "00:05:00",
    "action": "clockUpdate",
    "clockIsPM": "0",
    "clockOverrun": "true",
    "clockName": "Countdown 1",
    "clockIndex": "0",
    "clockType": "0",
    "clockElapsedTime": "0:00:00"
}
```
#### Response
No response

### clockStart
#### Description
Start clock with index _n_
#### Parameters
* _clockIndex_ (int): Index of Clock
#### Request
```
{
    "action": "clockStart",
    "clockIndex": "0"
}
```
#### Response
No response

### clockStop
#### Description
Stop clock with index _n_
#### Parameters
* _clockIndex_ (int): Index of Clock
#### Request
```
{
    "action": "clockStop",
    "clockIndex": "0"
}
```
#### Response
No response

### clockReset
#### Description
Reset clock with index _n_
#### Parameters
* _clockIndex_ (int): Index of Clock
#### Request
```
{
    "action": "clockReset",
    "clockIndex": "0"
}
```
#### Response
```
{
    "action": "clockResetIndex",
    "clockIndex": 0
}
```

### clockStartAll
#### Description
Start all clocks
#### Parameters
#### Request
```
{
    "action": "clockStartAll"
}
```
#### Response
```
{
    "clockInfo": [
        [1, true, "0:05:00"],
        [1, true, "--:--:--"],
        [1, true, "--:--:--"]
    ],
    "action": "clockStartStopAll"
}
```

### clockStopAll
#### Description
Stop all clocks
#### Parameters
#### Request
```
{
    "action": "clockStopAll"
}
```
#### Response
```
{
    "clockInfo": [
        [1, false, "0:03:30"],
        [1, false, "7:28:03"],
        [1, false, "0:01:30"]
    ],
    "action": "clockStartStopAll"
}
```

### clockResetAll
#### Description
Reset all clocks
#### Parameters
#### Request
```
{
    "action": "clockResetAll"
}
```
#### Response
```
{
    "action": "clockResetAll"
}
```

### messageSend
#### Description
Send message to front-message (???)
#### Parameters
* _messageValues_ (array): ???
* _messageIndex_ (int): ???
* _messageKeys_ (array): ???
#### Request
```
{
    "action": "messageSend",
    "messageValues": [""],
    "messageIndex": "1",
    "messageKeys": ["Countdown 1: H:MM:SS"]
}
```
#### Response
```
{
    "messageIndex": 1,
    "action": "messageSend"
}
```

### stageDisplaySets
#### Description
Request all Stage Display Sets available
#### Parameters
#### Request
```
{
    "action": "stageDisplaySets"
}
```
#### Response
```
{
    "action": "stageDisplaySets",
    "stageDisplayIndex": 1,
    "stageDisplaySets": ["Default","Clocks"]
}
```

### stageDisplaySendMessage
#### Description
Send message to Message panel on Stage Display
#### Parameters
* _stageDisplayMessage_ (string): Message
#### Request
```
{
    "action": "stageDisplaySendMessage",
    "stageDisplayMessage": "Hello"
}
```
#### Response
No response

### stageDisplayHideMessage
#### Description
Hide message from Message panel on Stage Display
#### Parameters
#### Request
```
{
    "action": "stageDisplayHideMessage"
}
```
#### Response
No response

### stageDisplaySetIndex
#### Description
Set another Stage Display as active with index _n_
#### Parameters
* _stageDisplayIndex_ (int): Index of StageDisplay Set
#### Request
```
{
    "action": "stageDisplaySetIndex",
    "stageDisplayIndex": "0"
}
```
#### Response
```
{
    "action": "stageDisplaySetIndex",
    "stageDisplayIndex": "0"
}
```

## Sent from server

### clockNameChanged
#### Description
Clock name was changed on ProPresenter
#### Parameters
#### Request
```
{
    "clockName": "Countdown 1",
    "clockIndex": 0,
    "clockInfo": [1, "Countdown 1"],
    "action": "clockNameChanged"
}
```

### clockStopAll
#### Description
#### Parameters
#### Request
```
{
    "action": "clockStopAll"
}
```

### audioTriggered
#### Description
#### Parameters
#### Request
```
{
    "audioArtist": "",
    "action": "audioTriggered",
    "audioName": "Dramatic Sound Effect"
}
```

### presentationTriggerIndex
#### Description
#### Parameters
#### Request
```
{
    "action": "presentationTriggerIndex",
    "slideIndex": 3,
    "presentationPath": "Untitled.pro6"
}
```
