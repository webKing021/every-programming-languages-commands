# CSS Commands Reference

## CSS Integration

```css
/* External CSS file (styles.css) */

/* Internal CSS (within HTML <style> tags) */
<style>
  /* CSS rules go here */
</style>

/* Inline CSS (within HTML element) */
<div style="color: blue; margin: 20px;">Content</div>

/* Import other CSS files */
@import url('other-stylesheet.css');
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
```

## Selectors

```css
/* Element selector */
div { color: blue; }

/* Class selector */
.classname { color: blue; }

/* ID selector */
#idname { color: blue; }

/* Universal selector */
* { margin: 0; padding: 0; }

/* Attribute selector */
[type="text"] { border: 1px solid gray; }
[data-value] { color: blue; }
[class^="prefix"] { font-weight: bold; }  /* Starts with */
[class$="suffix"] { font-style: italic; }  /* Ends with */
[class*="contains"] { text-decoration: underline; }  /* Contains */

/* Descendant selector */
div p { color: blue; }

/* Child selector */
div > p { color: blue; }

/* Adjacent sibling selector */
h1 + p { color: blue; }

/* General sibling selector */
h1 ~ p { color: blue; }

/* Multiple selectors */
h1, h2, .title { color: blue; }

/* Pseudo-classes */
a:link { color: blue; }
a:visited { color: purple; }
a:hover { color: red; }
a:active { color: green; }

input:focus { border-color: blue; }
p:first-child { font-weight: bold; }
p:last-child { font-style: italic; }
p:nth-child(odd) { background-color: #f0f0f0; }
p:nth-child(even) { background-color: #e0e0e0; }
p:nth-child(3n+1) { text-decoration: underline; }
p:nth-last-child(2) { color: red; }

div:empty { display: none; }
input:checked { border: 2px solid green; }
input:disabled { background-color: #f0f0f0; }
input:enabled { background-color: white; }
input:required { border-color: red; }
input:optional { border-color: gray; }
input:valid { border-color: green; }
input:invalid { border-color: red; }

/* Pseudo-elements */
p::first-line { font-weight: bold; }
p::first-letter { font-size: 2em; }
::selection { background-color: yellow; }
::placeholder { color: gray; }
::before { content: "Before"; }
::after { content: "After"; }

/* Combinators */
.container .item { margin: 10px; }  /* Descendant */
.container > .item { padding: 5px; }  /* Child */
h2 + p { font-weight: bold; }  /* Adjacent sibling */
h2 ~ p { color: gray; }  /* General sibling */
```

## Box Model

```css
/* Width and height */
.box {
  width: 100px;
  height: 100px;
  min-width: 50px;
  max-width: 200px;
  min-height: 50px;
  max-height: 200px;
}

/* Margin */
.box {
  margin: 10px;  /* All sides */
  margin: 10px 20px;  /* Top/bottom, left/right */
  margin: 10px 20px 30px;  /* Top, left/right, bottom */
  margin: 10px 20px 30px 40px;  /* Top, right, bottom, left (clockwise) */
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 30px;
  margin-left: 40px;
  margin: 0 auto;  /* Center horizontally */
}

/* Padding */
.box {
  padding: 10px;  /* All sides */
  padding: 10px 20px;  /* Top/bottom, left/right */
  padding: 10px 20px 30px;  /* Top, left/right, bottom */
  padding: 10px 20px 30px 40px;  /* Top, right, bottom, left (clockwise) */
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 30px;
  padding-left: 40px;
}

/* Border */
.box {
  border: 1px solid black;  /* Width, style, color */
  border-width: 1px;
  border-style: solid;
  border-color: black;
  
  border-top: 1px solid black;
  border-right: 2px dashed red;
  border-bottom: 3px dotted green;
  border-left: 4px double blue;
  
  border-width: 1px 2px 3px 4px;  /* Top, right, bottom, left */
  border-style: solid dashed dotted double;  /* Top, right, bottom, left */
  border-color: black red green blue;  /* Top, right, bottom, left */
  
  border-top-width: 1px;
  border-top-style: solid;
  border-top-color: black;
  
  border-radius: 10px;  /* All corners */
  border-radius: 10px 20px;  /* Top-left/bottom-right, top-right/bottom-left */
  border-radius: 10px 20px 30px;  /* Top-left, top-right/bottom-left, bottom-right */
  border-radius: 10px 20px 30px 40px;  /* Top-left, top-right, bottom-right, bottom-left (clockwise) */
  border-top-left-radius: 10px;
  border-top-right-radius: 20px;
  border-bottom-right-radius: 30px;
  border-bottom-left-radius: 40px;
}

/* Box sizing */
.box {
  box-sizing: content-box;  /* Default */
  box-sizing: border-box;  /* Include padding and border in width/height */
}

/* Outline */
.box {
  outline: 1px solid red;  /* Width, style, color */
  outline-width: 1px;
  outline-style: solid;
  outline-color: red;
  outline-offset: 2px;  /* Space between border and outline */
}
```

