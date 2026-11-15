<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Button States</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to give buttons useful visual feedback with pseudo-classes.

## Give the buttons a starting appearance

Add this rule:

```css
.action-button {
  padding: 12px 16px;
  border: none;
  border-radius: 6px;
  background-color: #0f766e;
  color: white;
  cursor: pointer;
}
```

These are the buttons’ normal styles.

A **pseudo-class** lets us apply styles when an element meets a condition, such as being hovered over or disabled.

## Show when the pointer is over a button

Add:

```css
.action-button:hover {
  background-color: #115e59;
}
```

Move your pointer over **Start shift**.

The color change gives immediate feedback that the button is interactive. This is a common pattern for navigation links, shopping-cart buttons, and game controls.

CSS handles this appearance change without a JavaScript event listener.

## Show a button being pressed

Add:

```css
.action-button:active {
  background-color: #134e4a;
}
```

Press and hold the button briefly.

`:active` applies during activation, such as while the mouse button is held down. It does not remember that the player selected something earlier. [developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:active)

For a lasting game state, such as a selected card, we would store that state in JavaScript and update the display.

## Show keyboard focus

A player may use the keyboard to move between controls.

Add:

```css
.action-button:focus-visible {
  outline: 3px solid #1d4ed8;
  outline-offset: 3px;
}
```

Press **Tab** to move focus to a button.

The outline identifies the control that will receive keyboard input. `:focus-visible` applies when the browser determines that a visible focus indicator is needed, commonly during keyboard navigation. [developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:focus-visible)

`outline-offset` leaves space between the button and its outline.

## Show an unavailable action

Our **Reset shift** button already has the HTML `disabled` attribute. Before a shift starts, there is nothing to reset.

Add:

```css
.action-button:disabled {
  background-color: #e2e8f0;
  border-color: #64748b;
  color: #475569;
  cursor: not-allowed;
}
```

The attribute disables the button. The CSS makes that state easier to recognize.

Changing a button’s color alone would not disable it. [developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:disabled)


<!-- 
## Restrict hover and pressed styles to available buttons

A disabled button can still have a pointer over it. We only want our interaction colors on enabled buttons.

Change the earlier hover selector to:

```css
.action-button:enabled:hover {
  background-color: #115e59;
}
```

Change the earlier active selector to:

```css
.action-button:enabled:active {
  background-color: #134e4a;
}
```

Read the first selector as:

> Select an action button that is enabled **and** hovered.

These replace the earlier hover and active rules. -->

## Connect the states to JavaScript

In `js/app.js`, select the controls separately:

```js
const startButtonEl = document.querySelector('#start')
const resetButtonEl = document.querySelector('#reset')
const messageEl = document.querySelector('#message')

console.log(startButtonEl, resetButtonEl, messageEl)
```

Starting a shift should make **Reset shift** available and prevent another start.

Add:

```js
startButtonEl.addEventListener('click', () => {
  startButtonEl.disabled = true
  resetButtonEl.disabled = false
  messageEl.textContent = 'Your shift has started.'
})
```

The `disabled` property accepts a Boolean. CSS automatically responds when that property changes.

## 🎓 You Do
Resetting should restore the starting interface.  Add an event listener to the `reset` button.  It should do the following:

- Make the `start` button clickable again (enable it).
- Disable the `reset` button.
- Change the `message` text back to: 'Ready to start.'

<!-- ```js
resetButtonEl.addEventListener('click', () => {
  startButtonEl.disabled = false;
  resetButtonEl.disabled = true;
  messageEl.textContent = 'Ready to start.';
});
``` -->

> 💡 Keep important labels and instructions visible without hovering. Players using touchscreens may have no hover interaction.


## Bonus `pseudo-classes`.  Try these on your own:

| Pseudo-class | Useful for | Independent challenge |
| --- | --- | --- |
| `:checked` | Checked checkboxes and selected radio buttons, such as sound settings or difficulty choices | Add a **Sound effects** checkbox. Give it a colored outline only when checked. |
| `:nth-child()` | Styling particular items or repeating patterns | Give every second game tile a different background using `.tile:nth-child(even)`. Experiment with `odd` and `3`. |

📖 [MDN pseudo-class reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-classes)