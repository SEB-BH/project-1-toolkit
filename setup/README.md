<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Setup</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to open a practice page with connected HTML, CSS, and JavaScript files.

## Prepare the files

Navigate to your lectures direcotry and create a `project-toolkit` folder:

```bash
cd ~/code/ga/lectures
mkdir project-toolkit
```

Enter the project directory:

```bash
cd project-toolkit
```

## Create the project files

Create your HTML, CSS, and JavaScript files:

```bash
mkdir css js
touch index.html css/style.css js/app.js
```

Open the project in VS Code:

```bash
code .
```

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

Download the [assets folder](./assets/).  Be sure to save it inside of `project-toolkit`.