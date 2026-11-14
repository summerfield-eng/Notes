# Intermediate CSS

## Reset and Reboot

Some of the default styling in CSS can cause the design of the webpage to look different than we expected or we do not like the default design and would simply like to design it ourselves. So some developers started to create their own _default_ styles by declaring on the stylesheet file.

**Here are the sources:**

- [Reboot, Resets, and Reasoning]
- [Making the case for CSS normalize and reset stylesheets in 2023]
- [Josh Comeau’s custom CSS reset ]

**Here are my resets**

```CSS
*,
*::before,
*::after {
  box-sizing: border-box;
  }

*:not(dialog) {
  margin: 0;
  }

body {
  line-height: 1.5; -webkit-font-smoothing: antialiased;
  }

img, picture, video, canvas, svg {
  display: block; max-width: 100%;
  }

input, button, textarea, select {
  font: inherit;
  }

p, h1, h2, h3, h4, h5, h6 {
  overflow-wrap: break-word;
  }

p {
  text-wrap: pretty;
  }

h1, h2, h3, h4, h5, h6 {
  text-wrap: balance;
  }

```

## CSS Units

### Absolute units

- These are units that are always the same in any context. An example would be the <span style="color: oklch(52.5% 0.223 3.958)">px</span>. It does not change the pixel size that is relative on the page.

### Relative units

- This are unit that changes based on the context. This can be use for responsive wep pages.

#### `em` and `rem`

- Both of these units uses the `font-size` declared to get their sizes.
- `em` takes it's relative size with respect to the **parent element**. So if you declare a `font-size: 100px`, `1em` is equivalent to `100px`, `2em` is `200px` and so on.
- `rem` or root em, takes its relative size from the **root font size**(either <span style="color: oklch(52.5% 0.223 3.958)">:root</span> or <span style="color: oklch(52.5% 0.223 3.958)">html </span>). So if you declare a font size of `16px`, `1rem` is `16px`, `2rem` is `32px` and so on.

### `vh` and `vw`

- the **v** stands for _viewport._ It relates its size to the size of the viewport. <span style="color: oklch(52.5% 0.223 3.958)">1vh</span> is equal to <span style="color: oklch(52.5% 0.223 3.958)">1%</span> of the viewport heigth. and <span style="color: oklch(52.5% 0.223 3.958)">1vw</span> is equal to the <span style="color: oklch(52.5% 0.223 3.958)">1%</span> of the viewport width

### Typography

- If we want to have a responsive fonts. Use this:

```CSS
body {
  // font grows 1px for every 100px of viewport width
  font-size: calc(16px + 1vw);
  // leading grows along with font,
  // with an additional 0.1em + 0.5px per 100px of the viewport
  line-height: calc(1.1em + 0.5vw);
}
```

- This came from [Fun with Viewport Units ].

## More Text Styles

