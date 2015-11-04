plastik-collapsible
============

`plastik-collapsible` is a list of collapsible and expandable items. It extends
`iron-selector`, and thus supports the same functionality, with the exception of
the ability to change the `selectable` attribute.

Demos and documentation are available on the 
[component page](http://www.plastikit.org/1.x/#!/components/plastik-collapsible).

Pull requests are always welcome. If you encounter any bugs, please feel free to
[submit an issue](https://github.com/Plastikit/plastik-collapsible/issues/new/).

## Installation

```sh
bower install plastik-collapsible --save
```
## Basic usage

 > _See [component page](http://www.plastikit.org/1.x/#!/components/plastik-collapsible)
 > for more details._

Items must be tagged with the `.collapsible-item` class, and must have two
children: an `.item-header` and an `.item-content`.

`plastik-collapsible` is minimally styled and therefore must have styles applied
to it. The element will only give itself borders between and around items, style
backgrounds, and style the element's layout.

Additionally, `plastik-collapsible` does not require explicitly defined knowledge
of the header heights and will calculate them automatically and individually.

All of this was done to allow for ample flexibility.

### Example

```html
    <plastik-collapsible>
      <div class="collapsible-item">
        <div class="item-header">Header</div>
        <div class="item-content">
          ...
        </div>
      </div>
      <div class="collapsible-item">
        <div class="item-header">Header</div>
        <div class="item-content">
          ...
        </div>
      </div>
    </plastik-collapsible>
```

## Multi-selection

Just like `iron-selector`, `plastik-collapsible` supports multi-selection. When
multi-selection is enabled, more than one item can be expanded at a time. Simply
add the `multi` attribute or set the `multi` property to true.

### Example

```html
    <plastik-collapsible multi>
      <div class="collapsible-item">
        <div class="item-header">Header</div>
        <div class="item-content">
          ...
        </div>
      </div>
      <div class="collapsible-item">
        <div class="item-header">Header</div>
        <div class="item-content">
          ...
        </div>
      </div>
    </plastik-collapsible>
```
 
## Styling

`plastik-collapsible` applies the `.item-expanded` CSS class by default to any
items which have been expanded. Collapsed items do not have any special class
applied to them.

### Example

```html
    <dom-module id="my-custom-element">
      <style>
        :host {
          .item-expanded {
            background-color: #B3E5FC;
            color: #000;
          };
        }
      </style>
      
      <template>
        <plastik-collapsible multi>
          <div class="collapsible-item">
            <div class="item-header">Header</div>
            <div class="item-content">
              ...
            </div>
          </div>
          <div class="collapsible-item">
            <div class="item-header">Header</div>
            <div class="item-content">
              ...
            </div>
          </div>
        </plastik-collapsible>
      ...
```

Be aware that because `plastik-collapsible` does not rely on statically supplied
header heights, and instead calculates them when items are collapsed or expanded,
that if you change any style or content such that it affects an item's height,
you must call `updateCollapseStyles()` to recalculate the heights appropriately.
If the change only affects an individual item, you can call
`updateCollapseStyles(value)` with the value (or index, if attrForSelected is
unspecified) of the specific item in question.
