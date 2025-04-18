---
id: 2940c834-7062-47a1-957c-88a69e790cbb
blueprint: page
title: Fieldsets
template: page
intro: 'Fieldsets are used to store and organize reusable fields.'
related_entries:
  - 54548616-fd6d-44a3-a379-bdf71c492c63
  - 9a1d8b88-c600-46f2-8727-1deb56f2e87a
---
## Overview

Fieldsets are almost functionally equivalent to [Blueprints](/blueprints), except that they exist for you to be able to create reusable fields.

While Blueprints attach directly to content like collections or forms, Fieldsets are not directly attached to anything.

Fieldsets contain [fields](/fields), just like Blueprints, but the benefit of using a Fieldset is that you can import their fields (or the whole thing) into other Blueprints. You can even import fieldsets into certain fieldtypes, like [Grid](/fieldtypes/grid), [Replicator](/fieldtypes/replicator), or [Bard](/fieldtypes/bard).

Fieldsets can only have fields. They don't have sections like Blueprints can.


## Creating fieldsets

There are 2 ways to create fieldsets:

- In the **Fieldsets** area of the control panel.
- Creating a YAML file in the appropriate place within `resources/fieldsets/`. More on that in a moment.

Once created, you can begin to define its fields.

## Directory structure

Whether you manually create your fieldsets's YAML file, or use the control panel, they will all end up as YAML files in the `resources/fieldsets` directory.

``` files theme:serendipity-light
resources/
  fieldsets/
    bard-image.yaml
    bard-quote.yaml
    common.yaml
```

## YAML structure

At its most basic, a fieldset has an array of fields.

```yaml
fields:
  -
    handle: content
    type: markdown
  -
    handle: featured
    type: toggle
```

## Using fields

As mentioned earlier, a Fieldset is not inherently attached to anything. In order to use a field (or fields) in a fieldset, you'll need to approach it from the Blueprint side.

See the [Reusable Fields](/blueprints#reusable-fields) section of the Blueprint docs for more details.