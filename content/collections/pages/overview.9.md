---
id: ae0d8e5a-3e14-4766-827b-38f3e9a36c85
blueprint: page
title: 'UI Components Overview'
nav_title: Overview
---
When building custom areas of the Control Panel, you should aim to use the UI components as much as possible.

These will allow you to write UIs that match the design of Statamic without needing to worry about styles or Tailwind classes. It also allows you to keep your UIs in sync with our design system without having to do any additional work. In short, they're here to make your life easier.

You can treat these components like an extension of HTML itself. They should *just work*.

For example, if you need a card, don't use `<div class="bg-white p-4 rounded border shadow-sm">`, use the `<ui-card>` component!

## Syntax

All of the components are available with their kebab-cased name prefixed with `ui-`. For example:

```blade
<ui-card>
    <ui-heading text="A lovely card" />
    <ui-button @click="doSomething" text="Click me" />
</ui-card>
```

This syntax works in Blade _and_ Vue, which is especially handy for those times when you're bouncing back and forth between them.

## Importing

You can optionally import the UI components and namespace them, which gives your IDE the ability to autocomplete, link to the original components, and other useful dev-centric workflows. You import them from `@statamic/cms/ui`.

```vue
<script setup>
import { Card, Heading, Button } from '@statamic/cms/ui';
</script>

<template>
    <Card>
        <Heading text="A lovely card" />
        <Button @click="doSomething" text="Click me" />
    </Card>
</template>
```

## Anatomy of a Component

Most of our components use [Reka](https://reka-ui.com/) under the hood, and are built with Vue.js's [composition API](https://vuejs.org/api/composition-api-setup).

We utilize [Class Variariance Authority](https://cva.style/docs) to dynamically assemble our classes and styles based on variants and props.

## Components

### Listings

You can create a fully fledged listing using the aptly named `Listing` component with search, filters, column customization, etc.

In most cases, you can use the self-closed component and control the behavior using props.

```vue
<script setup>
import { Listing } from '@statamic/cms/ui';
</script>

<template>
    <Listing :items="..." />
</template>
```

| Prop                          | Description                                                                                  |
|-------------------------------|----------------------------------------------------------------------------------------------|
| url                           | The URL from which to retrieve results. Either use this or `items`.                          |
| items                         | If no URL is provided, you can provide an array of items to populate the table.              |
| allowPresets                  | Lets you disable presets.                                                                    |
| allowBulkActions              | Lets you disable bulk actions.                                                               |
| actionUrl                     | The URL from which to retrieve actions.                                                      |
| actionContext                 | The extra data to pass to the server when using actions.                                     |
| allowActionsWhileReordering   | Enables the action twirldown while reordering is enabled.                                    |
| reorderable                   | Adds drag handles to the rows.                                                               |
| preferencesPrefix             | Any preferences (preferred columns, etc) will be saved nested under this.                    |
| columns                       | The columns to display. Can be array of string or column definitions. v-modelable.           |
| allowCustomizingColumns       |                                                                                              |
| sortColumn                    | Defines the sort column. v-modelable                                                         |
| sortDirection                 | Defines the sort direction. Defaults to asc for most fields, desc for dates. v-modelable     |
| sortable                      |                                                                                              |
| selections                    | Array of checked items. v-modelable.                                                         |
| maxSelections                 |                                                                                              |
| pushQuery                     | Adds the parameters to the current URL.                                                      |
| additionalParameters          | Extra data to send to the ajax URL.                                                          |
| allowSearch                   |                                                                                              |
| searchQuery                   | v-modelable                                                                                  |
| filters                       | You can get this by doing `Scope::filters($name, $context)`                                  |
| filtersForReordering          | A function that returns array of filter values to be activated when reordering is enabled.   |
| perPage                       |                                                                                              |
| showPaginationTotals          | Shows the totals in the paginator. e.g. "1-5 of 10"                                          |
| showPaginationPageLinks       | Shows the page links. e.g. 1,2,3,4. With this disabled you'll just get the prev/next arrows. |
| showPaginationPerPageSelector | Shows the per page dropdown.                                                                 |

| Event                | Description                                                                                                                                                                                                               |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| update:columns       | Emits the column definitions when the column customizer is used.                                                                                                                                                          |
| update:sortColumn    | Emits the sort column when a table header is clicked.                                                                                                                                                                     |
| update:sortDirection | Emits the sort direction when a table header is clicked.                                                                                                                                                                  |
| update:selections    | Emits the selected IDs when checkboxes are used.                                                                                                                                                                          |
| update:searchQuery   | Emits the search query when the input is used.                                                                                                                                                                            |
| requestCompleted     | Emits the response when the AJAX request is completed.                                                                                                                                                                    |
| reordered            | Emits an array of IDs after a row has been moved.                                                                                                                                                                         |
| refreshing           | Emitted when the listing should refresh, for example when an action is completed. Useful when using the `items` prop. Not useful when using the `url` prop as the listing will refresh automatically by making a request. |

| Slot                  | Description                                                                                                                                                     |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| initializing          | Displayed when the listing is getting its initial data. Defaults to a loading spinner.                                                                          |
| default               | Allows overriding the entire listing's contents. By default, the sub-components of the listing will be used. Useful if you wanted something other than a table. |
| cell-*                | Allows customization of specific table cells. The slot name will use the column name. e.g. `cell-my_field`.                                                     |
| prepended-row-actions | Allows adding to the action twirldown in each row. You should only add `DropdownItem` components.                                                               |

### Everything else...

You can find documentation for our other [UI Components here](/ui-components/all-ui-components).