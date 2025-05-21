---
id: test-id
title: test title
tags:
  - Demo
  - Getting started
published_at: 2023-03-30
---


# Test


## Mermaid
```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```


## Annotations
:::note

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::tip

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::info

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::caution

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::danger

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

## Admonition
- is not working in the current version
```html
<Admonition type="tip" icon="💡" title="Did you know...">
  <p>
    Use plugins to introduce shorter syntax for the most commonly used JSX
    elements in your project.
  </p>
</Admonition>
``
