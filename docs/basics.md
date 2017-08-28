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
  - [Dump and Import](#dump-and-import)
  - [Render](#render)

- [Architecture](#architecture)

- [Traversing](#accessing-data)
  - How to access tracks, measures, beats and notes?
  - Getter rules

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

__Type__ *string|array*

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

Accessing data is made by getter/setter methods.

Starting from one point, you can find your way with the [Music-Object-Model reference](phptabs.html#top).

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/basics.md{% endcapture %}
{% include edit-doc-link.html %}
