---
layout: default
permalink: render-as-vextab.html
---

{% include vexflow-js.html %}

# Render a track as a VexTab string

## Quick Usage

Print all tabstaves of the first track.

```php

include 'vendor/autoload.php';

use PhpTabs/PhpTabs;

$tab = new PhpTabs('mytab.gp4');

// Render track 0
echo $tab
  ->getRenderer('vextab')
  ->render(0);

```

Will ouput something like:

```
options tempo=96 width=520 scale=1 space=16

tabstave
	notation=true
	tablature=true
	clef=treble
	time=4/4

notes | :8 0/5 9/3 7/4 7/3 T7/3 7/4 0/5 5/3

```

That renders:

{% include_relative examples/_example01.html %}

With a little bit of js vexflow.

------------------------------------------------------------------------
