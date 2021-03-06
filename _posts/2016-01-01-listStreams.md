---
layout: post
title: listStreams
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: liststreams
---

Provides a detailed description of all active streams.

|   **Parameter Name**   | **Mandatory** | **Default Value** | **Description**                          |
| :--------------------: | :-----------: | :---------------: | ---------------------------------------- |
| disableInternalStreams |     false     |     *1 true*      | If this is 1 (true), internal streams (origin-edge related) are filtered out from the list |

------

**Example:**

**API Call:**

``` 
listStreams
```

**JSON Response:**

``` 
{
"data":[
{
    "appName":"evostreamms",
    "audio":{
        "bytesCount":727893,
        "codec":"AAAC",
        "codecNumeric":4702111241970122752,
        "droppedBytesCount":0,
        "droppedPacketsCount":0,
        "packetsCount":2243
        },
    "bandwidth":0,
    "connectionType":1,
    "creationTimestamp":14480 05740350.4519,
    "edgePid":0,
    "farIp":"54.239.131.224",
    "farPort":1935,
    "ip":"192.168. 2.35",
    "name":"testpullstream",
    "nearIp":"192.168.2.35",
    "nearPort":1607,
    "outStream sUniqueIds":null,
    "pageUrl":"",
    "port":1607,
    "processId":12848,
    "processType":"origi n",
    "pullSettings":{
      "_callback":null,
      "audioCodecBytes":"",
      "configId":1,
      "emulateUs erAgent":"EvoStream Media Server (www.evostream.com) player",
      "forceTcp":false,
      "httpProxy":"",
      "isAudio":true,
      "keepAlive":true,
      "localStreamName":"testpullstream",
      "operationType":1,
      "pageUrl":"",
      "ppsBytes":"",
      "rangeEnd":-1,
      "rangeStart":-2,
      "rtcp DetectionInterval":10,
      "sendRenewStream":false,
      "spsBytes":"",
      "ssmIp":"",
      "swfUrl":"",
      "tcUrl":"",
      "tos":256,
      "ttl":256,
      "uri":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\ /cfx\/st\/mp4:sintel.mp4"},
      "queryTimestamp":1448005784755.9919,
      "serverAgent":"FM S\/3,5,7,7009",
      "swfUrl":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:si ntel.mp4",
      "tcUrl":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.m p4",
      "type":"INR",
      "typeNumeric":5282249572905648128,
      "uniqueId":36,
      "upTime":44405.5400,
      "video":{
        "bytesCount":4881934,
        "codec":"VH264",
        "codecNumeric":62172744939670 07744,
        "droppedBytesCount":0,
        "droppedPacketsCount":0,
        "height":306,
        "level":30,
        "pac ketsCount":1255,
        "profile":66,
        "width":720
        }
}
],
"description":"Available streams",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details about each stream:

- data – The data to parse.
  
  - appName - ??
    
  - audio – stats about the audio portion of the stream
    
    - bytesCount – Total amount of audio data received
    - codec - ??
    - codecNumeric - ??
    - droppedBytesCount - The number of video bytes lost
    - droppedBytesCount – The number of audio bytes lost
    - droppedPacketsCount – The number of lost audio packets
    - packetsCount – Total number of audio packets received
    
  - bandwidth – The current bandwidth utilization of the stream
    
  - connectionType - ??
    
  - canDropFrames – *Outstreams only*. Flag set by client allowing for dropped frames/packets
    
  - creationTimestamp – The UNIX timestamp for when the stream was created. UNIX time is expressed as the number of seconds since the UNIX Epoch (Jan 1, 1970)
    
  - edgePid – Internal flag used for clustering
    
  - farIp - The IP address of the distant party
    
  - farPort - The port used by the distant party
    
  - ip - IP address of the source stream’s host
    
  - inStreamUniqueID – *For pushed streams.* The id of the source stream.
    
  - name – the “localstreamname” for this stream
    
  - nearIp - The IP address used by the local computer
    
  - nearPort - The port used by the local computer
    
  - outStreamsUniqueIDs – *For pulled streams.* An array of the “out” stream IDs associated with this “in” stream
    
  - pageUrl - A link to the page that originated the request (often unused)
    
  - port - The port bound to the service
    
  - processId - ??
    
  - processType - ??
    
  - pullSettings/pushSettings – *Not present for streams requested by a third party (IE player/client).* A copy of the parameters used in the **pullStream** or **pushStream** command
    
    - configId – The identifier for the pullPushConfig.xml entry
    - emulateUserAgent – The string that the EMS uses to identify itself with the other server. It can be modified so that EMS identifies itself as, say, a Flash Media Server
    - forceTcp – Whether TCP MUST be used, or if UDP can be used
    - httpProxy - May either be IP:Port combination or self
    - isAudio - Indicates if the currently pulled stream is an audio source
    - keepAlive – If true, the stream will try to reconnect if the connection is severed
    - localStreamName – Same as the above “name” field
    - operationType – The type of operation
    - pageUrl – A link to the page that originated the request (often unused)
    - ppsBytes - The video PPS bytes of this RTP stream if it is video
    - rangeEnd - The length in seconds for the playback
    - rangeStart - A value from which the playback should start expressed in seconds
    - rtcpDetectionInterval – Used for RTSP. This is the time period the EMS waits to determine if an RTCP connection is available for the RTSP/RTP stream. (RTSP is used for synchronization between audio and video)
    - sendRenewStream - If 1, the server will send RenewStream via SET\_PARAMETER when a new client connects
    - spsBytes - The video SPS bytes of this RTP stream if it is video
    - ssmIp - The source IP from source-specific-multicast
    - swfUrl – The location of the Flash Client that is generating the stream (if any)
    - tcUrl – An RTMP parameter that is essentially a copy of the URI
    - tos – Type of Service network flag
    - ttl – Time To Live network flag
    - uri – The parsed values of the source streams URI
    
  - queryTimestamp – The time (in UNIX seconds) when the information in this request was populated
    
  - serverAgent - ??
    
  - swfUrl - The location of the Flash Client that is generating the stream (if any)
    
  - tcUrl - An RTMP parameter that is essentially a copy of the URI
    
  - type – The type of stream this is. The first two characters are of most interest:
    
    - char 1 = I for inbound, O for outbound
      
    - char 2 = N for network, F for file
      
    - char 3+ = further details about stream
      
      example: INR = Inbound Network Stream (a stream coming from the network into the EMS)
    
  - typeNumeric - ??
    
  - uniqueId – The unique ID of the stream (integer)
    
  - uptime – The time in seconds that the stream has been alive/running for
    
  - video – Stats about the video portion of the stream
    
    - bytesCount – Total amount of video data received
    - codec - ??
    - codecNumeric - ??
    - droppedBytesCount – The number of video bytes lost
    - droppedPacketsCount – The number of lost video packets
    - height – The video stream’s pixel height
    - level - ??
    - packetsCount – Total number of video packets received
    - profile - ??
    - width - The video stream’s pixel width
  
- description – Describes the result of parsing/executing the command
  
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
