---
id: 81617b1f-000e-4d18-b5ea-592b9d845ccb
blueprint: variables
types:
  - system
title: 'Xml Header'
---
Simply outputs an XML Header tag.

Statamic's template parser will encode `<?` and `?>` because they are PHP tags. Silly XML. This global will get you around that.

::tabs

::tab antlers
```antlers
{{ xml_header }}
```
::tab blade
```blade
{{ $xml_header }}
```
::

```html
<?xml version="1.0" encoding="utf-8" ?>
```
