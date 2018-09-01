Version 1:
1) Creative ways to use background images
2) How to group and position multiple elements with CSS

1) Creative ways to use background images
  - <div> multi-purpose tag (allows style group of elememts with the same CSS)
  We are going to layer descriptive text over a picture of what each dish looks like.

  - Anna's site, all HTML inside <body>; which affect every single page element with CSS body style, only write once!

  - Jeff's blog <article> tag as a container for post titles and content.  Then you created an article style in the CSS that controlled the appearance of the tag contained inside of each article.

  - <article> tag is a semantic tag: it ways something useful, and defining, about its content.  ex) semantic tags <header>, <nav> (short for navigation), or <footer>.

  - <div> tag: non-semantic, for all purpose: can use it as a container to group any type of content so it can be styled by a single bit of CSS.

Wrap all 3 menu items with opening and closing div tags.
Next, style div tag! (height 200px)
- done with creating new style for div with height
- Wrapt with div around each menu items (name, descrip)

* Adding background image (room for pictures)
div {
  height: 200px;
  background: url(http://dash.ga.co/assets/firstcourse.jpg);
}

- 3 issues at this version
1) background img 'tiling': repeating to fill the width of the screen
  solution: give the div a background-size for stop from tiling

  background: url(http://dash.ga.co/assets/firstcourse.jpg);
  /* keeps img from tiling */
  background-size: cover; 
  
2) All three <div> have the same background img.

3) text hard to read!

