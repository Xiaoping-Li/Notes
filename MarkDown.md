## Headers
You can write headers using the `pound/hash/octothorpe` symbol `#` placed before the text. One `#` renders as an h1 header, two `##` is an h2, and so on. Looks like this:
```
# Header 1
## Header 2
### Header 3
```

## Links
Linking in Markdown is done by _enclosing text in square brackets and the URL in parentheses_, like this `[Udacity's home page](https://www.udacity.com)` for a link to Udacity's home page.

You can add emphasis through _bold_ or _italics_ with asterisks or underscores (`*` or `_`). For italics, wrap the text in one asterisk or underscore, `_gelato_` or `*gelato*` renders as gelato.

Bold text uses _two_ symbols, `**aardvark**` or `__aardvark__` looks like aardvark.

Either asterisks or underscores are fine as long as you use the same symbol on both sides of the text.

## Code
There are two different ways to display code: 
* Inline with text. To format inline code, wrap the text in backticks. For example, `string.punctuation`.  
* As a code block separated from the text. To create a code block, start a new line and wrap the text in _three backticks_.
  ```
  import requests
  response = requests.get('https://www.udacity.com')
  ```
  or indent each line of the code block with four spaces.
    import requests
    response = requests.get('https://www.udacity.com')



