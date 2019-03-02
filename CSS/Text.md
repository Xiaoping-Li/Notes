# Text
## _color_
The `color` property is used to set the color of the text. The default text color for a page is defined in the _body_ selector.  
**Note**: For W3C compliant CSS: If you define the color property, you must also define the background-color.

## _text-align_
The `text-align` property is used to set the horizontal alignment of a text.
* left: left alignment is default if text direction is left-to-right.
* right: right alignment is default if text direction is right-to-left.  
* center
* justify: When the `text-align` property is set to "justify", each line is _stretched_ so that every line has equal width, and the left and right margins are straight (like in magazines and newspapers).

## _text-decoration_
The `text-decoration` property is used to set or remove decorations from text.

The value `text-decoration: none;` is often used to remove underlines from _links_ (a tag).
* none
* overline
* line-through
* underline

**Note**: It is not recommended to underline text that is not a link, as this often confuses the reader.

## _text-transform_
The `text-transform` property is used to specify uppercase and lowercase letters in a text.
* uppercase
* lowercase
* capitalize: capitalize the first letter of each word

## _text-indent_
The `text-indent` property is used to specify the _indentation_ of the first line of a text.

## _letter-spacing_
The `letter-spacing` property is used to specify the _space_ between the characters in a text.

The following example demonstrates how to increase or decrease the space between characters:
```
h1 {
  letter-spacing: 3px;
}

h2 {
  letter-spacing: -3px;
}
```

## _line-height_
The `line-height` property is used to specify the space between lines:
```
p.small {
  line-height: 0.8;
}

p.big {
  line-height: 1.8;
}
```

## _direction_
The `direction` property is used to change the text direction of an element.   
Change the default left-to-right direction to right-to-left(rtl):
```
p {
  direction: rtl;
}
```

## _word-spacing_
The `word-spacing` property is used to specify the space between the words in a text.

The following example demonstrates how to increase or decrease the space between words: 
```
h1 {
  word-spacing: 10px;
}

h2 {
  word-spacing: -5px;
}
```

## _text-shadow_
The `text-shadow` property adds shadow to text.

The following example specifies the position of the horizontal shadow (3px), the position of the vertical shadow (2px) and the color of the shadow (red):
```
h1 {
  text-shadow: 3px 2px red;
}
```

## _vertical-align_
The `vertical-align` property sets the vertical alignment of an element.

Value | Description
--- | ---
baseline	| The element is aligned with the baseline of the parent. This is default	
length	| Raises or lower an element by the specified length. Negative values are allowed. Read about length units	
%	| Raises or lower an element in a percent of the "line-height" property. Negative values are allowed	
sub |	The element is aligned with the subscript baseline of the parent	
super |	The element is aligned with the superscript baseline of the parent	
top |	The element is aligned with the top of the tallest element on the line	
text-top |	The element is aligned with the top of the parent element's font	
middle |	The element is placed in the middle of the parent element	
bottom |	The element is aligned with the lowest element on the line	
text-bottom |	The element is aligned with the bottom of the parent element's font	
initial |	Sets this property to its default value. Read about initial	
inherit |	Inherits this property from its parent element. Read about inherit





