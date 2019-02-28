# Border Properties
## _border-style_
The `border-style` property specifies what kind of border to display.

The following values are allowed:

* `dotted` - Defines a dotted border
* `dashed` - Defines a dashed border
* `solid` - Defines a solid border
* `double` - Defines a double border
* `groove` - Defines a 3D grooved border. The effect depends on the border-color value
* `ridge` - Defines a 3D ridged border. The effect depends on the border-color value
* `inset` - Defines a 3D inset border. The effect depends on the border-color value
* `outset` - Defines a 3D outset border. The effect depends on the border-color value
* `none` - Defines no border
* `hidden` - Defines a hidden border

The `border-style` property can have from _one to four values_ (for the `top border, right border, bottom border, and the left border`).


## _border-width_
The `border-width` property specifies the width of the four borders.

The width can be set as a specific size (in px, pt, cm, em, etc) or by using one of the three pre-defined values: `thin, medium, or thick`.

The `border-width` property can have from _one to four values_ (for the `top border, right border, bottom border, and the left border`).


## _border-color_
The `border-color` property is used to set the color of the four borders.

The color can be set by:

* name - specify a color name, like "red"
* Hex - specify a hex value, like "#ff0000"
* RGB - specify a RGB value, like "rgb(255,0,0)"
* transparent
The `border-color` property can have from _one to four values_ (for the `top border, right border, bottom border, and the left border`). 

If `border-color` is not set, it inherits the color of the element.


## _border-radius_
The `border-radius` property is used to add rounded borders to an element:
```
p {
  border: 2px solid red;
  border-radius: 5px;
}
```


## Shorthand Property: _border_
The `border` property is a shorthand property for the following individual border properties:

* border-width
* border-style (required)
* border-color

You can also specify all the individual border properties for just one side:
```
p {
  border-left: 6px solid red;
}
```

## Individual Sides of border
In CSS, there are also properties for specifying each of the borders (top, right, bottom, and left):
```
p {
  border-top-style: dotted;
  border-right-style: solid;
  border-bottom-style: dotted;
  border-left-style: solid;
}
```
If the `border-style` property has four values:

* **border-style: dotted solid double dashed;**
  * top border is dotted
  * right border is solid
  * bottom border is double
  * left border is dashed
  
If the `border-style` property has three values:

* **border-style: dotted solid double;**
  * top border is dotted
  * right and left borders are solid
  * bottom border is double
  
If the `border-style` property has two values:

* **border-style: dotted solid;**
  * top and bottom borders are dotted
  * right and left borders are solid
  
If the `border-style` property has one value:

* **border-style: dotted;**
  * all four borders are dotted
  
It also works with `border-width` and `border-color`.
