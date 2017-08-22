---
layout: default
permalink: phptabs.html
title: Music Object Model Overview
excerpt: How to traverse Music Object Model
---

# Music Object Model Overview

PhpTabs makes a song fully-traversable.

It builds a music-tree which is called the __Music-Object-Model__ (MOM).

## MOM

__Song__ (= A PhpTabs instance)

- []__Channel__
  - []ChannelParameter

  [... channels]

- []__MeasureHeader__
  - _Song_ [parent]
  - Tempo
  - TimeSignature

  [... measureHeaders ]

- []__Track__
  - _Song_ [parent]
  - Color
  - Lyric
  - []__Measure__
    - _Track_ [parent]
    - Marker
    - MeasureHeader
    - TimeSignature
    - []__Beat__
      - _Measure_ [parent]
      - Stroke
      - Chord
      - Text
      - []__Voice__
        - _Beat_ [parent]
        - Duration
        - []__Note__
          - _Voice_ [parent]
          - NoteEffect
            - EffectBend
            - EffectGrace
            - EffectHarmonic
            - EffectTremoloBar
            - EffectTremoloPicking
            - EffectTrill
        
        [... notes ]
      
      [... voices ]

    [... beats ]

  [... measures ]

  - []TabString

[... tracks ]

## Traversing the tree is made simple

In this example, we read the fret value and string number, for the first
 note of the first track.

```php

$song = new PhpTabs('mytab.gp4');

// We read a note
$note = $song
  ->getTrack(0)     # Track 0
  ->getMeasure(0)   # Measure 0
  ->getBeat(0)      # Beat 0
  ->getVoice(0)     # Voice 0
  ->getNote(0);     # Note 0


// Print fret and string numbers
echo sprintf(
  "Note: %s/%d",
  $note->getValue(),
  $note->getString()
);

```

Below, we make the same thing, for all tracks.

```php

$tab = new PhpTabs('mytab.gp4');

foreach ($tab->getTracks() as $track) {

  // We read a note
  $note = $track
    ->getMeasure(0)   # Measure 0
    ->getBeat(0)      # Beat 0
    ->getVoice(0)     # Voice 0
    ->getNote(0);     # Note 0

  // Print track, fret and string numbers
  echo sprintf(
    "\nTrack %d - Note: %s/%d ",
    $track->getNumber(),
    $note->getValue(),
    $note->getString()
  );
}

```

It will ouput something like:

```
Track 1 - Note: 13/2 
Track 2 - Note: 5/2
```

Now, we read all the beats for the first measure of all tracks.

```php

$tab = new PhpTabs('mytab.gp4');

foreach ($tab->getTracks() as $track) {

  foreach ($track->getMeasure(0)->getBeats() as $idxBeat => $beat) {

    // We read a note
    $note = $beat
      ->getVoice(0)     # Voice 0
      ->getNote(0);     # Note 0

    // Print Track, Beat, fret and string numbers
    echo sprintf(
      "\nTrack %d - Beat %d - Note: %s/%d ",
      $track->getNumber(),
      $idxBeat,
      null !== $note ? $note->getValue() : '-',
      null !== $note ? $note->getString(): '-'
    );
  }
}

```

Outputs:

```
Track 1 - Beat 0 - Note: -/0 
Track 1 - Beat 1 - Note: -/0 
Track 1 - Beat 2 - Note: 11/3 
Track 1 - Beat 3 - Note: 0/2 
Track 2 - Beat 0 - Note: 5/2 
Track 2 - Beat 1 - Note: 5/2 
Track 2 - Beat 2 - Note: 5/2 
Track 2 - Beat 3 - Note: 5/2 
Track 2 - Beat 4 - Note: 5/2 
Track 2 - Beat 5 - Note: 5/2
```

Note the first two beats, they must be rest beats.

A short but useful view of the MOM is :

- PhpTabs
  - Track
    - Measure
      - Beat
        - Voice
          - Note

You can traverse it this way:

```php
$tab
  ->getTrack(0)
  ->getMeasure(0)
  ->getBeat(0)
  ->getVoice(0)
  ->getNote(0);
```

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
