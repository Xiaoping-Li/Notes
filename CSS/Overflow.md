# Overflow
## properties
The CSS `overflow` property controls what happens to content that is too big to fit into an area. The `overflow-x` and `overflow-y` properties specifies whether to change the overflow of content just horizontally or vertically (or both).
* **overflow**: specifies whether to clip the content or to add scrollbars when the content of an element is too big to fit in the specified area. 
* **overflow-x**: specifies what to do with the left/right edges of the content. 
* **overflow-y**: specifies what to do with the top/bottom edges of the content.

## Values
* `visible` - Default. The overflow is not clipped. The content renders outside the element's box.
* `hidden` - The overflow is clipped, and the rest of the content will be invisible.
* `scroll` - The overflow is clipped, and a scrollbar is added to see the rest of the content. Setting the value to `scroll`, the `overflow` is clipped and a scrollbar is added to scroll inside the box. Note that this will add a scrollbar both horizontally and vertically (even if you do not need it).
* `auto` - Similar to scroll, but it adds scrollbars _only when necessary_.

**Note**: The overflow property only works for block elements with a specified height.

**Note**: In OS X Lion (on Mac), scrollbars are hidden by default and only shown when being used (even though "overflow:scroll" is set).