## Display and Positioning

```css
/* Display */
.element {
  display: block;
  display: inline;
  display: inline-block;
  display: flex;
  display: grid;
  display: table;
  display: none;
}

/* Visibility */
.element {
  visibility: visible;
  visibility: hidden;  /* Takes up space but not visible */
  opacity: 0.5;  /* 50% transparent */
}

/* Position */
.element {
  position: static;  /* Default */
  position: relative;  /* Relative to normal position */
  position: absolute;  /* Relative to nearest positioned ancestor */
  position: fixed;  /* Relative to viewport */
  position: sticky;  /* Hybrid of relative and fixed */
  
  top: 10px;
  right: 20px;
  bottom: 30px;
  left: 40px;
  z-index: 10;  /* Stacking order */
}

/* Float */
.element {
  float: left;
  float: right;
  float: none;
  clear: left;
  clear: right;
  clear: both;
  clear: none;
}

/* Overflow */
.container {
  overflow: visible;  /* Default */
  overflow: hidden;  /* Clip content */
  overflow: scroll;  /* Always show scrollbars */
  overflow: auto;  /* Show scrollbars when needed */
  
  overflow-x: auto;  /* Horizontal overflow */
  overflow-y: auto;  /* Vertical overflow */
}
```

## Flexbox

```css
/* Container properties */
.flex-container {
  display: flex;
  display: inline-flex;
  
  flex-direction: row;  /* Default: left to right */
  flex-direction: row-reverse;  /* Right to left */
  flex-direction: column;  /* Top to bottom */
  flex-direction: column-reverse;  /* Bottom to top */
  
  flex-wrap: nowrap;  /* Default: single line */
  flex-wrap: wrap;  /* Multiple lines */
  flex-wrap: wrap-reverse;  /* Multiple lines, reversed */
  
  flex-flow: row nowrap;  /* Shorthand for flex-direction and flex-wrap */
  
  justify-content: flex-start;  /* Default: items at start */
  justify-content: flex-end;  /* Items at end */
  justify-content: center;  /* Items at center */
  justify-content: space-between;  /* Items with space between */
  justify-content: space-around;  /* Items with space around */
  justify-content: space-evenly;  /* Items with equal space */
  
  align-items: stretch;  /* Default: stretch to fill container */
  align-items: flex-start;  /* Items at start of cross axis */
  align-items: flex-end;  /* Items at end of cross axis */
  align-items: center;  /* Items at center of cross axis */
  align-items: baseline;  /* Items aligned by text baseline */
  
  align-content: flex-start;  /* Lines at start */
  align-content: flex-end;  /* Lines at end */
  align-content: center;  /* Lines at center */
  align-content: space-between;  /* Lines with space between */
  align-content: space-around;  /* Lines with space around */
  align-content: stretch;  /* Lines stretch to fill container */
  
  gap: 10px;  /* Gap between items */
  row-gap: 10px;  /* Gap between rows */
  column-gap: 20px;  /* Gap between columns */
}

/* Item properties */
.flex-item {
  order: 0;  /* Default order (can be negative) */
  
  flex-grow: 0;  /* Default: don't grow */
  flex-grow: 1;  /* Grow to fill available space */
  
  flex-shrink: 1;  /* Default: can shrink */
  flex-shrink: 0;  /* Don't shrink */
  
  flex-basis: auto;  /* Default size before growing/shrinking */
  flex-basis: 100px;  /* Specific size */
  
  flex: 0 1 auto;  /* Shorthand for flex-grow, flex-shrink, flex-basis */
  flex: 1;  /* Same as flex: 1 1 0% */
  
  align-self: auto;  /* Default: inherit from container */
  align-self: flex-start;  /* Override container alignment */
  align-self: flex-end;
  align-self: center;
  align-self: baseline;
  align-self: stretch;
}
```

