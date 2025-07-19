# HTML Commands Reference

## Document Structure

```html
<!-- Basic HTML5 document structure -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document Title</title>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>

<!-- HTML comment -->
```

## Metadata Tags

```html
<!-- Character encoding -->
<meta charset="UTF-8">

<!-- Viewport for responsive design -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Page description -->
<meta name="description" content="Description of the page">

<!-- Keywords -->
<meta name="keywords" content="keyword1, keyword2, keyword3">

<!-- Author -->
<meta name="author" content="Author Name">

<!-- Refresh/redirect -->
<meta http-equiv="refresh" content="5; url=https://example.com">

<!-- Robots control -->
<meta name="robots" content="index, follow">

<!-- Open Graph Protocol (for social media) -->
<meta property="og:title" content="Title Here">
<meta property="og:description" content="Description Here">
<meta property="og:image" content="image.jpg">
<meta property="og:url" content="https://example.com">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@username">
<meta name="twitter:title" content="Title Here">
<meta name="twitter:description" content="Description Here">
<meta name="twitter:image" content="image.jpg">
```

## CSS and JavaScript Integration

```html
<!-- Internal CSS -->
<style>
    body { font-family: Arial, sans-serif; }
</style>

<!-- External CSS -->
<link rel="stylesheet" href="styles.css">

<!-- Internal JavaScript -->
<script>
    function myFunction() {
        console.log('Hello, world!');
    }
</script>

<!-- External JavaScript -->
<script src="script.js"></script>

<!-- Defer JavaScript loading -->
<script src="script.js" defer></script>

<!-- Async JavaScript loading -->
<script src="script.js" async></script>

<!-- Module JavaScript -->
<script type="module" src="module.js"></script>
```

## Text Formatting

```html
<!-- Headings -->
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>

<!-- Paragraphs -->
<p>This is a paragraph.</p>

<!-- Line break -->
<br>

<!-- Horizontal rule -->
<hr>

<!-- Bold text -->
<b>Bold text</b>
<strong>Strong text (semantically important)</strong>

<!-- Italic text -->
<i>Italic text</i>
<em>Emphasized text (semantically emphasized)</em>

<!-- Underlined text -->
<u>Underlined text</u>

<!-- Strikethrough -->
<s>Strikethrough text</s>
<del>Deleted text</del>

<!-- Subscript and superscript -->
<sub>Subscript</sub>
<sup>Superscript</sup>

<!-- Marked/highlighted text -->
<mark>Highlighted text</mark>

<!-- Small text -->
<small>Small text</small>

<!-- Abbreviation -->
<abbr title="HyperText Markup Language">HTML</abbr>

<!-- Citation -->
<cite>Citation</cite>

<!-- Definition -->
<dfn>Definition term</dfn>

<!-- Code -->
<code>Computer code</code>
<pre>Preformatted text</pre>
<kbd>Keyboard input</kbd>
<samp>Sample output</samp>
<var>Variable</var>

<!-- Quotations -->
<blockquote>Block quotation</blockquote>
<q>Inline quotation</q>
```

## Lists

```html
<!-- Unordered list -->
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>

<!-- Ordered list -->
<ol>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ol>

<!-- Ordered list with type -->
<ol type="A">  <!-- A, B, C, ... -->
    <li>Item A</li>
    <li>Item B</li>
</ol>
<ol type="a">  <!-- a, b, c, ... -->
    <li>Item a</li>
    <li>Item b</li>
</ol>
<ol type="I">  <!-- I, II, III, ... -->
    <li>Item I</li>
    <li>Item II</li>
</ol>
<ol type="i">  <!-- i, ii, iii, ... -->
    <li>Item i</li>
    <li>Item ii</li>
</ol>
<ol type="1" start="5">  <!-- 5, 6, 7, ... -->
    <li>Item 5</li>
    <li>Item 6</li>
</ol>

<!-- Description list -->
<dl>
    <dt>Term 1</dt>
    <dd>Definition 1</dd>
    <dt>Term 2</dt>
    <dd>Definition 2</dd>
</dl>

<!-- Nested lists -->
<ul>
    <li>Item 1</li>
    <li>Item 2
        <ul>
            <li>Subitem 2.1</li>
            <li>Subitem 2.2</li>
        </ul>
    </li>
    <li>Item 3</li>
</ul>
```

## Links

```html
<!-- Basic link -->
<a href="https://example.com">Link text</a>

<!-- Link with title -->
<a href="https://example.com" title="Visit Example">Link with title</a>

<!-- Open link in new tab -->
<a href="https://example.com" target="_blank">Open in new tab</a>

<!-- Link to email -->
<a href="mailto:email@example.com">Send email</a>

<!-- Link to phone number -->
<a href="tel:+1234567890">Call us</a>

<!-- Link to file download -->
<a href="file.pdf" download>Download PDF</a>

<!-- Link to specific part of page -->
<a href="#section-id">Go to section</a>
<h2 id="section-id">Section Title</h2>

<!-- Link with image -->
<a href="https://example.com">
    <img src="image.jpg" alt="Link image">
</a>
```

