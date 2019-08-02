# Responsive Design
`Responsive design` refers to the ability of a website to resize and reorganize its content based on:
* The size of other content on the website.
* The size of the screen the website is being viewed on.

## Em
One unit of measurement you can use in CSS to create _relatively-sized_ content is the em, written as `em` in CSS.

## Rem
**Rem** stands for _root em_. It acts similar to _em_, but instead of checking `parent elements` to size font, it checks the `root element`. The root element is the `<html> tag`.

Most browsers set the font size of `<html>` to _16 pixels_, so by default `rem` measurements will be compared to that value. To set a different font size for the root element, you can add a CSS rule.
```
html {
  font-size: 20px;
}

h1 {
  font-size: 2rem;
}
```
**Note:** One advantage of using `rems` is that all elements are compared to the same font size value, making it easy to predict how large or small font will appear. If you are interested in sizing elements consistently across an entire website, the `rem` measurement is the best unit for the job. If you’re interested in sizing elements in comparison to other elements nearby, then the `em` unit would be better suited for the job.

## Percentages: Height & Width
To size _non-text_ HTML elements relative to their parent elements on the page you can use `percentages`.

`Percentages` are often used to size `box-model` values, like `width and height, padding, border, and margins`. They can also be used to set positioning properties (top, bottom, left, right).

When `percentages` are used, elements are sized relative to the dimensions of their parent element (also known as a container). Be careful, a child element’s dimensions may be set _erroneously_ if the dimensions of its parent element aren’t set first.

**Note:** Because the box model includes padding, borders, and margins, setting an element’s width to 100% may cause content to _overflow_ its parent container. While tempting, 100% should only be used when content will not have padding, border, or margin.

## Percentages: Padding & Margin
When height and width are set using percentages, you learned that the dimensions of child elements are calculated based on the dimensions of the parent element.

When percentages are used to set padding and margin, however, they are calculated based only on the _width_ of the parent element. An unset height (the parent’s) results in a constantly changing height due to changes to the child element. This is why vertical padding and margin are based on the width of the parent, and not the height.

**Note:** When using relative sizing, `ems` and `rems` should be used to size _text_ and dimensions on the page related to text size (i.e. padding around text). This creates a consistent layout based on text size. Otherwise, `percentages` should be used.

## Width: Minimum & Maximum
Although relative measurements provide consistent layouts across devices of different screen sizes, elements on a website can lose their integrity when they become too small or large. You can limit how wide an element becomes with the following properties:
* min-width — ensures a minimum width for an element.
* max-width — ensures a maximum width for an element.
```
p {
  min-width: 300px;
  max-width: 600px;
}
```
In the example above, when the browser is resized, the width of paragraph elements will not fall below 300 pixels, nor will their width exceed 600 pixels.

When a browser window is narrowed or widened, text can become either very compressed or very spread out, making it difficult to read. These two properties ensure that content is legible by limiting the minimum and maximum widths.

**Note:** The unit of pixels is used to ensure hard limits on the dimensions of the element(s).

## Height: Minimum & Maximum
You can also limit the minimum and maximum _height_ of an element.
* min-height — ensures a minimum height for an element’s box.
* max-height — ensures a maximum height for an element’s box.
```
p {
  min-height: 150px;
  max-height: 300px;
}
```
What will happen to the contents of an element if the `max-height` property is set too low for that element? It’s possible that content will **overflow** outside of the element, resulting in content that is not legible.

## Scaling Images and Videos
Many websites contain a variety of different media, like images and videos. When a website contains such media, it’s important to make sure that it is scaled proportionally so that users can correctly view it.
```
.container {
  width: 50%;
  height: 200px;
  overflow: hidden;
}

.container img {
  max-width: 100%;
  height: auto;
  display: block;
}
```
In the example above, `.container` represents a container `div`. It is set to a width of `50%` (half of the browser’s width, in this example) and a height of 200 pixels. Setting `overflow` to `hidden` ensures that any content with dimensions larger than the container will be hidden from view.

The second CSS rule ensures that images scale with the width of the container. The `height` property is set to `auto`, meaning an image’s height will automatically scale proportionally with the width. Finally, the last line will display images as `block` level elements (rather than `inline-block`, their default state). This will prevent images from attempting to align with other content on the page (like text), which can add unintended margin to the images.

It’s worth memorizing the entire example above. It represents a very `common design pattern` used to scale images and videos proportionally.

**Note:** The example above scales the width of an image (or video) to the width of a container. If the image is larger than the container, the vertical portion of the image will overflow and will not display. To swap this behavior, you can set max-height to 100% and width to auto (essentially swapping the values). This will scale the height of the image with the height of the container instead. If the image is larger than the container, the horizontal portion of the image will overflow and not display.

## Scaling Background Images
Background images of HTML elements can also be scaled responsively using CSS properties.
```
body {
  background-image: url('#');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
```
* In the example above, the first CSS declaration sets the background image (# is a placeholder for an image URL in this example). 
* The second declaration instructs the CSS compiler to not repeat the image (by default, images will repeat). 
* The third declaration centers the image within the element.
* The final declaration, however, is the focus of the example above. It’s what scales the background image. The image will cover the entire background of the element, all while keeping the image in proportion. If the dimensions of the image exceed the dimensions of the container then only a portion of the image will display.