## Grid

```css
/* Container properties */
.grid-container {
  display: grid;
  display: inline-grid;
  
  grid-template-columns: 100px 200px 100px;  /* 3 columns with fixed widths */
  grid-template-columns: 1fr 2fr 1fr;  /* 3 columns with fractional widths */
  grid-template-columns: repeat(3, 1fr);  /* 3 equal columns */
  grid-template-columns: minmax(100px, 1fr) 2fr;  /* Min/max width for first column */
  grid-template-columns: auto 1fr auto;  /* Auto-sized columns */
  
  grid-template-rows: 100px 200px;  /* 2 rows with fixed heights */
  grid-template-rows: 1fr 2fr;  /* 2 rows with fractional heights */
  grid-template-rows: repeat(3, 100px);  /* 3 equal rows */
  grid-template-rows: minmax(100px, auto);  /* Min height for row */
  
  grid-template-areas:
    "header header header"
    "sidebar content content"
    "footer footer footer";
  
  grid-template: 100px 1fr 100px / 1fr 3fr;  /* Shorthand for rows / columns */
  
  grid-auto-columns: 100px;  /* Size for auto-generated columns */
  grid-auto-rows: 100px;  /* Size for auto-generated rows */
  
  grid-auto-flow: row;  /* Default: fill rows first */
  grid-auto-flow: column;  /* Fill columns first */
  grid-auto-flow: dense;  /* Fill in gaps */
  
  justify-items: stretch;  /* Default: items fill cell width */
  justify-items: start;  /* Items at start of cell */
  justify-items: end;  /* Items at end of cell */
  justify-items: center;  /* Items at center of cell */
  
  align-items: stretch;  /* Default: items fill cell height */
  align-items: start;  /* Items at top of cell */
  align-items: end;  /* Items at bottom of cell */
  align-items: center;  /* Items at center of cell */
  
  justify-content: start;  /* Grid at start of container */
  justify-content: end;  /* Grid at end of container */
  justify-content: center;  /* Grid at center of container */
  justify-content: stretch;  /* Grid stretches to fill container */
  justify-content: space-between;  /* Equal space between columns */
  justify-content: space-around;  /* Equal space around columns */
  justify-content: space-evenly;  /* Equal space between and around columns */
  
  align-content: start;  /* Grid at top of container */
  align-content: end;  /* Grid at bottom of container */
  align-content: center;  /* Grid at center of container */
  align-content: stretch;  /* Grid stretches to fill container */
  align-content: space-between;  /* Equal space between rows */
  align-content: space-around;  /* Equal space around rows */
  align-content: space-evenly;  /* Equal space between and around rows */
  
  gap: 10px;  /* Gap between rows and columns */
  row-gap: 10px;  /* Gap between rows */
  column-gap: 20px;  /* Gap between columns */
}

/* Item properties */
.grid-item {
  grid-column-start: 1;  /* Start at column line 1 */
  grid-column-end: 3;  /* End at column line 3 */
  grid-column: 1 / 3;  /* Shorthand for start / end */
  grid-column: 1 / span 2;  /* Start at 1, span 2 columns */
  grid-column: 2;  /* Occupy column 2 */
  
  grid-row-start: 1;  /* Start at row line 1 */
  grid-row-end: 3;  /* End at row line 3 */
  grid-row: 1 / 3;  /* Shorthand for start / end */
  grid-row: 1 / span 2;  /* Start at 1, span 2 rows */
  grid-row: 2;  /* Occupy row 2 */
  
  grid-area: 1 / 1 / 3 / 3;  /* row-start / column-start / row-end / column-end */
  grid-area: header;  /* Named area from grid-template-areas */
  
  justify-self: stretch;  /* Default: fill cell width */
  justify-self: start;  /* Item at start of cell */
  justify-self: end;  /* Item at end of cell */
  justify-self: center;  /* Item at center of cell */
  
  align-self: stretch;  /* Default: fill cell height */
  align-self: start;  /* Item at top of cell */
  align-self: end;  /* Item at bottom of cell */
  align-self: center;  /* Item at center of cell */
}
```

