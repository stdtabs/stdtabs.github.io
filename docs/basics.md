---
layout: default
permalink: basics.html
title: Basics
excerpt: All documentation for basic PhpTabs features.
---

# PhpTabs basics

## Table of contents

- [Features](#features)
  - [Read from a file](#read-from-a-file)
  - [Save to a file](#save-to-a-file)
  - [Convert](#convert)
  - [Dump and Import](#dump-and-import-data)
  - [Render](#render)

- [Architecture](#architecture)

- [Traversing](#traversing)
  - [Getter/setter/counter rules](#gettersettercounter-rules)
  - [Traversing, a naive example](#traversing-a-naive-example)
  - Traversing, real world example

------------------------------------------------------------------------

## Features

PhpTabs basics are the read, write, convert, dump, import and render operations.

This document describes the best way to use these tools.

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### Read from a file

Files are binary resources such Guitar Pro or MIDI files.

A read operation involves reading and parsing the entire file.

All elements are represented in the [internal data model](phptabs.html#top).

A read operation is automatically made when instanciating a PhpTabs object.

#### Example

```php

// A read operation is made
$tab = new PhpTabs('mytabs.gp4');

```

After a read operation, the instance is containing the entire [song](music-song.html#top).

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### Save to a file

A PhpTabs instance is containing all data.

It's possible to save this data to the disk or to the buffer with the `save()` method.

#### Example

```php

// Instanciating
$tab = new PhpTabs('mytabs.gp4');

// Saving to the buffer with the default format
echo $tab->save();

// Saving to the disk
$tab->save('new_filename_for_mytabs.gp4');

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### Convert

When saving data, an implicit conversion is made if needed.

#### Example

```php

// Instanciating
$tab = new PhpTabs('mytabs.gp4');

// Converts and save with gp5 format
echo $tab->save('mytabs.gp5');

```

Printing data to the buffer with another format is possible with an __explicit conversion__.

#### Example

```php

// Instanciate a gp4 file
$tab = new PhpTabs('mytabs.gp4');

// Explicit conversion and print with gp5 format
echo $tab->convert('gp5');

```

#### Note

Available file formats are .gp3, .gp4, .gp5, .mid and .midi.


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### Dump and import data

Dump operation are made to put all internal data to a machine readable format (XML, JSON, YML, PHP array).

It's useful to transport data and make some debug, some caching, etc...

After data has been dumped, it's possible to import it with import methods.

#### dump($format)

__Type__ *string\|array*

__Parameter__ *string* $format 

Dumps are made to visualize the internal music-tree or to communicate 
with a third-party application.

Following formats are allowed:

| Parameter        | Type      | Description                  |
|:-----------------|:----------|:-----------------------------|
| array            | *array*   | a raw PHP array              |
| xml              | *string*  | an XML string                |
| json             | *string*  | a JSON string                |
| var_export       | *string*  | a raw PHP array as string    |
| serialize        | *string*  | a PHP serialized             |
| text             | *string*  | a non standardized text      |
| txt              | *string*  | same as text                 |
| yaml             | *string*  | a YAML representation        |
| yml              | *string*  | same as yaml                 |

```php

$tab = new PhpTabs('mytabs.gp4');

// Get as a PHP array
$data = $tab->dump();
$data = $tab->dump('array');

// Get as an XML string
echo $tab->dump('xml');

// Get as a JSON string
echo $tab->dump('json');

// Get as a YAML string
echo $tab->dump('yml');
echo $tab->dump('yaml');

// Dump content into a file as XML
file_put_contents(
  'tab.xml',
  $tab->dump('xml')
);

```

#### Import

_Not yet implemented_ 

Planned for 0.6.0

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### Render

_Not yet implemented_ 

Planned for 0.5.0 (testable in the master branch)

Render is made in 2 steps:

1. __Get a specific renderer with `getRenderer($type)`__
  
    Following renderer types are allowed:

    | Parameter      | Type      | Description             |
    |:---------------|:----------|:------------------------|
    | vextab         | *string*  | A vextab string         |

2. __Render as string with `render()` method__

#### Example

First, create a renderer instance.
Then, render all tracks.

```php

$tab = new PhpTabs('mytabs.gp4');

// Get a vextab renderer
$renderer = $tab->getRenderer('vextab');

// Render all tracks one-by-one
for ($i = 0; $i < $tab->countTracks(); $i++) {

  echo $renderer->render($i);

}

```

It's easy to make the same thing with one line.

```php

$tab = new PhpTabs('mytabs.gp4');

// Render all tracks one-by-one
for ($i = 0; $i < $tab->countTracks(); $i++) {

  echo $tab
    ->getRenderer('vextab')
    ->render($i);

}

```

[See another example of the VexTab renderer](render-as-vextab.html#top)


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## Architecture

### Component schema

{% include_relative basics/architecture-schema.html %}                             

### Component roles

- __Reader__ imports data from files to the internal model,
- __Writer__  exports data to a binary file,
- __Renderer__ exports data to a human-readable representation,
- __Dumper__ exports data to machine compliant formats,
- __Importer__ imports data from internal dumps

With the internal model, you can easily convert files from one type to another.

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## Traversing

Starting from one point, you can find your way with the [Music-Object-Model reference](phptabs.html#top).

Traversing data is made by getter/setter/counter methods.

A traversal is done in read-write mode

### Getter/setter/counter rules

There are 4 rules for getter names:

1. __get + {objectName} + ()__

	It's a __property getter__ method.
  ie: there can be only one Tempo per MeasureHeader, 
	so the method name to get the tempo for a given measure is [$header->getTempo()](music-measureheader.html#gettempo).

2. __count + {objectName} + s()__

	It's a __child nodes counter__ method.
  ie: there can be several measures per Track,
  so the method name to count them is [$track->countMeasures()](music-track.html#countmeasures).
  
3. __get + {objectName} + s()__

	It's a __child-nodes getter__ method, it returns an array with all child-nodes. 
  ie: there can be several measures per Track,
  so the method name to get them is [$track->getMeasures()](music-track.html#getmeasures).

4. __get + {objectName} + ($index)__

	It's a child-node getter by index, it returns one child resource.
  `$index` is starting from 0 to n-1, with n=child count (returned by the counter method)
  ie: there can be several measures per Track,
  so the method name to get one measure(the first) is [$track->getMeasure(0)](music-track.html#getmeasureindex).

When in doubt, reference should be made to the [Music-Object-Model reference](phptabs.html#top).

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

### Traversing, a naive example

In the following example, all notes will be printed.

```php

$tab = new PhpTabs('mytab.gp4');

# Get all tracks
foreach ($tab->getTracks() as $track)
  # Get all measures
  foreach ($track->getMeasures() as $measure)
    # Get all beats
    foreach ($measure->getBeats() as $beat)
      # Get all voices
      foreach ($beat->getVoices() as $voice)
        # Get all notes
        foreach ($voice->getNotes() as $note)
          
          printNote($note);


/**
 * Print all referential
 *
 * @param \PhpTabs\Music\Note $note
 */
function printNote($note)
{
  echo sprintf(
    "\nTrack %d - Measure %d - Beat %d - Voice %d - Note %s/%s",
    $note->getVoice()->getBeat()->getMeasure()->getTrack()->getNumber(),
    $note->getVoice()->getBeat()->getMeasure()->getNumber(),
    $note->getVoice()->getBeat()->getStart(),
    $note->getVoice()->getIndex(),
    $note->getValue(),
    $note->getString()
  );
}

```

will output something like

```
Track 1 - Measure 1 - Beat 6240 - Voice 0 - Note 11/3
Track 1 - Measure 1 - Beat 6480 - Voice 0 - Note 0/2

[...]

Track 2 - Measure 1 - Beat 960 - Voice 0 - Note 5/2
Track 2 - Measure 1 - Beat 1920 - Voice 0 - Note 5/2
Track 2 - Measure 1 - Beat 2880 - Voice 0 - Note 5/2
Track 2 - Measure 1 - Beat 3840 - Voice 0 - Note 5/2

[...]

```


All referential can be accessed starting from a note.

This example does not take into account some aspects of the referential
 such as rest beats, durations, dead notes, note effects and chord beats.

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/basics.md{% endcapture %}
{% include edit-doc-link.html %}
