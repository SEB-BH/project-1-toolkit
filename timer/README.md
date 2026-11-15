<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">A Simple Countdown</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to start, stop, and reset a countdown.

## Give the shift a time limit

Our delivery game needs a countdown. Clicking **Start shift** will start it. Each update will reduce the remaining time until it reaches zero.

We will use our existing buttons and update their event listeners.

## 1. Display the remaining time

In `index.html`, add this below the message paragraph:

```html
<p>Time left: <span id="time-left">0</span> seconds</p>
```

The `<span>` gives us a place to update the number without replacing the surrounding words.

In `js/app.js`, cache our new `time-left` element:

```js
const timeLeftEl = document.querySelector('#time-left')

console.log(timeLeftEl)
```

Before we can implement our timer, we need variables to hold how much time remains, and we need to update our element with that time:

```js
let timeLeft = 30
let timerId = null

timeLeftEl.textContent = timeLeft
```

`timeLeft` stores the remaining seconds.

`timerId` will store an identifier for the repeating timer so we can stop it later. For now, `null` represents no active timer.  This will be important when we call `clearInterval(timerId)` to stop the timer.

Refresh the page. It should display **Time left: 30 seconds**.

## 2. Write one countdown update

Next we need a function which can subtract 1 second at a time from our `timeLeft`:

```js
const updateTimer = () => {
  timeLeft = timeLeft - 1
  timeLeftEl.textContent = timeLeft
}
```

Each time we call this function, it subtracts one from our data and displays the new value.

We now need the browser to repeat this action.

## 3. Start repeating when the shift starts

**Replace the existing Start shift event listener** with:

```js
startButtonEl.addEventListener('click', () => {
  startButtonEl.disabled = true
  resetButtonEl.disabled = false
  messageEl.textContent = 'Your shift has started.'

  timerId = setInterval(updateTimer, 1000)
})
```

`setInterval()` asks the browser to keep calling a function:

- `updateTimer` is the function to repeat.
- `1000` is the requested delay in milliseconds: one second.
- The returned identifier is stored in `timerId`.

Notice that we pass `updateTimer` **without parentheses**. We give the browser the function so it can call it later.

Disabling "Start shift" prevents the player from clicking it repeatedly and starting several countdowns.

## 4. Stop at zero

The timer currently keeps subtracting. We need a rule that stops it when time runs out.

Inside `updateTimer`, after updating `textContent`, add:

```js
if (timeLeft === 0) {
  clearInterval(timerId)
  timerId = null
  messageEl.textContent = 'Shift finished! Select Reset shift to try again.'
}
```

`clearInterval(timerId)` stops that repeating timer.

Setting `timerId` back to `null` records that it is no longer active. This assignment alone would not stop the timer—we need `clearInterval()` first.

Start shift remains disabled until the player resets.

## 5. Reset the countdown

Resetting the number is only part of the job. If the timer is still running, it would immediately continue counting down.

**Replace the existing Reset shift event listener** with:

```js
resetButtonEl.addEventListener('click', () => {
  startButtonEl.disabled = false
  resetButtonEl.disabled = true
  messageEl.textContent = 'Ready to start.'

  // clear the old timer, in case user presses reset before the time is up
  clearInterval(timerId)
  timerId = null

  // reset the seconds and render the reset time
  timeLeft = 30
  timeLeftEl.textContent = timeLeft
})
```

This stops any active timer, restores the number, and prepares the buttons for another shift.

> 💡 This is a basic practice countdown. Browsers can delay timer updates, especially in background tabs, so it is not a precise clock.

