<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Google Fonts</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to load a Google Font and apply it with a fallback font.

## Give the interface a consistent font

A website may use a particular font to match its visual identity. An online shop, for example, may use the same font across its product pages and checkout.

Our page currently uses a font installed on the player’s device. We will load **Nunito** as a web font.

There are two separate jobs:

1. Make the font available.
2. Tell CSS where to use it.

## Make the font available

Inside `<head>`, add this **before your own stylesheet link**:

```html
<link
  rel="stylesheet"
  href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;700&amp;display=swap"
>
```

This requests the regular and bold versions of Nunito.

`display=swap` allows text to appear using a fallback while the requested font loads. [developers.google.com](https://developers.google.com/fonts/docs/css2?utm_source=chatgpt.com)

## Apply the font

In your existing `body` rule, replace the `font-family` declaration with:

```css
font-family: 'Nunito', sans-serif;
```

Refresh the page.

The heading, paragraphs, and buttons should use the new font. Our earlier `font: inherit` rule helps the buttons follow the page’s font settings.

> 💡 The font link loads a resource over the internet. Keeping `sans-serif` provides a fallback if that resource is unavailable.

## 🎓 You Do

Temporarily remove `'Nunito',` from the `font-family` value and compare the appearance. Restore it afterward.

For your own project, choose a font from [Google Fonts](https://fonts.google.com/) and use its supplied embed code with the matching `font-family`.
