# Shapes

Write a program that draws the following shapes on a canvas:

1. A trapezoid (a rectangle that is wider on one side)

2. A red diamond (a rectangle rotated 45 degrees or ¼π radians)

3. A zigzagging line

4. A spiral made up of 100 straight line segments

5. A yellow star

![Picture showing the shapes you are asked to draw](https://eloquentjavascript.net/img/exercise_shapes.png)

When drawing the last two shapes, you may want to refer to the explanation of `Math.cos` and `Math.sin` in [Chapter 14](https://eloquentjavascript.net/14_dom.html#sin_cos), which describes how to get coordinates on a circle using these functions.

I recommend creating a function for each shape. Pass the position, and optionally other properties such as the size or the number of points, as parameters. The alternative, which is to hardcode numbers all over your code, tends to make the code needlessly hard to read and modify.

```html
<canvas width="600" height="200"></canvas>
<script>
  let cx = document.querySelector("canvas").getContext("2d");

  // Your code here.
</script>
```

<details>
<summary>Hint</summary>

The trapezoid (1) is easiest to draw using a path. Pick suitable center coordinates and add each of the four corners around the center.

The diamond (2) can be drawn the straightforward way, with a path, or the interesting way, with a `rotate` transformation. To use rotation, you will have to apply a trick similar to what we did in the `flipHorizontally` function. Because you want to rotate around the center of your rectangle and not around the point (0, 0), you must first `translate` to there, then rotate, and then translate back.

Make sure you reset the transformation after drawing any shape that creates one.

For the zigzag (3) it becomes impractical to write a new call to `lineTo` for each line segment. Instead, you should use a loop. You can have each iteration draw either two line segments (right and then left again) or one, in which case you must use the evenness (`% 2`) of the loop index to determine whether to go left or right.

You'll also need a loop for the spiral (4). If you draw a series of points, with each point moving farther along a circle around the spiral's center, you get a circle. If, during the loop, you vary the radius of the circle on which you are putting the current point and go around more than once, the result is a spiral.

The star (5) depicted is built out of `quadraticCurveTo` lines. You could also draw one with straight lines. Divide a circle into eight pieces for a star with eight points, or however many pieces you want. Draw lines between these points, making them curve toward the center of the star. With `quadraticCurveTo`, you can use the center as the control point.

</details>

---

From [Eloquent JavaScript, Chapter 17: Drawing on Canvas](https://eloquentjavascript.net/17_canvas.html).
