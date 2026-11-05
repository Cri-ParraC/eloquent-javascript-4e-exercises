# Conway's Game of Life

Conway's Game of Life is a simple simulation that creates artificial "life" on a grid, each cell of which is either alive or not. In each generation (turn), the following rules are applied:

* Any live cell with fewer than two or more than three live   neighbors dies.

* Any live cell with two or three live neighbors lives on to the next   generation.

* Any dead cell with exactly three live neighbors becomes a live cell.

A _neighbor_ is defined as any adjacent cell, including diagonally adjacent ones.

Note that these rules are applied to the whole grid at once, not one square at a time. That means the counting of neighbors is based on the situation at the start of the generation, and changes happening to neighbor cells during this generation should not influence the new state of a given cell.

Implement this game using whichever data structure you find appropriate. Use `Math.random` to populate the grid with a random pattern initially. Display it as a grid of checkbox fields, with a button next to it to advance to the next generation. When the user checks or unchecks the checkboxes, their changes should be included when computing the next generation.

```html
<div id="grid"></div>
<button id="next">Next generation</button>

<script>
  // Your code here.
</script>
```

<details>
<summary>Hint</summary>

To solve the problem of having the changes conceptually happen at the same time, try to see the computation of a generation as a pure function, which takes one grid and produces a new grid that represents the next turn.

Representing the matrix can be done with a single array of width × height elements, storing values row by row, so, for example, the third element in the fifth row is (using zero-based indexing) stored at position 4 × _width_ + 2. You can count live neighbors with two nested loops, looping over adjacent coordinates in both dimensions. Take care not to count cells outside of the field and to ignore the cell in the center, whose neighbors we are counting.

Ensuring that changes to checkboxes take effect on the next generation can be done in two ways. An event handler could notice these changes and update the current grid to reflect them, or you could generate a fresh grid from the values in the checkboxes before computing the next turn.

If you choose to go with event handlers, you might want to attach attributes that identify the position that each checkbox corresponds to so that it is easy to find out which cell to change.

To draw the grid of checkboxes, you can either use a `<table>` element (see [Chapter 14](https://eloquentjavascript.net/14_dom.html#exercise_table)) or simply put them all in the same element and put `<br>` (line break) elements between the rows.

</details>

---

From [Eloquent JavaScript, Chapter 18: HTTP and Forms](https://eloquentjavascript.net/18_http.html).
