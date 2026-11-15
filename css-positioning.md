# Positioning

## Static and Relative positioning

### Static positioning

- The default position mode of every element in a page is the <span style ="color:oklch(52.5% 0.223 3.958)">**position:static**</span>.
- The properties <span style ="color:oklch(52.5% 0.223 3.958)">top</span>, <span style ="color:oklch(52.5% 0.223 3.958)">right</span>,<span style ="color:oklch(52.5% 0.223 3.958)">bottom</span>,<span style ="color:oklch(52.5% 0.223 3.958)">left</span>, does **not** affect the position.

### Relative positioning

- The same as <span style ="color:oklch(52.5% 0.223 3.958)">position:static</span>, but the properties <span style ="color:oklch(52.5% 0.223 3.958)">top</span>, <span style ="color:oklch(52.5% 0.223 3.958)">right</span>,<span style ="color:oklch(52.5% 0.223 3.958)">bottom</span>,<span style ="color:oklch(52.5% 0.223 3.958)">left</span>, does affect the position of the element where it is applied. Meaning it _displaces_ that element..
- The element is **not** removed from the _normal document flow_.
- It's position is **relative to where it is in the document**. Meaning, _it is relative to itself_.
- **NOTE:** When you declare the position of an element to this position, it will limit the scope of a `position:absolute` element.

## Absolute positioning

- Allows you position an element without affecting any other element. Meaning it does not displace any element. It is also not affected by any element.
- It removes the element from the _normal flow_ of the document.
- Allows you to position an element using the <span style ="color:oklch(52.5% 0.223 3.958)">top</span>, <span style ="color:oklch(52.5% 0.223 3.958)">right</span>, <span style ="color:oklch(52.5% 0.223 3.958)">bottom</span>, <span style ="color:oklch(52.5% 0.223 3.958)">left</span> properties.
- It's position is **relative to it's ancestor element**. That ancestor element should **not** be <span style ="color:oklch(52.5% 0.223 3.958)">position:static</span>. Because even if the child element is <span style ="color:oklch(52.5% 0.223 3.958)">position:absolute</span>, it would get its position relative to the <span style ="color:oklch(52.5% 0.223 3.958)">viewport</span>.
- To position an element relative to its container, the ancestor element should be <span style ="color:oklch(52.5% 0.223 3.958)">position:relative</span>, <span style ="color:oklch(52.5% 0.223 3.958)">position:absolute</span>, <span style ="color:oklch(52.5% 0.223 3.958)">position:sticky</span> or <span style ="color:oklch(52.5% 0.223 3.958)">position:fixed</span>. The most use position with the absolute is <span style ="color:oklch(52.5% 0.223 3.958)">position:relative</span>.
- Common uses:
  - Dialogs
  - Modals
  - Icons on top of an element

## Fixed positioning

- It is similar to absolute positioning that it removes an element from the _normal flow_ of the document. But it's position is relative to the <span style ="color:oklch(52.5% 0.223 3.958)">viewport</span>.
- The properties <span style ="color:oklch(52.5% 0.223 3.958)">top</span>, <span style ="color:oklch(52.5% 0.223 3.958)">right</span>, <span style ="color:oklch(52.5% 0.223 3.958)">bottom</span>, <span style ="color:oklch(52.5% 0.223 3.958)">left</span> are use to position an element.
- It will stay on the position as the user scrolls. Meaning it moves with the page as you scroll.
- Common uses:
  - Navigation bars
  - floating chat buttons

## Sticky positioning

- Combination or relative positioning and fixed positioning.
- Behaves like normal elements until you scroll past them and they will act like fixed elements.
- It does not take an element out of the _normal flow_ of the element.
- Same with absolute positioning, it starts its positiong relative to its ancestor element that has the other positioning except the static.

## Other

### Stacking context

Most of those positions will create a `stacking context` except static. It is a 3D visualization of the html. Just think of it as stacking paper on top of it other. The value that decides which paper goes on top is called the`z-index`. The higher the `z-index`, the higher the stack of that page.

We have a normal flow of the html. It's `z-index` is `0`. We can cover that page with another element by declaring the `z-index` of that element to `1` or higher.

## Reference

[Learn CSS Position in 9 Minutes: Web Dev Simplified](https://www.youtube.com/watch?v=jx5jmI0UlXU)  
[CSS Position MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/position)  
[Stacking Context](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Positioned_layout/Stacking_context)  
[fixed vs sticky](https://www.kevinpowell.co/article/positition-fixed-vs-sticky/)
