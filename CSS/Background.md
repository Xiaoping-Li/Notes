# _Background_ properties
* background-color
* background-image
  * background-repeat
  * background-position
* background-attachment

## background-image
```
selector {
  background-image: url("paper.gif");
}
```

## background-repeat
* background-repeat: repeat-x;   ---> repeat horizontally
* background-repeat: repeat-y;   ---> repeat vertically
* background-repeat: no-repeat;

## background-position
`background-position` sets the _initial_ position for each background _image_. The position is relative to the position layer set by `background-origin`.
```
background-position: right 35% bottom 45%;
background-position: 25% 75%;
background-position: left;
background-position: left top;
```

## background-attachment
The `background-attachment` CSS property sets whether a background image's position is fixed within the _viewport_, or scrolls with its containing block. (fixed, scroll, local)
```
background-attachment: fixed;
background-attachment: local, scroll;
```

## _background_: Shorthand property 
To shorten the code, it is also possible to specify all the background properties in one single property. This is called a shorthand property.

When using the shorthand property the order of the property values is:

* background-color
* background-image
* background-repeat
* background-attachment
* background-position
It does not matter if one of the property values is missing, as long as the other ones are in this order.
```
background: #ffffff url("img_tree.png") no-repeat right top;
```
