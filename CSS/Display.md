# CSS Layout - The display Property
The `display` property is the most important CSS property for controlling _layout_. The display property specifies `if/how` an element is displayed. Every HTML element has a default display value depending on what type of element it is. The default display value for most elements is `block` or `inline`.

* **Block-level Elements**: A `block-level` element always starts on a new line and takes up the full width available (stretches out to the left and right as far as it can).
  * `<div>`
  * `<h1> - <h6>`
  * `<p>`
  * `<form>`
  * `<header>`
  * `<footer>`
  * `<section>`
* **Inline Elements**: An inline element does not start on a new line and only takes up as much width as necessary.
  * `<span>`
  * `<a>`
  * `<img>`
  
## `Display: none;`
`display: none;` is commonly used with JavaScript to hide and show elements without deleting and recreating them. The `<script>` element uses `display: none;` as default. 

## Override The Default Display Value
As mentioned, every element has a default display value. However, you can override this. Changing an inline element to a block element, or vice versa, can be useful for making the page look a specific way, and still follow the web standards.

**Note**: Setting the display property of an element only changes **how the element is displayed**, NOT what kind of element it is. So, an _inline element_ with `display: block;` is not allowed to have other block elements inside it.

## Hide an Element - `display:none` or `visibility:hidden`?
* Hiding an element can be done by setting the `display: none;`. The element will be hidden, and the page will be displayed as if the element is not there.
* `visibility:hidden;` also hides an element. However, the element will still take up the same space as before. The element will be hidden, but still affect the layout.
