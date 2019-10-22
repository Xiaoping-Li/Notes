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


## Writing to a File
```
f = open('my_path/my_file.txt', 'w')
f.write("Hello there!")
f.close()
```
1. Open the file in writing (`'w'`) mode. If the file does not exist, Python will create it for you. If you open an existing file in writing mode, any content that it had contained previously will be deleted. If you're interested in adding to an existing file, without deleting its content, you should use the append (`'a'`) mode instead of write.
2. Use the write method to add text to the file.
3. Close the file when finished.



