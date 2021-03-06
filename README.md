# Salesforce Marketing Cloud - Developer Tools (Google Chrome Extension)

## Introduction

### NOTE:

**This extension is neither an official porduct of Salesforce, nor in any way associated with Salesforce!** I'm just a software developer using Marketing Cloud on a daily basis and I'm sharing this extension I built for myself at start to help me with my daily work.

### Description

This is an extension of Google Chrome developer tools, that makes life easier for Salesforce Marketing Cloud users. Information that needs to be gathered by checking out all the network requests' responses or using workarounds like starting a wizard for a task you don't want to perform right now just to get the desired information isn't necessary anymore when using this extension.

However, this extension is currently being developed so the featureset will grow over time. If you have any questions, discovered bugs or just have an idea on how to improve this extension, feel free to raise an issue here on github.

## Features (v0.2.4)

### Gather Instance Information

If you open this extension and visit the Marketing Cloud Dashboard, basic information about the account and the currently logged in user is displayed. Furthermore the Marketing Cloud applications are shown along with the information if they are provisioned in this account and the current user is allowed to access them.

### Expose Publication List Ids

Adds the ids of your publication lists to the name column of the Publication List view in Email Studio. If you need the data for further programmatic use, an array of all publication lists including id, name and category is printed to the console. This is all as easy as clicking a button while being on the Publication Lists page in Email Studio. The console output looks like this:

`Publication Lists: [{"listId":1234,"categoryId":1234,"name":"Test"},{"listId":1235,"categoryId":1234,"name":"Test 2"}]`

### Expose Activity Keys

Adds the keys of your canvas activities in Journey Builder above the activity icon on the journey canvas (e.g. 3 days <i>(WAIT-1)</i>). In combination with the "Journey Details"-feature this helps with the programmatic analysis of goal attainment in specific paths of your journey (you can find a description of this feature below; further information is available on [my blog](https://markus.codes/2017/08/03/salesforce-marketing-cloud-developer-tools-journey-details-feature)).

### Display Data Extension Details

This feature helps displaying important information about your data extensions that isn't available without inspecting network requests or going to the details page of your data extension for example. Some of this can be useful if you need to develop custom entry events for example (e.g. an [event using transaction keys](https://github.com/mslabina/sfmc-customevent-with-transactionkey) to allow correct evaluation of multiple entries per subscriber). As soon as you navigate to the folder containing the data extensions you want to check, the data will be presented in the "Data Extension Details" tab.

### Display Journey Details

This feature helps displaying important information about a journey and it's versions in one combined view. Listed data includes Name, Id, CustomerKey, number of versions, information about the goal as well as goal attainment of each version. Additionally there is a breakdown into goal attainment at specific activities in the current journey version which is also available as JSON and therefore enables the user to easily reuse this information in external systems, programs and scripts. Furthermore an overview of all activities of the current version including id, key, type, name and the triggeredSendId for email activities is available in the interface as well as in JSON-format so it can be copy-pasted to an external system for further processing. As soon as you open the journey you want to check, the data will be presented in the "Journey Details" tab.

Example goal attainment JSON-output:

```json
{
  "totalMetGoal": 579,
  "activities": [
    {
      "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
      "metGoal": 123,
      "key": "WAIT-1"
    },
    {
      "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
      "metGoal": 456,
      "key": "WAIT-2"
    }
  ]
}
```

Example activity JSON-output:

```json
{
  "activities": [
    {
      "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
      "key": "WAIT-1",
      "type": "WAIT",
      "name": ""
    },
    {
      "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
      "key": "EMAILV2-1",
      "type": "EMAILV2",
      "name": "Example email",
      "triggeredSendId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
    }
  ]
}
```

### Expose Error Messages

Displays error messages, even the ones not shown in the user interface. Instead of having to fiddle around inspecting requests, the error-responses are displayed in a table in this extension. If the message is available in the actual response of the server, the error displyed in Salesforce Marketing Cloud (see figure 4) will be shown including the http-status, status-information and the given message (see figure 5). However, this only works if the error occured while having the devtools opened, so I highly recommended having this extension open everytime you are working with Salesforce Marketing Cloud.

## Project Links

 - [Project Website](https://markus.codes/sfmc-chrome-devtools)
 - [Extension in the Google Chrome Webstore](https://chrome.google.com/webstore/detail/salesforce-marketing-clou/bkmmmgaljahinmpijhdggabkdngpadbn?hl=en-US)

## Contributors

|Major Contributors | |
|:----|----:|
|Markus Slabina |[![mslabina on Twitter](https://raw.githubusercontent.com/ExactTarget/fuelux/gh-pages/invertobird-sm.png)](https://twitter.com/mslabina) [![mslabina on Github](https://raw.githubusercontent.com/ExactTarget/fuelux/gh-pages/invertocat-sm.png)](https://github.com/mslabina) |

## License (MIT)

__Copyright © 2017 [Markus Slabina](https://github.com/mslabina)__

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
