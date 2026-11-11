<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Favicons</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to add an icon to a browser tab.

## Help players recognize the tab

A **favicon** is the small icon a browser can display beside a page’s title.

It helps people recognize a site when several tabs are open. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel?utm_source=chatgpt.com)

Place the supplied `favicon.png` in your `assets` folder.

Inside `<head>`, add:

```html
<link rel="icon" type="image/png" href="./assets/favicon.png">
```

The path starts from `index.html`.

Refresh the page and look at the browser tab. If it still shows an older icon, close and reopen the tab.

## 🎓 You Do

Change the page’s `<title>` to include your own game idea. For your project, choose a simple square icon that remains recognizable at a small size.
