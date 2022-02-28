---
template: blog-post
title: CSS's Modern Features
slug: /article-3
date: 2022-02-27 20:19
description: CSS's Modern Features
featuredImage: /assets/gatsby-starter-foundation-dark-mode.jpg
---


***Dark & Light Theming***

One of the most frequently requested app and website design features is dark mode. Dark mode has a number of potential advantages, including saving battery life and minimizing eye strain in low-light situations. Users can enable dark mode at the system level on most devices/operating systems. This normally works across the entire system, including both default and third-party applications.

**Using prefers-color-scheme in Media Queries**

                The prefers-color-scheme media query is used to determine the user's preferred color scheme in the OS. If you choose dark mode in your OS settings, for example, all websites that support dark mode will be shown in your preferred mode, using the CSS rules established in the preferences. There are two prefers-color-scheme values to choose from. Light - the user has indicated or has not expressed an active preference for a page that is in light mode. Dark – the user has indicated that they prefer a dark-mode website.

**How to Add User Choice Mode With prefers-color-scheme and JavaScript**

                Users who have set their color settings to dark mode on their operating system may nevertheless want to see some websites in light mode, and vice versa. Markup and Styles Configuration

* Create the simplified markup 

```HTML
<body>
   <div class="wrapper">
      <svg class="lightsaber first">...</svg>
      <svg class="lightsaber second">...</svg>
      <button class="btn">Toggle mode</button>
  </div>
</body>
```

* Use CSS variables to choose your colors and styles

```CSS
/* default, light mode styles set with variables */
:root {
   --color-background: #f9f9f9;
   --color-default: #000;
   --color-accent-1: deepskyblue;
   --color-accent-2: violet;
}

body{
   background-color: car(--color-background);
}

/* Toggle button */
.btn {
   background-color: var(--color-background);
   border: var(---color-default) solid 3px;
   color: var(--color-default);
}

/* SVG lightsabers */
.first-blade {
   fill: var(--color-accent-1);
}

.second-blade {
   fill: var(--color-accent-2);
}

.handle {
   fill: var(--color-default);
}
```

* After that, specify the dark mode styles.

  * It will be toggled or added automatically when a button is pressed to apply alternate dark mode color values to the full document.

```CSS
/*Dark-mode*/
.dark-mode .example-2 {
   --color-background: #000;
   --color-default: #f9f9f9;
   --color-accent-1: cyan;
   --color-accent-2: magenta;
}
```

***Fluid Typography***

                Color, contrast, size, font, alignment, and other characteristics that directly affect the style of text on a web page are referred to as typography. Contrast on a web page (focused on typography) can be defined as the difference in color between the text and the background. The size and kind of font are the two most important aspects of the font. The end strokes of serif typefaces are pointed, but the end strokes of sans-serif fonts are not. These two font types can have a significant impact on the reader's perception of your material.

**The Responsiveness of Fonts in Fluid Typography**

                Fluid typography makes typography responsive, meaning that as the screen size changes, the font size, font height, spacing, and other type parameters alter as well. No matter how much focus you have put up on the typography, all the hard work is down the drain if it is not fluid in nature.

**CSS Media Queries for Fluid Typography**

                The selectors used by media queries are used to determine the media device on which the website is rendered and apply the defined media rules to them. We may design a rule to modify the font size based on the current viewport of the device using fixed values in our media queries. By defining the font size in vw, we can avoid the calculation and rely solely on CSS to adjust the font to the viewport. The only issue with constant values is that they only function for a limited number of resolutions. If the resolution is too high, the font will be too large, which isn't always necessary.

```CSS
@media screen and (max-width: 840px) {
   p {
      color: red;
   }
}
```

**CSS Clamp Method for Fluid Typography**

                Two boundaries and a preferred value are required by the CSS Clamp function. These are the minimum and maximum boundaries. The function moves around these limits, picking a value from somewhere in the middle. The minimal bound is utilized if the desired values fall below the minimum bound. When it exceeds the maximum bound, on the other hand, the maximum bound is used.

```CSS
<style>
   p {
      font-size: clamp(12px, 40px, 200px);
      margin-top: 40px;
      text-align: center;
   }
</style>
```

***Responsive Units of Measurement and How to Use Them***

                When building a responsive website, CSS units are crucial. CSS Units are divided into two categories: absolute length unit and relative length unit

**Absolute Length Unit**

                It is a constant unit across all devices, but it may vary in screen resolution according to the DPI (dots per inch) of each screen. These units include:

* Px – pixel
* Pt – point
* Pc – picas
* In – inch
* Cm – centimeter
* Mm – millimeter

Pixels are a typical unit of measurement for developing a website's layout. It is dependent on the viewing device and has a consistent effect across a wide range of screen sizes. It's useful when creating a border since, unlike font sizes, we want it to stay the same across all screen sizes.

**Relative Length Unit**

                It does not have set sizes; instead, they are proportional to something, such as a parent element's font size or the size of a viewport. These units are useful since they modify the screen sizes. They include:

* Em – relative to font-size of the element
* Ex – relative to the x-height of the current font
* % - relative to the parent element
* Ch – relative to the width of zero
* Rem – relative to the root element
* Vw – the viewport width is relative to 1% of the width viewport (browser window)
* Vh – the viewport height is relative to 1% of the height viewport (browser window)
* Vmin – the viewport minimum is relative to 1% of the viewport(browser window) for smaller dimension
* Vmax – the viewport maximum is relative to 1% of the viewport (browser window) for larger dimension