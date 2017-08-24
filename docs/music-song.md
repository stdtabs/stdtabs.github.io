---
layout: default
permalink: music-song.html
title: MOM/Song documentation
excerpt: API Music\Song usage
---

# API: Music / Song

Song has a special role. It's the root node of PhpTabs.

You can access its methods by 2 ways:

```php

$tab = new PhpTabs('mytabs.gp4');

// Directly
$tab->method();

// Getting the Song object
$tab->getSong()->method();

```

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
	- [getTrack()](#gettrack-index)
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
	- [addTrack()](#addtrack)
	- [moveTrack()](#movetrack)
	- [removeTrack()](#removetrack)
	- [addChannel()](#addchannel)
	- [moveChannel()](#movechannel)
	- [removeChannel()](#removechannel)
	- [addMeasureHeader()](#addmeasureheader)
	- [removeMeasureHeader()](#removemeasureheader)

- [Updating properties](#updating-properties)
	- [setName()](#setname)
	- [setAlbum()](#setalbum)
	- [setAuthor()](#setauthor)
	- [setArtist()](#setartist)
	- [setDate()](#setdate)
	- [setCopyright()](#setcopyright)
	- [setWriter()](#setwriter)
	- [setTranscriber()](#settranscriber)
	- [setComments()](#setcomments)
	- [clear()](#clear)
	- [copyFrom()](#copyfrom)

- [Examples](#examples)

------------------------------------------------------------------------

## Parent container

Song object has no parent container.

------------------------------------------------------------------------

## Accessing child nodes

### countMeasureHeaders()

This method returns the number of measures contained by each track.


#### Type

integer

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

### addMeasureHeader()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### removeMeasureHeader()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getMeasureHeaders()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### addTrack()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### moveTrack()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### removeTrack()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getTrack()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getTracks()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### addChannel()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### moveChannel()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### removeChannel()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getChannel($index)

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getChannelById($channelId)

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getChannels()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## Accessing properties

------------------------------------------------------------------------


### getName()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setName()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getAlbum()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setAlbum()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getAuthor()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setAuthor()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getArtist()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setArtist()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getDate()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setDate()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getCopyright()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setCopyright()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getWriter()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setWriter()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getTranscriber()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setTranscriber()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getComments()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setComments()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### countChannels()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### countTracks()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------


### clear()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### isEmpty()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### copyFrom()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------


## Updating children

------------------------------------------------------------------------

## Updating properties

------------------------------------------------------------------------

## Examples

_None_

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/music-song.md{% endcapture %}
{% include edit-doc-link.html %}
