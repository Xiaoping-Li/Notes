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
