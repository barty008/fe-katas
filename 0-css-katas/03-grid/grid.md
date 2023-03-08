# Grid

CSS Grid is an extremely powerful tool allows us to be specific about where sections of our website should be placed. It allows us to divide our website into columns and rows that elements can be placed into.

This really shines when dealing with responsive design and media queries as existing sections can be moved around to git different areas of the grid depending on the screen size. 

By combining grid for elements to be displayed in a fixed place and flex for dynamic content we can avoid a lot of the traditional CSS pain points such as centering elements.

## display:grid

Similarly to `flex` CSS Grid works by having a parent element with a display property of grid. This parent will define rows and columns that all of it children can be placed into. These children will also need grid specific properties to define which of the parents rows and columns they will fit into. This is done by using row / column numbers or named `areas` of the grid.

## Useful grid parent properties

- [display: grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout): sets an element to be a grid (or inline-grid) that it's children will fit into
- [grid-template-columns](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns): defines the number and size of the columns in the grid
- [grid-template-rows](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows): defines the number and size of the rows in the grid. e.g.

```css
grid-template-columns: 100px auto 100px;
grid-template-rows: 20vh auto
```

has 3 columns and 2 rows. The left and right columns are fixed to 100px wide and the middle column takes the remaining space. There are 2 rows, the first takes 20% of the viewport height and the second row takes all remaining space

- [grid-template-areas](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas): names areas of the grid that children can occupy. e.g. for the above layout these areas can be named `header`, `nav`, `content` and `aside`. 

```css
grid-template-areas: 
  "header header header"
  "nav content aside";
```
Here the `header` spans the whole first row with the others taking the columns underneath.

Each new string represents a row and the columns are space separated. Areas can span as many rows / columns as you like to make your preferred layout.

## Useful grid child properties

Unlike flex you will have to set some child properties to give the children their places in the grid. By default children will take the next available grid "cell" which is rarely what we want. They can be positioned explicitly with:

- [grid-column](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column): defines which columns the element will take up
- [grid-row](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row): defines which rows the element will take up


```css
grid-column: 1 / 3;
grid-row: 1 / 4
```

In a 4 x 4 grid the above element spans columns 1 -> 2 and rows 1 -> 3. The end row and column are not inclusive

- [grid-area](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-area): defines a named grid area for the element to occupy (must exist in the parent grid or it will be ignored)

e.g. in the above grid layout and element can take up the whole first row by specifying the grid area of `header` **nb** this property has no quotation marks around `header` which is notably different from a JS string.
```css
grid-area: header;
```

**Goal**:

- Align the components of this page in a grid. They should maintain this shape no matter what size the browser window is.
- The `sidebar` should be a _fixed_ width and _not_ expand/shrink when the browser window is resized.
- The `content` and `sidebar` components should expand downwards when more content is added.

![grid target](./grid.png)
