# Generalizations

## Nesting 
* **Nesting** is the process of placing child selectors and properties in the scope of a parent selector. This allows a programmer to draw DOM relationships and avoid repetition.
```
.container {                                                          .container .icon {
  text-align: center;                                                     display: inline-block;
  font-family: 'Pacifico', cursive;                >>>                    font-size: 32px;
  .icon {                                                             }
    display: inline-block;
    font-size: 32px;
  }
}
```

## Variables 
* **Variables** make it easy to update code and reference values by allowing you to assign an identifier to a value.
```
$translucent-white: rgba(255,255,255,0.3);
$icon-square-length: 300px;
$standard-border: 4px solid black;
```

## Sass Data Types 
**include:**
* Numbers: `8.11, 12, and 10px`
* Strings: `"potato", 'tomato', span`
* Booleans: `true and false`
* null: which is considered an empty value.
* Lists: can be separated by either spaces or commas. You can also surround a list with parentheses and create lists made up of lists. 
```
1.5em Helvetica bold;
Helvetica, Arial, sans-serif;
```
* Maps: are very similar to lists, but instead each object is a `key-value` pair. In a map, the value of a key can be a list or another map. The typical map looks like: `(key1: value1, key2: value2);`

## The & Selector in Nesting
In CSS, a `pseudo-element` is used to style parts of an element, for example:
* Styling the content `::before` or `::after` the content of an element.
* Using a pseudo class such as `:hover` to set the properties of an element when the user’s mouse is touching the area of the element.

In Sass, the **&** character is used to specify exactly where a parent selector should be inserted. It also helps write psuedo classes in a much less repetitive way.
```
.notecard{                                                        .notecard:hover {
  &:hover{                                                           transform: rotatey(-180deg);
    @include transform (rotatey(-180deg));       >>>               }
  }
}
```

## _mixin_
### _mixin_ Argument
In Sass, a **mixin** lets you make groups of CSS declarations that you want to reuse throughout your site. Mixin names and all other Sass identifiers use hyphens and underscores interchangeably. Mixins also have the ability to take in a value. An _argument_, or _parameter_, is a value passed to the mixin that will be used inside the mixin. 

**In fact, you should only ever use a _mixin_ if it takes an argument.** 
```
@mixin backface-visibility($visibility) {
  backface-visibility: $visibility;
  -webkit-backface-visibility: $visibility;
  -moz-backface-visibility: $visibility;
  -ms-backface-visibility: $visibility;
  -o-backface-visibility: $visibility;
}
```
Using _mixin_:
```
.notecard {
.front, .back {
    width: 100%;
    height: 100%;
    position: absolute;

    @include backface-visibility(hidden);
  }
}
```

### Default Value
Mixin arguments can be assigned a **_default value_** in the mixin definition by using a special notation.

A _default value_ is assigned to the argument if no value is passed in when the mixin is included. Defining a default value for each argument is optional.
```
@mixin backface-visibility($visibility: hidden) {
   backface-visibility: $visibility;
  -webkit-backface-visibility: $visibility;
  -moz-backface-visibility: $visibility;
  -ms-backface-visibility: $visibility;
  -o-backface-visibility: $visibility;
}
```

### Mixin Facts
In general, here are 5 important facts about arguments and mixins:
* Mixins can take multiple arguments.
* Sass allows you to explicitly define each argument in your `@include` statement.
* When values are explicitly specified you can send them out of order.
* If a mixin definition has a combination of arguments with and without a default value, you should define the ones with no default value first.
* Mixins can be nested.
```
@mixin dashed-border($width, $color: #FFF) {
  border: {
     color: $color;
     width: $width;
     style: dashed;
  }
}

span { //only passes non-default argument
    @include dashed-border(3px);
}

p { //passes both arguments
    @include dashed-border(3px, green);
}

div { //passes out of order but explicitly defined
   @include dashed-border(color: purple, width: 5px); 
}
```

