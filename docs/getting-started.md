---
layout: default
permalink: getting-started.html
---

# Getting started

## Install with composer

```bash

composer require stdtabs/phptabs

```

## Quick Usage

- Print a song name

```php

include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$song = new PhpTabs('mytab.gp4');

echo $song->getName();

```

- Print all track names

```php

include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$song = new PhpTabs('mytab.gp4');

foreach ($song->getTracks() as $track) {
  echo sprinf(
    '\n#%d - %s',
    $track->getNumber(),
    $track->getName()
  );
}

```

- Print PhpTabs version (PhpTabs >= 0.6)

```php

include 'vendor/autoload.php';

use PhpTabs\PhpTabs;

$song = new PhpTabs('mytab.gp4');

echo $song->getVersion(); // 0.6.0

```


For more examples, see [traversing the tree](/phptabs.html#traversing-the-tree-is-made-simple) documentation



------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/getting-started.md{% endcapture %}
{% include edit-doc-link.html %}
