# Flexbox

## Values of Flex

1. `flex: none` - `flex: 0 0 auto;`
2. `flex: initial` - `flex: 0 1 auto;`
3. `flex: auto` - `flex: 1 1 auto;`
4. `flex: <1 or infinity>` - `flex: <1 or infinity> 1 0;`

- `flex-grow` - increases the size of the flex item with respect to its other flex items inside the flex container
- `flex-shrink` - decreases the size of the flex item with respect to the flex container. It would only be applied _if_ the sizes of the flex items exceeds the flex container, then it would shrink to fit the flex container. Example, we have a flex container that is set to `width: 300px;`. Inside that flex container are 3 divs/flex items set to `width:150px;. If we set `flex-shrink: 0;, the flex items would overflow the flex container.
- `flex-basis` - sets the initial size where the increasing or shrinking starts. It's default value would be zero. Using the same example below if we set `flex: 0 0 150;`. Then the flex item would not grow no shrink, but it would respect the size property given to it, which in this case is the width, so its width would be 150 and it would still overflow from the flex containe.

## Axes

Flex has two axes.

1. `flex-direction: row` - this is the main axis. It means the flex items lines up from left-to-right. This is the default axis orientation of `flex`.
2. `flex-direction: column` - this is the vertical axis. This mean that flex items lines up from top-to-bottom.

Note that `flex-direction` changes the way `flex-basis` refer to a dimension. `flex-direction: row` makes the `flex-basis` refer to `width` property. Whie `flex-direction: column` makes the `flex-basis` refer to the `heigth` propety.

## Alignment

You can align how the flex items while inside the flex container. Since `flex` can only affect the growing and shrinking of a flex item, we need a way to align these flex items the way we want. Whether along the x-axis(main axis) or the y-axis (cross axis).

### justify-content

`justify-content` - allows us to align the flex items across the main axis(primary axis).

### align-items

`align-items` - allows us to align the flex items across the vertical axis(cross axis).

One thing to note between these two methods of aligning flex items, is that when you change the default `flex-direction: row` to `flex-direction: column`, the `justify-content` aligns the flex item across the vertical axis, and `align-items` aligns the flex items across the main axis. This is one of the leading confusion between beginners.

## Gap

Gap is another property of `flex`. This allows us to create spaces between flex items similar to margins.

_Reference_
[An interactive guide](https://www.joshwcomeau.com/css/interactive-guide-to-flexbox/);
[Values of flex](https://www.w3.org/TR/css-flexbox-1/#flex-common);
[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/flex);