### List Arguments
Sass allows you to pass in multiple arguments in a list or a map format.
```
@mixin stripes($direction, $width-percent, $stripe-color, $stripe-background: #FFF) {
  background: repeating-linear-gradient(
    $direction,
    $stripe-background,
    $stripe-background ($width-percent - 1),
    $stripe-color 1%,
    $stripe-background $width-percent
  );
}
```
In this scenario, it makes sense to create a map with these properties in case we ever want to update or reference them.
```
$college-ruled-style: ( 
    direction: to bottom,
    width-percent: 15%,
    stripe-color: blue,
    stripe-background: white
);
```
When we include our mixin, we can then pass in these arguments in a map with the following `...` notation:
```
.definition {
      width: 100%;
      height: 100%;
      @include stripes($college-ruled-style...);
 }
 ```
 **OR**
 ```
 $stripe-properties: to bottom, 15%, blue, white;
 ----------
 .definition {
    @include stripes($stripe-properties...);
 }
 ```
 
### String Interpolation
In Sass, `string interpolation` is the process of placing a variable string in the middle of two other strings.

In a _mixin_ context, `interpolation` is handy when you want to make use of variables in selectors or file names. The notation is as follows:
```
@mixin photo-content($file) {
  content: url(#{$file}.jpg); //string interpolation
  object-fit: cover;
}

//....

.photo { 
  @include photo-content('titanosaur');
  width: 60%;
  margin: 0px auto; 
}
```
`String interpolation` would enable the following CSS:
```
.photo { 
  content: url(titanosaur.jpg);
  width: 60%;
  margin: 0px auto; 
}
```

### The _&_ Selector in Mixins
Sass allows **&** selector usage inside of mixins. 
* The **&** selector gets assigned the value of the parent at the point where the mixin is included.
* If there is no parent selector, then the value is _null_ and Sass will throw an error.
```
@mixin text-hover($color){
  &:hover {
      color: $color; 
  }
}
```
In the above, the value of the parent selector will be assigned based on the parent at the point where it is invoked.
```
.word { //SCSS: 
  display: block; 
  text-align: center;
  position: relative;
  top: 40%;
  @include text-hover(red);
}
```
The above will compile to the following CSS:
```
.word{ 
  display: block;
  text-align: center;
  position: relative;
  top: 40%;
}
.word:hover{
  color: red;
}
```
Notice that the mixin inherited the parent selector `.word` because that was the parent at the point where the _mixin_ was included.

## Functions in SCSS
**Functions** and **operations** in Sass allow for computing and iterating on styles. With Sass functions you can:
* Operate on color values
* Iterate on lists and maps
* Apply styles based on conditions
* Assign values that result from math operations
### Arithmetic and Color
As mentioned, Sass specifically comes equipped with functions that make working with colors easier.

The _alpha parameter_ in a color like RGBA or HSLA is a mask denoting opacity. It specifies how one color should be merged with another when the two are on top of each other.
* In Sass, the function `fade-out` makes a color more transparent by taking a number between 0 and 1 and decreasing opacity, or the alpha channel, by that amount:
```
$color: rgba(39, 39, 39, 0.5);
$amount: 0.1;
$color2: fade-out($color, $amount);//rgba(39, 39, 39, 0.4) 
```
* The `fade-in` color function changes a color by increasing its opacity:
```
$color: rgba(55,7,56, 0.5);
$amount: 0.1;
$color2: fade-in($color, $amount); //rgba(55,7,56, 0.6)
```
* The function `adjust-hue($color, $degrees)` changes the hue of a color by taking color and a number of degrees (_usually between -360 degrees and 360 degrees_), and rotate the color wheel by that amount.

### Color Functions
Sass also allows us to perform mathematical functions to compute measurements— including colors. Here is how Sass computes colors:
* The operation is performed on the red, green, and blue components.
* It computes the answer by operating on every two digits.
* Sass arithmetic can also compute HSLA and string colors such as red and blue.
```
$color: #010203 + #040506;

01 + 04 = 05
02 + 05 = 07
03 + 06 = 09

color: #050709;
```

