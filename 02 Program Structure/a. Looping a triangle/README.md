# Looping a triangle

Write a loop that makes seven calls to `console.log` to output the following triangle:

```
#
##
###
####
#####
######
#######
```

It may be useful to know that you can find the length of a string by writing `.length` after it.

```js
let abc = "abc";
console.log(abc.length);
// → 3
```

Most exercises contain a piece of code that you can modify to solve the exercise. Remember that you can click code blocks to edit them.

```js
// Your code here.
```

<details>
<summary>Hint</summary>

You can start with a program that prints out the numbers 1 to 7, which you can derive by making a few modifications to the [even number printing example](https://eloquentjavascript.net/02_program_structure.html#loops) given earlier in the chapter, where the `for` loop was introduced.

Now consider the equivalence between numbers and strings of hash characters. You can go from 1 to 2 by adding 1 (`+= 1`). You can go from `"#"` to `"##"` by adding a character (`+= "#"`). Thus, your solution can closely follow the number-printing program.

</details>

---

From [Eloquent JavaScript, Chapter 2: Program Structure](https://eloquentjavascript.net/02_program_structure.html).
