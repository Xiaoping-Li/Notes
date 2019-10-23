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


## Techniques for Importing Modules
1. To import an individual function or class from a module:
```
from module_name import object_name
```
2. To import multiple individual objects from a module:
```
from module_name import first_object, second_object
```
3. To rename a module:
```
import module_name as new_name
```
4. To import an object from a module and rename it:
```
from module_name import object_name as new_name
```
5. To import every object individually from a module (DO NOT DO THIS):
```
from module_name import *
```
6. If you really want to use all of the objects from a module, use the standard import module_name statement instead and access each of the objects with the dot notation.
```
import module_name
```

### Modules, Packages, and Names
In order to manage the code better, modules in the Python Standard Library are split down into sub-modules that are contained within a package. A **package** is simply a module that contains sub-modules. A sub-module is specified with the usual dot notation.

Modules that are submodules are specified by the package name and then the submodule name separated by a dot. You can import the submodule like this.
```
import package_name.submodule_name
```

## Third-Party Libraries
There are tens of thousands of third-party libraries written by independent developers! You can install them using `pip`, a package manager that is included with Python 3. pip is the standard package manager for Python, but it isn't the only one. One popular alternative is `Anaconda` which is designed specifically for data science.

To install a package using pip, just enter "pip install" followed by the name of the package in your command line like this: `pip install package_name`. This downloads and installs the package so that it's available to import in your programs. 
* Once installed, you can import third-party packages using the same syntax used to import from the standard library.
* It's standard practice to put the import statements for third-party libraries after imports from the standard library.

### Using a `requirements.txt` File
Larger Python programs might depend on dozens of third party packages. To make it easier to share these programs, programmers often list a project's dependencies in a file called `requirements.txt`. This is an example of a _requirements.txt_ file.
```
beautifulsoup4==4.5.1
bs4==0.0.1
pytz==2016.7
requests==2.11.1
```
Each line of the file includes the name of a package and its version number. The version number is optional, but it usually should be included. Libraries can change subtly, or dramatically, between versions, so it's important to use the same library versions that the program's author used when they wrote the program.

You can use pip to install all of a project's dependencies at once by typing `pip install -r requirements.txt` in your command line.

## Useful Third-Party Packages
Being able to install and import third party libraries is useful, but to be an effective programmer you also need to know what libraries are available for you to use. People typically learn about useful new libraries from online recommendations or from colleagues. If you're a new Python programmer you may not have many colleagues, so to get you started here's a list of packages that are popular with engineers at Udacity.

* [IPython](https://ipython.org/) - A better interactive Python interpreter
* **requests** - Provides easy to use methods to make web requests. Useful for accessing web APIs.
* [Flask](https://palletsprojects.com/p/flask/) - a lightweight framework for making web applications and APIs.
* [Django](https://www.djangoproject.com/) - A more featureful framework for making web applications. Django is particularly good for designing complex, content heavy, web applications.
* [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/) - Used to parse HTML and extract information from it. Great for web scraping.
* [pytest](http://doc.pytest.org/en/latest/) - extends Python's builtin assertions and unittest module.
* [PyYAML](https://pyyaml.org/wiki/PyYAML) - For reading and writing [YAML](https://en.wikipedia.org/wiki/YAML) files.
* [NumPy](https://numpy.org/) - The fundamental package for scientific computing with Python. It contains among other things a powerful N-dimensional array object and useful linear algebra capabilities.
* [pandas](https://pandas.pydata.org/) - A library containing high-performance, data structures and data analysis tools. In particular, pandas provides dataframes!
* [matplotlib](https://matplotlib.org/) - a 2D plotting library which produces publication quality figures in a variety of hardcopy formats and interactive environments.
* [ggplot](http://ggplot.yhathq.com/) - Another 2D plotting library, based on R's ggplot2 library.
* [Pillow](https://python-pillow.org/) - The Python Imaging Library adds image processing capabilities to your Python interpreter.
* [pyglet](http://pyglet.org/) - A cross-platform application framework intended for game development.
* [Pygame](https://www.pygame.org/news) - A set of Python modules designed for writing games.
* [pytz](http://pytz.sourceforge.net/) - World Timezone Definitions for Python
