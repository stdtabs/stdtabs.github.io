---
layout: default
permalink: api-model-overview.html
---

# Model Overview

PhpTabs makes a full song traversable.

It builds a music-tree which is called the __Music-Object-Model__ (MOM)

To have a complete visualization of the MOM, the dump method can be used.

_Before traversing the tree, let's instanciate our tab._

```php
$song = new PhpTabs('mytab.gp4');
```



## First level tree

- song:
  - name
  - artist
  - album
  - author
  - copyright
  - writer
  - comments
  - channels[]:
    - channel:
    
    [...]
  - measureHeaders[]:
    - header:
    
    [...]
  
  - tracks[]:
    - track:

    [...]


------------------------------------------------------------------------

## Traversing the first level

A Song object contains:

- meta data (Name, artist, etc...)
- channels
- measure headers
- tracks

Channel, MeasureHeader and Track can be accessed with following methods:

------------------------------------------------------------------------

### Traversing Channels

#### `getChannels()`, `getChannel()` and `getChannelById()` methods

In this example, we print the channel names.

```php

// Working with all channels
foreach ($song->getChannels as $channel) {
  echo $channel->getName() . PHP_EOL;
}

// Accessing by index
echo $song->getChannel(0)->getName() . PHP_EOL;
// Outputs something like "Clean Guitar 1"

// Accessing by id
echo $song->getChannelById(1)->getName() . PHP_EOL;
// Outputs something like "Clean Guitar 1"

```

------------------------------------------------------------------------

### Traversing MeasureHeaders

#### `getMeasureHeaders()` and `getMeasureHeader()` methods

In this example, we print the tempo for each measure.

```php

// Working with all measure headers
foreach ($song->getMeasureHeaders() as $header) {
  echo $header->getTempo()->getValue() . PHP_EOL;
}

// Accessing by index to the first header
echo $song->getMeasureHeader(0)->getTempo()->getValue() . PHP_EOL;
// Outputs something like "90"

```

------------------------------------------------------------------------

### Traversing Tracks

#### `getTracks()` and `getTrack()` methods

In this example, we print the number of measures by track.

```php

// Working with all tracks
foreach ($song->getTracks() as $track) {
  echo $track->countMeasures() . PHP_EOL;
}

// Accessing by index to the first track
echo $song->getTrack(0)->countMeasures() . PHP_EOL;
// Outputs something like "4" (small tab!)

```

------------------------------------------------------------------------
