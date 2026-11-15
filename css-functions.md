# CSS Functions

Although the css does not allow us to make our own functions, we can still use them.

Notice how some properties looked like a function being called? Like the `rgb(0, 0, 0)`, or the `calc()` which allows us to do some calculations.

## Below are some functions in excel.

### `calc()`

The most powerful use cases for calc include:

Mixing units
The ability to nest `calc( calc () - calc () )`

```css
:root {
  --header: 3rem;
  --footer: 40px;
  --main: calc(100vh - calc(var(--header) + var(--footer)));
}
```

`--header`, `--footer`, and `--main` are all examples of CSS variables.

### `min()`

`min()` does an excellent job of helping us create responsive websites. Take a look at this example:

```css
#iconHolder {
  width: min(150px, 100%);
  height: min(150px, 100%);
  box-sizing: border-box;
  border: 6px solid blue;
}
```

This checks whether 100% of the parent element’s width is smaller than 150px. If 100% would be narrower than 150px, the element will take up the full width of the container (100%). Otherwise, it will be 150px wide.

You are able to do basic math inside a `min()`. For example, `width: min(80ch, 100vw - 2rem);` (you don’t even need calc() in this case).

### `max()`

`max()` works the same way as min(), only in reverse.

```css
width: max(100px, 4em, 50%);
```

The above compares all three values and sets the element’s width to whichever is largest. If `50%` of the parent container is bigger than 100px and `4em`, the width will be `50`%. If `4em` is larger than the others, it will use `4em`.

### `clamp()`

```css
h1 {
  font-size: clamp(1.5rem, 5vw, 3rem);
}
```

`clamp()` is a great way to make elements fluid and responsive. `clamp()` takes 3 values:

1. the minimum value `1.5rem`
2. the scaling value `5vw`
3. the maximum value `3rem`

## How can these help me?

Cool, now I know what these are, so why do i need to learn it?

Well knowing this allows you to set the width of an element so that the viewer can easily read your text. We can set the perfect width.

According to The Elements of Typographic Style by Robert Bringhurst:

> Anything from 45 to 75 characters is widely regarded as a satisfactory length of line for a single-column page set in a serifed text face in a text size.

To ensure that your text blocks stay between 45 and 75 characters wide, use clamp() and the ch (0-width character advance) unit:

```css
p {
  width: clamp(45ch, 50%, 75ch);
}
```

The code above will make the text scaling more fluid.

## Reference

[Complet list of CSS Functions](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/Functions)
[min(), max(), and clamp() in depth](https://web.dev/articles/min-max-clamp)
