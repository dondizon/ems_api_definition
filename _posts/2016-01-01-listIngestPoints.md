---
layout: post
title: listIngestPoints
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: listingestpoints
---

Lists the currently available Ingest Points.

This function has no parameters.

------

**Example:**

**API Call:**

``` 
listIngestPoints
```

**JSON Response:**

``` 
{
"data":{
    "privateStreamName":"theIngestPoint",
    "publicStreamName":"useMeToViewStream"
},
"description":"Available ingest points",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - Listof pairs:
    - privateStreamName –The private stream name which was set
    - publicStreamName – The public stream name which was set
- description – Describes the result of parsing/executing the command


- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not