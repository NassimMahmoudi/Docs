---
id: createConfiguration
title: Configuration
---

:::info

After [installation](installation.md).

:::


### Configuration file
Write a configuration in file eg. ( index.html )

```html
<script>
    const config = {
        "sessionConfigurations": {
            "storage": "cookie",
            "expiration": 43200
        },
        "endpointConfigurations": {
            "url": "api to catching events (we send post request with json data)"
        },
        "pickerConfigurations": {
            ....
        }
    }
    picker.initPicker.fromConfigFile(config);
</script>
```
or paste link to configuration.
```html
<script>
    const url = "url to configuration";
    picker.initPicker.fromUrl(url);
</script>
```

### Options

Avaiable options in configuration file (json object):

- sessionConfigurations
    - storage
        - **desc:** where we store information user browser
    - expiration
        - **desc:** how long the cookie is valid
- endpointConfigurations
    - url
        - **desc:** url to endpoint where we send catching events
        - **method:** POST
        - **data:** JSON
- pickerConfigurations - most important piece of configuration
    - documents - we can catching events on eg. products div
        - **type:** Array
    - sorting - we can catching events on sorting (eg. desc, asc)
        - **type:** Array
    - filter - we can catching events on filters
        - **type:** Array
    - pagination - we can catching events when we click next page on pagination
        - **type:** Array
    - search-query - we can catching events on search input event
        - **type:** Array

------

### Picker Configurations

Avaiable options in **pickerConfigurations**

:::info Information

All Options belowe are avaiable in pickerConfigurations keys (
documents, sorting, filter, pagination, search-query
).
:::

<small>All with <Color color="#f00">*</Color> are required</small>

| Option      | Description |
| ----------- | ----------- |
| eventSelector <Color color="#f00">*</Color>  | Main parent css selector for selected element, eg .search related DOM elements can be extended with according data-attributes  <br /> ```.search-box #custom-search-input .input-group .category-item[data-category-value]``` |
| event <Color color="#f00">*</Color>   | event to listener on the element,eg. <br /> ```click, keyup, observe``` |
| fields <Color color="#f00">*</Color>   | action on what fields working  <br />  [Fields Options](#fields-options) |
| id | call to id if used this object on different place, eg. <br /> ```search_input``` |
| observe | watching relation child to parent, eg. <br /> ```#custom-search-input .input-group``` |


export const Color = ({children, color}) => (
  <span
    style={{
      color: color,
    }}>
    {children}
  </span>
);

### Fields Options

Fields tell us which element we can track. Fields are type array of object.

<small>All with <Color color="#f00">*</Color> are required</small>

| Option      | Description |
| ----------- | ----------- |
| key <Color color="#f00">*</Color> | Name of the tracking element, you can type here anything. |
| selector | Child css selector to track in parent element (eventSelector), if not set we taking value from "eventSelector". <small>(also check, [Helpers](#helpers) section)</small> |
| attribute | Getting value from selector attribute , if set "selector", we taking value from here, if not from "eventSelector". |
| [func](#function) | We can create own function to catching some others events. <small>(also check, [Helpers](#helpers) section)</small> |

### Function (func)

Example calling:

```json
    {
        "func": function(element, elements, helpers) {
            return element.value;
        }
    }
```
Example accesing element by id:
```json
    {
        "func": function(element, elements, helpers) {
            return elements['search_input'].value;
        }
    }
```

Function parameters:

| Option      | Description |
| ----------- | ----------- |
| element | Providing DOM element |
| elements | Providing DOM elements of all field configuration with has an id attribute assigned |
| [helpers](#helpers) | Helpers function |

### Helpers

Functions implemented by us for non-standard cases.

| Helper (function) | Description |
| ----------- | ----------- |
| absolutePathFromEventSelector(eg. ".parent .h1") | Function to getting events from child to parent |

Two ways of calling a function

```json
    {
        ...,
        "func": function(element, helpers) {
            return helpers.absolutePathFromEventSelector(".widget > .filter-title");
        }
    }
```
or
```json
    {
        ...,
        "selector": "absolutePathFromEventSelector:'.widget > label > span'",
        ...
    }
```
