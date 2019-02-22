# 7 steps to web design and development

## 1. Goal of the project:

Show what Omnifood does, how it works and in which cities it operates in. Then, make people sign up on a subscription plan.

Audience:  
Busy people who don't have time to cook or don't like it;

## 2. Simple Navigation

One-page webpage containing information provided by Omnifood, with simple navigation

Content:
provided by Omnifood in form of a text document and a couple of images.

Navigation:
Also provided by Omnifood in a text document.

## 3. Wireframing

wireframe or sketchout roughly some examples of the interface (Wireframes attached)

## 4.Design

Color: flat orange - friendly, confident, courage,
Font: LATO typeface -warm, stabiilty, serious but friendly

## 5. Create a folder structure

omnifood>resources> css >img (landing page use with css) >styles.css > data > img (projects images)

> js > vendors > css (download from internet) > fonts ( icons ) > js ( jquery ...) >README.md ( documentation )

---

# HTML boiler plate

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <!-- normalize.css css the same to all browser, must go before owner css-->
    <link rel="stylesheet" type="text/css" href="vendors/css/normalize.css" />
    <!-- owner css -->
    <link rel="stylesheet" type="text/css" href="resources/css/style.css" />
    <!-- google fonts LATO goes after owner css -->
    <link
      href="https://fonts.googleapis.com/css?family=Lato:100,300,300i,400"
      rel="stylesheet"
      type="text/css"
    />
    <title>Omni Food</title>
  </head>
  <body></body>
</html>

- style.css
  /_ target all elements _/

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  background-color: #fff; /* white background */
  color: #555; /* grey */
  font-family: "Lato", "Arial", "san-serif"; /* if Lato and Arial doesn't work, then use css default san-serif */
  font-size: 20px;
  font-weight: 300;
  text-rendering: optimizeLegibility; /* rendering text prefectly */
}
```

Set up responsive webdesign - mobile - rank higher by google

1. Fluid grid: all layout elements are sized in relative units, such us percentate, instead of absolute units
2. Flexible images: are also sized in relative units - prevent images goes outside of their parents
3. Media queries: allow us to specify different CSS style rules for different browser units.

Set up fluid grid.

- www.responsivegridsystem.com - any layout
- download grid.css copy and paste in the vendor/css/
- include grid.css in index.html

<!-- responsive grid system -->
<link rel="stylesheet" type="text/css" href="vendors/css/grid.css" />
add google font
<link
      href="https://fonts.googleapis.com/css?family=Lato:100,300,300i,400"
      rel="stylesheet"
      type="text/css"
    />

# Style font and grid in resources/css/style.css

```css
html {
  background-color: #fff;
  color: #555;
  font-family: "Lato", "Arial", "san-serif"; /* if Lato and Arial doesn't work, then use css default san-serif */
  font-size: 20px;
  font-weight: 300;
  text-rendering: optimizeLegibility; /* rendering text prefectly */
}

.row {
  max-width: 1140px; /* maximun width */
  margin: 0 auto; /* center row */
}
```

In the index.html

<div class="row">
<h1>Omni food<h1>
</div>

---

# Build the Header part 1

- New HTML elements:
  header, nav, ul, li
    <header>
      <!-- center box -->
      <div class="hero-text-box">
        <h1>Goodbye junk food. Hello super healthy meals.</h1>
        <a href="#">I'm Hungry</a> <a href="#">Show Me More</a>
      </div>
    </header>

* Put text on an image: make image darker.
* How to make image as high as the browser viewport
* How to make a vertically a horizontally center box
  ```css
  header {
    /* darker image on top of the image using linear-gradient property
          like 2 image on top of each other with 70% transparency
          linear-gradient(rgba(0, 0, 0, 0.70), rgba(0, 0, 0, 0.70)) */
    background-image: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)),
      url(img/hero.jpg);
    background-size: cover; /* image cover the whole screen */
    background-position: center; /* center image */
    height: 100vh; /* 100% view port height with the image */
  }
  h1 {
    /* normalize.css give some padding to h1 so set margin to 0 */
    margin: 0;
  }
  ```

---

# Build the Header part 2

```css
h1 {
  /* normalize.css give some padding to h1 so set margin to 0 */
  margin-top: 0;
  margin-bottom: 20px; /* spaces between header text and buttons */
  color: #fff;
  font-size: 200%; /* which is 40px 2x20px 20px in the html{} */
  font-weight: 300; /* h1 font-weight is bold so decrease font-weight to 300*/
  text-transform: uppercase;
  letter-spacing: 1px;
  word-spacing: 3px; /* 3px between each word*/
}
.hero-text-box {
  position: absolute; /* free floating position to parent elememt */
  width: 1140px; /* set width as the parent elememt */
  top: 50%; /* whole text box start 50% from top of screen 1140px down and 50% to left */
  left: 50%;
  /* translate(x,y) move element to vertically and horizontally to the left by 50% */
  transform: translate(-50%, -50%);
}
```

Add a line break in html file

<h1>Goodbye junk food. <br />Hello super healthy meals.</h1>

- How to design buttons
- The 4 link states in CSS: link(default), visited, hover, active

Add 2 buttons. First one is orange and second is outline orange
<a class="btn btn-full" href="#">I'm Hungry</a>

<a class="btn btn-ghost" href="#">Show Me More</a>

```css
.btn {
  /* make buttons inline with padding and margin */
  display: inline-block;
  padding: 10px 30px; /* top bottom 10px left/right 30px */
  font-weight: 300; /* thinner font */
  text-decoration: none;
  border-radius: 200px; /* rounded right and left side of button */
  color: #fff;
  /* background color, border, text color, change when hover buttons .2 seconds*/
  transition: background-color 0.2s, border 0.2s, color 0.2s;
}

.btn-full {
  /* use flatuicolors */
  background-color: #e67e22;
  /* also add border here because of border box it's add the margin in btn-ghost*/
  border: 1px solid #e67e22;
}

.btn-full:link,
.btn-full:visited {
  /* use flatuicolors */
  background-color: #e67e22;
  /* also add border here because of border box it's add the margin px*/
  border: 1px solid #e67e22;
}

