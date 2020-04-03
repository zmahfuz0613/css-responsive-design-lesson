# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)  SOFTWARE ENGINEERING IMMERSIVE

# Responsive design

### Objectives
*After this lesson, students will be able to:*

- Describe media queries and how to write them
- Create rules that adjust styles for phones, tablets, and computers

### Preparation
*Before this lesson, students should already be able to:*

- Write basic HTML/CSS

## Introduction: Responsive Design

"Responsive Design" is the strategy of making a site that "responds" to the browser and device that it is being shown on... by looking awesome no matter what.

#### Responsive Design is _not_ Device-Specific

A responsive site doesn't just look good on the newest phone, watch, tablet, or mega-screen; it looks good on any screen. This might seem impossible, but it's relatively straightforward. All that's required is writing a series of rules, known as media queries, that check the size of the browser/device on which the site is being viewed, and adjust the CSS as needed.


## How to do Responsive Design wrong - Demo (10 mins)

If you're not planning before you begin to create a responsive design, you're doing it wrong. Changing a web platform to a mobile platform is much more difficult than going from mobile to web.

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
- You can select any device using the dropdown menu at the top



## Media Queries and Mobile First Design

In order to have your content fit the screens of different devices automatically, we need to use media-queries. Media queries are conditional style rules for the size of the browser/device rendering the site. 

#### Breakpoints

CSS breakpoints are points where the website content responds according to the device width, allowing you to show the best possible layout to the user.

The ideal option for deciding breakpoints is based on the content of your site. This method allows you to simply add breakpoints where your content needs layout adjustment. This will make your media query a lot simpler and manageable.

This breakpoint means the CSS will apply when the device width is 768px and above.

```css
@media (min-width: 768px){
 ...
}
```

#### When to use min-width or max-width

If you are designing your layout with a mobile-first approach, then use `min-width` breakpoints and work your way up.

Likewise, if you are designing for larger devices first, then set your default CSS as you normally would and adjust for smaller devices with the `max-width` approach.

#### Viewport Meta Tag

Mobile devices are clever: they pretend they have a width of 960px and scale the website.  We need to override this default behavior and force the mobile to respond to our media queries.

Put the following code into our header.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
This ensures that the viewport is the same as the screen, and displays at a natural zoom of 100%.

If you don't include this tag, the browser gets to choose the default viewport width and will not adhere to the correct media query style rules. In other words, a mobile browser might set its viewport width to `1080px` and display the layout meant for a screen that size.

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

## Demo / Codealong: Responsive Design

So how can we make more impactful changes to our site using media queries? The flexbox approach to layout eliminated the need to use media queries to adjust the grid on your page. But what if you're working on a project with existing code using float? And what about adjusting other elements on the page using media queries? It's important to understand all methods when approaching responsive design.

Consider this [HTML](codealong/albums/index.html) and [CSS](codealong/albums/css/main-1.css), which renders like this on a large screen:

![albums-1](assets/albums-1.png)

And like this on a small screen:

![albums-1-400](assets/albums-1-400.png)

The issues with the layout in the smaller screen rendering are evident, from the top of the page to the bottom:
- The `nav` takes up too much vertical space.
- The title and description are too large.
- The 6-column layout is too narrow for the content.

It's important that we work "big to small" – meaning we address the large layout concerns first, then work through the details of adjusting sizing. We also have to keep in mind that there may be some breakpoints in between a common desktop size and a common mobile size. For now, let's work on adding styles for a small screen size at `400px`.

One way to approach media queries is to start by adding in styles you want for the smaller size *at the end of your CSS document*. These styles will overwrite the rules above! Compare this [new CSS](codealong/albums/main-2.css) to the [previous CSS](codealong/albums/css/main-1.css) and see how it renders on a large screen:

![albums-2](assets/albums-2.png)

All content on the page is aligned in a single column, whether viewed on a small or large screen width. Now we need to specify **at which width** we want these styles to be applied. We can do this by adding in media queries to our [updated CSS](codealong/albums/main-3.css).

Here are the four different layouts as we reduce the screen size:

![albums-1](assets/albums-1.png)

![albums-3-med](assets/albums-3-med.png)

![albums-3-sm](assets/albums-3-sm.png)

![albums-3-xs](assets/albums-3-xs.png)

Now our layout looks great on all screen sizes! The final touch is to adjust the copy on the page. Here's the [final CSS](codealong/albums/main-4.css) and how it renders on a small screen:

![albums-4](assets/albums-4.png)

You can access all of the code [here](codealong/albums).

## Conclusion

As noted earlier in the lesson, since mobile is increasingly becoming the user default, any project should consider mobile styling from the start.  

Also, note that images and tables are often difficult to make responsive.

Since images sometimes stretch or "squish", `max-width` is your friend. Sometimes it may be more sensible to serve different images for different devise sizes: a 1200px image doesn't make sense to load on a mobile device.

Though we won't cover this explicitly in this lesson, consider this while your building in the future.

- Describe media queries.
- Identify the different tools you can use to practice responsive design.
- What are the steps to ensure mobile devises are using media queries when loading your web app?

## Additional Resources

### Exercises
- [Make the Dream Team Responsive!](independent-practice/starter-code)
  - [Check Your Work](independent-practice/solution-code)

### Videos
- [CSS Responsive Design](https://www.youtube.com/watch?v=BsuCBmzLf_U&list=PLdnONIhPScST0Vy4LrIZiYKpFNoxgyH7J&index=21)
- [CSS Responsive Design - Media Queries](https://www.youtube.com/watch?v=GYygtVolViM&list=PLdnONIhPScST0Vy4LrIZiYKpFNoxgyH7J&index=23)
- [CSS Mobile First - min/max-width/height](https://www.youtube.com/watch?v=iQIj7Lu64M4&index=22&list=PLdnONIhPScST0Vy4LrIZiYKpFNoxgyH7J)

### Readings
- [Responsive Web Design - An Original Introduction](http://alistapart.com/article/responsive-web-design)
- [Why You Don't Need Device Specific Breakpoints](https://responsivedesign.is/articles/why-you-dont-need-device-specific-breakpoints)
- [7 Habits of Highly Effective Media Queries](http://bradfrost.com/blog/post/7-habits-of-highly-effective-media-queries/)
- [Media Queries for Standard Devices](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)
- [Logical Operators in Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Logical_operators)
- [A Tale of Two Viewports](http://www.quirksmode.org/mobile/viewports.html)
- [Responsive Design Pattern Examples](https://bradfrost.github.io/this-is-responsive/patterns.html)
- [Complex Navigation Patterns for Responsive Design](http://bradfrost.com/blog/web/complex-navigation-patterns-for-responsive-design/)
- [mediaqueri.es - a collection of responsive site examples](http://mediaqueri.es/)
