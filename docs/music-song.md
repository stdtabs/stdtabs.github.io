---
layout: default
permalink: music-song.html
title: MOM/Song documentation
excerpt: API Music\Song usage
---

# API: Music / Song

## Table of contents

- [Parent container](#parent-container)
- [Accessing child nodes](#accessing-child-nodes)
	- [countMeasureHeaders()](#countmeasureheaders)
	- [getMeasureHeader()](#getmeasureheaderindex)
	- [getMeasureHeaders()](#getmeasureheaders)
	- [countChannels()](#countchannels)
	- [getChannel()](#getchannelindex)
	- [getChannelById()](#getchannelbyidchannelid)
	- [getChannels()](#getchannels)
	- [countTracks()](#counttracks)
	- [getTrack()](#gettrackindex)
	- [getTracks()](#gettracks)

- [Accessing properties](#accessing-properties)
	- [getName()](#getname)
	- [getAlbum()](#getalbum)
	- [getAuthor()](#getauthor)
	- [getArtist()](#getartist)
	- [getDate()](#getdate)
	- [getCopyright()](#getcopyright)
	- [getWriter()](#getwriter)
	- [getTranscriber()](#gettranscriber)
	- [getComments()](#getcomments)
	- [isEmpty()](#isempty)

- [Updating children](#updating-children)
	- [addTrack()](#addtracktrack)
	- [moveTrack()](#movetrackindex-track)
	- [removeTrack()](#removetracktrack)
	- [addChannel()](#addchannelchannel)
	- [moveChannel()](#movechannelindex-channel)
	- [removeChannel()](#removechannelchannel)
	- [addMeasureHeader()](#addmeasureheadermeasureheader)
	- [removeMeasureHeader()](#removemeasureheaderindex)

- [Updating properties](#updating-properties)
	- [setName()](#setnamename)
	- [setAlbum()](#setalbumalbum)
	- [setAuthor()](#setauthorauthor)
	- [setArtist()](#setartistartist)
	- [setDate()](#setdatedate)
	- [setCopyright()](#setcopyrightcopyright)
	- [setWriter()](#setwriterwriter)
	- [setTranscriber()](#settranscribertranscriber)
	- [setComments()](#setcommentscomments)
	- [clear()](#clear)
	- [copyFrom()](#copyfromsong)

------------------------------------------------------------------------

## Parent container

As the Song object is the root node of PhpTabs, it has no parent 
container.

You can access its methods by 2 ways:

```php

$tab = new PhpTabs('mytabs.gp4');

// Directly
$tab->method();

// Getting the Song object
$tab->getSong()->method();

```

------------------------------------------------------------------------

## Accessing child nodes

### countMeasureHeaders()

This method returns the number of measures contained by each track.

#### Type

_integer_

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Count the number of measures
echo $tab->countMeasureHeaders();

// Will print a number between 0 and n-1

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getMeasureHeader($index)

This method returns a [MeasureHeader](/music-measureheader.html) resource.

#### Parameters

- _integer_ $index 

#### Type

[\PhpTabs\Music\MeasureHeader](/music-measureheader.html)

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Get the fourth measure header
$header = $tab->getMeasureHeader(3);

if ($header !== null) {
	echo $header->getNumber();
} else {
	echo "header number 4 / index 3 is not defined';
}

```

If the measure header number 4 exists, $header is containing a
 [MeasureHeader](/music-measureheader.html). Otherwise, it's a null value.

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getMeasureHeaders()

This method returns an array of [MeasureHeader](/music-measureheader.html) resources.

These are all measure headers.

#### Type

\[\][\PhpTabs\Music\MeasureHeader](/music-measureheader.html)

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Get all measure headers
$headers = $tab->getMeasureHeaders();

// Print number and index for all measure headers 
foreach ($headers as $index => $header) {
	echo sprintf(
		"\nHeader number=%d, index=%d",
		$header->getNumber(),
		$index
	);
}

```

will ouput something like:

```

Header number=1, index=0
Header number=2, index=1
Header number=3, index=2
Header number=4, index=3

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### countChannels()

This method returns the number of channels contained by the [Song](/music-song.html) resource.

#### Type

integer

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Count channels
echo $tab->countChannels();

// Print something like 4 if there is four types of instruments

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getChannel($index)

This method returns a [Channel](/music-channel.html) resource.

#### Parameters

- _integer_ $index

#### Type

[\PhpTabs\Music\Channel](/music-channel.html)

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Get the second channel
$channel = $tab->getChannel(1);

if ($channel !== null) {
	echo $channel->getChannelId();
} else {
	echo "Channel at index 1 is not defined';
}

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getChannelById($channelId)

This method returns a [Channel](/music-channel.html) resource.

#### Parameters

- _integer_ $channelId

#### Type

[\PhpTabs\Music\Channel](/music-channel.html)

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Is there any channel using a Piano?
$channel = $tab->getChannelById(0);

if ($channel !== null) {
	echo "Yes";
} else {
	echo "No;
}

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getChannels()

This method returns an array of [Channel](/music-channel.html) resources.

These are all channels.

#### Type

\[\][\PhpTabs\Music\Channel](/music-channel.html)

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Get all channels
$channels = $tab->getChannels();

// Print channelId and volume for all channels
foreach ($channels as $index => $channel) {
	echo sprintf(
		"\nChannel index=%d, id=%d, volume=%d",
		$index,
		$channel->getChannelId(),
		$channel->getVolume()
	);
}

```

will ouput something like:

```

Channel index=0, id=28, volume=127
Channel index=1, id=0, volume=65

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### countTracks()

This method returns the number of tracks contained by the [Song](/music-song.html) resource.

#### Type

integer

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Count tracks
echo $tab->countTracks();

// Print something like 2 if there is 2 tracks

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getTrack($index)

This method returns a [Track](/music-track.html) resource.

#### Parameters

- _integer_ $index

#### Type

[\PhpTabs\Music\Track](/music-track.html)

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

// Is the first track using a Piano channel?
$track = $tab->getTrack(0);

if ($track->getChannelId() == 0) {
	echo "Yes";
} else {
	echo "No;
}

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getTracks()

This method returns an array of tracks contained by the [Song](/music-song.html) resource.

#### Type

\[\][\PhpTabs\Music\Track](/music-track.html)

#### Example

Let's print the channel id for all tracks

```php

$tab = new PhpTabs('mytabs.gp4');

foreach($tab->getTracks() as $track) {
	echo sprintf(
		"\nTrack %d, channel %d",
		$track->getNumber(),
		$track->getChannelId()
	);
}

```

will ouput something like:

```

Track 1, channel 28
Track 2, channel 0

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## Accessing properties

### getName()

This method returns the name of the song.

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getName();

// Will output "My song name"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getAlbum()

This method returns the album of the song.

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getAlbum();

// Will output "My song album name"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getAuthor()

This method returns the author of the song.

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getAuthor();

// Will output "Author name"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getArtist()

This method returns the artist of the song.

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getArtist();

// Will output "Artist name"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getDate()

This method returns the date of the song.

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getDate();

// Will output "12/12/2012"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getCopyright()

This method returns the copyright of the song.

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getCopyright();

// Will output a string which represents licensing conditions

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getWriter()

This method returns the writer of the song.

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getWriter();

// Will output "Writer name"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getTranscriber()

This method returns the transcriber of the song.

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getTranscriber();

// Will output "Transcriber name"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getComments()

This method returns comments (multiple lines).

#### Type

string

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

echo $tab->getComments();

// Will output "Comment line 1\nComment line 2"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### isEmpty()

This method returns true if the song has not any measure header or tracks.

Otherwise, it returns false.

#### Type

boolean

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

if ($tab->isEmpty()) {
  echo "Empty song";
} else {
  echo "Song has at least one measure header and one track";
}

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## Updating children

### addTrack($track)

This method adds a new [Track](/music-track.html) at the end of the stack.

#### Parameters

- [\PhpTabs\Music\Track](/music-track.html) $track

#### Example

```php

use PhpTabs\Music\TabString;
use PhpTabs\Music\Track;

$tab   = new PhpTabs('mytabs.gp4');

$track = new Track();

// Attach a song
$track->setSong($tab->getSong());
// Set at the end
$track->setNumber($tab->countTracks() + 1);
// Set a name
$track->setName('My track name');

// Prepare a one-string instrument
$string = new TabString();
$string->setNumber(1);
$string->setValue(34);
$track->addString($string);

// Add the new track
$tab->addTrack($track);

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### moveTrack($index, $track)

This method moves a [Track](/music-track.html) from its last position to the given index.

#### Parameters

- _integer_ $index
- [\PhpTabs\Music\Track](/music-track.html) $track

#### Example

In this example, the first track will be put at the last position.

```php

$tab   = new PhpTabs('mytabs.gp4');

$track = $tab->getTrack(0);
$index = $tab->countTracks() - 1;

$tab->moveTrack($index, $track);

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### removeTrack($track)

This method removes and _clears_ the given [Track](/music-track.html).

#### Parameters

- [\PhpTabs\Music\Track](/music-track.html) $track

#### Example

In this example, all tracks will be removed.

```php

$tab   = new PhpTabs('mytabs.gp4');

foreach ($tab->getTracks() as $track) {
  $tab->removeTrack($track);
}

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### addChannel($channel)

This method adds a new [Channel](/music-channel.html) at the end of the stack.

#### Parameters

- [\PhpTabs\Music\Channel](/music-channel.html) $channel

#### Example

In this example, a new channel will be added with default configuration.

```php

use Phptabs\Music\Channel;

$tab = new PhpTabs('mytabs.gp4');

$channel = new Channel();
$channel->setChannelId(
  $tab->countChannels() + 1
);

$tab->addChannel($channel);

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### moveChannel($index, $channel)

This method moves [Channel](/music-channel.html) to an index position.

#### Parameters

- _integer_ $index
- [\PhpTabs\Music\Channel](/music-channel.html) $channel

#### Example

In this example, the last channel will be moved to the first position.

```php

$tab = new PhpTabs('mytabs.gp4');

// Get the last defined channel
$channel = $tab->getChannel(
  $tab->countChannels() - 1
);

// Set at the first position
$tab->moveChannel(0, $channel);

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### removeChannel($channel)

This method removes a [Channel](/music-channel.html).

#### Parameters

- [\PhpTabs\Music\Channel](/music-channel.html) $channel

#### Example

In this example, the first channel will be removed.

```php

$tab = new PhpTabs('mytabs.gp4');

// Get a channel
$channel = $tab->getChannel(0);

// Remove it
$tab->removeChannel($channel);

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### addMeasureHeader($measureHeader)

This method adds a new measure header at the end of the stack.

#### Parameters

- [\PhpTabs\Music\MeasureHeader](/music-measureheader.html) $measureHeader

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$measureHeader = new MeasureHeader();
$measureHeader->setNumber(
  $tab->countMeasureHeaders()
);

// Add the new header
$tab->addMeasureHeader($measureHeader);

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### removeMeasureHeader($index)

This method removes a [MeasureHeader](/music-measureheader.html) at given index.

#### Parameters

- _int_ $index

#### Example

In this example, the first measure header will be removed.

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->removeMeasureHeader(0);

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## Updating properties

### setName($name)

This method sets the name attribute.

#### Parameters

- _string_ $name

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setName('My new song title');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setAlbum($album)

This method sets the album attribute.

#### Parameters

- _string_ $album

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setAlbum('My new album title');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setAuthor($author)

This method sets the author attribute.

#### Parameters

- _string_ $author

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setAuthor('My new author name');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setArtist($artist)

This method sets the artist attribute.

#### Parameters

- _string_ $artist

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setArtist('My new artist name');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setDate($date)

This method sets the date attribute.

#### Parameters

- _string_ $date

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setDate('12/12/2012');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setCopyright($copyright)

This method sets the copyright attribute.

#### Parameters

- _string_ $copyright

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setCopyright('License LGPL2.1+');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setWriter($writer)

This method sets the writer attribute.

#### Parameters

- _string_ $writer

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setWriter('Writer name');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setTranscriber($transcriber)

This method sets the transcriber attribute.

#### Parameters

- _string_ $transcriber

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setTranscriber('Transcriber name');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setComments($comments)

This method sets the comments attribute.

#### Parameters

- _string_ $comments

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->setComments('Comment line 1
Comment line 2
Etc...');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### clear()

This method clears all channels, measure headers and tracks.

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->clear();

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### copyFrom($song)

This method converts all data of a given song into internal data.

#### Parameters

- [\PhpTabs\Music\Song](/music-song.html) $song

#### Example

In this example, an empty song will replace actual data.

```php

$tab = new PhpTabs('mytabs.gp4');

$tab->copyFrom(new Song());

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/music-song.md{% endcapture %}
{% include edit-doc-link.html %}