.btn-ghost:link,
.btn-ghost:visited {
  border: 1px solid #e67e22;
  color: #e67e22;
}
/* :pseudo class:hover , visited - state when clicked and come back from another page
    we want buttons with a darker orange when hover  . tools to do darker color 0to255.com*/
.btn:hover,
.btn:active {
  background-color: #cf6d17; /* dipper orange */
}

.btn-full:hover,
.btn-full:active {
  border: 1px solid #cf6d17;
}

.btn-ghost:hover,
.btn-ghost:active {
  border: 1px solid #cf6d17;
  color: #fff; /* text's color orange w/white bc */
}
```

CSS3 transitions for small animations

```css
.btn:link,
.btn:visited {
  /* make buttons inline with padding and margin */
  display: inline-block;
  padding: 10px 30px;
  font-weight: 300;
  /* roundedrightandleftsideofbutton */
  border-radius: 200px;
  color: #fff;
  /*background color, border, text color, change when hover buttons .2 seconds */
  transition: background-color 0.2s, border 0.2s, color 0.2s;
}

.btn-full:link,
.btn-full:visited {
  ... margin-right: 15px;
}
```

# Build the Header part 3

Structure CSS by using comments

```css
/*----------------------------------------------------*/
/*  BASIC SETUP* /
/*----------------------------------------------------*/
/* target all elements */

* {
  ...;
}

html {
  ...;
}

/*----------------------------------------------------*/
/*  REUSEABLE * /
/*----------------------------------------------------*/

.row {
  ..;
}

/*---------------------  HEADING ----------------------*/
h1 {
}

/*----------------------------------------------------*/
/*  HEADERS * /
/*----------------------------------------------------*/
header {
  ...;
}

.hero-text-box {
  ...;
}
/*-----------------------   BUTTONS  -----------------------------*/
.btn:link,
.btn:visited {
  ...;
}

/* same color when user click */
.btn-full:link,
.btn-full:visited {
  ...;
}

.btn-ghost:link,
.btn-ghost:visited {
  ...;
}
.btn:hover,
.btn:active {
  ...;
}

.btn-full:hover,
.btn-full:active {
  ...;
}

.btn-ghost:hover,
.btn-ghost:active {
  ...;
}
```

How to create a simple navigation

<header>
<nav>
        <div class="row">
          <!-- logo image -->
          <img
            src="resources/img/logo-white.png"
            alt="Omnifood logo"
            class="logo"
          />
          <!-- nav links -->
          <ul class="main-nav">
            <li><a href="#">Food delivery</a></li>
            <li><a href="#">How it works</a></li>
            <li><a href="#">Our cities</a></li>
            <li><a href="#">Sign up</a></li>
          </ul>
        </div>
      </nav>
</header>

```css
/*----------------------------------------------------*/
/*  HEADERS * /
/*----------------------------------------------------*/
.logo {
  height: 100px;
  width: auto;
  float: left;
  margin-top: 20px;
}
.main-nav {
  float: right;
  /* no bullets points */
  list-style: none;
}
/* select all li elements */
.main-nav li {
  /* side by side */
  display: inline-block;
  /* 40px spacing between the li */
  margin-left: 40px;
  margin-top: 55px;
}
/* select anchor tag, color show the same when click :link and :visited*/
.main-nav li a:link,
.main-nav li a:visited {
  /* add padding top and bottom*/
  padding: 8px 0;
  color: #fff;
  /* no underline for links */
  text-decoration: none;
  text-transform: uppercase;
  /* 18px/20px = 90%, 90% font-size of parent element 20px in the html{}*/
  font-size: 90%;
  /* before we hover to see the bottom border, we have show it first and make it transparent*/
  border-bottom: 2px solid transparent;
  /* animate with css transition border-bottom */
  transition: border-bottom 0.2s;
  /* more center out animation
  https://stackoverflow.com/questions/28623446/hover-effect-expand-bottom-border */
}
/* hover effect for nav link */
.main-nav li a:hover,
.main-nav li a:active {
  /* nice border at the bottom */
  border-bottom: 2px solid #e67e22;
}
```

---

# Feature Section

- How to put content on a website directly from CSS with the :after pseudo class
- We'll use the fluil grid for the first time
- We'll learn how to use icons (https://ionicons.com/)

  1. html section

  ```html
  <!-- feature section -->
  <section class="section-feature">
    <div class="row">
      <!-- html entity dash &mdash; -->
      <h2>Get food fast &mdash; not fast food.</h2>
      <p class="long-copy">
        Hello, we’re Omnifood, your new premium food delivery service. We know
        you’re always busy. No time for cooking. So let us take care of that,
        we’re really good at it, we promise!
      </p>

      <!-- use fluid grid -->
      <div class="row">
        <div class="col span-1-of-4">
          <ion-icon name="infinite"></ion-icon>
          <h3>Up to 365 days/year</h3>
          <p>
            Never cook again! We really mean that. Our subscription plans
            include up to 365 days/year coverage. You can also choose to order
            more flexibly if that's your style.
          </p>
        </div>
        <div class="col span-1-of-4">
          <ion-icon name="stopwatch"></ion-icon>
          <h3>Ready in 20 minutes</h3>
          <p>
            You're only twenty minutes away from your delicious and super
            healthy meals delivered right to your home. We work with the best
            chefs in each town to ensure that you're 100% happy.
          </p>
        </div>
        <div class="col span-1-of-4">
          <ion-icon name="nutrition"></ion-icon>
          <h3>100% organic</h3>
          <p>
            All our vegetables are fresh, organic and local. Animals are raised
            without added hormones or antibiotics. Good for your health, the
            environment, and it also tastes better!
          </p>
        </div>
        <div class="col span-1-of-4">
          <ion-icon name="cart"></ion-icon>
          <h3>Order anything</h3>
          <p>
            We don't limit your creativity, which means you can order whatever
            you feel like. You can also choose from our menu containing over 100
            delicious meals. It's up to you!
          </p>
        </div>
      </div>
    </div>
  </section>
  ```

  2. include ionicons css and javascript file
     In the head tag at the top add ionicons css cdn and javascript right before at the body tag.
     <!-- ionicons css -->
     <link
       href="https://unpkg.com/ionicons@4.5.5/dist/css/ionicons.min.css"
       rel="stylesheet"
     />
         <script src="https://unpkg.com/ionicons@4.5.5/dist/ionicons.js"></script>
     </body>

---

## Add White Space between Section and Restyle h1 h3 h3 paragraphs and icons

```css
section {
  /* add white space top and bottom between section */
  padding: 80px 0;
}