## Typography

```css
/* Font properties */
.text {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;
  font-weight: normal;
  font-weight: bold;
  font-weight: 400;  /* 100 to 900 */
  font-style: normal;
  font-style: italic;
  font-variant: normal;
  font-variant: small-caps;
  font-stretch: normal;
  font-stretch: condensed;
  font-stretch: expanded;
  
  /* Shorthand */
  font: italic bold 16px/1.5 Arial, sans-serif;  /* style weight size/line-height family */
}

/* Text properties */
.text {
  color: red;
  color: #ff0000;
  color: rgb(255, 0, 0);
  color: rgba(255, 0, 0, 0.5);  /* With alpha */
  color: hsl(0, 100%, 50%);
  color: hsla(0, 100%, 50%, 0.5);  /* With alpha */
  
  text-align: left;
  text-align: right;
  text-align: center;
  text-align: justify;
  
  text-decoration: none;
  text-decoration: underline;
  text-decoration: overline;
  text-decoration: line-through;
  text-decoration: underline red wavy;  /* line, color, style */
  
  text-transform: none;
  text-transform: capitalize;
  text-transform: uppercase;
  text-transform: lowercase;
  
  text-indent: 20px;
  
  letter-spacing: 2px;
  word-spacing: 4px;
  
  line-height: 1.5;
  line-height: 24px;
  
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);  /* h-offset v-offset blur color */
  
  white-space: normal;
  white-space: nowrap;
  white-space: pre;
  white-space: pre-wrap;
  white-space: pre-line;
  
  word-break: normal;
  word-break: break-all;
  word-break: keep-all;
  
  overflow-wrap: normal;
  overflow-wrap: break-word;
  
  text-overflow: clip;
  text-overflow: ellipsis;
  
  writing-mode: horizontal-tb;  /* Default */
  writing-mode: vertical-rl;
  writing-mode: vertical-lr;
  
  direction: ltr;  /* Left to right */
  direction: rtl;  /* Right to left */
}

/* Lists */
ul, ol {
  list-style-type: disc;  /* Default for ul */
  list-style-type: circle;
  list-style-type: square;
  list-style-type: decimal;  /* Default for ol */
  list-style-type: decimal-leading-zero;
  list-style-type: lower-roman;
  list-style-type: upper-roman;
  list-style-type: lower-alpha;
  list-style-type: upper-alpha;
  list-style-type: none;
  
  list-style-position: outside;  /* Default */
  list-style-position: inside;
  
  list-style-image: url('bullet.png');
  
  /* Shorthand */
  list-style: square inside url('bullet.png');  /* type position image */
}
```

## Background

