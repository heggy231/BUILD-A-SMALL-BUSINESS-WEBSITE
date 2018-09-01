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

  - revision: background-size: cover; stretches the img to full screen width;
  img to sit in the center of screen.  
  body {
    margin: 0 auto;
    max-width: 600px;
  }

  * Why max-width? In case body width is bigger than its container width (HTML) This prevents overflowing of content.
2) All three <div> have the same background img.
  - make different <div> to show 3 images.  Use class on div!
    this css looks for variety!  not like <p>, <h2> all the same
    ex) FIRST:CLASS
    Classes let you name and group HTML tags.
      ex) <input type="email"> or <pizza size="large" crust="thin" type="pepperoni">
    HTML for specifying a class looks very similar: 
      ex) <tag class="name">
          class = tag's attribute
          name = attribute's value
    - ACTION!  Give each div some class!!
    <div class="first"> <div class="second"> <div class="dessert">
      Note: nothing changes yet b/c the page-wide div style is still calling the first background img, and b/c you haven't given the unique classes any background images yet.

    - Note: even though div still says to give all div firstcourse img; class trumps the div instruction.  Therefore, we see first course img only on the first class instruction.  
div {
  height: 200px;
    /* keeps img from tiling */
  background-size: cover; 
  background: url(http://dash.ga.co/assets/firstcourse.jpg);
}
.first {
  background: url(http://dash.ga.co/assets/firstcourse.jpg);
}
.second {
  background: url(http://dash.ga.co/assets/secondcourse.jpg);
}
.dessert {
  background: url(http://dash.ga.co/assets/dessertcourse.jpg);
}

  - Ex of specificity: style flow down in order of specificity.  Class is more specific than div tag.
  - Summary of what just happened with img, body.  
    * img is inside of class, div, the body tag.
    The body tag tells it to be 600 px wide.  It's 200 px tall b/c div style tells it to be.  
    * It obeys until they disagree. HTML listens to CSS that's most closest to it.
    * the div {} style with background img code is cruft (excess code that doesn't perform a meaningful function)
3) text hard to read! Repositioning element
  - ADD <p> text color white, background color black. solid color for alpha: 1

p {
  background: rgba(0,0,0,1); // black background
  color: rgba(255,255,255,1); // white font
}

rgba color mixing
000 black
255 0 0 red
0 255 0 Green
0 0 255 blue
255 255 255 white
0 255 255 cyan (green, blue)
255 0 255 magenta (red, blue)
255 255 0 yellow (red, green)

- Issue Paragraph containers sill centered in the divs, need fixing

  * Let's format text to make it easy to read!
    - Add padding around the words, a new style called line-height.  
    Line-height lets us increase or decrease the vertical space btwn lines.
    1. give p padding 10 px all around
    2. use text-align to justify the paragraph style
    3. set paragraph line-height to 28px

    padding: 10px;
    text-align: justify;
    line-height: 28px;