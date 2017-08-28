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

```php

include 'vendor/autoload.php';

use PhpTabs/PhpTabs;

$song = new PhpTabs('mytab.gp4');

echo $song->getName();

```

------------------------------------------------------------------------

{% capture doc_url %}{{ site.github_doc_repository_url }}/docs/getting-started.md{% endcapture %}
{% include edit-doc-link.html %}
