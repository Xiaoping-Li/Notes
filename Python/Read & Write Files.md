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

### Calling the read Method with an Integer
In the code you saw earlier, the call to `f.read()` had no arguments passed to it. This defaults to reading all the remainder of the file from its current position - the whole file. If you pass the `read` method an integer argument, it will read up to that number of characters, output all of them, and keep the _'window'_ at that position ready to read on.

Let's see this in an example that uses the following file, `camelot.txt`:
```
We're the knights of the round table
We dance whenever we're able
```
Here's a script that reads in the file a little at a time by passing an integer argument to `.read()`.
```
with open("camelot.txt") as song:
    print(song.read(2))
    print(song.read(8))
    print(song.read())
```
Outputs:
```
We
're the 
knights of the round table
We dance whenever we're able
```
Each time we called `read` on the file with an integer argument, it read up to that number of characters, outputted them, and kept the 'window' at that position for the next call to `read`. This makes moving around in the open file a little tricky, as there aren't many landmarks to navigate by.

## Writing to a File
```
f = open('my_path/my_file.txt', 'w')
f.write("Hello there!")
f.close()
```
1. Open the file in writing (`'w'`) mode. If the file does not exist, Python will create it for you. If you open an existing file in writing mode, any content that it had contained previously will be deleted. If you're interested in adding to an existing file, without deleting its content, you should use the append (`'a'`) mode instead of write.
2. Use the write method to add text to the file.
3. Close the file when finished.

## With
Python provides a special syntax that auto-closes a file for you once you're finished using it.
```
with open('my_path/my_file.txt', 'r') as f:
    file_data = f.read()
```
This `with` keyword allows you to open a file, do operations on it, and automatically close it after the indented code is executed, in this case, reading from the file. Now, we don’t have to call `f.close()`! You can only access the file object, `f`, within this indented block.
