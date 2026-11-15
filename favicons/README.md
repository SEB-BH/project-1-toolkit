<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Favicons</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to add an icon to a browser tab.

## Help players recognize the tab

A **favicon** is the small icon a browser can display beside a page’s title.

It helps people recognize a site when several tabs are open. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel)

Inside `<head>`, add:

```html
<link rel="icon" type="image/png" href="./assets/favicon.png">
```

The path starts from `index.html`.

Refresh the page and look at the browser tab. If it still shows an older icon, close and reopen the tab.


## Favicon from an Emoji

Replace our earlier link with:

```html
<link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>🎯</text></svg>">
```

This code snippet takes an emoji and treats it like an svg image.  Try replacing the `🎯` with an emoji of your choice.

[Source: CSS Tricks](https://css-tricks.com/emoji-as-a-favicon/)

## Favicon Generator

Try out a website like [Favicon.io](https://favicon.io/) for turning your own image, text, or emoji into a favicon.