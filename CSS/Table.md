# Table
```
HTML Table Format

<table>
  <tr>
    <th>Company</th>
    <th>Contact</th>
    <th>Country</th>
  </tr>
  <tr>
    <td>Alfreds Futterkiste</td>
    <td>Maria Anders</td>
    <td>Germany</td>
  </tr>
  <tr>
    <td>Berglunds snabbköp</td>
    <td>Christina Berglund</td>
    <td>Sweden</td>
  </tr>
</table>
```

## Table Borders: _border_
To specify table borders in CSS, use the `border` property.

The example below specifies a black border for `<table>, <th>, and <td>` elements:
```
table, th, td {
  border: 1px solid black;
}
```
**Notice** that the table in the example above has double borders. This is because both the `<table>` and the `<th> and <td>` elements have separate borders.

## Collapse Table Borders: _border-collapse_
The `border-collapse` property sets whether the table borders should be collapsed into a single border. If you only want a border around the table, only specify the border property for `<table>`.

## Horizontal Dividers: _border-bottom_
Add the `border-bottom` property to `<th> and <td>` for horizontal dividers:
```
th, td {
  border-bottom: 1px solid #ddd;
}
```

## Hoverable Table: _:hover_
Use the `:hover` selector on `<tr>` to highlight table rows on mouse over:
```
tr:hover {
  background-color: #f5f5f5;
}
```

## Striped Tables
For _zebra-striped_ tables, use the `nth-child()` selector and add a `background-color` to all _even_ (or _odd_) table rows:
```
tr:nth-child(even) {
  background-color: #f2f2f2;
}
```

## Responsive Table
A responsive table will display a horizontal scroll bar if the screen is too small to display the full content. Add a container element (like `<div>`) with `overflow-x:auto` around the `<table>` element to make it responsive:
```
<div style="overflow-x:auto;">
  <table>
    ... table content ...
  </table>
</div>
```





