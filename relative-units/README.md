<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Relative Units</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to choose units based on text size or viewport size.

## Choose what a size should follow

So far, most of our sizes use pixels.

Sometimes we want a size to follow something else:

- Text and spacing can follow the page’s base font size.
- A panel can follow the browser’s width.
- A page can fill the available screen height.

These are different jobs, so we use different units.

## Use `rem` for sizes that should follow text

A **`rem`** is based on the font size of the root HTML element, `<html>`.

A common browser default is `16px`, but users can change it. With that default:

| CSS value | Calculated size |
| --- | ---: |
| `0.5rem` | 8px |
| `1rem` | 16px |
| `2rem` | 32px |

The useful part is the relationship: `2rem` means twice the root font size. [MDN](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Values_and_units?utm_source=chatgpt.com)

Add:

```css
.game-panel h1 {
  font-size: 2rem;
}
```

Inside `.action-button`, add:

```css
font-size: 1rem;
```

Replace its existing padding declaration with:

```css
padding: 0.75rem 1rem;
```

The button’s text and padding now both relate to the same base font size.

## See why this relationship helps

Imagine someone prefers larger text. We want the button’s surrounding space to grow along with its label.

Temporarily add:

```css
html {
  font-size: 20px;
}
```

The heading becomes `40px`, the button text becomes `20px`, and its horizontal padding becomes `20px`.

We changed one base value, and several related sizes followed it.

**Remove this temporary `html` rule afterward.** Leaving the root font size unset allows the browser’s default font-size preference to provide the base.

> 💡 `rem` does not automatically change when the browser becomes narrower. It follows the root font size. Normal browser zoom can enlarge both pixel-based and rem-based content.

Pixels are still useful for details such as a thin border or the exact dimensions of a sprite frame.

## Let the panel follow the viewport width

The **viewport** is the browser area used to display the page.

`1vw` is 1% of the viewport width.

In `.game-panel`, replace:

```css
width: 320px;
```

with:

```css
width: 90vw;
```

Resize the browser. The panel now changes width with it.

On a wide desktop screen, however, the panel could become unnecessarily wide. Add:

```css
max-width: 40rem;
```

The panel can use 90% of the viewport width, but its maximum width is `40rem`.

Also replace the panel’s padding with:

```css
padding: 1.25rem;
```

Our panel rule now looks like this:

```css
.game-panel {
  width: 90vw;
  max-width: 40rem;
  padding: 1.25rem;
  border: 4px solid #0f766e;
  background-color: white;
  margin: 0 auto;
}
```

> 💡 A percentage width such as `width: 100%` generally follows the containing element’s width. `vw` follows the viewport, even when the element is nested inside a smaller container.

## Give the page a minimum screen height

`1vh` is 1% of the large viewport height. On mobile, that corresponds to the larger area available when browser controls are retracted.

Add this inside `body`:

```css
min-height: 100vh;
```

The body now has a minimum height of one viewport.

We use **`min-height`** so that it can grow when the content needs more room.

## Account for mobile browser controls

Mobile address bars can appear and disappear as someone scrolls.

The **`dvh`** unit follows the dynamic viewport height as those browser controls expand or retract. [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/length?utm_source=chatgpt.com)

Immediately after the previous declaration, add:

```css
min-height: 100dvh;
```

Keep both declarations in this order:

```css
min-height: 100vh;
min-height: 100dvh;
```

A browser that supports `dvh` uses the second declaration. A browser that does not understand it can keep the first.

This is a useful pattern for a game page, login page, or dashboard that should fill the screen while remaining able to grow.

## 🎓 You Do

Change the panel’s maximum width to `32rem` and resize the browser. Notice when the panel follows the viewport and when it stops growing.

Restore `40rem` before continuing.
