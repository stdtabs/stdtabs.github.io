---
layout: default
permalink: render-as-vextab.html
---

{% include vexflow-js.html %}

# Render a tablature formatted as VexTab

## Quick Usage

Print all tabstaves for the first track.

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
options tempo=96 width=1024 scale=1 space=16

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

<script>

// render vextabExample01

vextab = VexTabDiv;
$(function() {
  VexTab = vextab.VexTab;
  Artist = vextab.Artist;
  Renderer = Vex.Flow.Renderer;
  Artist.DEBUG = false;
  VexTab.DEBUG = false;
  // Create VexFlow Renderer from canvas element with id #boo
  renderer = new Renderer($('#vextabExample01')[0], Renderer.Backends.SVG);
  // Initialize VexTab artist and parser.
  artist = new Artist(10, 10, 1024, {scale: 0.8});
  vextab = new VexTab(artist);
  function render() {
    try {
      vextab.reset();
      artist.reset();
      vextab.parse($("#vextabExample01Staves").val());
      artist.render(renderer);
      $(".editor-error").text("");
    } catch (e) {
      $(".editor-error").html(e.message.replace(/[\n]/g, '<br/>'));
    }
  }
  $("#vextabExample01Staves").keyup(_.throttle(render, 250));
  render();
});

</script>