```css
.element {
  background-color: red;
  background-color: transparent;
  
  background-image: url('image.jpg');
  background-image: linear-gradient(to right, red, blue);
  background-image: radial-gradient(circle, red, blue);
  background-image: repeating-linear-gradient(45deg, red, blue 10%);
  background-image: repeating-radial-gradient(circle, red, blue 10%);
  background-image: conic-gradient(from 45deg, red, blue);
  
  background-repeat: repeat;  /* Default */
  background-repeat: repeat-x;
  background-repeat: repeat-y;
  background-repeat: no-repeat;
  background-repeat: space;  /* Evenly distributed with no clipping */
  background-repeat: round;  /* Stretched to avoid gaps */
  
  background-position: left top;  /* Default */
  background-position: center;
  background-position: 50% 50%;
  background-position: 20px 30px;
  
  background-size: auto;  /* Default */
  background-size: cover;  /* Cover entire area, may crop image */
  background-size: contain;  /* Fit entire image, may leave empty space */
  background-size: 200px 100px;
  background-size: 50% 50%;
  
  background-attachment: scroll;  /* Default: scrolls with content */
  background-attachment: fixed;  /* Fixed to viewport */
  background-attachment: local;  /* Scrolls with element's contents */
  
  background-origin: padding-box;  /* Default: starts at padding edge */
  background-origin: border-box;  /* Starts at border edge */
  background-origin: content-box;  /* Starts at content edge */
  
  background-clip: border-box;  /* Default: extends to outer border edge */
  background-clip: padding-box;  /* Clipped to padding edge */
  background-clip: content-box;  /* Clipped to content edge */
  background-clip: text;  /* Clipped to text */
  
  /* Shorthand */
  background: red url('image.jpg') no-repeat center / cover fixed;  /* color image repeat position/size attachment */
  
  /* Multiple backgrounds */
  background: url('image1.jpg') no-repeat center,
              url('image2.jpg') no-repeat bottom / 100% 50%,
              linear-gradient(to right, rgba(255,0,0,0.5), rgba(0,0,255,0.5));
}
```

## Transforms

```css
.element {
  transform: translate(50px, 100px);  /* Move right 50px, down 100px */
  transform: translateX(50px);  /* Move right 50px */
  transform: translateY(100px);  /* Move down 100px */
  transform: translateZ(10px);  /* Move forward 10px (3D) */
  transform: translate3d(50px, 100px, 10px);  /* 3D translation */
  
  transform: scale(2);  /* Scale to 200% */
  transform: scale(2, 0.5);  /* Scale width 200%, height 50% */
  transform: scaleX(2);  /* Scale width 200% */
  transform: scaleY(0.5);  /* Scale height 50% */
  transform: scaleZ(0.5);  /* Scale depth 50% (3D) */
  transform: scale3d(2, 0.5, 1);  /* 3D scaling */
  
  transform: rotate(45deg);  /* Rotate 45 degrees clockwise */
  transform: rotateX(45deg);  /* Rotate around X-axis (3D) */
  transform: rotateY(45deg);  /* Rotate around Y-axis (3D) */
  transform: rotateZ(45deg);  /* Same as rotate(45deg) */
  transform: rotate3d(1, 1, 1, 45deg);  /* 3D rotation */
  
  transform: skew(10deg, 20deg);  /* Skew X by 10deg, Y by 20deg */
  transform: skewX(10deg);  /* Skew horizontally */
  transform: skewY(20deg);  /* Skew vertically */
  
  transform: matrix(1, 0.5, 0.5, 1, 50, 20);  /* 2D transformation matrix */
  transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1);  /* 3D matrix */
  
  /* Multiple transforms */
  transform: translate(50px, 50px) rotate(45deg) scale(2);
  
  /* Transform origin */
  transform-origin: center;  /* Default */
  transform-origin: top left;
  transform-origin: 50px 50px;
  transform-origin: 50% 50%;
  transform-origin: 50% 50% 0;  /* With Z-axis for 3D */
  
  /* 3D settings */
  transform-style: flat;  /* Default: children don't preserve 3D */
  transform-style: preserve-3d;  /* Children maintain 3D positioning */
  
  perspective: 1000px;  /* Depth of 3D scene */
  perspective-origin: center;  /* Vanishing point */
  
  backface-visibility: visible;  /* Default: show back side */
  backface-visibility: hidden;  /* Hide back side */
}
```

## Transitions

