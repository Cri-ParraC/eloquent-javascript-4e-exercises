# Real Promises

Rewrite the function from the previous exercise without `async`/`await`, using plain `Promise` methods.

```js
function activityTable(day) {
  // Your code here
}

activityTable(6)
  .then(table => console.log(activityGraph(table)));
```

In this style, using `Promise.all` will be more convenient than trying to model a loop over the logfiles. In the `async` function, just using `await` in a loop is simpler. If reading a file takes some time, which of these two approaches will take the least time to run?

If one of the files listed in the file list has a typo, and reading it fails, how does that failure end up in the `Promise` object that your function returns?

<details>
<summary>Hint</summary>

The most straightforward approach to writing this function is to use a chain of `then` calls. The first promise is produced by reading the list of logfiles. The first callback can split this list and map `textFile` over it to get an array of promises to pass to `Promise.all`. It can return the object returned by `Promise.all`, so that whatever that returns becomes the result of the return value of this first `then`.

We now have a promise that returns an array of logfiles. We can call `then` again on that, and put the timestamp-counting logic in there. Something like this:

```js
function activityTable(day) {
  return textFile("camera_logs.txt").then(files => {
    return Promise.all(files.split("\n").map(textFile));
  }).then(logs => {
    // analyze...
  });
}
```

Or you could, for even better work scheduling, put the analysis of each file inside of the `Promise.all`, so that that work can be started for the first file that comes back from disk, even before the other files come back.

```js
function activityTable(day) {
  let table = []; // init...
  return textFile("camera_logs.txt").then(files => {
    return Promise.all(files.split("\n").map(name => {
      return textFile(name).then(log => {
        // analyze...
      });
    }));
  }).then(() => table);
}
```

This shows that the way you structure your promises can have a real effect on the way the work is scheduled. A simple loop with `await` in it will make the process completely linear—it waits for each file to load before proceeding. `Promise.all` makes it possible for multiple tasks to conceptually be worked on at the same time, allowing them to make progress while files are still being loaded. This can be faster, but it also makes the order in which things will happen less predictable. In this case, we're only going to be incrementing numbers in a table, which isn't hard to do in a safe way. For other kinds of problems, it may be a lot more difficult.

When a file in the list doesn't exist, the promise returned by `textFile` will be rejected. Because `Promise.all` rejects if any of the promises given to it fail, the return value of the callback given to the first `then` will also be a rejected promise. That makes the promise returned by `then` fail, so the callback given to the second `then` isn't even called, and a rejected promise is returned from the function.

</details>

---

From [Eloquent JavaScript, Chapter 11: Asynchronous Programming](https://eloquentjavascript.net/11_async.html).
