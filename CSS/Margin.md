# Margin
## Properties
* margin-top
* margin-right
* margin-bottom
* margin-left
* margin: short-hand, order: top right bottom left

## Values
* auto - the browser calculates the margin
* length - specifies a margin in px, pt, cm, etc.
* % - specifies a margin in % of the width of the containing element
* inherit - specifies that the margin should be inherited from the parent element

**Tip**: Negative values are allowed.

## Margin - Shorthand Property
If the `margin` property has four values:

* **margin: 25px 50px 75px 100px;**
  * top margin is 25px
  * right margin is 50px
  * bottom margin is 75px
  * left margin is 100px
  
If the `margin` property has three values:

* **margin: 25px 50px 75px;**
  * top margin is 25px
  * right and left margins are 50px
  * bottom margin is 75px

If the `margin` property has two values:

* **margin: 25px 50px;**
* top and bottom margins are 25px
* right and left margins are 50px

If the `margin` property has one value:

* **margin: 25px;**
  * all four margins are 25px
  
## The auto Value
You can set the margin property to `auto` to _horizontally center_ the element within its container.

The element will then take up the specified width, and the remaining space will be split equally between the _left_ and _right_ margins.

**Note**: Center aligning has no effect if the width property is not set (or set to 100%).

## The inherit Value
This example lets the left margin of the `<p class="ex1">` element be _inherited_ from the parent element (`<div>`).
 ```
 div {
  border: 1px solid red;
  margin-left: 100px;
}

p.ex1 {
  margin-left: inherit;
}
```

## Margin Collapse
`Top` and `bottom` margins of elements are sometimes collapsed into a single margin that is equal to the largest of the two margins.

This does not happen on left and right margins! Only top and bottom margins!
```
h1 {
  margin: 0 0 50px 0;
}

h2 {
  margin: 20px 0 0 0;
}
```
In the example above, the <h1> element has a bottom margin of 50px and the <h2> element has a top margin set to 20px.

Common sense would seem to suggest that the vertical margin between the <h1> and the <h2> would be a total of 70px (50px + 20px). But due to margin collapse, the actual margin ends up being 50px.

