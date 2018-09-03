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

  - Slide the paragraph down to bottom of div.  We need add new stye to p, div.
   * This requires 2 steps.  
   1) position: absolute; to paragraph style.  This will break it out of the document's regular flow.
   2) bottom: 0; to paragraph.  this will move to zero pixels from the bottom of...

  - New Issue: We want these paragraphs to be zero pixels from the bottom of each div, but paragraphs are all sitting on top of each other at the page bottom.
    * Solution: Give div relative to its child element paragraph so paragraph could be position relative to its parents.
      div { position: relative; }

    * Still not quite there since, paragraph isn't all the way at the bottom of the div yet!
      p { margin: 0; } // this will stick p to the bottom of div

  - Move h2 down with p in CSS.  
    * There is no easy way to bring h2 down where p is with CSS.  We will use cheat!  
    1st cheat: Get rid of <h2>, and dropping the meal names into the paragraph tags.  

  - Now all the content is chunked in big paragraphs- How do we break those back up again visually? header and content!
    * HTML's line break is just the thing for this!!
    <br> or <br /> self closing tag!
    * Make rest of the content smaller look
    <small> </small>

  - divs are stacked tightly on top of each other!  No, we want some spaces inbetween them!
    * Which CSS element controls space around an HTML element? Margin! Add Margin only on top.
      margin: 40px 0 0 0;

    * make div round edge
      border-radius: 12px;

    - Issue: why border only showed up on the top two corners of the <div>?
     * cuz bottom div is hiding under <p> styling.
     - action: try commenting out p stying css

- 3 Missions: 
  1) More precise ways to position
  2) Making colors fade across the screen
  3) Adding some fancy fonts

  1) More precise ways to position:
  - Adv. Layout:
    * Move the price flush-right: 
    p { text-align: right; }
  HTML has a tag that effects certain content behave differently.  Span tag.
  Use <span> tag inside another tag (inside <p>) to make any bit of content display differently from the rest of the content in the sam tag

    - Use class to make 3 different element behave exactly like one another, by giving them a shared class name.

  - Text-align: right for style class="price"
  * Nothing happened why not?
    - Block vs. Inline element.
    Block takes whole pg width vs. inline only take up as much of the screen as they need to.
    - span is inline and text-aligh only align blocks to the right.
      ex) Blocks vs Inline:
      paragraphs <p>, headers <h1>, <h2>, lists <ul>, <ol>, <li>, divs <div>
      Inline: Hyperlinks <p>, images <img>, form fields <input>, spans <span>

- The best way to right-justify only the price in our inline spans is CSS property called float.  Floats let you slide the content of a <span>, or more frequently, allow you to slide an image, around inside its container element.
  .price {
    float: right;
  }

- Next fix: black box to not hide picture
  Use p backgroun rgba alpha channel transparency of a color.  Control alpha on a scale from 0 to 1 (0% color: totally see-through) (100% color: opaque)

  Gradient: 
    background: linear-gradient(bottom, rgba(0,0,0,1), rgba(0,0,0,.4));  // opaque to lighter transparency

    - Radial: radiate outward in all directions, from a central point.
    - Linear: Linear gradients only go in one direction, in a line.

    Rule of linear: start with bottom of the html element that contains it.  When it starts at the bottom, it's black with 100% opacity.

    When it ends at the top, it is black with 40% opacity. begin solid black a the bottom, and end as 40% black at the top.
      background: linear-gradient(bottom, rgba(0,0,0,1), rgba(0,0,0,.4));

    If you change rgb numbers, 
    yellow, rgba(255,255,0,1) to red, rgba(255,0,0,1) you'd get orange in the middle auto.

    our ex) gradient is black (r=0, g=0, b=0) all the way through, only opacity changes, not color
    - change solid black background to a semi-transparent linear gradient.
    ex) 
    p {background: linear-gradient(bottom, rgba(0,0,0,1), rgba(0,0,0,.4));
    }

    - to make linear-gradient work we need vendor-prefix.  

    * chrome, opera, safari: 
    background: -webkit-linear-gradient;
    * firebox: 
    background: -moz-linear-gradient;

p {
  background: linear-gradient(bottom, rgba(0,0,0,1), rgba(0,0,0,.4));
  background: -webkit-linear-gradient(bottom, rgba(0,0,0,1), rgba(0,0,0,.4));
  background: -moz-linear-gradient(bottom, rgba(0,0,0,1), rgba(0,0,0,.4));

  - Graceful degradation: for browser that does not support background linear-gradient, use p {
  background: rgb(0, 0, 0);
  