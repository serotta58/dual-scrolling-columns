# React app demo with Two Column layout with scrolling

Andrea Pereira de Almeida wrote a blog post about how to [Use Flexbox to create a sticky header and sidebar with flexible content](https://www.bitovi.com/blog/use-flexbox-to-create-a-sticky-header-and-sidebar-with-flexible-content).  She used this layout in the design of the [CanJS](https://canjs.com/) website.  Check it out.  It has some nice features:

- Sticky header composed of two synced column headers
- Two column layout, each column with its own auto scroll functionality
- Left column sizes to fit the width of its variable content
- Right column fills the remaining space
- Right header navigation content moves along with resizing of right column

I wanted to use this in a React app, but it required a few tweaks in order to work.  This demo code fixes those issues.

## Issues

I copied the code from the HTML and CSS from the [JS Bin](https://jsbin.com/qusudim/edit?css,output) linked in the article.  I dropped the HTML code structure into the React App render() and imported the CSS.  But the `<body>` tag triggered console warnings due to the original body tags wrapping the whole React App.  Changing it to a `<div>` eliminated the warning, but then the scroll bars disappeared.  The columns in a div (id='app-body') with this style to create the columns:

```css
#app-body {
  height: 100%;
  display: flex;  /*arranges following left/right divs into columns*/
}
```

And the following is required to prevent the whole page from scrolling (which also eliminates the individual column scrolling):

```css
body {
  height: 100%;
  display: flex;
}
```

This can be a useful starting template for a layout.  You could add a right column, and optionally hide or show the left or right column and the inner column would expand or shrink to fill the remaining area.
