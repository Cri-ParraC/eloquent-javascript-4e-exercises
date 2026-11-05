# Roads module

Write an ES module based on the example from [Chapter 7](https://eloquentjavascript.net/07_robot.html) that contains the array of roads and exports the graph data structure representing them as `roadGraph`. It depends on a module `./graph.js` that exports a function `buildGraph`, used to build the graph. This function expects an array of two-element arrays (the start and end points of the roads).

```js
// Add dependencies and exports

const roads = [
  "Alice's House-Bob's House",   "Alice's House-Cabin",
  "Alice's House-Post Office",   "Bob's House-Town Hall",
  "Daria's House-Ernie's House", "Daria's House-Town Hall",
  "Ernie's House-Grete's House", "Grete's House-Farm",
  "Grete's House-Shop",          "Marketplace-Farm",
  "Marketplace-Post Office",     "Marketplace-Shop",
  "Marketplace-Town Hall",       "Shop-Town Hall"
];
```

<details>
<summary>Hint</summary>

Since this is an ES module, you have to use `import` to access the graph module. That was described as exporting a `buildGraph` function, which you can pick out of its interface object with a destructuring `const` declaration.

To export `roadGraph`, you put the keyword `export` before its definition. Because `buildGraph` takes a data structure that doesn't precisely match `roads`, the splitting of the road strings must happen in your module.

</details>

---

From [Eloquent JavaScript, Chapter 10: Modules](https://eloquentjavascript.net/10_modules.html).
