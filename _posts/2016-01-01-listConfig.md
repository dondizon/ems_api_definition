---
layout: post
title: listConfig
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: listconfig
---

Returns a list with all push/pull configurations.

Whenever the pullStream or pushStream interfaces are called, a record containing the details of the pull or push is created in the pullpushconfig.xml file. Then, the next time the EMS is started, the pullpushconfig.xml file is read, and the EMS attempts to reconnect all of the previous pulled or pushed streams.

This function has no parameters.

------

**Example:**

**API Call:**

``` 
listConfig
```

**JSON Response:**

``` 
{
"data":{
    "dash":[details of dash streams ],
    "hds":[details of hds streams ],
    "hls":[details of hls streams],
    "mss":[details of mss streams],
    "process":[ details of on process streams],
    "pull":[ details of pulled streams],
    "push":[details of pushed streams],
    "record":[details of recorded streams],
    "webrtc":[details of webRTC streams ]
    },
"description":"Run-time configuration",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details about the pull/push configuration:

- data – The data to parse
  - hds (see fields of **`createHDSStream`** command)
  - hls (see fields of **`createHLSStream`** command)
  - mss (see fields of **`createMSSStream`** command)
  - dash (see fields of **`createDASHStream`** command)
  - pull (see fields of **`pullStream`** command)
  - push (see fields of **`pushStream`** command)
  - record (see fields of **`record`** command)
    - status (within the stream types shown above) – array of current and previous states


- current/previous
  - code – An integer representing the state of the stream.
  - description – Describes the state of the stream.
  - timestamp – The time (in Unix secs) the state was updated.


- description – Describes the result of parsing/executing the command.
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not