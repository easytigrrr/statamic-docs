---
id: e1c41970-5894-4c23-a5af-08f4dd1901ed
blueprint: modifiers
title: 'Parse Url'
modifier_types:
  - string
  - utility
---
Get information about a URL.

``` yaml
url: 'http://example.com/path?query=1'
```

::tabs

::tab antlers
``` antlers
{{ url | parse_url }}
{{ url | parse_url('host') }}
```
::tab blade
```blade
{{ Statamic::modify($url)->parseUrl() }}
{{ Statamic::modify($url)->parseUrl('host') }}
```
::

```php
[
  'scheme'   => 'http',
  'host'     => 'example.com',
  'path'     => '/path',
  'query'    => 'query=1',
]
```

```
example.com
```
