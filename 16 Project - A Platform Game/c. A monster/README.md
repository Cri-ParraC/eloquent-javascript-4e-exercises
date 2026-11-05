# A monster

It is traditional for platform games to have enemies that you can defeat by jumping on top of them. This exercise asks you to add such an actor type to the game.

We'll call this actor a monster. Monsters move only horizontally. You can make them move in the direction of the player, bounce back and forth like horizontal lava, or have any other movement pattern you want. The class doesn't have to handle falling, but it should make sure the monster doesn't walk through walls.

When a monster touches the player, the effect depends on whether the player is jumping on top of them or not. You can approximate this by checking whether the player's bottom is near the monster's top. If this is the case, the monster disappears. If not, the game is lost.

```html
<link rel="stylesheet" href="css/game.css">
<style>.monster { background: purple }</style>

<body>
  <script>
    // Complete the constructor, update, and collide methods
    class Monster {
      constructor(pos, /* ... */) {}

      get type() { return "monster"; }

      static create(pos) {
        return new Monster(pos.plus(new Vec(0, -1)));
      }

      update(time, state) {}

      collide(state) {}
    }

    Monster.prototype.size = new Vec(1.2, 2);

    levelChars["M"] = Monster;

    runLevel(new Level(`
..................................
.################################.
.#..............................#.
.#..............................#.
.#..............................#.
.#...........................o..#.
.#..@...........................#.
.##########..............########.
..........#..o..o..o..o..#........
..........#...........M..#........
..........################........
..................................
`), DOMDisplay);
  </script>
</body>
```

<details>
<summary>Hint</summary>

If you want to implement a type of motion that is stateful, such as bouncing, make sure you store the necessary state in the actor object—include it as a constructor argument and add it as a property.

Remember that `update` returns a _new_ object rather than changing the old one.

When handling collision, find the player in `state.actors` and compare its position to the monster's position. To get the _bottom_ of the player, you have to add its vertical size to its vertical position. The creation of an updated state will resemble either `Coin`'s `collide` method (removing the actor) or `Lava`'s (changing the status to `"lost"`), depending on the player position.

</details>

---

From [Eloquent JavaScript, Chapter 16: Project: A Platform Game](https://eloquentjavascript.net/16_game.html).