```css
.element {
  transition-property: all;  /* Properties to transition */
  transition-property: transform, opacity;  /* Multiple properties */
  
  transition-duration: 1s;  /* Duration of transition */
  transition-duration: 0.5s, 1s;  /* Different durations for properties */
  
  transition-timing-function: ease;  /* Default timing */
  transition-timing-function: linear;  /* Constant speed */
  transition-timing-function: ease-in;  /* Slow start */
  transition-timing-function: ease-out;  /* Slow end */
  transition-timing-function: ease-in-out;  /* Slow start and end */
  transition-timing-function: cubic-bezier(0.1, 0.7, 1.0, 0.1);  /* Custom curve */
  transition-timing-function: steps(5, end);  /* Step function */
  
  transition-delay: 0s;  /* Default: no delay */
  transition-delay: 0.5s;  /* Wait before starting */
  transition-delay: 0.5s, 1s;  /* Different delays for properties */
  
  /* Shorthand */
  transition: all 1s ease 0s;  /* property duration timing-function delay */
  transition: transform 0.5s ease-out, opacity 1s linear;  /* Multiple transitions */
}
```

## Animations

```css
/* Keyframe definition */
@keyframes slide-in {
  0% {  /* or 'from' */
    transform: translateX(-100%);
    opacity: 0;
  }
  100% {  /* or 'to' */
    transform: translateX(0);
    opacity: 1;
  }
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.2); }
  100% { transform: scale(1); }
}

/* Animation properties */
.element {
  animation-name: slide-in;  /* Name of @keyframes */
  
  animation-duration: 1s;  /* Duration of animation */
  
  animation-timing-function: ease;  /* Default timing */
  animation-timing-function: linear;
  animation-timing-function: ease-in;
  animation-timing-function: ease-out;
  animation-timing-function: ease-in-out;
  animation-timing-function: cubic-bezier(0.1, 0.7, 1.0, 0.1);
  animation-timing-function: steps(5, end);
  
  animation-delay: 0s;  /* Default: no delay */
  animation-delay: 0.5s;  /* Wait before starting */
  
  animation-iteration-count: 1;  /* Default: play once */
  animation-iteration-count: 3;  /* Play 3 times */
  animation-iteration-count: infinite;  /* Loop forever */
  
  animation-direction: normal;  /* Default: forward */
  animation-direction: reverse;  /* Backward */
  animation-direction: alternate;  /* Forward then backward */
  animation-direction: alternate-reverse;  /* Backward then forward */
  
  animation-fill-mode: none;  /* Default: no styles before/after */
  animation-fill-mode: forwards;  /* Retain end state */
  animation-fill-mode: backwards;  /* Apply first keyframe during delay */
  animation-fill-mode: both;  /* Both forwards and backwards */
  
  animation-play-state: running;  /* Default: playing */
  animation-play-state: paused;  /* Paused */
  
  /* Shorthand */
  animation: slide-in 1s ease 0s 1 normal forwards;  /* name duration timing-function delay iteration-count direction fill-mode */
  
  /* Multiple animations */
  animation: slide-in 1s ease, pulse 2s ease infinite;
}
```

## Media Queries

