---
title: 'Session:Set'
description: 'Store and persist data in the user session.'
intro: Data set in the session will be available in all future requests until such time that the session is cleared over time (sessions eventually expire) or intentionally. Session variables can be retrieved with the main [session](/tags/session) tag.
id: 90796c5b-6b11-4b02-9e6b-fd70211c825a
---
## Example

This can be used for many different things. For example, you could set a variable on the form success page if a user has filled out a special survey form.

::tabs

::tab antlers
```antlers
{{ session:set entered_survey="true" }}
```
::tab blade
```blade
{{-- Using Antlers Blade Components --}}
<s:session:set entered_survey="true" />

{{-- Using session() helper --}}
@php(session()->put('entered_survey', true))
```
::

Later you could decide to show a message instead of the form if the user has already filled it out.

::tabs

::tab antlers
```antlers
{{ session }}
    {{ if entered_survey }}
        <p>You already filled out the form.</p>
    {{ /if }}
{{ /session }}
```
::tab blade
```blade
@if (session()->get('entered_survey'))
  <p>You already filled out the form.</p>
@endif
```
::

## Multiple Variables

You can set multiple variables at once and reference interpolated data (references to variables).

::tabs

::tab antlers
```antlers
{{ session:set likes="hats" :visited="url" }}
```
::tab blade
```blade
{{-- Using Antlers Blade Components --}}
<s:session:set likes="hats" :visited="url" />
```
::

## Tag Pair

This tag is also available as a pair, which can be used to immediately display set data.

::tabs

::tab antlers
```antlers
{{ session:set likes="boomboxes" }}
    <p>You like {{ likes }}, huh?</p>
{{ /session:set }}
```
::tab blade
```blade
<s:session:set likes="boomboxes">
  <p>You like {{ $likes }}, huh?</p>
</s:session:set>
```
::

## Setting Array Data

Array data can be set with dot notation.

::tabs

::tab antlers
```antlers
{{ session:set likes.books="true" likes.hats="true" }}
```
::tab blade
```blade
{{-- Using Antlers Blade Components --}}
<s:session:set likes.books="true" likes.hats="true" />
```
::

## Forgetting Data

Data can be removed from the session [session:forget](/tags/session-forget), and the entire session flushed with [session:flush](/tags/session-flush). 🚽
