_from freecodecamp_

We saw earlier how spread operator can effectively spread, or unpack, the contents of the array.

We can do something similar with objects as well. `Destructuring assignment` is special syntax for neatly assigning values taken directly from an object to variables.

Consider the following ES5 code:
```
var voxel = {x: 3.6, y: 7.4, z: 6.54 };
var x = voxel.x; // x = 3.6
var y = voxel.y; // y = 7.4
var z = voxel.z; // z = 6.54
```