```css
/* Basic media query */
@media screen and (max-width: 768px) {
  /* Rules for screens <= 768px */
  body {
    font-size: 14px;
  }
}

/* Media types */
@media screen { /* For screens */ }
@media print { /* For printing */ }
@media speech { /* For screen readers */ }
@media all { /* Default: all media types */ }

/* Width and height */
@media (min-width: 768px) { /* Width >= 768px */ }
@media (max-width: 767px) { /* Width <= 767px */ }
@media (width: 768px) { /* Width exactly 768px */ }

@media (min-height: 600px) { /* Height >= 600px */ }
@media (max-height: 599px) { /* Height <= 599px */ }
@media (height: 600px) { /* Height exactly 600px */ }

/* Orientation */
@media (orientation: landscape) { /* Width > Height */ }
@media (orientation: portrait) { /* Height >= Width */ }

/* Aspect ratio */
@media (aspect-ratio: 16/9) { /* Exactly 16:9 */ }
@media (min-aspect-ratio: 16/9) { /* At least 16:9 */ }
@media (max-aspect-ratio: 16/9) { /* At most 16:9 */ }

/* Display quality */
@media (resolution: 300dpi) { /* Exactly 300 DPI */ }
@media (min-resolution: 300dpi) { /* At least 300 DPI */ }
@media (max-resolution: 300dpi) { /* At most 300 DPI */ }

/* Color */
@media (color) { /* Color device */ }
@media (min-color: 8) { /* At least 8 bits per color component */ }
@media (color-gamut: srgb) { /* At least sRGB gamut */ }
@media (color-gamut: p3) { /* At least Display P3 gamut */ }
@media (color-gamut: rec2020) { /* At least Rec. 2020 gamut */ }

/* Display features */
@media (hover: hover) { /* Hover capability */ }
@media (hover: none) { /* No hover capability */ }
@media (pointer: fine) { /* Precise pointer (mouse) */ }
@media (pointer: coarse) { /* Imprecise pointer (touch) */ }
@media (pointer: none) { /* No pointer */ }

/* Light level */
@media (prefers-color-scheme: dark) { /* Dark mode */ }
@media (prefers-color-scheme: light) { /* Light mode */ }

/* Motion preferences */
@media (prefers-reduced-motion: reduce) { /* Reduced motion */ }
@media (prefers-reduced-motion: no-preference) { /* No motion preference */ }

/* Logical operators */
@media (min-width: 768px) and (max-width: 1023px) { /* AND */ }
@media (max-width: 767px), (min-width: 1024px) { /* OR */ }
@media not (color) { /* NOT */ }

/* Nested media queries */
@media screen {
  .sidebar { width: 300px; }
  
  @media (max-width: 768px) {
    .sidebar { width: 100%; }
  }
}
```

## Variables (Custom Properties)

```css
/* Defining variables */
:root {
  --main-color: #3498db;
  --secondary-color: #2ecc71;
  --font-size-base: 16px;
  --spacing-unit: 8px;
  --border-radius: 4px;
}

/* Using variables */
.element {
  color: var(--main-color);
  margin: var(--spacing-unit);
  padding: calc(var(--spacing-unit) * 2);
  border-radius: var(--border-radius, 2px);  /* With fallback */
}

/* Scoped variables */
.dark-theme {
  --main-color: #2980b9;
  --text-color: white;
}

/* Media query variables */
@media (max-width: 768px) {
  :root {
    --font-size-base: 14px;
    --spacing-unit: 4px;
  }
}

/* JavaScript interaction */
/* In JS: element.style.setProperty('--dynamic-width', '500px'); */
.element {
  width: var(--dynamic-width, 100%);
}
```

## Filters

```css
.element {
  filter: blur(5px);  /* Gaussian blur */
  filter: brightness(150%);  /* Brightness adjustment */
  filter: contrast(200%);  /* Contrast adjustment */
  filter: grayscale(100%);  /* Convert to grayscale */
  filter: hue-rotate(90deg);  /* Rotate colors */
  filter: invert(100%);  /* Invert colors */
  filter: opacity(50%);  /* Transparency */
  filter: saturate(200%);  /* Saturation adjustment */
  filter: sepia(100%);  /* Convert to sepia */
  filter: drop-shadow(5px 5px 5px rgba(0,0,0,0.5));  /* Shadow effect */
  
  /* Multiple filters */
  filter: contrast(175%) brightness(103%) blur(1px);
  
  /* Backdrop filters (applied to background) */
  backdrop-filter: blur(10px);
  backdrop-filter: brightness(50%) blur(5px);
}
```

## Miscellaneous

