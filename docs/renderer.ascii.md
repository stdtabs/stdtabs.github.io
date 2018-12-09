---
layout: default
permalink: render-as-an-ascii-tab.html
title: Render a song as a ASCII tablature
excerpt: PhpTabs tutorial for rendering a track as an tablature.
---

# Render as an ASCII tablature

ASCII tablature is a must-have feature, PhpTabs (>= 0.6.0) can [render](basics.html#render) a
whole tablature or a single track as an ASCII string. 

## Quick Usage

The following code prints all tabstaves of the first track.

```php
include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$tab = new PhpTabs('mytab.gp4');

// Render first track
echo $tab
  ->getRenderer('ascii')
  ->render(0);

```

The [render()](basics.html#render) method takes a track index as 
parameter.
It starts from 0 for the first track.

This example will ouput something like:

```
E|------------------------|-10-----10-----------------------------------------------------|
B|--------------------X---|-------------13------------------------------------------------|
G|-%-------%------11------|------------------12---12--10------------10----------%---------|
D|-%-------%--------------|-------------------------------12--12--------12--10--%---12----|
A|------------------------|---------------------------------------------------------------|
E|------------------------|---------------------------------------------------------------|

```

------------------------------------------------------------------------

## Customize ASCII options

Some options can be passed to customize tabstaves.

__Track informations__ can be printed with *trackHeader* option.

```php
include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$tab = new PhpTabs('mytab.gp4');

// Render first track with track number and name
echo $tab
  ->getRenderer('ascii')
  ->setOptions(['trackHeader' => true])
  ->render(0);
```
It will output something like:

```
Track 1: Guitar
E|------------------------|-10-----10-----------------------------------------------------|
B|--------------------X---|-------------13------------------------------------------------|
G|-%-------%------11------|------------------12---12--10------------10----------%---------|
D|-%-------%--------------|-------------------------------12--12--------12--10--%---12----|
A|------------------------|---------------------------------------------------------------|
E|------------------------|---------------------------------------------------------------|

```

__Song informations__ can be printed with *songHeader* option.

```php
include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$tab = new PhpTabs('mytab.gp4');

// Render first track with song meta data
echo $tab
  ->getRenderer('ascii')
  ->setOptions(['songHeader'  => true])
  ->render(0);
```
It will output something like:

```
Title: Testing name
Album: Testing album
Artist: Testing artist
Author: Testing author


E|------------------------|-10-----10-----------------------------------------------------|
B|--------------------X---|-------------13------------------------------------------------|
G|-%-------%------11------|------------------12---12--10------------10----------%---------|
D|-%-------%--------------|-------------------------------12--12--------12--10--%---12----|
A|------------------------|---------------------------------------------------------------|
E|------------------------|---------------------------------------------------------------|

```


__Song informations__ and __track informations__ can be combined.

```php
include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$tab = new PhpTabs('mytab.gp4');

// Render first track with song meta data and track informations
echo $tab
  ->getRenderer('ascii')
  ->setOptions(['songHeader'  => true, 'trackHeader' => true])
  ->render(0);
```
It will output something like:

```
Title: Testing name
Album: Testing album
Artist: Testing artist
Author: Testing author


Track 1: Guitar
E|------------------------|-10-----10-----------------------------------------------------|
B|--------------------X---|-------------13------------------------------------------------|
G|-%-------%------11------|------------------12---12--10------------10----------%---------|
D|-%-------%--------------|-------------------------------12--12--------12--10--%---12----|
A|------------------------|---------------------------------------------------------------|
E|------------------------|---------------------------------------------------------------|

```

- __To format line length__ as you want, a *maxLineLength* option is available. It represents how 
many characters can be printed before going to a new line.

```php
include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$tab = new PhpTabs('mytab.gp4');

// Render a limited number of characters.
echo $tab
  ->getRenderer('ascii')
  ->setOptions(['maxLineLength' => 10])
  ->render(0);
```
It will output something like:

```
E|------------------------|
B|--------------------X---|
G|-%-------%------11------|
D|-%-------%--------------|
A|------------------------|
E|------------------------|


E|-10-----10-----------------------------------------------------|
B|-------------13------------------------------------------------|
G|------------------12---12--10------------10----------%---------|
D|-------------------------------12--12--------12--10--%---12----|
A|---------------------------------------------------------------|
E|---------------------------------------------------------------|

```

- Last but not the least, the whole song can be easily printed using the
```render()``` method without any parameters.

```php
include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$tab = new PhpTabs('mytab.gp4');

// Render all song with song and track informations
echo $tab
  ->getRenderer('ascii')
  ->setOptions(['songHeader'  => true, 'trackHeader' => true])
  ->render();
```
It will output something like:

```
Title: Testing name
Album: Testing album
Artist: Testing artist
Author: Testing author


Track 1: Guitar
E|------------------------|-10-----10-----------------------------------------------------|
B|--------------------X---|-------------13------------------------------------------------|
G|-%-------%------11------|------------------12---12--10------------10----------%---------|
D|-%-------%--------------|-------------------------------12--12--------12--10--%---12----|
A|------------------------|---------------------------------------------------------------|
E|------------------------|---------------------------------------------------------------|


Track 2: Voice
E|-------------------------------------|-0-----------3-----------------------|
B|-5-----5-----5-----5-----5-----5-----|-5-----5-----5-----5-----5-----5-----|
G|-------------------------------------|-------------5-----------------------|
D|-------------------------------------|-------------5-----------------------|
A|-------------------------------------|-------------3-----------------------|
E|-------------------------------------|-------------3-----------------------|

```

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/renderer.vextab.md{% endcapture %}
{% include edit-doc-link.html %}
