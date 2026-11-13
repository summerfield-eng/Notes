# Tables

Table is essential if we want to present a data in a more logical and readable way.

## Element of a table

- `<table></table>` - this tell JavaScript that we want to create a table.
- `<td><td>` - this is the smallest unit of a table. Think of it as a _cell_ in excel. `<td></td>` could stand for _table data_.
- `<tr></tr>` - this contitutes as a one row of a table. Think of it as _table row._
- `<th></th>` - this is when we want to create a _header_ for our table. This will make the headers bold.

## Properties of an element

- `colspan` - if we want to make the cell(`td` or `th`) occupy more rows, we will use this property.
- `rowspan` - if we want to make the cell(`td` or `th`) occupy more columns, we will use this property.

## `colgroup` and `col`

- Lets say we want to apply styles to an entire column of a cell. We can do that by using the `colgroup` element. It should be placed after the `<table>` element.
- Inside the `colgroup` we can put one or more `col` element. The `col` element allows us to target the columns of a table if we want to add some styles on it.

- Properties of `col`
  - `span` - this works the same way as span, if we want to design two or more columns, then we can do `<col span="2" />` this will tell JavaScript that it should include the column next to it if we applied any design.
  - `class` - this is the same as the usual usage of class when we want to target some certain elements.

## Notes:

- Sometime you will encounter that a style which you add does not work. Try zooming in and out.
