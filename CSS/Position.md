# CSS Layout - The position Property
The `position` property specifies the type of positioning method used for an element. There are five different position values:
* static
* relative
* fixed
* absolute
* sticky

Elements are then positioned using the `top, bottom, left, and right` properties. However, these properties will not work unless the `position` property is _set first_. They also work differently depending on the position value.

## `position: static;`
HTML elements are positioned _static_ by default. Static positioned elements are **not affected by the top, bottom, left, and right properties**. An element with `position: static;` is not positioned in any special way; it is always positioned according to the normal flow of the page.

## `position: relative;`
An element with `position: relative;` is positioned relative to its _normal position_. Setting the `top, right, bottom, and left` properties of a relatively-positioned element will cause it to be adjusted away from its normal position. Other content will not be adjusted to fit into any gap left by the element.

## `position: fixed;`
An element with `position: fixed;` is positioned relative to the **viewport** (_browser window_), which means it always stays in the same place even if the page is scrolled. The `top, right, bottom, and left` properties are used to position the element. A fixed element does not leave a gap in the page where it would normally have been located.

## `position: absolute;`
An element with `position: absolute;` is positioned relative to the nearest positioned ancestor (instead of positioned relative to the viewport, like fixed). However, if an absolute positioned element has no positioned ancestors, it uses the **document body** (_HTML page_), and moves along with page scrolling.

**Note**: A "positioned" element is one whose position is anything except **static**.

## `position: sticky;`
An element with `position: sticky;` is positioned based on the user's **scroll position**. A sticky element toggles between _relative_ and _fixed_, depending on the scroll position. It is positioned relative until a given offset position is met in the _viewport_ - then it "sticks" in place (like position:fixed).

**Note**: Internet Explorer, Edge 15 and earlier versions do not support sticky positioning. Safari requires a -webkit- prefix (see example below). You must also specify at least one of `top, right, bottom or left` for sticky positioning to work.

## Overlapping Elements: _z-index_
When elements are positioned, they can overlap other elements. The `z-index` property specifies the stack order of an element (which element should be placed in front of, or behind, the others). An element can have a `positive or negative` stack order. (For example, an image has a z-index of -1, it will be placed behind the text)

An element with greater stack order is always in front of an element with a lower stack order.

**Note**: If two positioned elements overlap **without a z-index** specified, the element positioned last in the HTML code will be shown on top.
