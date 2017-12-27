---
layout: default
permalink: iofactory.html
title: IOFactory - Instanciate PhpTabs
excerpt: How to read data from files with PhpTabs
---

# IOFactory - Instanciate PhpTabs

IOFactory is done in order to:

- create empty PhpTabs,
- load PhpTabs from files and strings 

## Table of contents

- [create()](#create)
- [fromFile()](#fromfilefilename-type)
- [fromJsonFile()](#fromjsonfilefilename)
- [fromSerializedFile()](#fromserializedfilefilename)
- [fromJson()](#fromjsonstring)
- [fromSerialized()](#fromserializedstring)

All these methods return a [PhpTabs](/phptabs.html) resource.

------------------------------------------------------------------------

## create()

This method returns an empty [PhpTabs](/phptabs.html) resource.

#### Type

[\PhpTabs\PhpTabs](/phptabs.html)

#### Example

```php

use PhpTabs\IOFactory;

// Equivalent to 'new PhpTabs()'
$tab = IOFactory::create();

// Print track number
echo "Track count=" . $tab->countTracks();

// Should return "Track count=0"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## fromFile($filename, $type)

This method returns a [PhpTabs](/phptabs.html) resource, loaded from a 
file.

#### Parameters

- _string_ $filename 
- _string_ $type __Optional__ 

#### Type

[\PhpTabs\PhpTabs](/phptabs.html)

#### Examples

```php

use PhpTabs\IOFactory;

// Create a PhpTabs instance
$tab = IOFactory::fromFile('mytabs.gp4');

// Print track number
echo "Track count=" . $tab->countTracks();

// Should return "Track count=2"

```

In case you need to force a parser type, use the second parameter.

```php

use PhpTabs\IOFactory;

// Create a PhpTabs instance from a JSON file
$tab = IOFactory::fromFile('mytabs.dat', 'json');

// Print track number
echo "Track count=" . $tab->countTracks();

// Should return "Track count=2"

```


[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## fromJsonFile($filename)

This method returns a [PhpTabs](/phptabs.html) resource, loaded from a 
JSON file.

#### Parameters

- _string_ $filename 

#### Type

[\PhpTabs\PhpTabs](/phptabs.html)

#### Examples

```php

use PhpTabs\IOFactory;

// Create a PhpTabs instance
$tab = IOFactory::fromJsonFile('mytabs.json');

// Print track number
echo "Track count=" . $tab->countTracks();

// Should return "Track count=2"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## fromSerializedFile($filename)

This method returns a [PhpTabs](/phptabs.html) resource, loaded from a 
PHP serialized file.

#### Parameters

- _string_ $filename 

#### Type

[\PhpTabs\PhpTabs](/phptabs.html)

#### Examples

```php

use PhpTabs\IOFactory;

// Create a PhpTabs instance
$tab = IOFactory::fromSerializedFile('mytabs.ser');

// Print track number
echo "Track count=" . $tab->countTracks();

// Should return "Track count=2"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## fromJson($string)

This method returns a [PhpTabs](/phptabs.html) resource, loaded from a 
JSON string.

#### Parameters

- _string_ $string 

#### Type

[\PhpTabs\PhpTabs](/phptabs.html)

#### Examples

```php

use PhpTabs\IOFactory;

// Create a PhpTabs instance
$tab = IOFactory::fromJson('{"song":{"name":null,"artist":null,"album":null,"author":null,"copyright":null,"writer":null,"comments":null,"channels":[],"measureHeaders":[],"tracks":[]}}');

// Print track number
echo "Track count=" . $tab->countTracks();

// Should return "Track count=0"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

## fromSerialized($string)

This method returns a [PhpTabs](/phptabs.html) resource, loaded from a 
PHP serialized string.

#### Parameters

- _string_ $string 

#### Type

[\PhpTabs\PhpTabs](/phptabs.html)

#### Examples

```php

use PhpTabs\IOFactory;

// Create a PhpTabs instance
$tab = IOFactory::fromSerialized('a:1:{s:4:"song";a:10:{s:4:"name";N;s:6:"artist";N;s:5:"album";N;s:6:"author";N;s:9:"copyright";N;s:6:"writer";N;s:8:"comments";N;s:8:"channels";a:0:{}s:14:"measureHeaders";a:0:{}s:6:"tracks";a:0:{}}}');

// Print track number
echo "Track count=" . $tab->countTracks();

// Should return "Track count=0"

```

[_^ Table of contents_]({{ page.permalink }}#top)

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/iofactory.md{% endcapture %}
{% include edit-doc-link.html %}
