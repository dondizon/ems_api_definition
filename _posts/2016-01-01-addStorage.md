---
layout: post
title: addStorage
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: addstorage
---

Adds a new storage location.

This function has the following parameters:

|    Parameter Name     | Mandatory | Default Value | Description                              |
| :-------------------: | :-------: | :-----------: | ---------------------------------------- |
|      mediaFolder      |   true    |    *null*     | The path to the media folder             |
|      description      |   false   |    *null*     | Description given to this storage. Used to better identify the storage |
|   clientSideBuffer    |   false   |      15       | How much data should be maintained on the client side when a file is played from this storage |
|      enableStats      |   false   |     false     | If true, \*.stats files are going to be generated once the media files are used |
| externalSeekGenerator |   false   |     false     | If true, \*.seek and \*.meta files are going to be generated by another external tool |
|     keyframeSeek      |   false   |     false     | If true, the seek/meta files are going to be generated having only keyframe seek points |
|      metaFolder       |   false   |   *(null)*    | Path to the folder which is going to contain all the seek\\/meta files. If missing, the seek/meta files are going to be generated inside the media folder |
|         name          |   false   |    *null*     | Name given to this storage. Used to better identify the storage |
|    seekGranularity    |   false   |     1000      | Sets the granularity for the seek files  |
|  maxPlaylistFileSize  |           |               |                                          |

------

**Example:**

**API Call:**

``` 
addStorage mediaFolder=C:\EvoStream\media1 description=TestStorage enableStats=1 externalSeekGenerator=1 keyframeSeek=1 metaFolder=C:\EvoStream\media1 name=TestNameStorage seekGranularity=300000
```

**JSON Response:**

``` 
{
"data":{
    "clientSideBuffer":15,
    "description":"TestStorage",
    "enableStats":true,
    "externalSeekGenerator":true,
    "keyframeSeek":true,
    "maxPlaylistFileSize":4096,
    "mediaFolder":"C:\\EvoStream\\media1\\",
    "metaFolder":"C:\\EvoStream\\media1\\",
    "name":"TestNameStorage",
    "seek Granularity":300000
},
"description":"Storage created",
"status":"SUCCESS"
```

------

The JSON response contains the following details:

- data – The data to parse
  - clientSideBuffer – How much data should be maintained on the client side when a file is played from this storage
  - description – Description given to this storage. Used to better identify the storage
  - enableStats – If true, \*.stats files are going to be generated once the media files are used
  - externalSeekGenerator – If true, \*.seek and \*.meta files are going to be generated by another external tool
  - keyframeSeek – If true, the seek/meta files are going to be generated having only keyframe seek points
  - maxPlaylistFileSize - ??
  - mediaFolder – The path to the media folder
  - metaFolder – Path to the folder which is going to contain all the seek/meta files. If missing, the seek/meta files are going to be generated inside the media folder
  - name – Name given to this storage. Used to better identify the storage
  - seekGranularity – Sets the granularity for the seek files in milliseconds
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
