---
layout: default
excerpt: Read, write and render music scores, GuitarPro tabs and MIDI files.
---

# PHP Simple Music

PhpTabs is a PHP library for reading, writing and rendering tabs and MIDI files.

It provides direct methods to read a song name, get a list of instruments or whatever be your needs.

- Support for PHP 5.4, 5.5, 5.6, 7.0, 7.1 and HHVM

------------------------------------------------------------------------

## Read, edit and render the entire tab

- Read, update, write and convert GuitarPro/MIDI files
- Access metadata and data
- Dump data into JSON, XML, YAML and other formats
- Render a song in VexTab notation (Web)

------------------------------------------------------------------------

## Supported formats

- GuitarPro 3, 4 & 5 (.gp3, .gp4 and .gp5)
- MIDI files (.mid, .midi)

------------------------------------------------------------------------

## Documentation

- [Getting started](/getting-started.html)

- [Music-Object-Model overview](/phptabs.html)
  - [Song](/music-song.html)
    - [Track](/music-track.html)

- Some use-cases examples:

  - Read and update song metadata (Name, author)

  - [Render a track as a VexTab string](/render-as-vextab.html)

  - Read measures for a particular track

  - Read notes for a particular measure

  - Create a tab from scratch (An empty song)

------------------------------------------------------------------------

## Contribution and Support

If you have any questions, need another output type, please open an issue.

You want to write another parser? Please open a pull request.

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/index.md{% endcapture %}
{% include edit-doc-link.html %}