## Images

```html
<!-- Basic image -->
<img src="image.jpg" alt="Image description">

<!-- Image with width and height -->
<img src="image.jpg" alt="Image description" width="500" height="300">

<!-- Responsive image -->
<img src="image.jpg" alt="Image description" style="max-width:100%; height:auto;">

<!-- Image with title -->
<img src="image.jpg" alt="Image description" title="Image title on hover">

<!-- Image map -->
<img src="image.jpg" alt="Image map" usemap="#mapname">
<map name="mapname">
    <area shape="rect" coords="0,0,100,100" href="page1.html" alt="Area 1">
    <area shape="circle" coords="200,200,50" href="page2.html" alt="Area 2">
</map>

<!-- Figure with caption -->
<figure>
    <img src="image.jpg" alt="Image description">
    <figcaption>Image caption</figcaption>
</figure>

<!-- Picture element for responsive images -->
<picture>
    <source media="(min-width: 1200px)" srcset="large.jpg">
    <source media="(min-width: 600px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Responsive image">
</picture>
```

## Tables

```html
<!-- Basic table -->
<table>
    <tr>
        <th>Header 1</th>
        <th>Header 2</th>
    </tr>
    <tr>
        <td>Row 1, Cell 1</td>
        <td>Row 1, Cell 2</td>
    </tr>
    <tr>
        <td>Row 2, Cell 1</td>
        <td>Row 2, Cell 2</td>
    </tr>
</table>

<!-- Table with caption and structure -->
<table>
    <caption>Table Caption</caption>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Row 1, Cell 1</td>
            <td>Row 1, Cell 2</td>
        </tr>
        <tr>
            <td>Row 2, Cell 1</td>
            <td>Row 2, Cell 2</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Footer 1</td>
            <td>Footer 2</td>
        </tr>
    </tfoot>
</table>

<!-- Table with colspan and rowspan -->
<table>
    <tr>
        <th>Header 1</th>
        <th colspan="2">Header 2-3</th>
    </tr>
    <tr>
        <td rowspan="2">Row 1-2, Cell 1</td>
        <td>Row 1, Cell 2</td>
        <td>Row 1, Cell 3</td>
    </tr>
    <tr>
        <td>Row 2, Cell 2</td>
        <td>Row 2, Cell 3</td>
    </tr>
</table>
```

## Forms

```html
<!-- Basic form -->
<form action="/submit" method="post">
    <!-- Form elements go here -->
    <input type="submit" value="Submit">
</form>

<!-- Text input -->
<input type="text" name="username" placeholder="Enter username">

<!-- Password input -->
<input type="password" name="password" placeholder="Enter password">

<!-- Email input -->
<input type="email" name="email" placeholder="Enter email">

<!-- Number input -->
<input type="number" name="quantity" min="1" max="10" step="1">

<!-- Date input -->
<input type="date" name="birthdate">

<!-- Time input -->
<input type="time" name="meeting-time">

<!-- Color picker -->
<input type="color" name="favorite-color">

<!-- Range slider -->
<input type="range" name="volume" min="0" max="100" step="1">

<!-- File upload -->
<input type="file" name="document">
<input type="file" name="photos" multiple accept="image/*">

<!-- Hidden input -->
<input type="hidden" name="user-id" value="12345">

<!-- Radio buttons -->
<input type="radio" name="gender" id="male" value="male">
<label for="male">Male</label>
<input type="radio" name="gender" id="female" value="female">
<label for="female">Female</label>

<!-- Checkboxes -->
<input type="checkbox" name="interests" id="sports" value="sports">
<label for="sports">Sports</label>
<input type="checkbox" name="interests" id="music" value="music">
<label for="music">Music</label>

<!-- Textarea -->
<textarea name="message" rows="4" cols="40" placeholder="Enter your message"></textarea>

<!-- Select dropdown -->
<select name="country">
    <option value="">Select a country</option>
    <option value="us">United States</option>
    <option value="ca">Canada</option>
    <option value="uk">United Kingdom</option>
</select>

<!-- Select with option groups -->
<select name="car">
    <optgroup label="Japanese Cars">
        <option value="toyota">Toyota</option>
        <option value="honda">Honda</option>
    </optgroup>
    <optgroup label="German Cars">
        <option value="bmw">BMW</option>
        <option value="audi">Audi</option>
    </optgroup>
</select>

<!-- Multiple select -->
<select name="skills" multiple>
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="js">JavaScript</option>
</select>

<!-- Datalist (suggestions) -->
<input list="browsers" name="browser">
<datalist id="browsers">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Safari">
    <option value="Edge">
</datalist>

<!-- Fieldset and legend -->
<fieldset>
    <legend>Personal Information</legend>
    <label for="fname">First name:</label>
    <input type="text" id="fname" name="fname">
    <label for="lname">Last name:</label>
    <input type="text" id="lname" name="lname">
</fieldset>

<!-- Form with labels -->
<form>
    <div>
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required>
    </div>
    <div>
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required>
    </div>
    <button type="submit">Login</button>
</form>

<!-- Form validation attributes -->
<input type="text" name="username" required minlength="3" maxlength="20">
<input type="email" name="email" required pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$">
<input type="number" name="age" min="18" max="100" required>
```