- `@font-face` - this will allow font to be downloaded alonng with your page. Read more [here](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Text_styling/Web_fonts#web_fonts)

```css
@font-face {
  font-family: "myFont";
  src: url("myFont.woff2");
}

html {
  font-family: "myFont", "Bitstream Vera Serif", serif;
}
```

- `clamp()` - this will help you control the minimun and maximum value of the scaling of your fonts. It takes three values, `clamp(minimum, the value you pass to calc ,maximum)`

```css
html {
  font-size: clamp(1rem, 0.75rem + 1.5vw, 2rem);
}
```

- [Line length] - According to someone, the satisfactory line length of a sigle column page is between 45 to 75 characters. You can't set a line length directly in CSS. There is no line-length property. But you can stop text from getting too wide by limiting how wide the container can be. The `max-inline-size` property is perfect for this.

```css
article {
  max-inline-size: 66ch;
}
```

- [Font Best Practices](http://web.dev/articles/font-best-practices)
- [Design Typography](https://web.dev/learn/design/typography)
- You can read more about text styles here: [More Text Styles]
- ellipsis: https://css-tricks.com/snippets/css/truncate-string-with-ellipsis/
- You can use `max-inline-size: 100%` to tell the browser to never let the image passed its containers

## More CSS Styles

### Background

- `Background` is a _shorthand_ for 8 background properties. Enables you to declare all CSS background properties in a single declaration: Below are the properties and their default values.
  - background-image: `none`
  - background-position: `0% 0%`
  - background-size: `auto auto`
  - background-repeat: `repeat`
  - background-origin: `padding-box`
  - background-clip: `border-box`
  - background-attachment: `scroll`
  - background-color: `transparent`
- If the background is attached to the `<body>` element then it covers the whole page.

### Borders

- `Border` is a shorthand for 3 border properties. And those 3 properties are also shorthand for the 4 directions.
  - border-width: as each of the properties of the shorthand:
    - border-top-width: `medium`
    - border-right-width: `medium`
    - border-bottom-width: `medium`
    - border-left-width: `medium`
  - border-style: as each of the properties of the shorthand:
    - border-top-style: `none`
    - border-right-style: `none`
    - border-bottom-style: `none`
    - border-left-style: `none`
  - border-color: as each of the properties of the shorthand:
    - border-top-color: `currentcolor`
    - border-right-color: `currentcolor`
    - border-bottom-color: `currentcolor`
    - border-left-color: `currentcolor`
- `Border-radius` is a shorthand property of 4 general directions of `border-radius`. This allows us to round the corners of an elements outer border edge.
- If the border radius is half of the element's height or width, then what you have is a circle.
  - border-top-left-radius: `0`
  - border-top-right-radius: `0`
  - border-bottom-right-radius: `0`
  - border-bottom-left-radius: `0`
- Note: the parameters after this border radius can help us control where we want to place the border.
  - 4 parameters means: top, rigth, bottom, left
  - 3 parameters means: top, left and right, bottom
  - 2 parameters means: top and bottom, left and right
  - 1 parameter means: all sides are the same border sizes
- `corner-shape` - This property is a shorthand for the following physical properties:
  - corner-top-left-shape: `round`
  - corner-top-right-shape: `round`
  - corner-bottom-left-shape: `round`
  - corner-bottom-right-shape: `round`

### Box-shadow

- `box-shadow` - this will add a shadow effect to an element.
  - `color` - specifies the color of the shadow.
  - `length`
    - If there are two values, it will be taken as the offset of the shadow.
    - If nonem then it will considered as 0 offset
    - If there are three values, then the third will be interpreted as `blur-radius`
    - If there are four values, then the fourth value will be interpreted as `spread-radius`.
  - `inset` - places the shadow inside of the element.
- Apparently you can animate the shadow. It has something to do with Interpolation.

### Overflow

- `overflow` - This property is a shorthand for the following CSS properties:
  - `overflow-x`
  - `overflow-y`
- Below are the values of this properties

  ```css
  /* Keyword values */
  overflow: visible;
  overflow: hidden;
  overflow: clip;
  overflow: scroll;
  overflow: auto;

  /* Two-value syntax: horizontal | vertical */
  overflow: hidden visible;
  ```

### Opacity

- `opacity` - sets the opacity of an element.

## Reference

[Reboot, Resets, and Reasoning]: (https://css-tricks.com/reboot-resets-reasoning/)
[Making the case for CSS normalize and reset stylesheets in 2023]: (https://mattbrictson.com/blog/css-normalize-and-reset)
[Josh Comeau’s custom CSS reset ]: (https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Values_and_units)
[CSS values and units ]: (https://www.joshwcomeau.com/css/custom-css-reset/)
[CSS units ]: (https://web.archive.org/web/20251130034321/https://codyloyd.com/2021/css-units/)
[Fun with Viewport Units ]: (https://css-tricks.com/fun-viewport-units/)
[More Text Styles]: (https://www.theodinproject.com/lessons/node-path-intermediate-html-and-css-more-text-styles)
[Line length]: (https://web.dev/learn/design/typography#line_lengthe)
