<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Child Selectors</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to distinguish a descendant selector from a direct-child selector.

## Highlight the status message

Our status message should stand out from the instructions.

Try this rule:

```css
.game-panel p {
  background-color: #e0f2fe;
  padding: 8px;
}
```

Both paragraphs receive the style.

The space between `.game-panel` and `p` means:

> Select paragraphs anywhere inside `.game-panel`.

This is a **descendant selector**.

## Look at the nesting

The relevant HTML has this structure:

```html
<main class="game-panel">
  <p id="message">Ready to start.</p>

  <section class="instructions">
    <h2>How to play</h2>
    <p>Complete deliveries before the battery runs out.</p>
  </section>
</main>
```

The message paragraph is directly inside `<main>`.

The instructions paragraph is directly inside `<section>`. It is also a descendant of `<main>`, but it is not its direct child.

## Select one level down

Replace the previous selector with:

```css
.game-panel > p {
  background-color: #e0f2fe;
  padding: 8px;
}
```

The `>` means **direct child**. Only the message paragraph matches this selector. [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/Child_combinator?utm_source=chatgpt.com)

| Selector | What it selects |
| --- | --- |
| `.game-panel p` | Paragraphs anywhere inside the panel |
| `.game-panel > p` | Paragraphs directly inside the panel |

This is useful for nested menus, cards containing other cards, and layouts with several levels of content.

> 💡 Use an ID or class when you want to identify a particular element. Use a child selector when the relationship between elements is what matters.

## 🎓 You Do

Give the paragraph directly inside `.instructions` a dashed border. Begin your selector with `.instructions >`.
