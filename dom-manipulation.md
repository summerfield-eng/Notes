# DOM Manipulation

## Targeting nodes with selectors

```JavaScript
<div id="container">
  <div class="display"></div>
  <div class="controls"></div>
</div>
```

- When working with the DOM, you use “selectors” to target the nodes you want to work with. You can use a combination of CSS-style selectors and relationship properties to target the nodes you want. Let’s start with CSS-style selectors.
  - `div.display`
  - `.display`
  - `#container > .display`
  - `div#container > div.display`
- You can also use relational selectors (i.e., firstElementChild or lastElementChild, etc.) with special properties owned by the nodes.

  ```JavaScript
  // selects the #container div (don't worry about the syntax, we'll get there)
  const container = document.querySelector("#container");

  // selects the first child of #container => .display
  const display = container.firstElementChild;
  console.log(display);  // <div class="display"></div>
  ```

  ```JavaScript
  // selects the .controls div
  const controls = document.querySelector(".controls");

  // selects the prior sibling => .display
  const display = controls.previousElementSibling;
  console.log(display); // <div class="display"></div>
  ```

## DOM Methods

### Query Selectors

- Query selectors
  - `element.querySelector(selector)` - returns a reference to the first match of selector.
  - `element.querySelectorAll(selectors)` - returns a “NodeList” containing references to all of the matches of the selectors.

### Element creation

- `document.createElement(tagName, [options])` - creates a new element of tag type tagName. [options] in this case means you can add some optional parameters to the function. Don’t worry about these at this point.

### Append elements

### Remove elements

### Altering elements

### Adding inline style

### Editing Attributes

### Working with classes

### Adding text content

### Adding HTML content

## Reference

[TOP](https://www.theodinproject.com/lessons/foundations-dom-manipulation-and-events)
