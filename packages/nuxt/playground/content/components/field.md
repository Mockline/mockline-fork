---
title: Field
description: Components for displaying and grouping properties, parameters, and field documentation.
---

## Overview

The Field components provide a consistent way to document properties, parameters, and fields in your content. They include two main components: `Field` for individual items and `FieldGroup` for organizing multiple fields together.

## Components

### Field Component

The Field component displays individual properties or parameters with their types, requirements, and descriptions.

::code-preview
:::field{name="username" type="string" required}
The user's unique identifier. Must be between 3 and 20 characters.
:::

#code
```vue
<Field name="username" type="string" required>
  The user's unique identifier. Must be between 3 and 20 characters.
</Field>
```
::

### With Default Value

::code-preview
:::field{name="theme" type="'light' | 'dark'" default="light"}
The color theme for the component. Supports light or dark modes.
:::

#code
```vue
<Field name="theme" type="'light' | 'dark'" default="light">
  The color theme for the component. Supports light or dark modes.
</Field>
```
::

### With Rich Content

::code-preview
:::field{name="format" type="string"}
Supports **markdown** formatting with:
- Lists
- *Emphasis*
- `code`
:::

#code
```vue
<Field name="format" type="string">
  Supports **markdown** formatting with:
  - Lists
  - *Emphasis*
  - `code`
</Field>
```
::

### FieldGroup Component

The FieldGroup component organizes multiple fields into a cohesive list.

::code-preview
:::field-group
  :::field{name="name" type="string" required}
  The name of the configuration.
  :::
  :::field{name="enabled" type="boolean" default="false"}
  Whether the feature is enabled.
  :::
  :::field{name="options" type="object"}
  Additional configuration options.
  :::
:::

#code
```vue
<FieldGroup>
  <Field name="name" type="string" required>
    The name of the configuration.
  </Field>
  <Field name="enabled" type="boolean" default="false">
    Whether the feature is enabled.
  </Field>
  <Field name="options" type="object">
    Additional configuration options.
  </Field>
</FieldGroup>
```
::

## Props

### Field Props

::field-group
  ::field{name="name" type="string" required}
  The name of the field, property, or parameter.
  ::

  ::field{name="type" type="string" required}
  The data type of the field (e.g., string, number, boolean, etc.).
  ::

  ::field{name="required" type="boolean"}
  Indicates if the field is required.
  ::

  ::field{name="default" type="string"}
  The default value of the field, if any.
  ::

  ::field{name="class" type="string"}
  Additional classes to apply to the field container.
  ::
::

### FieldGroup Props

::field-group
  ::field{name="class" type="string"}
  Additional classes to apply to the group container.
  ::
::

## Slots

### Field Slots

::field-group
  ::field{name="default" type="any"}
  The description content for the field. Supports Markdown formatting.
  ::
::

### FieldGroup Slots

::field-group
  ::field{name="default" type="any"}
  Container for Field components.
  ::
::

## Best Practices

1. Field Documentation:
   - Use clear and concise names
   - Provide detailed type information
   - Include default values when applicable
   - Write descriptive explanations

2. Organization:
   - Group related fields together
   - Use consistent formatting
   - Order fields logically (required first)
   - Maintain consistent documentation style

3. Content Writing:
   - Use markdown for rich formatting
   - Include examples when helpful
   - Document edge cases and limitations
   - Keep descriptions focused and clear

4. Accessibility:
   - Use proper heading hierarchy
   - Write descriptive field names
   - Ensure color contrast for required indicators
   - Make documentation screen-reader friendly
