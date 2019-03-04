# Font Size
Being able to manage the text size is important in web design. However, you should not use font size adjustments to make paragraphs look like headings, or headings look like paragraphs.

Always use the proper HTML tags, like `<h1> - <h6>` for headings and `<p>` for paragraphs.

The font-size value can be an absolute, or relative size.
* Absolute size:
  * Sets the text to a specified size
  * Does not allow a user to change the text size in all browsers (bad for accessibility reasons)
  * Absolute size is useful when the physical size of the output is known
* Relative size:
  * Sets the size relative to surrounding elements
  * Allows a user to change the text size in browsers

**Note**: If you do not specify a font size, the default size for normal text, like paragraphs, is 16px (16px=1em).

## Set Font Size With Pixels
Setting the text size with pixels gives you full control over the text size.   
**Tip**: If you use pixels, you can still use the zoom tool to resize the entire page.

## Set Font Size With Em
To allow users to resize the text (in the browser menu), many developers use `em` instead of pixels. The `em` size unit is recommended by the W3C. _1em_ is equal to the current font size. The default text size in browsers is 16px. So, the default size of `1em is 16px`. The size can be calculated from pixels to em using this formula: `pixels/16=em`. However, with the `em` size, it is possible to adjust the text size in all browsers. Unfortunately, there is still a problem with older versions of IE. The text becomes larger than it should when made larger, and smaller than it should when made smaller.

## Use a Combination of Percent and Em
The solution that works in all browsers, is to set a default font-size in _percent_ for the <body> element.
```
 body {
  font-size: 100%;
}

h1 {
  font-size: 2.5em;
}
```


