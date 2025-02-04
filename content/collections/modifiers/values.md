---
id: b57caa5c-ae9e-4220-b8a6-f7c82d16f0df
blueprint: modifiers
title: Values
modifier_types:
  - array
  - utility
---
Retrieves just the values from the given array.

```yaml
the_team:
    jack: Jack McDade
    jason: Jason Varga
    jesse: Jesse Leite
    joshua: Joshua Blum
    duncan: Duncan McClean
```

::tabs

::tab antlers
```antlers
{{ the_team | values }}
```
::tab blade
```blade
{{ Statamic::modify($the_team)->values()->fetch() }}
```
::

```yaml
- Jack McDade
- Jason Varga
- Jesse Leite
- Joshua Blum
- Duncan McClean
```
