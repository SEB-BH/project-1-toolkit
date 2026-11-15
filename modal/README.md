Here’s the **new modal section** in copyable Markdown. Place it after Grid as a **10–15 minute extension**. It uses the browser’s built-in `<dialog>` element, including Escape-to-close support. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog?utm_source=chatgpt.com)

````md
<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Game Instructions Modal</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to open and close an instructions modal using HTML and JavaScript.

## Show instructions when players need them

Players need to understand the rules, but instructions can take up space on the game page.

We can place them inside a **modal**: a panel that appears over the page. While it is open, the player interacts with that panel before returning to the game.

Websites also use modals for tasks such as confirming a booking or changing settings.

We will use HTML’s `<dialog>` element to build one.

## 1. Add a button to request instructions

In `index.html`, add this button inside `.controls`, after the Reset shift button:

```html
<button class="action-button" id="open-instructions" type="button">
  How to play
</button>
```

The existing `.action-button` styles already give it the same appearance as our other controls.

The button is visible, but clicking it does nothing yet.

## 2. Put the instructions inside a dialog

Find the existing `<section class="instructions">`.

Replace that entire section, including its opening and closing tags, with:

```html
<dialog
  class="instructions"
  id="instructions-modal"
  aria-labelledby="instructions-title"
>
  <h2 id="instructions-title">How to play</h2>

  <p>Complete deliveries before the battery runs out.</p>
  <p>Select Start shift to begin. Use Reset shift to start again.</p>

  <button class="action-button" id="close-instructions" type="button">
    Close instructions
  </button>
</dialog>
```

The instructions and close button are now inside the dialog.

`aria-labelledby` connects the dialog to its heading so that screen readers can identify its title.

Refresh the page. The instructions have disappeared because a `<dialog>` is hidden until we open it.

## 3. Select the elements we need

We need JavaScript references to three elements:

- The button that opens the instructions.
- The dialog containing the instructions.
- The button that closes the instructions.

In `js/app.js`, add these variables below your existing element selections:

```js
const openInstructionsButtonEl = document.querySelector('#open-instructions');
const instructionsModalEl = document.querySelector('#instructions-modal');
const closeInstructionsButtonEl = document.querySelector('#close-instructions');
```

> 🧠 Temporarily use `console.dir(instructionsModalEl)` to check the selection. If it shows `null`, compare the selector with the HTML element’s ID.

## 4. Open the instructions

We already know how to listen for a button click. This time, the response will be to open the dialog.

Below your existing event listeners, add:

```js
openInstructionsButtonEl.addEventListener('click', () => {
  instructionsModalEl.showModal();
});
```

`.showModal()` is a method available on dialog elements.

It displays the dialog above the page and prevents the player from interacting with the page behind it.

Refresh and click **How to play**. The browser displays the dialog in the center of the screen.

Press **Escape** to close it for now.

## 5. Make the close button work

The close button needs its own event listener.

Add:

```js
closeInstructionsButtonEl.addEventListener('click', () => {
  instructionsModalEl.close();
});
```

`.close()` hides the dialog so the player can use the page again.

We now have a small, repeatable pattern:

| Player action | JavaScript response |
| --- | --- |
| Click How to play | `instructionsModalEl.showModal()` |
| Click Close instructions | `instructionsModalEl.close()` |

Open the instructions, close them with the button, and open them again.

## 6. Give the instructions some space

The modal works before we add any CSS. Now we can make it match our interface.

In `css/style.css`, add:

```css
#instructions-modal {
  width: 90vw;
  max-width: 28rem;
  padding: 1.5rem;
  border: 2px solid #0f766e;
  border-radius: 8px;
}
```

The width can follow the viewport, while `max-width` keeps the panel from becoming too wide.

Padding creates space between the instructions and the border.

## 7. Dim the page behind it

The browser provides a layer behind a modal called its **backdrop**.

Add:

```css
#instructions-modal::backdrop {
  background-color: rgba(0, 0, 0, 0.5);
}
```

`::backdrop` is a **pseudo-element** that lets us style that layer.

The first three numbers create black. The final value, `0.5`, makes it 50% opaque, so the page remains visible underneath.

Open the modal again. The darker background helps draw attention to the instructions.

> 💡 Opening a modal prevents interaction with the page behind it. It does not automatically pause JavaScript timers or other game logic.

## 🎓 You Do

Replace the example instructions with three short rules for your planned game. Test opening the modal, closing it with its button, and closing it with Escape.

## References

- [MDN: The dialog element](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog)
- [MDN: showModal()](https://developer.mozilla.org/en-US/docs/Web/API/HTMLDialogElement/showModal)
- [MDN: ::backdrop](https://developer.mozilla.org/en-US/docs/Web/CSS/::backdrop)
````