## Semantic Elements

```html
<!-- Header -->
<header>
    <h1>Website Title</h1>
    <nav>
        <!-- Navigation links -->
    </nav>
</header>

<!-- Navigation -->
<nav>
    <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Services</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>

<!-- Main content -->
<main>
    <!-- Main content of the page -->
</main>

<!-- Article -->
<article>
    <h2>Article Title</h2>
    <p>Article content...</p>
</article>

<!-- Section -->
<section>
    <h2>Section Title</h2>
    <p>Section content...</p>
</section>

<!-- Aside -->
<aside>
    <h3>Related Information</h3>
    <p>Sidebar content...</p>
</aside>

<!-- Footer -->
<footer>
    <p>&copy; 2023 Company Name. All rights reserved.</p>
</footer>

<!-- Figure with caption -->
<figure>
    <img src="image.jpg" alt="Description">
    <figcaption>Caption for the image</figcaption>
</figure>

<!-- Details and summary -->
<details>
    <summary>Click to expand</summary>
    <p>Hidden content that appears when expanded.</p>
</details>

<!-- Time -->
<time datetime="2023-01-01">January 1, 2023</time>

<!-- Mark -->
<p>This is <mark>highlighted</mark> text.</p>

<!-- Progress bar -->
<progress value="70" max="100">70%</progress>

<!-- Meter -->
<meter value="0.7" min="0" max="1">70%</meter>
```

## Embedding Content

```html
<!-- Iframe -->
<iframe src="https://example.com" width="600" height="400" frameborder="0"></iframe>

<!-- Iframe with sandbox -->
<iframe src="https://example.com" sandbox="allow-scripts allow-same-origin"></iframe>

<!-- Audio -->
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Your browser does not support the audio element.
</audio>

<!-- Video -->
<video width="320" height="240" controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    Your browser does not support the video element.
</video>

<!-- Video with poster image -->
<video width="320" height="240" controls poster="poster.jpg">
    <source src="video.mp4" type="video/mp4">
    Your browser does not support the video element.
</video>

<!-- YouTube embed -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allowfullscreen></iframe>

<!-- Google Maps embed -->
<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!..." width="600" height="450" frameborder="0" allowfullscreen></iframe>

<!-- Canvas -->
<canvas id="myCanvas" width="200" height="100"></canvas>

<!-- SVG -->
<svg width="100" height="100">
    <circle cx="50" cy="50" r="40" stroke="black" stroke-width="2" fill="red" />
</svg>

<!-- Math ML -->
<math>
    <mrow>
        <mi>x</mi>
        <mo>=</mo>
        <mfrac>
            <mrow>
                <mo>-</mo>
                <mi>b</mi>
                <mo>±</mo>
                <msqrt>
                    <msup>
                        <mi>b</mi>
                        <mn>2</mn>
                    </msup>
                    <mo>-</mo>
                    <mn>4</mn>
                    <mi>a</mi>
                    <mi>c</mi>
                </msqrt>
            </mrow>
            <mrow>
                <mn>2</mn>
                <mi>a</mi>
            </mrow>
        </mfrac>
    </mrow>
</math>
```

## Responsive Design

```html
<!-- Viewport meta tag -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Responsive image -->
<img src="image.jpg" alt="Responsive image" style="max-width:100%; height:auto;">

<!-- Picture element for art direction -->
<picture>
    <source media="(min-width: 1200px)" srcset="large.jpg">
    <source media="(min-width: 600px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Responsive image">
</picture>

<!-- Responsive table -->
<div style="overflow-x:auto;">
    <table>
        <!-- Table content -->
    </table>
</div>

<!-- Responsive iframe -->
<div style="position:relative; padding-bottom:56.25%; height:0; overflow:hidden;">
    <iframe style="position:absolute; top:0; left:0; width:100%; height:100%;" src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allowfullscreen></iframe>
</div>
```

## Accessibility