/*---------------------  HEADING ----------------------*/
/* restyle for h1 h2 h3*/
h1,
h2,
h3 {
  /* basic font-size is 20px from html element. 200% is 40px 2x20px */
  font-weight: 300;
  /* decrease font-weight to 300 */
  text-transform: uppercase;
}

h1 {
  /* normalize.css give some padding to h1 so set margin to 0 */
  margin-top: 0;
  margin-bottom: 20px;
  color: #fff;
  font-size: 240%;
  word-spacing: 3px;
  letter-spacing: 1px;
}

h2 {
  font-size: 180%;
  word-spacing: 2px;
  text-align: center;
  margin-bottom: 30px;
  letter-spacing: 1px;
}

h3 {
  font-size: 110%;
  margin-bottom: 15px;
}

/* yellow line with pseudo :after */
/* IMPORTANT: must have content property. empty this case. content: " " */
h2:after {
  display: block;
  height: 2px;
  background-color: #e67e22;
  content: " ";
  width: 100px;
  /* center line */
  margin: 0 auto;
  /* h2 margin-bottom goes first then the line with margin-top 30px */
  margin-top: 30px;
}

/*  -------- PARAGRAPHS ----------- */
.long-copy {
  /* line height should be from 125% to 145% */
  line-height: 145%;
  /* too many words to read, so we make less word */
  width: 70%;
  /* 15% on left and right + 70% = 100% width */
  margin-left: 15%;
}

/* add another class .box to col span-1-of-4, NEVER change the col span-1-of-4 class */
.box {
  padding: 1%;
}

/* all paragraphs inside the box */
.box p {
  font-size: 90%;
  line-height: 145%;
}

/*  -------- ICONS ----------- * /
/* make icons bigger */
.icon-big {
  font-size: 350%;
  display: block;
  color: #e67e22;
  margin-bottom: 10px;
}
```

Add .icon-big clas to icons in index.html for all 4 cols
<ion-icon class="icon-big" name="infinite"></ion-icon>

---

# Favorite Meals Section Part 1

- How to make a grid of beaufiful images

```html
<!-- Favorite Meals Section -->
<!-- 100% of browser width  with 2 ul-->
<section class="section-meals">
  <ul class="meals-showcase">
    <li>
      <!-- figure have image and caption -->
      <figure class="meal-photo">
        <img
          src="resources/img/1.jpg"
          alt="Korean bibimbap with egg and vegetables"
        />
      </figure>
    </li>
    <li>
      <figure class="meal-photo">
        <img
          src="resources/img/2.jpg"
          alt="Simple italian pizza with cherry tomatoes"
        />
      </figure>
    </li>
    <li>
      <figure class="meal-photo">
        <img
          src="resources/img/3.jpg"
          alt="Chicken breast steak with vegetables"
        />
      </figure>
    </li>
    <li>
      <figure class="meal-photo">
        <img src="resources/img/4.jpg" alt="Autumn pumpkin soup" />
      </figure>
    </li>
  </ul>

  <ul class="meals-showcase">
    <li>
      <figure class="meal-photo">
        <img src="resources/img/5.jpg" alt="Paleo beef steak with vegetables" />
      </figure>
    </li>
    <li>
      <figure class="meal-photo">
        <img
          src="resources/img/6.jpg"
          alt="Healthy baguette with egg and vegetables"
        />
      </figure>
    </li>
    <li>
      <figure class="meal-photo">
        <img src="resources/img/7.jpg" alt="Burger with cheddar and bacon" />
      </figure>
    </li>
    <li>
      <figure class="meal-photo">
        <img
          src="resources/img/8.jpg"
          alt="Granola with cherries and strawberries"
        />
      </figure>
    </li>
  </ul>
</section>
```

Style with CSS

```css
/*----------------------------------------------------*/
/*  -------- MEALS ----------- * /
/*----------------------------------------------------*/

.section-meals {
  padding: 0;
}
/* ul */
.meals-showcase {
  list-style: none;
  width: 100%;
}

/* li */
.meals-showcase li {
  display: block;
  /* side by side */
  float: left;
  width: 25%;
}

.meal-photo {
  /* same as parent */
  width: 100%;
  margin: 0;
}

.meal-photo img {
  width: 100%;
  height: auto;
}
```

---

# Favorite Meals Section Part 2
```css
1. Image zoom out and lighter
   .meal-photo img{
   /* scale image to 1.15 or 115% bigger image overflow its container or parent*/
   transform: scale(1.15);
   }
2. In the image container  
   .meal-photo {
   overflow: hidden;
   }
3. When hover, transform to normal by scale it to 1 but there's still a little white space at the bottom, so we scale it to 1.03
   .meal-photo img:hover {
   /*when hover transform to normal there's a little white space at the bottom scale(1.03)*/
   transform: scale(1.03);
   }
4. Animate the transform
   .meal-photo img{
   /* scale image to 1.15 or 115% bigger image overflow its container or parent*/
   transform: scale(1.15);
   /* animate transform */
   transition: transform 0.5s;
   }
5. Make image darker and make it lighter when hover
   .meal-photo img{
   /* make image darker but it's whitter. make the background-color black in the image container */
   opacity: 0.7;
   }
6. /* image container */
   .meal-photo {
   /_ behind the image, there's a black container background _/
   background-color: #000;
   }
7. Animate opacity to 1 when hover
   .meal-photo img:hover {
   transform: scale(1.03);
   opacity: 1;
   }
   .meal-photo img{
   transform: scale(1.15);
   /* animate transform and opacity */
   transition: transform 0.5s, opacity 0.5s;
   }
```

- How to make a nice "zoom-in" transition when hover, only using CSS
- A way to make <img> element darker

```css
/* image container */
.meal-photo {
  /* same as parent */
  width: 100%;
  margin: 0;
  overflow: hidden;
  /* behind the image, there's a black container background */
  background-color: #000;
}

