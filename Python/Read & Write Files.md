## Reading a File
```
f = open('my_path/my_file.txt', 'r')
file_data = f.read()
f.close()
```
1. First open the file using the built-in function, `open`. This requires a string that shows the path to the file. The `open` function returns a file object, which is a Python object through which Python interacts with the file itself. Here, we assign this object to the variable `f`.
2. There are optional parameters you can specify in the `open` function. One is the mode in which we open the file. Here, we use `r` or _read only_. This is actually the default value for the mode argument.
3. Use the `read` method to access the contents from the file object. This `read` method takes the text contained in a file and puts it into a string. Here, we assign the string returned from this method into the variable `file_data`.
4. When finished with the file, use the `close` method to free up any system resources taken up by the file.
