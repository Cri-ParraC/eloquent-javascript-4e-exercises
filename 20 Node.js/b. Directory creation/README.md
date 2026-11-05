# Directory creation

Though the `DELETE` method in our file server is able to delete directories (using `rmdir`), the server currently does not provide any way to _create_ a directory.

Add support for the `MKCOL` method ("make collection"), which should create a directory by calling `mkdir` from the `node:fs` module. `MKCOL` is not a widely used HTTP method, but it does exist for this same purpose in the _WebDAV_ standard, which specifies a set of conventions on top of HTTP that make it suitable for creating documents.

<details>
<summary>Hint</summary>

You can use the function that implements the `DELETE` method as a blueprint for the `MKCOL` method. When no file is found, try to create a directory with `mkdir`. When a directory exists at that path, you can return a 204 response so that directory creation requests are idempotent. If a nondirectory file exists here, return an error code. Code 400 ("bad request") would be appropriate.

</details>

---

From [Eloquent JavaScript, Chapter 20: Node.js](https://eloquentjavascript.net/20_node.html).
