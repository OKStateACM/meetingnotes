### HTML + CSS

#### ACM Meeting Agenda — February 1, 2017

***

##### Announcements

- GroupMe reminder

- ACM Highlight – ["Computing and the Fight against Epidemics"](http://www.huffingtonpost.com/entry/computing-and-the-fight-against-epidemics_us_587fd401e4b0aa1c47ac27d6) by Alessandro Vespignani

- Please let us know if you're a member of the official national ACM

	- Business Meeting tomorrow, 2/2 at 5:00 to discuss constitution/bylaws

- AI Workshop – February 11, 1:00pm - 4:00pm, in MSCS 203W

***

##### Introduction to HTML

- Hypertext Markup Language

    - We use markup to denote the _structure_ and _semantics_ of a webpage

        - This is opposed to CSS, which determines the appearance of a webpage

        - Markup takes the form of _tags_, which look like `<p>`

            - Most tags must be _closed_ to reflect the end of the effect. Closing tags take the form `</p>`. The overall use of tag + closing tag looks like `<p>This is a paragraph!</p>`. This combination of opening tag, content, and closing tag is called an *element*.

                - Some tags, such as `<br>`, `<hr>`, or `<img>` are _self-closing_, meaning the opening tag serves as the entire element, and there is no closing tag.

            - Many tags also have _attributes_, or modifiers. These are listed in the opening tag, like `<a href="about.html">`, which uses the `href` attribute to indicate that this hyperlink points to the `about.html` page of the website.

                - Attributes can be stacked: `<img src="logo.png" alt="OSU Logo" width="100px">` is an image tag that declares the image path with the `src` attribute, the alt/tooltip text with the `alt` attribute, and the image width with the `width` attribute.


- Formatting text using HTML

    - Create a file in your text editor, have it read
    ```html
    Hello world!
    ```
    and save it as `index.html`. Open this file with your browser.

    - To mark-up this text, try enveloping the text with `<h1>` tags, so it now reads
    ```html
    <h1>Hello world!</h1>
    ```
    Save your `index.html` file and refresh the page in your browser. What's changed?

    - HTML provides many tags for formatting your text, including the following:

| Tag           | Description  | Attributes |
|---------------|-------------|------------|
| `<a>` | Defines a hyperlink to another webpage | `href` – absolute or relative URL of linked content; `title` – tooltip text |
| `<blockquote>`| Defines a section of text that is quoted from another source (typically indented in browsers) | `cite` – URL which represents the source of the quote
| `<br>` | Self-closing tag which inserts a line break | |
| `<code>`| Defines a section of text as computer code (typically displayed with a monospace font in browsers) | |
| `<del>`    | Defines deleted text in a document (typically represented with struck-through text in browsers) | `cite` – URL of document which explains why the text was deleted; `datetime` – date and time of deletion in _YYYY-MM-DDThh:mm:ssTZD_ format|
| `<em>`    | Defines emphasized text (typically represented with _italicized_ text in browsers) | |
| `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`  | Headings of various sizes, `h1` being the largest and `h6` being the smallest | |
| `<hr>` | Self-closing tag which inserts a horizontal rule (divider line) | |
| `<ins>`    | Defines inserted text in a document (typically represented with underlined text in browsers, and generally for use with `<del>`) | `cite` – URL of document which explains why the text was inserted; `datetime` – date and time of insertion in _YYYY-MM-DDThh:mm:ssTZD_ format |
| `<mark>`    | Defines marked/highlighted text | |
| `<p>`         | Paragraph of text | |
| `<q>`         | Defines an inline quotation | `cite` – URL which represents the source of the  quote |
| `<small>`    | Defines smaller text | |
| `<strong>`    | Defines important text (typically represented with __bolded__ text in browsers) | |
| `<sub>`    | Defines subscripted text | |
| `<sup>`    | Defines superscripted text | | |

- HTML documents must follow the following boilerplate structure:

```html
<!DOCTYPE html>
<html>
    <head>
        <!-- THE CONTENT BETWEEN THE <head> TAGS DEFINES THE PAGE'S META INFORMATION -->
        <meta charset="utf-8">
        <title>Your Page Title Goes Here!</title>
    </head>
    <body>
        <!-- THE CONTENT BETWEEN THE <body> TAGS IS WHAT THE VIEWER WILL SEE -->
    </body>
</html>
```

- More fun things you can do with HTML

    - Images, using `<img src="image_url.png">`

        - The `src` attribute gives the absolute or relative URL of the image

        - The `alt` attribute gives the image's alt text, or a description of the image for use in screenreaders and search engine optimization, as well as for tooltip text or in cases when the image cannot be loaded

        - The `height` and `width` attributes are self-explanatory

            - If you only give one of these two attributes, the other will adjust to automatically maintain the aspect ratio

            - These attributes can take [absolute sizes or relative sizes](http://www.w3schools.com/cssref/css_units.asp). Absolutely sized elements, such as those with a length of `100px` for 100 pixels, are fixed. Relatively sized elements change size depending on some other element. A `width` of `100%`, for instance, spans the entire width of the image's container. A `width` of `50vw`, which uses [viewport units](https://web-design-weekly.com/2014/11/18/viewport-units-vw-vh-vmin-vmax/), would span half of the width of the entire webpage.

    - Lists, using `<ol>` for ordered (numbered) lists and `<ul>` for unordered (bulleted) lists, and `<li>` for each item in the list. Lists can be nested for subpoints.

        ```html
        <ol>
            <li>This is an ordered list.</li>
            <li>
                It has a nested ordered list!
                <ol>
                    <li>Like</li>
                    <li>this!</li>
                </ol>
            </li>
            <li>
                It also has a nested unordered list!
                <ul>
                    <li>Just</li>
                    <li>Like</li>
                    <li>This</li>
                </ul>
            </li>
        </ol>
        ```
        produces

        ```
        1. This is an ordered list.
        2. It has a nested ordered list!
            1. Like
            2. this!
        3. It also has a nested unordered list!
            • Just
            • Like
            • This
        ```

    - Tables use up to four different tags.

        - `<table>` creates the table

        - `<tr>` creates a table row

        - `<td>` creates a cell of data within a row

        - `<th>` replaces `<td>` to display a cell of data as a table heading

        ```html
        <table>
            <tr>
                <th>Position</th>
                <th>Name</th>
            </tr>
            <tr>
                <td>President</td>
                <td>Ben Myers</td>
            </tr>
            <tr>
                <td>Vice President</td>
                <td>Jacob Schlecht</td>
            </tr>
            <tr>
                <td>Secretary</td>
                <td>Alex Durville</td>
            </tr>
            <tr>
                <td>Treasurer</td>
                <td>Kaylee Hartman</td>
            </tr>
        </table>
        ```
        produces

        <table>
            <tr>
                <th>Position</th>
                <th>Name</th>
            </tr>
            <tr>
                <td>President</td>
                <td>Ben Myers</td>
            </tr>
            <tr>
                <td>Vice President</td>
                <td>Jacob Schlecht</td>
            </tr>
            <tr>
                <td>Secretary</td>
                <td>Alex Durville</td>
            </tr>
            <tr>
                <td>Treasurer</td>
                <td>Kaylee Hartman</td>
            </tr>
        </table>

    - `<div>` tags are useful for splitting your page up into sections that can be targeted by CSS or by other parts of your HTML page. It groups any content between the opening and closing `<div>` tags as one section under a given ID. For example

    ```html
    <div id="education">
        <h3>EDUCATION</h3>
		<table width="100%">
			<tr>
				<td>Oklahoma State University</td>
				<td align="right">Expected Graduation: May 2063</td>
			</tr>
			<tr>
				<td><strong>Bachelor of Science in Computer Science</strong></td>
				<td align="right">GPA: 4.0</td>
			</tr>
		</table>
    </div>
    ```
    groups the `h3` heading and the table as one section, called __education__, for targeting by CSS or other HTML elements. If we wanted to link directly to the __education__ section, for instance, we could use `href="#education"` in our `<a>` tags.

***

##### Introduction to CSS

- _Box Model_ – each HTML element has its own set of invisible boxes around it, and CSS allows you to change how those boxes and their contents are presented

![A diagram of the box model is displayed. From the inside-out, the model consists of content, padding, border, and margin. Width and height are shown to pertain to the content.](http://jharaphula.com/wp-content/uploads/2016/05/box-model.gif)

- Cascading Stylesheets

    - Create a file in the same directory as your `index.html` and call it `style.css`. This will be our _stylesheet_.

        - In the head of your `index.html` file, insert the line `<link rel="stylesheet" type="text/css" href="style.css">` so that your HTML page will be affected by the contents of the stylesheet.

    - In your new `style.css` file, you can now target elements to change their look.

        - To change the all `h1` headings to be green and in Arial, for instance, we could use

        ```css
        h1 {
            font-family: Arial;
            color: green;
        }
        ```
        - In the above example, the `h1` is called a _selector_, used to represent the elements we were targeting.

        - The

        ```css
        {
            font-family: Arial;
            color: green;
        }
        ```
        lines are _declarations_, and they determine how the targeted elements should be styled. Each declaration consists of a _property_ and a _value_.

            - If the declarations should be applied to more than one kind of element, such as both `h1` and `h2`, you can stack selectors by separating them with commas: `h1, h2`

        - As another example, let's give the entire body a background of America's Brightest Orange and to set the body's default text to bold Courier New, you could use

        ```css
        body {
            background-color: #FF6600;
            font-family: "Courier New";
            font-weight: bold;
        }
        ```
        - What would happen if you used the above `body` rule with the above `h1` rule? Both of them set the `font-family`, after all. Will `h1` elements inside the `body` be in Courier New or in Arial? CSS has a principle of _specificity_, meaning the more specific the selector, the higher priority its declarations will be. In this case, `h1` is more specific than `body`, so the `h1` headers will be in Arial.

        - [Taking advantage of the Box Model in CSS](http://www.w3schools.com/css/tryit.asp?filename=trycss_boxmodel_width)

    - Selectors come in many different forms

| Selector | Meaning | Example |
|----------|---------|---------|
| Universal selector | Applies to all elements in the document | `* {}` – Targets all elements in the page |
| Type selector | Matches element names | `h1, h2, h3 {}` – Targets the `<h1>`, `<h2>`, `<h3>` elements |
| Class selector | Matches an element whose class attribute has a value that matches the one specified after the period (or full stop) symbol | `.note {}` – Targets any element whose `class` attribute has a value of note; `p.note {}` – Targets only `<p>` elements whose `class` attribute has a value of `note` |
| ID selector | Matches an element whose `id` attribute has a value that matches the one specified after the pound or hash symbol | `#introduction {}` – Targets the element whose `id` attribute has a value of `introduction` |
| Child selector | Matches an element that is a direct child of another | `li>a {}` – Targets any `<a>` elements that are children of an `<li>` element (but not other `<a>` elements in the page) |
| Descendant selector | Matches an element that is a descendent of another specified element (not just a direct child of that element) | `p a {}` – Targets any `<a>` elements that sit inside a `<p>` element, even if there are other elements nested between them |
| Adjacent sibling selector | Matches an element that is the next sibling of another | `h1+p {}` – Targets the first `<p>` element after any `<h1>` element (but not other `<p>` elements) |
| General sibling selector | Matches an element that is a sibling of another, although it does not have to be the directly preceding element | `h1~p {}` – If you had two `<p>` elements that are siblings of an `<h1>` element, this rule would apply to both |
> —_HTML & CSS: Design and Build Websites_ by Jon Duckett, p. 238

***

##### Improving Your Site with External Tools

- [Bootstrap](http://getbootstrap.com) – a library by Twitter for faster, easier, and more attractive responsive front-end web development

    - [Instructions for configuring your webpage to use Bootstrap](http://getbootstrap.com/getting-started/)

    - [What all Bootstrap has to offer](http://getbootstrap.com/components/)

- [Google Fonts](https://fonts.google.com) – hosts fonts for use in web Design

    - [How to use Google Fonts in your website](https://developers.google.com/fonts/docs/getting_started)

***

##### Useful Resources

- [W3Schools](http://www.w3schools.com) – documentation and tutorials for pretty much everything HTML/CSS imaginable

- [DevTips](https://www.youtube.com/user/DevTipsForDesigners) – YouTube channel which covers various aspects of web design
