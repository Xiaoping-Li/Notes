# Float and Clear
## Float
The CSS `float` property specifies how an element should float. The `float` property is used for positioning and formatting content e.g. let an image float left to the text in a container.

The `float` property can have one of the following values:

* **left** - The element floats to the left of its container
* **right**- The element floats to the right of its container
* **none** - The element does not float (will be displayed just where it occurs in the text). This is _default_
* **inherit** - The element inherits the float value of its parent


## Clear
The CSS `clear` property specifies what elements can float beside the cleared element and on which side. The `clear` property specifies what elements can float beside the cleared element and on which side.

The `clear` property can have one of the following values:

* **none** - Allows floating elements on both sides. This is default
* **left** - No floating elements allowed on the left side
* **right**- No floating elements allowed on the right side
* **both** - No floating elements allowed on either the left or the right side
* **inherit** - The element inherits the clear value of its parent

The most common way to use the `clear` property is after you have used a `float` property on an element.

When clearing floats, you should match the `clear` to the `float`: If an element is floated to the left, then you should clear to the left. Your floated element will continue to float, but the cleared element will appear below it on the web page.

### The clearfix Hack
If an element is taller than the element containing it, and it is floated, it will "overflow" outside of its container. Then we can add `overflow: auto;` to the containing element to fix this problem. The `overflow: auto` clearfix works well as long as you are able to keep control of your margins and padding (else you might see scrollbars). The **new, modern clearfix hack** however, is safer to use, and the following code is used for most webpages:
```
.clearfix::after {
  content: "";
  clear: both;
  display: table;
}
```

