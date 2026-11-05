# A JavaScript workbench

Build an interface that allows users to type and run pieces of JavaScript code.

Put a button next to a `<textarea>` field that, when pressed, uses the `Function` constructor we saw in [Chapter 10](https://eloquentjavascript.net/10_modules.html#eval) to wrap the text in a function and call it. Convert the return value of the function, or any error it raises, to a string and display it below the text field.

```html
<textarea id="code">return "hi";</textarea>
<button id="button">Run</button>
<pre id="output"></pre>

<script>
  // Your code here.
</script>
```

<details>
<summary>Hint</summary>

Use `document.querySelector` or `document.getElementById` to get access to the elements defined in your HTML. An event handler for `"click"` or `"mousedown"` events on the button can get the `value` property of the text field and call `Function` on it.

Make sure you wrap both the call to `Function` and the call to its result in a `try` block so you can catch the exceptions it produces. In this case, we really don't know what type of exception we are looking for, so catch everything.

The `textContent` property of the output element can be used to fill it with a string message. Or, if you want to keep the old content around, create a new text node using `document.createTextNode` and append it to the element. Remember to add a newline character to the end so that not all output appears on a single line.

</details>

---

From [Eloquent JavaScript, Chapter 18: HTTP and Forms](https://eloquentjavascript.net/18_http.html).
