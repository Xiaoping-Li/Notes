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