```html
<!-- ARIA roles -->
<div role="button" tabindex="0">Click me</div>
<div role="alert">Important message</div>
<div role="navigation">Navigation menu</div>

<!-- ARIA states and properties -->
<button aria-pressed="false">Toggle</button>
<div aria-hidden="true">Hidden content</div>
<input aria-required="true">

<!-- Skip navigation -->
<a href="#main-content" class="skip-link">Skip to main content</a>
<main id="main-content">
    <!-- Main content -->
</main>

<!-- Form with accessible labels -->
<label for="username">Username:</label>
<input type="text" id="username" name="username">

<!-- Fieldset for grouping related form elements -->
<fieldset>
    <legend>Contact Information</legend>
    <!-- Form fields -->
</fieldset>

<!-- Image with alt text -->
<img src="image.jpg" alt="Description of image">

<!-- Tables with headers -->
<table>
    <caption>Monthly Budget</caption>
    <thead>
        <tr>
            <th scope="col">Category</th>
            <th scope="col">Amount</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">Rent</th>
            <td>$1000</td>
        </tr>
    </tbody>
</table>

<!-- Language -->
<html lang="en">
<p lang="fr">Bonjour</p>
```

## HTML5 APIs

```html
<!-- Local Storage -->
<script>
    // Store data
    localStorage.setItem('key', 'value');
    
    // Retrieve data
    const value = localStorage.getItem('key');
    
    // Remove data
    localStorage.removeItem('key');
    
    // Clear all data
    localStorage.clear();
</script>

<!-- Session Storage -->
<script>
    // Store data
    sessionStorage.setItem('key', 'value');
    
    // Retrieve data
    const value = sessionStorage.getItem('key');
    
    // Remove data
    sessionStorage.removeItem('key');
    
    // Clear all data
    sessionStorage.clear();
</script>

<!-- Geolocation -->
<script>
    if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(position => {
            const latitude = position.coords.latitude;
            const longitude = position.coords.longitude;
            console.log(`Latitude: ${latitude}, Longitude: ${longitude}`);
        });
    }
</script>

<!-- Web Workers -->
<script>
    const worker = new Worker('worker.js');
    
    worker.postMessage('Hello Worker');
    
    worker.onmessage = function(e) {
        console.log('Message received from worker:', e.data);
    };
</script>

<!-- Drag and Drop -->
<div draggable="true" id="draggable">Drag me</div>
<div id="droptarget">Drop here</div>

<script>
    const draggable = document.getElementById('draggable');
    const droptarget = document.getElementById('droptarget');
    
    draggable.addEventListener('dragstart', e => {
        e.dataTransfer.setData('text/plain', e.target.id);
    });
    
    droptarget.addEventListener('dragover', e => {
        e.preventDefault();
    });
    
    droptarget.addEventListener('drop', e => {
        e.preventDefault();
        const id = e.dataTransfer.getData('text/plain');
        const dragged = document.getElementById(id);
        droptarget.appendChild(dragged);
    });
</script>
```

## Character Entities

```html
<!-- Common character entities -->
&lt;       <!-- < (less than) -->
&gt;       <!-- > (greater than) -->
&amp;      <!-- & (ampersand) -->
&quot;     <!-- " (quotation mark) -->
&apos;     <!-- ' (apostrophe) -->
&copy;     <!-- © (copyright) -->
&reg;      <!-- ® (registered trademark) -->
&trade;    <!-- ™ (trademark) -->
&euro;     <!-- € (euro) -->
&pound;    <!-- £ (pound) -->
&yen;      <!-- ¥ (yen) -->
&cent;     <!-- ¢ (cent) -->
&sect;     <!-- § (section) -->
&deg;      <!-- ° (degree) -->
&plusmn;   <!-- ± (plus-minus) -->
&times;    <!-- × (multiplication) -->
&divide;   <!-- ÷ (division) -->
&frac14;   <!-- ¼ (one quarter) -->
&frac12;   <!-- ½ (one half) -->
&frac34;   <!-- ¾ (three quarters) -->
&nbsp;     <!-- Non-breaking space -->
&emsp;     <!-- Em space -->
&ensp;     <!-- En space -->
&thinsp;   <!-- Thin space -->
&mdash;    <!-- — (em dash) -->
&ndash;    <!-- – (en dash) -->
&laquo;    <!-- « (left angle quote) -->
&raquo;    <!-- » (right angle quote) -->
&lsquo;    <!-- ' (left single quote) -->
&rsquo;    <!-- ' (right single quote) -->
&ldquo;    <!-- " (left double quote) -->
&rdquo;    <!-- " (right double quote) -->
&hellip;   <!-- … (ellipsis) -->
&bull;     <!-- • (bullet) -->
&prime;    <!-- ′ (prime) -->
&Prime;    <!-- ″ (double prime) -->
&larr;     <!-- ← (left arrow) -->
&rarr;     <!-- → (right arrow) -->
&uarr;     <!-- ↑ (up arrow) -->
&darr;     <!-- ↓ (down arrow) -->
```