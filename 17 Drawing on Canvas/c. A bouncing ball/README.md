# A bouncing ball

Use the `requestAnimationFrame` technique that we saw in [Chapter 14](https://eloquentjavascript.net/14_dom.html#animationFrame) and [Chapter 16](https://eloquentjavascript.net/16_game.html#runAnimation) to draw a box with a bouncing ball in it. The ball moves at a constant speed and bounces off the box's sides when it hits them.

```html
<canvas width="400" height="400"></canvas>
<script>
  let cx = document.querySelector("canvas").getContext("2d");

  let lastTime = null;
  function frame(time) {
    if (lastTime != null) {
      updateAnimation(Math.min(100, time - lastTime) / 1000);
    }
    lastTime = time;
    requestAnimationFrame(frame);
  }
  requestAnimationFrame(frame);

  function updateAnimation(step) {
    // Your code here.
  }
</script>
```

<details>
<summary>Hint</summary>

A box is easy to draw with `strokeRect`. Define a binding that holds its size, or define two bindings if your box's width and height differ. To create a round ball, start a path and call `arc(x, y, radius, 0, 7)`, which creates an arc going from zero to more than a whole circle. Then fill the path.

To model the ball's position and speed, you can use the `Vec` class from [Chapter 16](https://eloquentjavascript.net/16_game.html#vector). Give it a starting speed, preferably one that is not purely vertical or horizontal, and for every frame multiply that speed by the amount of time that elapsed. When the ball gets too close to a vertical wall, invert the _x_ component in its speed. Likewise, invert the _y_ component when it hits a horizontal wall.

After finding the ball's new position and speed, use `clearRect` to delete the scene and redraw it using the new position.

</details>

---

From [Eloquent JavaScript, Chapter 17: Drawing on Canvas](https://eloquentjavascript.net/17_canvas.html).
