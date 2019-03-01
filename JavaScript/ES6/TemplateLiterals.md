# Template Literals

Template literals (formerly known as _template strings_) are string literals that allow for embedded expressions. We typically use them to _express strings spanning multiple lines_ or _for string interpolation_, which essentially allows us to create a template with one or more placeholders for inserting variable text at a later time.

While traditional strings are wrapped in single or double quotes, template literals are wrapped in backtick (\`) characters. A template literal can contain placeholders, which are preceded by a dollar sign (`$`) and wrapped in curly braces (`{}`). For example, in the template literal \``${expression}`\`, the text `expression` between the placeholders is passed to a function. The default function simply concatenates the template literal's parts into a single string.

Any time we see an expression preceding a template literal, we call the expression a _tag_ and the template string a _tagged template literal_. In these instances, we call the tag expression (typically a function) with the processed template literal, which we can then manipulate before outputting the final string.
