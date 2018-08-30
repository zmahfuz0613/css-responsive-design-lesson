---
title: Responsive design
type: lesson
duration: "1:25"
creator:
    name: Tony Guererro
    city: LA
competencies: Front-end intro
---

# Responsive design

### Objectives
*After this lesson, students will be able to:*

- Describe media queries and how to write them
- Create rules that adjust styles for phones, tablets, and computers

### Preparation
*Before this lesson, students should already be able to:*

- Write basic HTML/CSS

## What is responsive design? Intro (10 mins)

"Responsive Design" is the strategy of making a site that "responds" to the browser and device that it is being shown on... by looking awesome no matter what.

Or, the dryer Wikipedia definition:

"Responsive web design (RWD) is a web design approach aimed at crafting sites to provide an optimal viewing experience—easy reading and navigation with a minimum of resizing, panning, and scrolling—across a wide range of devices (from mobile phones to desktop computer monitors).""

#### More devices

Not that long ago, building a successful online presence meant just ensuring that your website worked correctly in all the major desktop browsers.

Fast forward to today, and the desktop computer is dying, more than 71% of the US population own a smartphone:

- **195 million** tablet devices were sold in 2013.
- The number of active mobile devices and human beings crossed over somewhere around the [7.19 billion mark](http://www.independent.co.uk/life-style/gadgets-and-tech/news/there-are-officially-more-mobile-devices-than-people-in-the-world-9780518.html).
- New devices like iWatches are changing the game too
- "Having a mobile friendly website is no longer just important, it’s critical.", [Forbes Ecommerce Marketing Checklist for 2013](http://www.forbes.com/sites/brentgleeson/2013/03/14/ecommerce-marketing-checklist-for-2013/)



## How to do Responsive Design wrong - Demo (10 mins)

If you're not planning before you begin to create a responsive design, you'r doing it wrong. Changing a web platform to a mobile platform is much more difficult than going from mobile to web.

#### Examples of non-responsive sites:

It is becoming harder and harder to find non-responsive websites.

- [Space Jam](https://www.warnerbros.com/archive/spacejam/movie/jam.htm)

> Note: Have students find examples of non-responsive sites.

#### Examples of responsive sites:

- [Monocle](https://monocle.com/)  
- [GA](https://generalassemb.ly/)
- [Farfetch](https://www.farfetch.com/)
- [Boston Globe](https://www.bostonglobe.com/)

What's the difference between these? Let's resize again.
Interestingly, **Boston Globe was the first example of a responsive website.**

#### Chrome's new developer tools

There is a really helpful tool in the Google Chrome developer tools:

- Let's visit GA's homepage
- Click on the device icon next to the magnifying glass
- You can change the pixel width (displayed at the top) using the drag tool
- You can select any device using the dropdown menu at the top


## Make a responsive website - Codealong (15 mins)

Download the [starter-code](starter-code)

Now open everything in Sublime Text and add the contents of a [reset.css](http://cssreset.com/) to the reset stylesheet.

#### Add some HTML

Now let's add some html into the index.html file:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Mobile-First Responsive Design</title>
  <link href='http://fonts.googleapis.com/css?family=Montserrat:400,700' rel='stylesheet' type='text/css'>
  <script type="text/javascript" src="./js/app.js"></script>
  <link rel="stylesheet" type="text/css" href="./stylesheets/reset.css">
  <link rel="stylesheet" type="text/css" href="./stylesheets/style.css">
</head>
<body>
<header>
  <div class="filler">Header Content</div>
</header>

<section>
  <article class="column">
    <h2>Exciting content</h2>
    <p>Web development is so fun...</p>
  </article>
  <article class="column">
    <h2>More content</h2>
    <p>Device testing is quite tedious...</p>
  </article>
  <article class="column">
    <h2>Even more content</h2>
    <p>But it has to be done now...</p>
  </article>
</section>
<aside>
  <div class="filler">Aside Content</div>
</aside>
<footer>
  <div class="filler">Footer Content</div>
</footer>
</body>
</html>
```
And then add some CSS:

```css
/*This applies from 0px to 600px --> MOBILE */
*, *:before, *:after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body {
  height: 100%;
}

body {
  background: darksalmon;
  font-family: 'Roboto', sans-serif;
  color: #141414;
}

```


## Media Queries and Mobile First Design

In order to have your content fit the screens of different devices automatically, we need to use media-queries.

What the heck is a media query? From [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries):

"A media query consists of a media type and at least one expression that limits the style sheets' scope by using media features, such as width, height, and color."

As there are lots of different devices, there can be lots of different media-queries.

- [CSS-Tricks](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/) is a good resource for reading up and refreshing yourself on media-queries.

```css
/* This applies from 600px onwards --> DESKTOP */
@media (min-width: 600px) {
    html,
    body {
      background: azure;
    }
}
```

## Mobile First = Content First

The mobile-first approach is exactly as it sounds: designing for the smallest screen and working your way up. The key to a mobile-first approach is a content centered one.

Since mobile has the most limitations (e.g. screen size and bandwidth), designing within these parameters in mind forces you to prioritize content ruthlessly.

Mobile first is additive.

## Using media queries in a mobile first approach - Codealong (25 mins)

When using a mobile-first approach you only need one media-query. This is the syntax:

#### Min-width 600px

```css
/*This applies from 0px to 600px*/
html,
body {
  /*background: red;*/
  height: 100%;
}

/*This applies from 600px onwards*/
@media (min-width: 600px) {  
  html,
  body {
    /*background: green;*/
    height: 100%;
  }
}
```

## On your phone - Codealong (10 mins)

Well if we want to check out the site, we'd have to upload the file to a web server; but this will be a pain, so let's run a little server from our computers and check out our site on our phones.

Run the following in the folder where you saved your index.html  

```bash
python -m SimpleHTTPServer  
```

To check it out on your computer go to:

```
http://0.0.0.0:8000
```

Great you are running a simple web server!

If your computer and phone share the same WiFi network, you can check out the site on your phone.  First, we need the ip address of our computer.

Type in `ifconfig` in the terminal. There should be something like:

```bash
inet 10.0.1.85
```

On your phone if you goto:

```
http://10.0.1.85:8000
```

and you should see your awesome website.

#### Meta viewport

Well, it will probably look like it does on your desktop.

Mobile devices are clever: they pretend they have a width of 960px and scale the website.  We need to override this and force the mobile to respond to our media queries.

Put the following code into our header.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Now, recheck to see your awesome, responsive website!

##Conclusion (5 mins)

As noted earlier in the lesson, since mobile is increasingly becoming the user default, any project should consider mobile styling from the start.  

Also, note that images and tables are often difficult to make responsive.

Since images sometimes stretch or "squish", `max-width` is your friend. Sometimes it may be more sensible to serve different images for different devise sizes: a 1200px image doesn't make sense to load on a mobile device.

Though we won't cover this explicitly in this lesson, consider this while your building in the future.

- Describe media queries.
- Identify the different tools you can use to practice responsive design.
- What are the steps to ensure mobile devises are using media queries when loading your web app?