.meal-photo img {
  width: 100%;
  height: auto;
  /* scale image to 1.15 or 115% bigger image overflow its container*/
  transform: scale(1.15);
  /* animate transform and opacity */
  transition: transform 0.5s, opacity 0.5s;
  /* make image darker but it's whitter. make the background-color black in the image container */
  opacity: 0.7;
}

.meal-photo img:hover {
  /* when hover transform to normal there's a little white space at the bottom scale(1.03)*/
  transform: scale(1.03);
  /* change to opacity: 1 when hover */
  opacity: 1;
}
```

Add margin bottom for long-copy in the .section-features

```css
/*----------------------------------------------------*/
/*  -------- FEATURES ----------- * /
/*----------------------------------------------------*/
.section-features .long-copy {
  margin-bottom: 30px;
}
```

---

# Building How-It-Works Section Part 1

In index.html, create the section

```html
<!-- How it works section -->
<section class="section-steps">
  <div class="row"><h2>How it works &mdash; Simple as 1, 2, 3</h2></div>
  <div class="row">
    <div class="col span-1-of-2">
      <img
        src="resources/img/app-iPhone.png"
        alt="Omnifood app in iphone"
        class="app-screen"
      />
    </div>
    <div class="col span-1-of-2">
      <div class="works-step">
        <div>1</div>
        <p>
          Choose the subscription plan that best fits your needs and sign up
          today.
        </p>
      </div>
      <div class="works-step">
        <div>2</div>
        <p>
          Order your delicious meal using our mobile app or website. Or you can
          even call us!
        </p>
      </div>
      <div class="works-step">
        <div>3</div>
        <p>
          Enjoy your meal after less than 20 minutes. See you the next time!
        </p>
      </div>
    </div>
    <!-- buttons -->
    <a href="#" class="btn-app"
      ><img src="resources/img/download-app.svg" alt="App Store Button"
    /></a>
    <a href="#" class="btn-app"
      ><img src="resources/img/download-app-android.png" alt="Play Store Button"
    /></a>
  </div>
</section>
```

# Building How-It-Works Section Part 2

- How to draw circles with css
- A cool technique to make separation between sections
- How to incorporate App Store and Play Store buttons

```css
/* separate section with very light color */
.section-steps {
  background-color: #f4f4f4;
}

/* add .step-box class to the 2 columns col span-1-of-2 */
/* select the first box column */
.steps-box-1 {
  /* align image */
  text-align: right;
  /* add space between 2 box. why percent-responsive design */
  padding-right: 5%;
  margin-top: 30px;
}

/* select the last box column */
.steps-box-2 {
  padding-left: 5%;
  margin-top: 70px;
}

.app-screen {
  /* resize image */
  width: 40%;
}

/* add space between work step */
.works-step {
  margin-bottom: 50px;
  line-height: 145%;
}

.works-step:last-of-type {
  margin-bottom: 80px;
}

/* select div in works-step which is the number with circle around it */
.works-step div {
  color: #e67e22;
  border: 2px solid #e67e22;
  /* number will be side by side with the text */
  display: inline-block;
  border-radius: 50%;
  height: 50px;
  width: 50px;
  text-align: center;
  padding: 5px;
  float: left;
  font-size: 150%;
  margin-right: 25px;
  line-height: 145%;
}

.btn-app img {
  height: 50px;
  width: auto;
  margin-right: 10px;
}
```

# Building Cities Section Pt 1

- Practice our new skill set.
- How to use small icons aligned with some text
- How to syle generic links
  Copy previous layout of feature do one city first and copy and paste for the other cities
  ```html
  <section class="section-cities">
        <div class="row"><h2>We're currently in these cities</h2></div>
        <div class="row">
          <!-- city -->
          <div class="col span-1-of-4 box">
            <img src="resources/img/lisbon-3.jpg" alt="Lisbon" />
            <h3>Lisbon</h3>
            <div class="city-feature">
              <ion-icon name="person"></ion-icon>
              1600+ happy eaters
            </div>
            <div class="city-feature">
              <ion-icon name="star"></ion-icon>
              60+ top chefs
            </div>
            <div class="city-feature">
              <ion-icon name="logo-twitter"></ion-icon>
              @omnifood_lx
            </div>
          </div>
          San Francisco 3700+ happy eaters 160+ top chefs @omnifood_sf Berlin
          2300+ happy eaters 110+ top chefs @omnifood_berlin London 1200+ happy
          eaters 50+ top chefs @omnifood_london
          <!-- city -->
          <div class="col span-1-of-4 box">
            <img src="resources/img/san-francisco.jpg" alt="San Francisco" />
            <h3>San Francisco</h3>
            <div class="city-feature">
              <ion-icon name="person"></ion-icon>
              3700+ happy eaters
            </div>
            <div class="city-feature">
              <ion-icon name="star"></ion-icon>
              160+ top chefs
            </div>
            <div class="city-feature">
              <ion-icon name="logo-twitter"></ion-icon>
              @omnifood_sf
            </div>
          </div>
          <!-- city -->
          <div class="col span-1-of-4 box">
            <img src="resources/img/berlin.jpg" alt="Berlin" />
            <h3>Berlin</h3>
            <div class="city-feature">
              <ion-icon name="person"></ion-icon>
              2300+ happy eaters
            </div>
            <div class="city-feature">
              <ion-icon name="star"></ion-icon>
              110+ top chefs
            </div>
            <div class="city-feature">
              <ion-icon name="logo-twitter"></ion-icon>
              @omnifood_berlin
            </div>
          </div>
          <!-- city -->
          <div class="col span-1-of-4 box">
            <img src="resources/img/london.jpg" alt="London" />
            <h3>London</h3>
            <div class="city-feature">
              <ion-icon name="person"></ion-icon>
              1200+ happy eaters
            </div>
            <div class="city-feature">
              <ion-icon name="star"></ion-icon>
              50+ top chefs
            </div>
            <div class="city-feature">
              <ion-icon name="logo-twitter"></ion-icon>
              @omnifood_london
            </div>
          </div>
        </div>
      </section>
  ```
# Building Cities Section Pt 2 - Styling

Resize cities images

```css
/*----------------------------------------------------*/
/*  -------- CITES ----------- * /
/*----------------------------------------------------*/
.box img {
  width: 100%;
  height: auto;
  margin-bottom: 15px;
}

