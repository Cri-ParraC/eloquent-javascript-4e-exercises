# Content negotiation

One of the things HTTP can do is called _content negotiation_. The `Accept` request header is used to tell the server what type of document the client would like to get. Many servers ignore this header, but when a server knows of various ways to encode a resource, it can look at this header and send the one that the client prefers.

The URL [_https://eloquentjavascript.net/author_](https://eloquentjavascript.net/author) is configured to respond with either plaintext, HTML, or JSON, depending on what the client asks for. These formats are identified by the standardized _media types_ `text/plain`, `text/html`, and `application/json`.

Send requests to fetch all three formats of this resource. Use the `headers` property in the options object passed to `fetch` to set the header named `Accept` to the desired media type.

Finally, try asking for the media type `application/rainbows+unicorns` and see which status code that produces.

```js
// Your code here.
```

<details>
<summary>Hint</summary>

Base your code on the `fetch` examples [earlier in the chapter](https://eloquentjavascript.net/18_http.html#fetch).

Asking for a bogus media type will return a response with code 406, "Not acceptable", which is the code a server should return when it can't fulfill the `Accept` header.

</details>

---

From [Eloquent JavaScript, Chapter 18: HTTP and Forms](https://eloquentjavascript.net/18_http.html).
