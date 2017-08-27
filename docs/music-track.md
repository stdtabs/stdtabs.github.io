---
layout: default
permalink: music-track.html
title: MOM/Track documentation
excerpt: API Music\Track usage
---

# API: Music / Track

## Table of contents

- [Parent container](#parent-container)
- [Accessing child nodes](#accessing-child-nodes)
	- [countMeasures()](#countmeasures)
	- [getMeasure()](#getmeasure)
	- [getMeasures()](#getmeasures)
	- [countStrings()](#countstrings)
	- [getString()](#getstring)
	- [getStrings()](#getstrings)

- [Accessing properties](#accessing-properties)
	- [getSong()](#getsong)
	- [getNumber()](#getnumber)
	- [getColor()](#getcolor)
	- [getName()](#getname)
	- [getOffset()](#getoffset)
	- [setOffset()](#setoffset)
	- [isSolo()](#issolo)
	- [isMute()](#ismute)
	- [getChannelId()](#getchannelid)
	- [getLyrics()](#getlyrics)
  
- [Updating children](#updating-children)
	- [addMeasure()](#addmeasure)
	- [removeMeasure()](#removemeasure)
	- [addString()](#addstring)
	- [setStrings()](#setstrings)

- [Updating properties](#updating-properties)
	- [setSong()](#setsong)
	- [setNumber()](#setnumber)
	- [setColor()](#setcolor)
	- [setName()](#setname)
	- [setSolo()](#setsolo)
	- [setMute()](#setmute)
	- [setChannelId()](#setchannelid)
	- [setLyrics()](#setlyrics)
	- [clear()](#clear)
	- [copyFrom()](#copyfrom)

- [Examples](#examples)

------------------------------------------------------------------------

## Parent container

A Track is contained by a [Song](music-song.html).

------------------------------------------------------------------------

## Accessing child nodes

### countMeasures()

This method returns the number of measures contained by the track.

#### Type

integer

#### Example

```php

$tab = new PhpTabs('mytabs.gp4');

$track = $tab->getTrack(0);

// Count the number of measures
echo $track->countMeasures();

// Will print a number between 0 and n-1

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getNumber()

This method returns the number identifier of the track.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setNumber()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getMeasures()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### addMeasure()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getMeasure()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### removeMeasure()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getStrings()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### addString()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setStrings()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getColor()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setColor()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

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

### getOffset()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setOffset()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### isSolo()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setSolo()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### isMute()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setMute()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getChannelId()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setChannelId()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getLyrics()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setLyrics()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getString()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### countStrings()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### getSong()

This method returns.

#### Parameters

_None_

#### Type

integer

#### Values


#### Example


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### setSong()

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


------------------------------------------------------------------------

## Accessing properties

------------------------------------------------------------------------

## Updating children

------------------------------------------------------------------------

## Updating properties

------------------------------------------------------------------------

## Examples

_None_

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/music-track.md{% endcapture %}
{% include edit-doc-link.html %}
