---
layout: default
excerpt: Read, write and render music scores, Guitar Pro tabs and MIDI files.
---

PhpTabs is a PHP library for reading, writing and rendering tabs and MIDI files.

It provides direct methods to [read a song name](music-song.html#getname), get a list of instruments or whatever be your needs.

Phptabs is built on the top of a [music stack](phptabs.html) that lets you create or modify your songs.

- [Features](#features)
- [Manual](#manual)
- [Supported formats](#supported-formats)
- [Requirements](#requirements)
- [Contribution and Support](#contribution-and-support)
- [License](#license)

------------------------------------------------------------------------

## Features

- [Read](basics.html#read-from-a-file), [convert](basics.html#convert) and [write](basics.html#save-to-a-file) GuitarPro/MIDI files
- Traverse and CRUD metadata and data
- [Export](basics.html#export-and-import-data) data to JSON, XML, YAML and other formats
- Web-rendering in [VexTab notation](render-as-vextab.html)

------------------------------------------------------------------------

## Manual

- [Getting started](/getting-started.html)

- [Basics](basics.html)
  - [Read a file](basics.html#read-from-a-file)
  - [Save to a file](basics.html#save-to-a-file)
  - [Export](basics.html#export-data)
  - [Import](basics.html#import-data)
  - [Render](basics.html#render)
  - [Architecture](basics.html#architecture)
  - [Traversing](basics.html#traversing)


- [Music-Object-Model overview](phptabs.html)
  - [Song](music-song.html)
    - [Track](music-track.html)

- Some use-cases examples:

  - Read and update song metadata (Name, author)

  - [Render a track as a VexTab string](render-as-vextab.html)

  - Read measures for a particular track

  - Read notes for a particular measure

  - Create a tab from scratch (An empty song)

------------------------------------------------------------------------

## Supported formats

PhpTabs currently supports the following file formats:

- GuitarPro 3 (.gp3)
- GuitarPro 4 (.gp4)
- GuitarPro 5 (.gp5)
- MIDI files (.mid, .midi)

------------------------------------------------------------------------

## Requirements

Support for PHP 5.4, 5.5, 5.6, 7.0, 7.1 and HHVM

------------------------------------------------------------------------

## Contribution and Support

If you have any questions, please [open an issue]({{ site.github_repository_url }}/issues).

You want to write another parser, to fix a bug? Please open [a pull request]({{ site.github_repository_url }}).

------------------------------------------------------------------------

## License

PhpTabs is licensed under [LGPL2.1+]({{ site.github_repository_url }}/blob/master/LICENSE).

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/index.md{% endcapture %}
{% include edit-doc-link.html %}
