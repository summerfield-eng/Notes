# Custom Properties

Just like in JavaScript, we call also create _variables_, assign some values into it, and then initialized it to a property. This is called Custom properties.

This will allow us to reference these design values multiple times decreasing the number of time we have to type it.
This will also allow us to change a certain element once. Lets say way have hundreds of borders on different element. Instead of looking and changing these one by one, we can change it once and it will change the whole border style.

## Using custom properties

The syntax for declaring and accessing a custom property is not too different from how we write normal rule declarations:

```css
.error-modal {
  --color-error-text: red;
  --modal-border: 1px solid black;
  --modal-font-size: calc(2rem + 5vw);

  color: var(--color-error-text);
  border: var(--modal-border);
  font-size: var(--modal-font-size);
}
```

That’s it! First, we declare our custom property with a double hyphen followed by a case-sensitive, hyphen-separated property name (`color-error-text` wouldn’t be the same as `Color-Error-Text`) which can be whatever name we want. The use of Kebab case (single hyphens to separate words) is very important here because spaces are not valid (`--color error text` would not work). Then we can store any valid CSS value in our newly declared custom property, whether it be a color value, shorthand values, or even a more complex function, just to give you a few examples.

When we want to access a custom property, we use the `var()` function as the value of a CSS property, and then place our custom property inside of the parenthesis (including the double hyphen at the beginning).

## Fallback values

The `var()` function actually accepts two parameters. The first parameter we’ve already gone over, which is the custom property we want to assign. The second parameter is an optional fallback value. When a fallback value is provided in addition to a custom property, the fallback value will be used if the custom property is invalid or hasn’t been declared yet. We can even pass in another custom property as a fallback, which can have its own fallback value as well!

```css
.fallback {
  --color-text: white;

  background-color: var(--undeclared-property, black);
  color: var(--undeclared-again, var(--color-text, yellow));
}
```

In the above example, our background-color property would have a value of black and our color property would have a value of white. If the --color-text custom property was invalid or didn’t exist, the fallback to our fallback would take over and the color property would have a value of yellow.

## Scope

Just like JavaScript variables, custom properties also have `scope`. That's why you will notice how we declared the custom properties and use it at the same selector.

## `:root` selector

To get around the scope issue more efficiently, we can declare our custom properties on the `:root` selector.

```css
:root {
  --main-color: red;
}

.cool-paragraph {
  color: var(--main-color);
}

.exciting-paragraph {
  background-color: var(--main-color);
}
```

## Creating themes with custom properties

With `:root` we can change or toggle between themes.

```html
<div class="container">
  <p>
    You're now viewing this example with the
    <span class="theme-name">dark</span> theme!
  </p>
  <button class="theme-toggle">Toggle Theme</button>
</div>
```

```css
:root.dark {
  --border-btn: 1px solid rgb(220, 220, 220);
  --color-base-bg: rgb(18, 18, 18);
  --color-base-text: rgb(240, 240, 240);
  --color-btn-bg: rgb(36, 36, 36);
}
​ :root.light {
  --border-btn: 1px solid rgb(36, 36, 36);
  --color-base-bg: rgb(240, 240, 240);
  --color-base-text: rgb(18, 18, 18);
  --color-btn-bg: rgb(220, 220, 220);
}
​ body,
.theme-toggle {
  color: var(--color-base-text);
}
​ body {
  background-color: var(--color-base-bg);
  padding: 10px;
}
​ .container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
​ p {
  font-size: 1.5rem;
}
​ .theme-toggle {
  background-color: var(--color-btn-bg);
  border: var(--border-btn);
  font-size: 1.125rem;
  padding: 10px 20px;
}
​ .theme-toggle:hover {
  cursor: pointer;
}
​ .theme-toggle:focus {
  outline: var(--border-btn);
}
```

```js
function setTheme() {
  const root = document.documentElement;
  const newTheme = root.className === "dark" ? "light" : "dark";
  root.className = newTheme;

  document.querySelector(".theme-name").textContent = newTheme;
}

document.querySelector(".theme-toggle").addEventListener("click", setTheme);
```

## Media queries

With `:root` we can also change the layout of our website based on the device which it is currently being viewed on.

```html
<div class="container">
  <p>
    Based on your theme setting in your OS or user agent, you're now viewing
    this example with the <span class="theme-name"></span> theme!
  </p>
</div>
```

```css
:root {
  --border-btn: 1px solid rgb(36, 36, 36);
  --color-base-bg: rgb(240, 240, 240);
  --color-base-text: rgb(18, 18, 18);
  --color-btn-bg: rgb(220, 220, 220);
  --theme-name: "light";
}

@media (prefers-color-scheme: dark) {
  :root {
    --border-btn: 1px solid rgb(220, 220, 220);
    --color-base-bg: rgb(18, 18, 18);
    --color-base-text: rgb(240, 240, 240);
    --color-btn-bg: rgb(36, 36, 36);
    --theme-name: "dark";
  }
}

body {
  background-color: var(--color-base-bg);
  color: var(--color-base-text);
  padding: 10px;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

p {
  font-size: 1.5rem;
}

.theme-name::after {
  content: var(--theme-name);
}
```
