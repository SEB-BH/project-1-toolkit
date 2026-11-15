<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">CSS Boilerplate</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to build a small, reusable CSS starting point.


## Apply a useful default everywhere

We made one panel use `border-box`. Future buttons, cards, and other elements could benefit from the same setting.

At the top of the stylesheet, add:

```css
* {
  box-sizing: border-box;
}
```

The **universal selector**, `*`, selects every HTML element.

Remove `box-sizing: border-box;` from `.game-panel`. The universal rule now supplies that setting.  You can also add `box-sizing: content-box` to the `.no-border-box` rule if you'd like to exempt it from our universal box-sizing.  You can also get rid of this rule and it's div altogether.

## Control the page’s outside space

Browsers provide some default styling. For example, the body normally has a margin.

Add:

```css
body {
  margin: 0;
}
```

We now control the space around our content.

Inside `body`, add:

```css
padding: 20px 0;
```

With two padding values, the first controls the top and bottom. The second controls the left and right.

## Establish readable defaults

Add these declarations inside `body`:

```css
background-color: #f1f5f9;
color: #172033;
font-family: system-ui, sans-serif;
line-height: 1.5;
```

`system-ui` uses the device’s interface font. The browser can use a general sans-serif font if needed.

`line-height: 1.5` gives lines of text some breathing room.

Our buttons should use the surrounding text’s font settings. Add a separate rule:

```css
button {
  font: inherit;
}
```

Here, `inherit` tells the button to use its parent’s font settings.

## Our final `CSS` boilerplate:

```css
* {
  box-sizing: border-box;
}

body {
  background-color: #f1f5f9;
  color: #172033;
  font-family: system-ui, sans-serif;
  line-height: 1.5;
  margin: 0px;
  padding: 20px 0;
}

button {
  font: inherit;
}
```

Your boilerplate can be more or less depending on what you like when you style your pages.  Some other things to consider adding to your boilerplate:

- Remove all borders by adding `border: none;` to the star selector:
  ```css
  * {
    box-sizing: border-box;
    border: none;
  }
  ```

- Remove bullet points (and the weird extra space from the bullet points) on all `ul` items:
  ```css
  ul {
    list-style: none;
    padding-left: 0;
  }
  ```
  
- Remove the default underline on links (anchor tags):
  ```css
  a {
    text-underline-position: under;
  }
  ```

> 💡 Boilerplate should contain defaults you understand. You can adjust it as a project’s needs become clearer.


## Position the panel

Inside `.game-panel`, add:

```css
margin: 0 auto;
```

The top and bottom margins are `0`. The browser shares the available horizontal space between the two automatic side margins, centering the panel.

## Recognize the reusable part

The rules for `*`, `body`, and `button` are our **boilerplate**: a small starting point we can reuse.

The `.game-panel` rule belongs to this particular design.