```css
/* Cursor */
.element {
  cursor: auto;  /* Default */
  cursor: pointer;  /* Hand icon */
  cursor: text;  /* Text input */
  cursor: move;  /* Move icon */
  cursor: grab;  /* Grab icon */
  cursor: grabbing;  /* Grabbing icon */
  cursor: zoom-in;  /* Zoom in icon */
  cursor: zoom-out;  /* Zoom out icon */
  cursor: not-allowed;  /* Prohibited icon */
  cursor: wait;  /* Wait icon */
  cursor: progress;  /* Progress icon */
  cursor: help;  /* Help icon */
  cursor: crosshair;  /* Crosshair icon */
  cursor: url('custom-cursor.png'), auto;  /* Custom cursor */
}

/* User selection */
.element {
  user-select: auto;  /* Default */
  user-select: none;  /* Prevent selection */
  user-select: text;  /* Allow text selection */
  user-select: all;  /* Select all on click */
}

/* Pointer events */
.element {
  pointer-events: auto;  /* Default */
  pointer-events: none;  /* Element doesn't receive pointer events */
}

/* Resize */
.element {
  resize: none;  /* Default: no user resizing */
  resize: both;  /* Resize both width and height */
  resize: horizontal;  /* Resize width only */
  resize: vertical;  /* Resize height only */
}

/* Object fit (for images and videos) */
.element {
  object-fit: fill;  /* Default: stretch to fill */
  object-fit: contain;  /* Maintain aspect ratio, fit within box */
  object-fit: cover;  /* Maintain aspect ratio, cover box */
  object-fit: none;  /* Keep original size */
  object-fit: scale-down;  /* Like contain, but never scale up */
  
  object-position: center;  /* Position within box */
  object-position: top left;
  object-position: 50% 50%;
}

/* Scrollbar customization */
.element {
  scrollbar-width: auto;  /* Default */
  scrollbar-width: thin;  /* Thin scrollbar */
  scrollbar-width: none;  /* No scrollbar */
  
  scrollbar-color: #6969dd #e0e0e0;  /* thumb track */
}

/* Webkit scrollbar (Chrome, Safari, Edge) */
.element::-webkit-scrollbar {
  width: 12px;
  height: 12px;
}

.element::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 10px;
}

.element::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 10px;
}

.element::-webkit-scrollbar-thumb:hover {
  background: #555;
}

/* Appearance */
.element {
  appearance: none;  /* Remove browser styling */
}

/* Columns */
.element {
  columns: 3;  /* Number of columns */
  columns: 200px;  /* Width of columns */
  columns: 3 200px;  /* Count and width */
  
  column-gap: 20px;  /* Gap between columns */
  column-rule: 1px solid #ddd;  /* Line between columns */
  
  column-span: none;  /* Default: don't span columns */
  column-span: all;  /* Span all columns */
}

/* Counters */
body {
  counter-reset: section;  /* Initialize counter */
}

h2::before {
  counter-increment: section;  /* Increment counter */
  content: "Section " counter(section) ": ";  /* Display counter */
}

/* Content property */
.element::before {
  content: "Before";  /* Text content */
  content: url(icon.png);  /* Image content */
  content: attr(data-label);  /* Attribute value */
  content: counter(section);  /* Counter value */
  content: "";  /* Empty content */
  content: "\201C";  /* Unicode character (left double quote) */
}

/* Clipping and masking */
.element {
  clip-path: circle(50% at 50% 50%);  /* Circular clip */
  clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);  /* Diamond shape */
  clip-path: inset(10px 20px 30px 40px);  /* Inset rectangle */
  clip-path: url(#clip-path-id);  /* SVG clip path */
  
  mask-image: linear-gradient(to bottom, rgba(0,0,0,1), rgba(0,0,0,0));
  mask-image: url(mask.png);
}

/* Will-change (performance optimization) */
.element {
  will-change: transform;  /* Hint for animations */
  will-change: opacity, transform;
}

/* Caret (text cursor) */
.element {
  caret-color: red;  /* Color of text input cursor */
}

/* Print-specific styles */
@media print {
  .no-print {
    display: none;
  }
  
  a::after {
    content: " (" attr(href) ")";
  }
  
  @page {
    margin: 2cm;
    size: A4 portrait;
  }
}
```