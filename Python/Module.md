## Importing Local Scripts
If the Python script you want to import is in the same directory as your current script, you just type `import` followed by the name of the file, without the _.py_ extension.
```
import useful_functions
```
It's the standard convention for `import` statements to be written at the top of a Python script, each one on a separate line. This `import` statement creates a **module** object called `useful_functions`. Modules are just Python files that contain definitions and statements. To access objects from an imported module, you need to use _dot notation_.
```
import useful_functions
useful_functions.add_five([1, 2, 3, 4])
```
We can add an alias to an imported module to reference it with a different name.
```
import useful_functions as uf
uf.add_five([1, 2, 3, 4])
```

### Using a main block
To avoid running executable statements in a script when it's imported as a module in another script, include these lines in an `if __name__ == "__main__"` block. Or alternatively, include them in a function called `main()` and call this in the `if main` block.

Whenever we run a script like this, Python actually sets a special built-in variable called `__name__` for any module. When we run a script, Python recognizes this module as the main program, and sets the `__name__` variable for this module to the string `"__main__"`. For any modules that are imported in this script, this built-in `__name__` variable is just set to the name of that module. Therefore, the condition `if __name__ == "__main__"`is just checking whether this module is the main program.





