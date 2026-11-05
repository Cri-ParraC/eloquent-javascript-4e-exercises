# The cat's hat

Extend the cat animation defined [earlier](https://eloquentjavascript.net/14_dom.html#animation) so that both the cat and his hat (`<img src="img/hat.png">`) orbit at opposite sides of the ellipse.

Or make the hat circle around the cat. Or alter the animation in some other interesting way.

To make positioning multiple objects easier, you'll probably want to switch to absolute positioning. This means that `top` and `left` are counted relative to the upper left of the document. To avoid using negative coordinates, which would cause the image to move outside of the visible page, you can add a fixed number of pixels to the position values.

```html
<style>body { min-height: 200px }</style>
<img src="img/cat.png" id="cat" style="position: absolute">
<img src="img/hat.png" id="hat" style="position: absolute">

<script>
  let cat = document.querySelector("#cat");
  let hat = document.querySelector("#hat");

  let angle = 0;
  let lastTime = null;
  function animate(time) {
    if (lastTime != null) angle += (time - lastTime) * 0.001;
    lastTime = time;
    cat.style.top = (Math.sin(angle) * 40 + 40) + "px";
    cat.style.left = (Math.cos(angle) * 200 + 230) + "px";

    // Your extensions here.

    requestAnimationFrame(animate);
  }
  requestAnimationFrame(animate);
</script>
```

<details>
<summary>Hint</summary>

`Math.cos` and `Math.sin` measure angles in radians, where a full circle is 2π. For a given angle, you can get the opposite angle by adding half of this, which is `Math.PI`. This can be useful for putting the hat on the opposite side of the orbit.

</details>

---

From [Eloquent JavaScript, Chapter 14: The Document Object Model](https://eloquentjavascript.net/14_dom.html).
