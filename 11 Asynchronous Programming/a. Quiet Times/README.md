# Quiet Times

There's a security camera near Carla's lab that's activated by a motion sensor. It is connected to the network and starts sending out a video stream when it is active. Because she'd rather not be discovered, Carla has set up a system that notices this kind of wireless network traffic and turns on a light in her lair whenever there is activity outside, so she knows when to keep quiet.

She's also been logging the times at which the camera is tripped for a while and wants to use this information to visualize which times, in an average week, tend to be quiet and which tend to be busy. The log is stored in files holding one time stamp number (as returned by `Date.now()`) per line.

```
1695709940692
1695701068331
1695701189163
```

The `"camera_logs.txt"` file holds a list of logfiles. Write an asynchronous function `activityTable(day)` that for a given day of the week returns an array of 24 numbers, one for each hour of the day, that hold the number of camera network traffic observations seen in that hour of the day. Days are identified by number using the system used by `Date.getDay`, where Sunday is 0 and Saturday is 6.

The `activityGraph` function, provided by the sandbox, summarizes such a table into a string.

To read the files, use the `textFile` function defined earlier—given a filename, it returns a promise that resolves to the file's content. Remember that `new Date(timestamp)` creates a `Date` object for that time, which has `getDay` and `getHours` methods returning the day of the week and the hour of the day.

Both types of files—the list of logfiles and the logfiles themselves—have each piece of data on its own line, separated by newline (`"\n"`) characters.

```js
async function activityTable(day) {
  let logFileList = await textFile("camera_logs.txt");
  // Your code here
}

activityTable(1)
  .then(table => console.log(activityGraph(table)));
```

<details>
<summary>Hint</summary>

You will need to convert the content of these files to an array. The easiest way to do that is to use the `split` method on the string produced by `textFile`. Note that for the logfiles, that will still give you an array of strings, which you have to convert to numbers before passing them to `new Date`.

Summarizing all the time points into a table of hours can be done by creating a table (array) that holds a number for each hour in the day. You can then loop over all the timestamps (over the logfiles and the numbers in every logfile) and for each one, if it happened on the correct day, take the hour it occurred in, and add one to the corresponding number in the table.

Make sure you use `await` on the result of asynchronous functions before doing anything with it, or you'll end up with a `Promise` where you expected a string.

</details>

---

From [Eloquent JavaScript, Chapter 11: Asynchronous Programming](https://eloquentjavascript.net/11_async.html).
