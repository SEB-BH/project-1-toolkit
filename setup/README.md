<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Setup</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to open a practice page with connected HTML, CSS, and JavaScript files.

## Prepare the files

Run these commands in Git Bash on Windows or your terminal on macOS:

```bash
mkdir project-toolkit
cd project-toolkit
mkdir css js assets
touch index.html css/style.css js/app.js
code .
```

If `code .` does not open VS Code, open the folder through **File → Open Folder**.

## Connect the files

Add this starting document to `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Delivery Dash</title>
  <link rel="stylesheet" href="./css/style.css">
  <script src="./js/app.js" defer></script>
</head>
<body>

</body>
</html>
```

The viewport setting helps mobile browsers display the page at the device’s width. The stylesheet controls appearance, and the script will handle our button demonstrations.

Inside `<body>`, add the practice interface:

```html
<main class="game-panel">
  <h1>Delivery Dash</h1>

  <p id="message">Ready to start.</p>

  <div class="controls">
    <button class="action-button" id="start" type="button">
      Start shift
    </button>

    <button class="action-button" id="reset" type="button" disabled>
      Reset shift
    </button>
  </div>

  <section class="instructions">
    <h2>How to play</h2>
    <p>Complete deliveries before the battery runs out.</p>
  </section>
</main>
```

This page gives us a place to practise layout and button states. We will add the JavaScript needed for those demonstrations.

## Confirm the connections

In `css/style.css`, add:

```css
body {
  background-color: lightyellow;
}
```

In `js/app.js`, add:

```js
console.log('Project toolkit connected.');
```

Open `index.html` in your browser. Confirm that the background is yellow and the message appears in the console.

Once both connections work, remove these two temporary checks.

> **Instructor preparation:** Reuse the images in the [previous lesson ZIP](https://chatgpt.com/library?file_id=libfile_5755fa20d8208191ad4f94f64deea111&account_id=personal), inside `game-page-layout/keyframes-and-sprites/assets/`. Give students `bird-frame-1.png`, renamed to `favicon.png`, and `bird-sprite-sheet.png`. Both belong in their new `assets` folder.
