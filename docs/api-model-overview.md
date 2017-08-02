---
layout: default
permalink: api-model-overview.html
---

# Model Overview

First thing we do with a tab is to browse a full song.

This page tries to give an overview of the music-tree. 

This tree is called the __Music-Object-Model__ (MOM)

To have a complete visualization of a tablature, dump method can be used.

Before traversing the tree, let's instanciate our tab.


{% highlight php %}}

$song = new PhpTabs('mytab.gp4');

{% endhighlight %}

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

In these example, we print the channel names.

{% highlight php %}

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

{% endhighlight %}

------------------------------------------------------------------------

### Traversing MeasureHeaders

#### `getMeasureHeaders()` and `getMeasureHeader()` methods

In these example, we print the tempo for each measure.

{% highlight php %}

// Working with all measure headers
foreach ($song->getMeasureHeaders() as $header) {
  echo $header->getTempo()->getValue() . PHP_EOL;
}

// Accessing by index to the first header
echo $song->getMeasureHeader(0)->getTempo()->getValue() . PHP_EOL;
// Outputs something like "90"

{% endhighlight %}

------------------------------------------------------------------------

### Traversing Tracks

#### `getTracks()` and `getTrack()` methods

In these example, we print the number of measures by track.

{% highlight php %}

// Working with all tracks
foreach ($song->getTracks() as $track) {
  echo $track->countMeasures() . PHP_EOL;
}

// Accessing by index to the first track
echo $song->getTrack(0)->countMeasures() . PHP_EOL;
// Outputs something like "4" (small tab!)

{% endhighlight %}

------------------------------------------------------------------------
