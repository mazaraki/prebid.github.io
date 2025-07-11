---
layout: page_v2
title: Intersection Module
display_name: Intersection

description: Real Time Intersection
page_type: module
module_type: rtd
module_code : intersectionRtdProvider
enable_download : true
sidebarType : 1
---

# Intersection Module
{:.no_toc}

* TOC
{:toc}

## Overview

The Intersection module provides intersection for ad slots on the page using
[Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API).

Implementation works like this:

1. Build the Intersection module into the Prebid.js package with:

    ```bash

    gulp build --modules=intersectionRtdProvider&...
    ```

2. Use `setConfig` to instruct the browser to obtain the intersection data

## Configuration

This module is configured as part of the `realTimeData.dataProviders` object:

```javascript

pbjs.setConfig({
    "realTimeData": {
        auctionDelay: 100,
        dataProviders:[{          
            "name": "intersection",
            "waitForIt": true
        }]
    }
});

```

The optional `waitForIt` flag instructs the module to delay the auction until intersection data is collected for all ad units or the `auctionDelay` timeout is reached. It defaults to `false`.

## Output

For each bidder, the module adds intersection in a JSON format.
Example:

```javascript

{
  "intersection":{
    'boundingClientRect': {
      'left': 10,
      'top': 10,
      'right': 310,
      'bottom': 260,
      'width': 300,
      'height': 250,
      'x': 10,
      'y': 10,
    },
    'intersectionRect': {/* ... */},
    'rootRect': {/* ... */},
    'intersectionRatio': 0.5,
    'isIntersecting': false,
    'time': 1636993868145
  }
}
```
