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
* In Sass, a **mixin** lets you make groups of CSS declarations that you want to reuse throughout your site. Mixin names and all other Sass identifiers use hyphens and underscores interchangeably. Mixins also have the ability to take in a value. An _argument_, or _parameter_, is a value passed to the mixin that will be used inside the mixin. 

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
* Mixin arguments can be assigned a **_default value_** in the mixin definition by using a special notation.

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
* **Mixin Facts**: In general, here are 5 important facts about arguments and mixins:
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
* List Arguments: Sass allows you to pass in multiple arguments in a list or a map format.
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
 
 * **String Interpolation**






