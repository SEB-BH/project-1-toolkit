<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">A Simple Grid</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to arrange elements in equal columns with CSS Grid.

## Arrange a set of items

Games often need a collection of tiles or cards. Other websites use similar layouts for products, bookings, or dashboard panels.

Inside `<main>`, after the instructions section, add:

```html
<h2>Route preview</h2>

<div class="board">
  <button class="tile" type="button">1</button>
  <button class="tile" type="button">2</button>
  <button class="tile" type="button">3</button>
  <button class="tile" type="button">4</button>
  <button class="tile" type="button">5</button>
  <button class="tile" type="button">6</button>
</div>
```

These buttons represent places on a future game board. For now, we are practising their arrangement.

Give the tiles a visible shape:

```css
.tile {
  min-height: 4rem;
  border: 2px solid #0f766e;
  background-color: white;
  color: #134e4a;
}
```

## Make the parent control the arrangement

Add:

```css
.board {
  display: grid;
}
```

`.board` is now a **grid container**. Its direct children become grid items.

We have enabled Grid, but we have not asked for multiple columns yet.

## Create three columns

Inside `.board`, add:

```css
grid-template-columns: 1fr 1fr 1fr;
```

Each `1fr` requests one share of the available space.

For these tiles, three equal shares produce three equal columns. The browser places the remaining tiles on the next row. [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/grid-template-columns?utm_source=chatgpt.com)

## Separate the tiles

Inside the same rule, add:

```css
gap: 0.5rem;
```

`gap` creates space between rows and columns.

The complete layout rule is:

```css
.board {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 0.5rem;
}
```

The parent controls the arrangement. The `.tile` rule controls each tile’s appearance.

## 🎓 You Do

Change the board to two equal columns. Then increase the gap to `1rem` and observe how the browser rearranges the same six buttons.

## Apply this to your project

Choose two tools from today that would help your planned game. Identify the element you would apply each tool to and the problem it would solve.

For example:

> “I will use `:disabled` on the submit button after a player finishes their turn.”
