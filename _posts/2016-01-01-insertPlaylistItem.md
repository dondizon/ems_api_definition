---
layout: post
title: insertPlaylistItem
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: insertplaylistitem
---

Inserts a new item into an RTMP playlist. insertPlaylistItem may be called on playlists which are actively being played by one or more clients/players.

**IMPORTANT NOTES:** 

- This function does NOT modify the actual playlist file. Instead it modifies ONLY the in-memory copy of the file.
  
- The `sourceOffset` and duration parameters behave exactly as they do when creating Playlist Files. However, they are measured in **MILLISECONDS** as opposed to seconds.
  
  ​

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|    playlistName    |     true      |      *null*       | The name of the \*.lst file into which the stream will be inserted |
|  localStreamName   |     true      |      *null*       | The name of the live stream or file that needs to be inserted. If a file is specified, the path must be relative to any of the mediaStorage locations |
|    insertPoint     |     false     |       -1000       | The absolute time in milliseconds on the playlist timeline where the insertion will occur. Any negative value will be considered as “immediate”, meaning it will start playing the stream being inserted the very next frame |
|    sourceOffset    |     false     |       -2000       | Specifies the starting position, in milliseconds, of the source stream. This parameter can also be used to indicate whether the stream is live or recorded. **-2000** means that the EMS will look for a live stream with the `localStreamName` specified. If a live stream is not found, it will attempt to play a media file with the `localStreamName`. If a media file with that name and path cannot be found the EMS will wait for a live stream to become available.                                                                                                                   **-1000** implies that the `localStreamName` is explicitly a live stream. If no live stream is found, the EMS waits indefinitely if `duration` is set to -1. If `duration` is another value the EMS will wait duration seconds before moving to the next item in the playlist. **0 or a positive number** implies that the specified localStreamName is a media file. The EMS will start playback `sourceOffset` milliseconds from the beginning of the file. If no file is found the playlist item is skipped. **Any negative number other than -1000 or -2000** will be assumed to be -2000 |
|      duration      |     false     |       -1000       | The duration of the playback of the stream in milliseconds. **-1000** means that the EMS will play a live stream until it is no longer available or a media file until its end. **0** means that only a single frame of the stream will be played. **All positive numbers** will cause the EMS to play the stream for duration milliseconds or until the end of the media file or live stream, whichever comes first. **Any negative number** passed other than -1000 will be assumed to be -1000 |

------

**Example:**

**API Call:**

``` 
insertPlaylistItem playlistName=testInPlaylist localStreamName=testPullStream insertPoint=-1000 sourceOffset=0 duration=0
```

**JSON Response:**

``` 
{
"data":{
    "duration":0,
    "insertPoint":-1000,
    "localStreamName":"TestInPlaylist",
    "playlistName":"TestPlaylist",
    "sourceOffset":0
},
"description":"Playlist item inserted",
"status":"SUCCESS"
}
```

------

The JSON response for generateServerPlaylist contains the following details:

- data – The data to parse
  - duration – An array of durations for each stream/file in the list, expressed in seconds
  - insertPoint - The absolute time in milliseconds on the playlist timeline where the insertion will occur
  - localStreamName – The name of the live stream or file that needs to be inserted
  - playlistName - The name of the \*.lst file into which the stream will be inserted
  - sourceOffsets – An array of offsets for each stream/file in the list
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not