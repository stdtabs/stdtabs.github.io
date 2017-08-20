---
layout: default
permalink: render-as-vextab.html
---

{% include vexflow-js.html %}

# Render as a VexTab string

VexTab format is supplied by vexflow.com. If you want to know more 
about VexTab format, there is a [good tutorial](http://www.vexflow.com/vextab/tutorial.html).

Tabs can be rendered as VexTab strings track-by-track.

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
options scale=1 space=16 width=520 tempo=66

tabstave notation=true time=4/4

notes | :8 0/5 9/3 7/4 7/3 T7/3 7/4 0/5 5/3

```

That renders:

{% include_relative examples/_example01.html %}

With a bit of vexflow JS.

------------------------------------------------------------------------

## Customize with VexTab options

Some options can be passed to override default VexTab options.

If the value is the same as VexTab defaults, it won't be printed.

```php

include 'vendor/autoload.php';

use PhpTabs/PhpTabs;

$tab = new PhpTabs('mytab.gp4');

// Available options
$options = [
  // Renderer options
  'measures_per_stave' => 1,

  // Global options
  'space'               => 16,        # An integer
  'scale'               => 0.8,       # A float or an integer
  'stave-distance'      => 20,        # An integer
  'width'               => 500,       # An integer, in pixel

  'font-size'           => 12,        # An integer
  'font-face'           => 'times',   # A string
  'font-style'          => 'italic',  # A string

  'tab-stems'           => true,      # A boolean, default: false
  'tab-stem-direction'  => 'down',    # A string up|down, default: up
  'player'              => false,     # A boolean, default: false

  // Tabstaves options
  'notation'           => true,       # A boolean, default: false
  'tablature'          => true,       # A boolean, default: true
];

// Render track 0
echo $tab
  ->getRenderer('vextab')
  ->setOptions($options)
  ->render(0);

```

Will ouput something like:

```
options scale=0.8 space=16 width=500 tab-stems=true tab-stem-direction=down stave-distance=20 font-size=12 font-face=times font-style=italic tempo=66

tabstave notation=true time=4/4

notes | :8 0/5 9/3 7/4 7/3 T7/3 7/4 0/5 5/3

```

That renders:

{% include_relative examples/_example02.html %}

Other options (tempo, clef, key, etc...) will be set by the tab object.

------------------------------------------------------------------------

# Supported VexTab features

Feature name | Representation | Supported


