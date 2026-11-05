# Reversing an array

Arrays have a `reverse` method that changes the array by inverting the order in which its elements appear. For this exercise, write two functions, `reverseArray` and `reverseArrayInPlace`. The first, `reverseArray`, should take an array as its argument and produce a _new_ array that has the same elements in the inverse order. The second, `reverseArrayInPlace`, should do what the `reverse` method does: _modify_ the array given as its argument by reversing its elements. Neither may use the standard `reverse` method.

Thinking back to the notes about side effects and pure functions in the [previous chapter](https://eloquentjavascript.net/03_functions.html#pure), which variant do you expect to be useful in more situations? Which one runs faster?

```js
// Your code here.

let myArray = ["A", "B", "C"];
console.log(reverseArray(myArray));
// → ["C", "B", "A"];
console.log(myArray);
// → ["A", "B", "C"];
let arrayValue = [1, 2, 3, 4, 5];
reverseArrayInPlace(arrayValue);
console.log(arrayValue);
// → [5, 4, 3, 2, 1]
```

<details>
<summary>Hint</summary>

There are two obvious ways to implement `reverseArray`. The first is to simply go over the input array from front to back and use the `unshift` method on the new array to insert each element at its start. The second is to loop over the input array backward and use the `push` method. Iterating over an array backward requires a (somewhat awkward) `for` specification, like `(let i = array.length - 1; i >= 0; i--)`.

Reversing the array in place is harder. You have to be careful not to overwrite elements that you will later need. Using `reverseArray` or otherwise copying the whole array (`array.slice()` is a good way to copy an array) works but is cheating.

The trick is to _swap_ the first and last elements, then the second and second-to-last, and so on. You can do this by looping over half the length of the array (use `Math.floor` to round down—you don't need to touch the middle element in an array with an odd number of elements) and swapping the element at position `i` with the one at position `array.length - 1 - i`. You can use a local binding to briefly hold onto one of the elements, overwrite that one with its mirror image, and then put the value from the local binding in the place where the mirror image used to be.

</details>

---

From [Eloquent JavaScript, Chapter 4: Data Structures: Objects and Arrays](https://eloquentjavascript.net/04_data.html).
