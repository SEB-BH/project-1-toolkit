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

The button is visible, but clicking it does nothing yet.

## 2. Put the instructions inside a dialog

Find the existing `<section class="instructions">`.

Replace the section element with a dialog element.

```html
  <dialog id="instructions">
    <h2>How to play</h2>
    <p>Complete deliveries before the battery runs out.</p>
  </dialog>
```

The instructions and close button are now inside the dialog.

Refresh the page. The instructions have disappeared because a `<dialog>` is hidden until we open it.

## 3. Select the elements we need

We need JavaScript references to both the dialog and the button meant to open it:

- The button that opens the instructions.
- The dialog containing the instructions.

In `js/app.js`, add these variables below your existing element selections:

```js
const openInstructionsButtonEl = document.querySelector('#open-instructions')
const instructionsModalEl = document.querySelector('#instructions')

console.log(openInstructionsButtonEl, instructionsModalEl)
```

## 4. Open the instructions

We already know how to listen for a button click. This time, the response will be to open the dialog.

Below your existing event listeners, add:

```js
openInstructionsButtonEl.addEventListener('click', () => {
  instructionsModalEl.showModal()
})
```

`.showModal()` is a method available on **dialog elements.**

It displays the dialog above the page and prevents the player from interacting with the page behind it.

Refresh and click **How to play**. The browser displays the dialog in the center of the screen.

Press **Escape** to close it for now.

## 5. Make a Close Button

In our `html` inside of the `instructions` dialog element, add a close button:

```html
    <button class="action-button" id="close-instructions" type="button">
      Close instructions
    </button>
```

The close button needs its own event listener, but first we need to cache it:

```js
const closeInstructionsButtonEl = document.querySelector('#close-instructions')

closeInstructionsButtonEl.addEventListener('click', () => {
  instructionsModalEl.close()
})
```

`.close()` hides the dialog so the player can use the page again.

## 6. Dim the page behind it

The browser provides a layer behind a modal called its **backdrop**.

Add:

```css
#instructions::backdrop {
  background-color: rgba(0, 0, 0, 0.5);
}
```

`::backdrop` is a **pseudo-element** that lets us style that layer.

The first three numbers create black. The final value, `0.5`, makes it 50% opaque, so the page remains visible underneath.

Open the modal again. The darker background helps draw attention to the instructions.

> 💡 Opening a modal prevents interaction with the page behind it. It does not automatically pause JavaScript timers or other game logic.



<!-- ### 7. Style the modal

```css
#instructions {
  width: 90vw;
  max-width: 28rem;
  padding: 1.5rem;
  border: 2px solid #0f766e;
  border-radius: 8px;
}
``` -->