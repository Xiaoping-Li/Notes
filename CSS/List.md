# List
## Different List Item Markers: _list-style-type_
The `list-style-type` property specifies the type of list item marker. Some of the values are for unordered lists, and some for ordered lists.
* ul
  * circle
  * square
* ol
  * upper-roman
  * lower-alpha
  
## An Image as The List Item Marker: _list-style-image_
The `list-style-image` property specifies an image as the list item marker.
```
ul {
  list-style-image: url('sqpurple.gif');
}
```

## Position The List Item Markers: _list-style-position_
The `list-style-position` property specifies the position of the list-item markers (bullet points).

* `list-style-position: outside;` means that the bullet points will be outside the list item. The start of each line of a list item will be aligned vertically. This is default.
* `list-style-position: inside;` means that the bullet points will be inside the list item. As it is part of the list item, it will be part of the text and push the text at the start.

## Remove Default Settings
The `list-style-type:none;` property can also be used to remove the markers/bullets. **Note** that the list also has default _margin_ and _padding_. To remove this, add `margin:0;` and `padding:0;` to `<ul> or <ol>`:
```
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```

## Shorthand property: _list-style_
The `list-style` property is a shorthand property. It is used to set all the list properties in one declaration. When using the shorthand property, the order of the property values are:

* `list-style-type` (if a list-style-image is specified, the value of this property will be displayed if the image for some reason cannot be displayed)
* `list-style-position` (specifies whether the list-item markers should appear inside or outside the content flow)
* `list-style-image` (specifies an image as the list item marker)

If one of the property values above are missing, the default value for the missing property will be inserted, if any.
```
ul {
  list-style: square inside url("sqpurple.gif");
}
```

## Styling List With Colors
We can also style lists with colors, to make them look a little more interesting.

Anything added to the `<ol> or <ul>` tag, affects the entire list, while properties added to the `<li>` tag will affect the individual list items.