.city-feature {
  /* add margin between image and its features */
  margin-bottom: 5px;
}
```

In the reusable css file, make icon-small class in index.html and style in css

```css
/*  -------- ICONS ----------- */
/* make icons bigger */
.icon-big {
  font-size: 350%;
  display: block;
  color: #e67e22;
  margin-bottom: 10px;
}

/* make icons small */
.icon-small {
  display: inline-block;
  width: 30px;
  text-align: center;
  color: #e67e22;
  font-size: 120%;
  margin-right: 10px;

  /* Secrets: to align with text and icons */
  line-height: 120%;
  vertical-align: middle;
  /* take top margin away by 4px */
  margin-top: -4px;
}

/*  ----- LINKS -----   */
styling and animate links a:link,
a:visited {
  color: #e67e22;
  text-decoration: none;
  padding-bottom: 1px;
  border-bottom: 1px solid #e67e22;
  transition: border-bottom 0.2s, color 0.2s;
}

a:hover,
a:active {
  color: #555;
  border-bottom: 1px solid transparent;
}
```

We have a problem with the app buttons, they also have border in 'How it works' section. So we add some code in css

```css
.btn-app:link,
.btn-app:visited {
  border: none;
}
```

---

# Building The Customer Testimonial Section Pt 1

- How to create a beautiful background-image effect
- How to effectively communicate what customers have to say

```html
<!-- Customer Testimonial section -->
<section class="section-testimonials">
  <div class="row"><h2>Our customers can't live without us</h2></div>
  <div class="row">
    <div class="col span-1-of-3">
      <blockquote>
        Omnifood is just awesome! I just launched a startup which leaves me with
        no time for cooking, so Omnifood is a life-saver. Now that I got used to
        it, I couldn't live without my daily meals!
        <cite
          ><img src="resources/img/customer-1.jpg" alt="Alberto Duncan" />
          Alberto Duncan</cite
        >
      </blockquote>
    </div>
    <div class="col span-1-of-3">
      <blockquote>
        Inexpensive, healthy and great-tasting meals, delivered right to my
        home. We have lots of food delivery here in Lisbon, but no one comes
        even close to Omifood. Me and my family are so in love!
        <cite
          ><img src="resources/img/customer-2.jpg" alt="Joana Silva" /> Joana
          Silva</cite
        >
      </blockquote>
    </div>
    <div class="col span-1-of-3">
      <blockquote>
        I was looking for a quick and easy food delivery service in San
        Franciso. I tried a lot of them and ended up with Omnifood. Best food
        delivery service in the Bay Area. Keep up the great work!
        <cite
          ><img src="resources/img/customer-3.jpg" alt="Milton Chapman" />
          Milton Chapman</cite
        >
      </blockquote>
    </div>
  </div>
</section>
```

#Building The Customer Testimonial Section Pt 2
Add a background image for the testimonial section.

```css
/*----------------------------------------------------*/
/*  TESTIMONIALS  */
/*----------------------------------------------------*/
.section-testimonials {
  /*  make image darker by using linear-gradient  */
  background-image: linear-gradient(rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.8)), url(img/back-customers.jpg);
  /*  cover 100% width  */
  background-size: cover;
  /*  white text  */
  color: white;
  /* cool effect background image stay fixed when we scroll down or up over image */
  background-attachment: fixed;

}
```
Do the same thing for the header image

## Define blockquotes
```css
blockquote {
  padding: 2%;
  font-style: italic;
  line-height: 145%;
}

cite {
  font-size: 90%;
  margin-top: 25px;
  /* need a line break */
  display: block;
}

cite img {
  height: 45px;
  border-radius: 50%;
  margin-right: 10px;
  /* align text vertical with image */
  vertical-align: middle;
}
```
Add quote mark using :before pseudo property
We need to use iso character
https://css-tricks.com/snippets/html/glyphs/
left double quote mark

# Building The Pricing Plan Section Pt 1
```html
   <!-- pricing plans section -->
    <section class="section-plans">
      <div class="row">
        <h2>Start eating healthy today</h2>
      </div>
      <div class="row">
        <!-- premium meal plan -->
        <div class="col span-1-of-3">
          <div class="plan-box">
            <div>
              <h3>Premium</h3>
              <p class="plan-price">
                $399 / month
              </p>
              <p class="plan-price-meal">
                That’s only 13.30$ per meal
              </p>
            </div>
            <div>
              <ul>
                <li><ion-icon name="checkmark"></ion-icon>1 meal very day</li>
                <li><ion-icon name="checkmark"></ion-icon>Order 24/7</li>
                <li>
                  <ion-icon name="checkmark"></ion-icon>Access to newest
                  creations
                </li>
                <li><ion-icon name="checkmark"></ion-icon>Free Delivery</li>
              </ul>
            </div>
            <div>
              <a href="#" class="btn btn-full">Sign Up</a>
            </div>
          </div>
        </div>
        <!-- Pro meal plan -->
        <div class="col span-1-of-3">
          <div class="plan-box">
            <div>
              <h3>Pro</h3>
              <p class="plan-price">
                149$ per month
              </p>
              <p class="plan-price-meal">
                That’s only $14.90 per meal
              </p>
            </div>
            <div>
              <ul>
                <li>
                  <ion-icon name="checkmark"></ion-icon>1 meal 10 days/month
                </li>
                <li><ion-icon name="checkmark"></ion-icon>Order 24/7</li>
                <li>
                  <ion-icon name="checkmark"></ion-icon>Access to newest
                  creations
                </li>
                <li><ion-icon name="checkmark"></ion-icon>Free Delivery</li>
              </ul>
            </div>
            <div>
              <a href="#" class="btn btn-ghost">Sign Up</a>
            </div>
          </div>
        </div>
        <!-- Starter meal plan -->
        <div class="col span-1-of-3">
          <div class="plan-box">
            <div>
              <h3>Starter</h3>
              <p class="plan-price">
                $19 / meal
              </p>
              <p class="plan-price-meal">
                <!-- empty -->
              </p>
            </div>
            <div>
              <ul>
                <li><ion-icon name="checkmark"></ion-icon>1 meal</li>
                <li>
                  <ion-icon name="checkmark"></ion-icon>Order from 8 am to 12 pm
                </li>
                <li><ion-icon name="close"></ion-icon></li>
                <li><ion-icon name="checkmark"></ion-icon>Free Delivery</li>
              </ul>
            </div>
            <div>
              <a href="#" class="btn btn-ghost">Sign Up</a>
            </div>
          </div>
        </div>
      </div>
    </section>