### Arithmetic
The Sass arithmetic operations are:
* addition +
* subtraction -
* multiplication *
* division /: In CSS the `/` character can be used as a separator. In Sass, the character is also used in division. Here are the specific instances `/` counts as division:
  * If the value, or any part of it, is stored in a variable or returned by a function.
  * If the value is surrounded by parentheses, unless those parentheses are outside a list and the value is inside.
  * If the value is used as part of another arithmetic expression.
  ```
  width: $variable/6; //division
  line-height: (600px)/9; //division
  margin-left: 20-10 px/ 2; //division
  font-size: 10px/8px; //not division
  ```
* modulo %

**Notes**:
* SCSS arithmetic requires that the units are compatible; for example, you can’t multiply _pixels_ by _ems_.
* Just like in regular math, multiplying two units together results in squared units: `10px * 10px = 100px * px`. Since there is no such thing as squared units in CSS, the above would throw an error. You would need to multiply `10px * 10` in order to obtain `100px`.

### Each Loops
_Each loops_ in Sass iterate on each of the values on a list. The syntax is as follows:
```
@each $item in $list {
  //some rules and or conditions
}
```
The value of `$item` is dynamically assigned to the value of the object in the list according to its position and the iteration of the loop.
```
$list: (orange, purple, teal);

//Add your each-loop here
@each $item in $list {
  .#{$item} {
    background: $item;
  }
}
```

### For Loops
_For loops_ in Sass can be used to style numerous elements or assigning properties all at once. Sass’s for loop syntax is as follows:
```
@for $i from $begin through $end {
   //some rules and or conditions
}
```
* `$i` is just a variable for the index, or position of the element in the list
* `$begin` and `$end` are _placeholders_ for the start and end points of the loop.
* The keywords `through` and `to` are interchangeable in Sass
```
$total: 10; //Number of .ray divs in our html
$step: 360deg / $total; //Used to compute the hue based on color-wheel


.ray {
  height: 30px;
}

//Add your for-loop here:
@for $i from 1 through $total {
  .ray:nth-child(#{$i}) {
    background: adjust-hue(blue, $i * $step);
  }
}
```

### Conditionals
In Sass, `if()` is a function that can only branch one of two ways based on a condition. You can use it inline, to assign the value of a property:
```
width: if( $condition, $value-if-true, $value-if-false);
```
For cases with more than two outcomes, the `@if`, `@else-if`, and `@else` directives allow for more flexibility.
```
@mixin deck($suit) {
 @if($suit == hearts || $suit == spades){
   color: blue;
 }
 @else-if($suit == clovers || $suit == diamonds){
   color: red;
 }
 @else{
   //some rule
 }
}
```

## SUSTAINABLE SCSS
In addition to having a solid file structure, a big part of staying organized is `splitting up the logic into smaller manageable components`.

Sass extends the existing CSS `@import` rule to allow including other SCSS and Sass files.
* Typically, all imported SCSS files are imported into a main SCSS file which is then combined to make a single CSS output file.
* The `main/global` SCSS file has access to any variables or mixins defined in its imported files. The `@import` command takes a filename to import.

By default, `@import` looks for a Sass file in the same or otherwise specified directory but there are a few circumstances where it will behave just like a CSS `@import` rule:
* If the file’s extension is `.css`.
* If the filename begins with `http://`.
* If the filename is a `url()`.
* If the `@import` has any media queries.

In addition to keeping code organized, importing files can also save you from repeating code. For example, if multiple SCSS files reference the same variables, importing a file with variables partial would save the trouble of redefining them each time.

### Organize with Partials
_Partials_ in Sass are the files you split up to organize specific functionality in the codebase.
* They use a `_` prefix notation in the file name that tells Sass to hold off on compiling the file individually and instead import it. `_filename.scss`
* To import this partial into the main file - or the file that encapsulates the important rules and the bulk of the project styles - omit the underscore. For example, to import a file named `_variables.scss`, add the following line of code: `@import "variables";`.




















