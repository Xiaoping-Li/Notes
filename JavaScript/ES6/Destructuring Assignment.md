_from freecodecamp_

## Use Destructuring Assignment to Assign Variables from Objects

We saw earlier how spread operator can effectively spread, or unpack, the contents of the array.

We can do something similar with objects as well. `Destructuring assignment` is special syntax for neatly assigning values taken directly from an object to variables.

Consider the following ES5 code:
```
var voxel = {x: 3.6, y: 7.4, z: 6.54 };
var x = voxel.x; // x = 3.6
var y = voxel.y; // y = 7.4
var z = voxel.z; // z = 6.54
```

Here's the same assignment statement with ES6 destructuring syntax:
```
const { x, y, z } = voxel; // x = 3.6, y = 7.4, z = 6.54
```
If instead you want to store the values of `voxel.x` into `a`, `voxel.y` into `b`, and `voxel.z` into `c`, you have that freedom as well.
```
const { x : a, y : b, z : c } = voxel // a = 3.6, b = 7.4, c = 6.54
```
You may read it as `"get the field x and copy the value into a,"` and so on.


## Use Destructuring Assignment to Assign Variables from Nested Objects

We can similarly destructure nested objects into variables.

Consider the following code:
```
const a = {
  start: { x: 5, y: 6},
  end: { x: 6, y: -9 }
};
const { start : { x: startX, y: startY }} = a;
console.log(startX, startY); // 5, 6
```
In the example above, the variable `start` is assigned the value of `a.start`, which is also an object.


## Use Destructuring Assignment to Assign Variables from Arrays

ES6 makes destructuring arrays as easy as destructuring objects.

One key difference between the `spread operator` and `array destructuring` is that the `spread operator` unpacks all contents of an array into a comma-separated list. Consequently, you cannot pick or choose which elements you want to assign to variables.

`Destructuring` an array lets us do exactly that:
```
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b); // 1, 2
```
The variable `a` is assigned the first value of the array, and `b` is assigned the second value of the array.

We can also access the value at any index in an array with destructuring by using commas to reach the desired index:
```
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c); // 1, 2, 5
```