```

# Building The Pricing Plan Section Pt 2
```css
/*----------------------------------------------------*/
/*  Pricing Plans   */
/*----------------------------------------------------*/

.section-plans {
  background-color: #f4f4f4;
}

/* We have the div.plan-box inside parent .col because we can adjust the width and
background-color */
.plan-box {
  background-color: #fff;
  border-radius: 5px;
  /* center */
  width: 90%;
  margin-left: 5%;
  /* add box shadow at the bottom of box  box-shadow: x-axix y-axis blur color */
  box-shadow: 0 2px 2px #efefef;
}

.plan-box div {
  /* divide section with light border */
  padding: 15px;
  border-bottom: 1px solid #e8e8e8;
}

/* select the first child and add a light suttle color background */
.plan-box div:first-child {
  background-color: #fcfcfc;
  /* light rounded top left and right of box */
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

/* select the last div to center button */
.plan-box div:last-child {
  text-align: center;
  border: 0;
}

.plan-price {
  /* make price font bigger */
  font-size: 300%;
  margin-bottom: 10px;
  /* font-weight: 200; */
  color: #e67e22;
}

.plan-price span {
  /* 30% of 300% parent element .plan-price*/
  font-size: 30%;
  font-weight: 300;
}

.plan-price-meal {
  font-size: 80%;
}

.plan-box ul {
  /* no bullet points */
  list-style: none;
}

.plan-box ul li {
  /* add top and bottom space between each li */
  padding: 5px 0;
}
```
---

# Building a Contact Form Section Pt 1
- How to use a set of new HTML elements to create 
  forms: form, label, input, select, option, textarea

```html
    <!-- contact form section -->
    <section class="section-plan">
      <div class="row">
        <h2>We're happy to hear from you</h2>
      </div>
      <div class="row">
        <form action="#" method="POST" >
          <div class="row">
            <!-- 32.26% -->
            <div class="col span-1-of-3">
              <label for="name">Name</label>
            </div>
            <!-- 66.13% -->
            <div class="col span-2-of-3">
              <input type="text" name="name" id="name" placeholder="Please Enter Your Name" required>
            </div>
          </div>
          <div class="row">
            <div class="col span-1-of-3">
              <label for="email">Email</label>
            </div>
            <div class="col span-2-of-3">
              <input type="email" name="email" id="email" placeholder="Please Enter Your Email" required>
            </div>
          </div>
          <div class="row">
            <div class="col span-1-of-3">
              <label for="find-us">How did you find us?</label>
            </div>
            <div class="col span-2-of-3">
              <!-- dropdown box -->
              <select name="find-us" id="find-us">
                <option value="friends" selected>Friends</option>
                <option value="search">Search Engine</option>
                <option value="ad">Advertisement</option>
                <option value="other">Other</option>
              </select>
            </div>
          </div>
          <div class="row">
              <div class="col span-1-of-3">
                <label for="">Newsletter</label>
              </div>
              <div class="col span-2-of-3">
                <!-- check box -->
                <input type="checkbox" name="news" id="news" checked> Yes, Please. 
              </div>
          </div>
          <div class="row">
              <div class="col span-1-of-3">
                <label for="">Drop us a line</label>
              </div>
              <div class="col span-2-of-3">
                <!-- text area -->
                <textarea name="message" placeholder="Enter your message here." id="" cols="30" rows="10"></textarea> 
              </div>
          </div>
          <div class="row">
              <div class="col span-1-of-3">
                <label for="">&nbsp;</label>
              </div>
              <div class="col span-2-of-3">
                <!-- button -->
                <input type="submit" value="Send it!">
              </div>
          </div>
        </form>
      </div>
    </section><!-- contact form section end -->
```

# Building a Contact Form Section Pt 2
- How to style these elements
```css
/*----------------------------------------------------*/
/*  Contact Form   */
/*----------------------------------------------------*/
.contact-form {
   /* make form 60% width and center form */
  width: 60%;
  margin: 0 auto;
}

/* select ONLY input type text and email NOT checkbox or button input*/
input[type=text],
input[type=email],
select,
textarea {
  width: 100%;
  padding: 7px;
  border-radius: 3px;
  border: 1px solid #ccc;
}

textarea {
  /* make text area 100px height */
  height: 100px;
}

/* style the button like the previous button by adding input[type=submit] to reusable btn css*/
.btn:link,
.btn:visited,
input[type=submit] {
  ...
}

/* same color when user click */
.btn-full:link,
.btn-full:visited,
input[type=submit] {
  ...
}
/* also add transition effect when hover with reusable btn css code*/
.btn:hover,
.btn:active,
input[type=submit]:hover,
input[type=submit]:active {
  background-color: #cf6d17;
}

input[type=checkbox] {
  /* add a little space around checkbox */
  margin: 10px 5px 10px 5px;
}

/* get rig of blue outline around input box with chrome default */
*:focus {
  outline: none;
}
```
---

# Building a Footer
- How to build a simple but effective footer
```html
<!-- footer -->
    <footer>
      <div class="row">
        <div class="col span-1-of-2">
          <ul class="footer-nav">
            <li><a href="#">About us</a></li>
            <li><a href="#">Blog</a></li>
            <li><a href="#">Press</a></li>
            <li><a href="#">IOS app</a></li>
            <li><a href="#">Android app</a></li>
          </ul>
        </div>
        <div class="col span-1-of-2">
            <ul class="social-links">
                <li><a href="#"><ion-icon class="facebook" name="logo-facebook"></ion-icon></a></li>
                <li><a href="#"><ion-icon class="twitter" name="logo-twitter"></ion-icon></a></li>
                <li><a href="#"><ion-icon class="googleplus" name="logo-googleplus"></ion-icon></a></li>
                <li><a href="#"><ion-icon class="instagram" name="logo-instagram"></ion-icon></a></li>
              </ul>
        </div>
      </div>
      <div class="row">
        <p>
          Copyright &copy; 2019 by Omnifood.  All rights reserved.
        </p>
      </div>
    </footer>
```
- A cool way of using social icons
```css
footer {
  /* darker background dark grey*/
  background-color: #333;
  padding: 50px;
  font-size: 80%;
}

.footer-nav {
  list-style: none;
  float: left;
}

.social-links {
  list-style: none;
  float: right;
}

/* nav li and social icon side by side */
.footer-nav li,
.social-links li {
  display: inline-block;
  margin-right: 20px;
}

.footer-nav li:last-child,
.social-links li:last-child {
  margin: 0;
}

.footer-nav li a:link,
.footer-nav li a:visited,
.social-links li a:link,
.social-links li a:visited {
  text-decoration: none;
  border: 0;
  color: #888;
  transition: color 0.2s;
}

/* hover effect nav */
.footer-nav li a:hover,
.footer-nav li a:active {
  color: #fff;
}

/* make social links a litter bigger */
.social-links a:link,
.social-links a:active {
  font-size: 160%;
}

.facebook,
.twitter,
.googleplus,
.instagram {
  transition: color 0.2s;
}

/* change social icon to corresponding color */
.facebook:hover {
  color: #3b5998;
}

.twitter:hover {
  color: #00aced;
}

.googleplus:hover {
  color: #dd4b39;
}

.instagram:hover {
  color: #3b5998;
}

footer p {
  color: #888;
  text-align: center;
  /* font-size: 90%; */
  margin-top: 20px;
}
```
---
# Making the website responsive part 1
Add media queries to corresponding breaking points
Create queries.css in the resources/css folder

```css
/* Big tablet to 1200px (widths smaller than the 1140px row) */
@media only screen and (max-width: 1200px) {
    .hero-text-box {
        width: 100%;
        padding: 0 2%;
    }

    .row {
        padding: 0 2%;
    }
}

/* Small tablet to big tablet: from 768px to 1023px */
@media only screen and (max-width: 1023px) {

    /* change font size in percentage */
    body {
        font-size: 18px;
    }

    /* change padding for each section */
    section {
        padding: 60px 0;
    }

    .long-copy {
        width: 80%;
        margin-left: 10%;
    }

}

/* Small phone to small tablets: from 481 to 767px */
@media only screen and (max-width: 767px) {}

/* Small phone: from 0 to 480px */
@media only screen and (max-width: 480px) {}
```

style.css
html,
body {
  phone screen stay still not moving
  ...
  overflow-x: hidden
}



# Cross Browsers Compatibility for CSS
The CSS prefixes are:
-webkit-  Android, Chrome, IOS, Safari\
-ms-     Internet explorer
-moz-   Firefox Mozilla
-o-     Opera

Example:
-webkit-border-radius: 25px;
-moz-border-radius: 25px;
-ms-border-radius: 25px;
-o-border-radius: 25px;
border-radius: 25px;

- Use extensions to add prefixes automatically
- vscode extensions - css-auto-prefix
- Works both for indented and single-line CSS styles. To activate it, just Ctrl+Shift+P into the workbench command window and type "Auto Prefix"

Test Omnifood on each browsers
  - ionic icons NOT showing on Internet Explorer
  - Test with Safari
    1. No ionic icons showing
    2. Testimonial text disappear

Older Browser
- include these 3 javascript cdn right before the closing body tag
<script src="https://cdn.jsdelivr.net/respond/1.4.2/respond.min.js"></script>
<script src="https://cdn.jsdelivr.net/html5shiv/3.7.2/html5shiv.min.js"></script>
<script src="https://cdn.jsdelivr.net/selectivizr/1.0.3b/selectivizr.min.js"></script>

-Use www.caniuse.com for CSS3 browser compatibility

---

# Cool Effects with jQuery

Webappers, huge list of plugins:
http://www.webappers.com/category/components/tool.ps/

jQuery Rain, another huge list of plugins:
http://www.jqueryrain.com/

Magnific popup:
http://dimsemenov.com/plugins/magnific-popup

Tooltipster:
http://iamceege.github.io/tooltipster/#demos
Maplace.js, google maps plugin:
http://maplacejs.com/
Typer, a plugin that types:
http://cosmos.layervault.com/typer-js.html
OnePageScroll:
http://www.thepetedesign.com/demos/onepage_scroll_demo.html

Include jQuery library before all the js scripts right above the body tag before
the website loaded
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js"></script>

---

# Build a 'Sticky' navigation Part 1
Add class="sticky" to nav tag
```css
.logo-black {
  /* hide black logo in normal stage */
  display: none;
  /* smaller black logo */
  height: 50px;
  width: auto;
  float: left;
  margin: 5px 0;
}
---
.sticky .main-nav {
  /* reduce margin top */
  margin-top: 18px;
}
.sticky .main-nav li a:link,
.sticky .main-nav li a:visited {
  padding: 23px 0;
  color: #555;
}

.sticky .logo {
  /* hide white logo in sticky stage */
  display: none;
}
.sticky .logo-black {
  /* display black logo in sticky stage */
  display: block;
}

```
---
# Build a 'Sticky' navigation Part 2
Remove 'sticky' class in the nav tag in index.html
Download jQuery waypoint and put it in the vendors/js folder
Include the script tag of jQuery waypoint at the bottom the index.html
 <script src="vendors/js/jquery.waypoints.min.js"></script>
Add js--section-features class the feature section in index.html
 <!-- display sticky nav at this section with js class -->
  <section class="section-features js--section-features">
In resources/js/script.js

```javascript
$(document).ready(function () {
    // select at this point of section features
    $('.js--section-features').waypoint(function (direction) {
        // if when user scroll down at this point
        if (direction == 'down') {
            // add sticky class
            $('nav').addClass('sticky');
        } else {
            // remove sticky class
            $('nav').removeClass('sticky');
        }

    }, {
        // 60px BEFORE it hits the .js--section-features
        offset: '60px'
    });
});

 /* Add z-index: 9999 to .sticky in css to make the sticky navigation the toppest layer */
.sticky {
  ...
  /* z-index - vertical stack layer.  the higher the number, the more top of layer 9999 is the highest value */
  z-index: 9999;
}
```
---
# Scroll to Elements
Define classes for buttons index.html
<a class="btn btn-full js--scroll-to-plans" href="#">I'm Hungry</a>
<a class="btn btn-ghost js--scroll-to-start" href="#">Show Me More</a>

In resources/js/script.js
```javascript
 /* Scroll on buttons */
    // select the button, when click, select html and body, animate by scroll to top of
    // selected section offset by 1 sec.
    $('.js--scroll-to-plans').click(function () {
        $('html, body').animate({
            // scroll to section plans
            scrollTop: $('.js--section-plans').offset().top
        }, 1000);
    });
    $('.js--scroll-to-start').click(function () {
        $('html, body').animate({
            // scroll to section features
            scrollTop: $('.js--section-features').offset().top
        }, 1000);
    });
    // click logo to scroll back to top
    $('.js--logo-black').click(function () {
        $('html, body').animate({
            // scroll to section features
            scrollTop: $('#top').offset().top
        }, 1000);
    });
```

Define id for navigation links
<li><a href="#features">... </li>
<li><a href="#works">... </li>
<li><a href="#cities">... </li>
<li><a href="#plans">... </li>

Now connect links to each section with id
<section class="section-features" id="features">
<section class="section-works" id="works">
<section class="section-cities" id="cities">
<section class="section-plans" id="plans">

Add third party scroll animation from https://css-tricks.com/snippets/jquery/smooth-scrolling/
```javascript
// Select all links with hashes
    $('a[href*="#"]')
        // Remove links that don't actually link to anything
        .not('[href="#"]')
        .not('[href="#0"]')
        .click(function (event) {
            // On-page links
            if (
                location.pathname.replace(/^\//, '') == this.pathname.replace(/^\//, '') &&
                location.hostname == this.hostname
            ) {
                // Figure out element to scroll to
                var target = $(this.hash);
                target = target.length ? target : $('[name=' + this.hash.slice(1) + ']');
                // Does a scroll target exist?
                if (target.length) {
                    // Only prevent default if animation is actually gonna happen
                    event.preventDefault();
                    $('html, body').animate({
                        scrollTop: target.offset().top
                    }, 1000, function () {
                        // Callback after animation
                        // Must change focus!
                        var $target = $(target);
                        $target.focus();
                        if ($target.is(":focus")) { // Checking if the target was focused
                            return false;
                        } else {
                            $target.attr('tabindex', '-1'); // Adding tabindex for elements not focusable
                            $target.focus(); // Set focus again
                        };
                    });
                }
            }
        });
```

---
# Add Animations on scroll
Animated.css
- Animate fadein for features rows
1. Define class js--wp-1 for features rows
2.  ```javascript
    /* Animations on scroll */    
    // features text fadein
    $('.js--wp-1').waypoint(function(direction){
        $('.js--wp-1').addClass('animated fadeIn');
    },
    {
        offset: '50%'
    });
    ``` 
3. Download animated.css and include in the head tag of index.html
  <!-- animated.css -->
  <link rel="stylesheet" type="text/css" href="vendors/css/animated.css" />
4. In style.css
  ```css
  /* ------------------------------- */
  /* Animations */
  /* ------------------------------- */
  /* in order to animate fadeIn we have to make it transparent  */
  .js--wp-1 {
    opacity: 0;
  }

  /* add class animated to .js--wp-1 */
  .js--wp-1 .animated {
    opacity: 1;
  }
  ```
Define class for iphone image slideInUp, cities fadeIn, and premium plan pulse for animation in index.html
<img src="resources/img/app-iPhone.png" alt="Omnifood app in iphone" class="app-screen js--wp-2" />

><div class="row js--wp-3">
      <!-- city -->
      <div class="col span-1-of-4 box">
        <img src="resources/img/lisbon-3.jpg" alt="Lisbon" />
        <h3>Lisbon</h3>
        <div class="city-feature">....
<section class="section-plans js--section-plans" id="plans">
    <div class="row">
      <h2>Start eating healthy today</h2>
    </div>
    <div class="row">
      <!-- premium meal plan -->
      <div class="col span-1-of-3">
>       <div class="plan-box js--wp-4">

In style.css
```css
.js--wp-1,
.js--wp-2,
.js--wp-3 {
  opacity: 0;

  -webkit-animation-duration: 1s;
  animation-duration: 1s;
}

.js-wp-4 {
  -webkit-animation-duration: 1s;
  animation-duration: 1s;
}

/* add class animated to .js--wp-1 */
.js--wp-1 .animated,
.js--wp-2 .animated,
.js--wp-3 .animated {
  opacity: 1;
}
```
# Making the navigation responsive
```css
    /* ----- mobile nav hamburger ------ */
    .mobile-nav-icon {
        display: inline-block;
    }

    .main-nav {
        float: left;
        /* reduce margin top and left */
        margin-top: 30px;
        margin-left: 25px;
    }

    .main-nav li {
        display: block;
    }

    .main-nav li a:link,
    .main-nav li a:visited {
        /* link stacks one on top each other */
        display: block;
        /* no underline border */
        border: 0;
        /* space between each link */
        padding: 10px 0;
        /* increase font size */
        font-size: 100%;

    }


    /* ----- mobile nav end ------ */
```
---
# Making a favicon for your website tab in the browser
Go to https://realfavicongenerator.net/ to generate a favicon icon
Download and unzip favicons and place in resources/favicons
Include the links in head tag right below the title tag.
```html
<title>Omni Food</title>
  <!-- favicons -->
  <link rel="apple-touch-icon" sizes="180x180" href="resources/favicons/apple-touch-icon.png">
  <link rel="icon" type="image/png" sizes="32x32" href="resources/favicons/favicon-32x32.png">
  <link rel="icon" type="image/png" sizes="16x16" href="resources/favicons/favicon-16x16.png">
  <link rel="manifest" href="resources/favicons/site.webmanifest">
  <link rel="mask-icon" href="resources/favicons/safari-pinned-tab.svg" color="#5bbad5">
  <meta name="msapplication-TileColor" content="#da532c">
  <meta name="theme-color" content="#ffffff">
</head>

```
--- 
# Optimize Performance Your Website
Optimize heavy picture
- resize with width pixels
- compress huge images with optimizilla.com now it's https://imagecompressor.com/


Minify CSS and jQuery code

- Use this website to minify css.  Use it in production only because it's hard to read the css file
https://cssminifier.com/

---

This project is under MIT License

Copyright 2018

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
S
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE