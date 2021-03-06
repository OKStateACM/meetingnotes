### Interactive Front-End Web Development with JavaScript and jQuery

#### ACM Meeting Agenda — February 22, 2017

***

##### Announcements

- ACM Highlight – [Making the Field of Computing More Inclusive](http://cacm.acm.org/magazines/2017/3/213827-making-the-field-of-computing-more-inclusive/fulltext)

- **Hackathon** – March 3, 5:30 pm - March 4, 5:30 pm

    - Awards for *Most Useful*, *Most Entertaining*, and *Best Designed*

- **Next week: Exxon-Mobil Meet & Greet**

***

###### These meeting notes are forever indebted to resources such as W3Schools and Jon Duckett's *JavaScript & jQuery: Interactive Front-End Web Development*.

***

##### A Brief Introduction

- [Previously](https://github.com/OKStateACM/meetingnotes/blob/master/2017-02-01%20-%20agenda.md), we've discussed HTML and CSS – tools for manipulating the structure and look of webpages. However, using HTML and CSS alone will only give you *static* webpages. *Dynamic* webpages require some amount of programming, using tools such as JavaScript and jQuery.

    - Three layers of web design:

        - **Content Layer** – HTML

        - **Presentation Layer** – CSS

        - **Behavior Layer** – JavaScript

- *JavaScript* is a programming language that runs *client-side*, meaning it's executed in the browser of anyone viewing your webpage.

    - JavaScript stands out from other languages you might have experienced in that it's very *event-driven*. There's a huge focus on things happening in response to other things, and your code is guaranteed to operate in the linear order you write it in.

- *jQuery* is a *[framework](https://jeffknupp.com/blog/2014/03/03/what-is-a-web-framework/)* for JavaScript that abstracts away a lot of the minutia of web development. JavaScript is kind of infamous for having many, many frameworks out there that do different things.

***

##### JavaScript – The Theory

- There are two ways to get JavaScript code to work in an HTML document

    - Using `<script>` tags. Anything between the opening `<script>` tag and the closing `</script>` tag is interpreted as JavaScript code rather than displayed to the user.
    ```html
    <script>
        // JavaScript code goes here
    </script>
    ```

    - Linking to a JavaScript file. For instance, if you have a JavaScript file called `myScript.js`, you could import it using
    ```html
    <script src="myScript.js"></script>
    ```
    The `src` attribute contains the absolute or relative reference to the script. Linking to a JavaScript file is a good practice because it promotes code reuse and leaves the HTML file much less cluttered.

- One of the biggest differences between writing JavaScript code and code from other languages such as, say, Java is how JavaScript handles *typing*. Whereas languages like Java may have explicit variable types such as `int`, `float`, `boolean`, or `String`, JavaScript's variables are all simply `var`.
    ```javascript
    var x = 5; // x starts off as a number
    x = "Hello"; // x now stores a string
    ```

    - JavaScript's **weak typing** leads to features that seem unintuitive for people coming from other languages.

        - For instance, `3 == "3"` returns `true`, even though you're comparing a number and a string. `3.0 == "3"` also returns a `true` because JavaScript only has one type for number.

            - If you want to check that two values are equal *and* their types match, you can use the `===` operator. `3 === "3"` returns `false`.

- JavaScript arrays work much like arrays work in other languages such as Java, with a few notable differences.

    - JavaScript arrays can store more than one type of element at any given time. `var myArray = [1, false, "Hello"];` is perfectly valid.

    - Array sizes are flexible. To add `"lemon"` to the end of the `fruits` array, use `fruits.push("lemon");`. Alternatively, we can use `fruits[n] = "lemon"` and, if `fruits` doesn't *have* an *n*<sup>th</sup> element, `"lemon"` will be inserted at index *n*.

- JavaScript *objects* are sets of key–value pairs which represent the object's *properties*.

    - Empty objects can be created using
    ```javascript
    var myObject = {};
    ```

    - You can also instantiate objects with properties using
        ```javascript
        var myObject{firstName:"Ben", lastName:"Myers", age:20};
        ```

        - This creates an object with the properties `firstName`, `lastName`, and `age` set to `"Ben"`, `"Myers"`, and `20` respectively.

    - Alternatively, you can create objects using the `new` operator:
        ```javascript
        var myObject = new Object();
        ```

    - New properties can be added to objects at any time. For instance, the following code creates an empty object, gives it a `message` property, and then successfully outputs that `message` property to the browser console.
    ```javascript
    var myObject = {};
    myObject.message = "This is a message!";
    console.log(myObject.message);
    ```

    - Objects' properties can also be accessed using a notation resembling that of arrays. For instance, in the above example, we could replace every instance of `myObject.message` with `myObject["message"]`.

- JavaScript really puts the *fun* in *functions*. <sub>*Please don't hurt me.*</sub>

    - Declaring a function to get the area of a rectangle given the rectangle's width and height might look like
    ```javascript
    function getArea(width, height) {
        return width * height;
    }
    ```
    This function can then be called later using
    ```javascript
    var area = getArea(3, 5); // area now stores 15
    ```

    - The above is fairly normal for people used to Java-like languages. However, JavaScript also does some... unique... things with functions.

        1. **Functions can be stored in variables and passed around as parameters.** Relatedly, __functions can be *anonymous*__, meaning they aren't given a name.
            ```javascript
            // Storing a function in a variable
            // This function is anonymous - it has no name
            var area = function(width, height) {
                return width * height;
            };

            var size = area(3, 5); // size now stores 15
            ```

            ```javascript
            // Here, a function is saved as the behavior of the 'button' object upon being clicked
            button.onclick = function() {
                console.log("I've been clicked!");
            };
            ```

            ```javascript
            // This code snippet does the same as the above code snippet,
            // except by passing an anonymous function as a parameter
            button.addEventListener("click", function() {
                console.log("I've been clicked!")
            });
            ```

            - Anonymous functions are good in cases such as:

                - Code that only needs to run one time in a script

                - Event handlers and listeners

                - Avoiding conflicting function names between two scripts

        2. In languages like Java, code is generally expected to be fairly linear. The code on line one executes, then the code on line two executes, and so forth. JavaScript code, however, will often end up being very **asynchronous**. In the following example, the invented `drawPhoto()` and `manipulatePhoto()` functions are called but, because downloading photos may be a very slow process, there's no guarantee that the photo has been downloaded and stored in `photo` before `handlePhoto()` is called.
            ```javascript
            var photo = downloadPhoto("www.sample.com/test.jpg");
            handlePhoto(photo); // 'photo' may not be defined in time for this!
            ```

            - [Reference on how to program with this asynchronicity in mind](http://callbackhell.com/)

***

##### JavaScript – Practice

- Sample [FizzBuzz](https://blog.codinghorror.com/why-cant-programmers-program/) implementation which prints each output on a new line
    ```javascript
    for(var i = 1; i <= 100; i++)
    {
        if(i % 15 == 0) // divisible by both 3 and 5
        {
            document.write("FizzBuzz<br>");
        }
        else if(i % 3 == 0) // divisible by 3, not 5
        {
            document.write("Fizz<br>");
        }
        else if (i % 5 == 0) // divisible by 5, not 3
        {
            document.write("Buzz<br>");
        }
        else // not divisible by 3 or 5
        {
            document.write(i + "<br>");
        }
    }
    ```

- Random color generator:

    - HTML:
        ```html
        <!DOCTYPE html>
        <html>
            <head>
                <meta charset="utf-8">
                <title></title>
                <script src="ColorGenerator.js"></script>
            </head>
            <body>
                <center>
                    <h1 id="hexCodeHeading">#ffffff</h1>
                    <button type="button" id="colorButton">Generate New Color!</button>
                <center>
            </body>
        </html>
        ```

    - JavaScript (`ColorGenerator.js`):
        ```javascript
        // Can't access anything like the button until we know the page has loaded
        window.onload = function() {
            // First, find and store the button using its 'id' tag
            var colorButton = document.getElementById("colorButton");

            // Let's also get access to the hex code heading
            var hexCodeHeading = document.getElementById("hexCodeHeading");

            // Give colorButton a clicking behavior
            colorButton.onclick = function() {

                // Generate new hex color
                var randomColor = generateColor();

                // Update the heading which shows the hex code
                hexCodeHeading.innerText = randomColor;

                // Set background color
                    // Notice that this targets the 'backgroundColor' attribute...
                    // of the CSS styling ('style')...
                    // of the body element of the document
                document.body.style.backgroundColor = randomColor;
            };
        };

        var hexDigits = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f'];

        // Generate a random hex color
        function generateColor()
        {
            var color = "#";
            for(var i = 0; i < 6; i++)
            {
                // Randomly choose which digit should be appended
                var digit = hexDigits[Math.round(Math.random() * 15)];

                // Append digit
                color += digit;
            }
            return color;
        }
        ```

***

##### jQuery – The Theory

- jQuery is not included in JavaScript by default – **you will need to import it before you can use it**. There are two ways you can do this:

    - **Download jQuery and host it yourself:** You can download jQuery from [jQuery.com](http://jquery.com/download/). jQuery.com allows you to install two versions of jQuery: the production version (which is minified and compressed) and the development version (which is spaced out and legible). You won't need to tinker with the jQuery code, so download the production version, `jquery-3.1.1.min.js`. Place it inside your webpage's directory. Link to the jQuery script using its relative path with the following element in the `<head>` section before any jQuery code is called:
        ```html
        <script src="jquery-3.1.1.min.js"></script>
        ```

    - __Get jQuery from a *content delivery network (CDN)*: *(recommended)*__ Both Google and Microsoft host jQuery, and you can just link to them! This has the advantage of the jQuery file likely already being cached in your viewers' browsers, meaning your page loads more quickly. Copy one of the following code snippets into your `<head>` section before you call any jQuery code:
        ```html
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
        ```
        ```html
        <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.1.1.min.js"></script>
        ```

- What is jQuery good for? jQuery doesn't really let you do anything plain JavaScript wouldn't let you do. However, jQuery provides three main advantages: simple selectors, simplified code for common tasks, and cross-browser compatibility.

- *[From W3Schools](https://www.w3schools.com/jquery/jquery_syntax.asp)*: The jQuery syntax is tailor-made for selecting HTML elements and performing some action on the element(s). The basic syntax is `$(selector).action()`

    - A `$` sign to define/access jQuery

    - A `(selector)` to "query (or find)" HTML elements. This selector is the same as the [relevant CSS selector](https://www.w3schools.com/jquery/jquery_selectors.asp).

        - For example, in CSS you would target our color-generating button, which has `id="colorButton"` using the selector `#colorButton`. Thus in jQuery we can target our color-generating button with
        ```javascript
        $("#colorButton")
        ```

        - Alternatively, you can target multiple elements of the same type. For instance, if you have several `<p>` tags on a page and you call `$("p")`, you get a list of all of the `p` elements on that page.

    - A jQuery `action()` to be performed on the element(s)

    - Examples:

        - `$(this).hide()` – hides the current element.

        - `$("p").hide()` – hides all `<p>` elements.

        - `$(".test").hide()` – hides all elements with `class="test"`.

        - `$("#test").hide()` – hides the element with `id="test"`.

- jQuery is also event-driven. For a complete list of the events jQuery supports, go [here](https://www.w3schools.com/jquery/jquery_selectors.asp).

    - We can refactor our color generator code using jQuery events. For instance, we can replace `window.onload` with a jQuery counterpart: `$(document).ready()`.
        ```javascript
        window.onload = function() { ... };
        ```
    becomes
        ```javascript
        $(document).ready(function() { ... });
        ```

        - [Technically these two methods are different and here's why.](http://www.dotnetbull.com/2013/08/document-ready-vs-window-onload.html)

    - We can also use the jQuery `.click()` function to refactor our button click event handler. Instead of calling
        ```javascript
        var colorButton = document.getElementById("colorButton");
        ```
        and
        ```javascript
        colorButton.onclick = function() { ... };
        ```
        Call
        ```javascript
        var $colorButton = $("#colorButton");
        ```
        and
        ```javascript
        $colorButton.click(function() { ... });
        ```

        - The `$` in the `$colorButton` variable name is a convention to denote that `$colorButton` stores a jQuery object.

    - In general, you can change event behavior using the `.on()` function. For instance, to change the `click` and `mouseover` behavior for `p` elements, you can use
        ```javascript
        $("p").on("click mouseover", function() { ... });
        ```

- Getting element content from a jQuery selection:

    - The `html()` function returns the HTML code from the *first* element in the matched set. In an example web page, `$("ul").html()` may return
        ```html
        <li id="one"><em>fresh</em> figs</li>
        <li id="two">pine nuts</li>
        <li id="three">honey</li>
        <li id="four">balsamic vinegar</li>
        ```
    but `$("li").html()` will only return
        ```html
        <em>fresh</em> figs
        ```

    - The `text()` function returns the text content from every element in that jQuery selection. In the same example web page, `$("ul").text()` may return
        ```
        fresh figs
        pine nuts
        honey
        balsamic vinegar
        ```
    but `$("li").text()` returns
        ```
        fresh figspine nutshoneybalsamic vinegar
        ```

- Modifying content with jQuery

    - We just saw how you can use `.html()` and `.text()` to *access* content. You can use the same functions, but with parameters, to modify the content in elements. For instance, we can *modify* the text in `hexCodeHeading` to reflect the new hex code using
        ```javascript
        $("#hexCodeHeading").text(randomColor);
        ```

    - You can also use `.replaceWith()` and `.remove()` to modify data.

    - You can also modify an element's CSS using jQuery.

        - Use `.addClass("my-css-class")` to add the CSS class `my-css-class` to an element. You can add several CSS classes at the same time using a space-separated list of the classes to add: `.addClass("my-css-class my-other-css-class")`

        - You can use the `.css()` function to manipulate an object's CSS properties. `.css()` takes two parameters: a string with the property name, and a string with that property's new value. For instance, to change the background color of all `p` elements to red, you would use
            ```javascript
            $("p").css("background-color", "red");
            ```

            - You can set multiple CSS properties at once like so:
                ```javascript
                $("p").css({
                    "background-color":"red",
                    "font-size": "200%"
                })
                ```

- jQuery gives you several functions for adding new content to a web page: `.before()`, `.after()`, `.prepend()`, and `.append()`.

    - `.before()` inserts content directly before the targeted element(s). `$("ul").before("<p>Important message!</p>")` will add a `p` element reading `Important message!` before every `ul` element on the page.

    - `.after()` inserts content directly after the targeted element(s). `$("ul").after("<p>Another important message!</p>")` will add a `p` element reading `Another important message!` after every `ul` element on the page.

    - `.prepend()` inserts content just after the selected element's/elements' opening HTML tags. For instance, `$("li.red").prepend("<em>")` will first find all `li` elements with the CSS class `red`, and then add `<em>` just after the opening `<li>` tag for each of them.

    - `.append()` inserts content just before the selected element's/elements' closing HTML tags. For instance, `$("li.red").append("</em>")` will first find all `li` elements with the CSS class `red`, and then add `</em>` just before the closing `</li>` tag for each of them.

- jQuery also lets you access modify HTML elements' properties.

    - The `.attr()` function, when given a single string parameter, will return the value of that HTML element's property. For instance, `$("p").attr("id")` will return the `id` attributes of all `p` elements on the page. When used with *two* string parameters, `.attr()` replaces the property with the new value -- the second parameter. `$("p").attr("class", "red")` sets all `p` elements' class attributes to `red`.

    - You can remove attributes using `.removeAttr()`. `$("p").removeAttr("id")` removes all `p` elements' `id` attributes.

- As mentioned plenty before, you can get a list of all elements matching a set of criteria if you use certain selectors. For instance, `$("p")` returns a list of all `p` elements on the page. Many functions will automatically operate on the entire elements of the returned list. Sometimes, however, you need to loop through that list. jQuery provides the `.each()` function for that. While inside that `.each()` loop, you can use the `this` selector or the `$(this)` selector to select the current element in the list. The following code gets a list of all `li` elements on the page, and then loops through that list, appending that `li` element's `id` to the end of that `li` element in a `<span>` tag.
    ```javascript
    $("li").each(function(){
        var id = this.id;
        $(this).append(" <span class=order>" + id + "</span>");
    });
    ```

***

##### jQuery – Practice

- There are far more things you can do with jQuery, but we have to stop somewhere. Using what we know, let's refactor our color generator code for jQuery.

- **HTML:** Our HTML page will be nearly identical. The only difference is that we need to import jQuery. Here we do so using the Google CDN link. Note that the jQuery import is inserted before the jQuerified `ColorGenerator.js` script is.
    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <title></title>
            <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
            <script src="ColorGenerator.js"></script>
        </head>
        <body>
            <center>
                <h1 id="hexCodeHeading">#ffffff</h1>
                <button type="button" id="colorButton">Generate New Color!</button>
            </center>
        </body>
    </html>
    ```

- **JavaScript:** Our JavaScript code will have quite a few differences. For one thing, we'll access elements using `$()`, and we'll denote that jQuery objects are being stored by prepending `$` to the variable names. For another, we'll use jQuery's event functions instead of vanilla JavaScript's.
    ```javascript
    // Can't access anything like the button until we know the page has loaded
    $(document).ready(function() {
        // First, find and store the button using its 'id' tag
        var $colorButton = $("#colorButton");

        // Let's also get access to the hex code heading
        var $hexCodeHeading = $("#hexCodeHeading");

        // Give colorButton a clicking behavior
        $colorButton.click(function() {
            // Generate new hex color
            var randomColor = generateColor();

            // Update the heading which shows the hex code
            $hexCodeHeading.text(randomColor);

            // Set background color
            $("body").css("background-color", randomColor);
        });
    });

    var hexDigits = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f'];

    // Generate a random hex color
    function generateColor()
    {
        var color = "#";
        for(var i = 0; i < 6; i++)
        {
            // Randomly choose which digit should be appended
            var digit = hexDigits[Math.round(Math.random() * 15)];

            // Append digit
            color += digit;
        }
        return color;
    }
    ```

- On your own time, trying seeing how you can further improve this web page using JavaScript and jQuery! For instance, can you add a list of previously generated colors? Can you make sure the heading text is always visible regardless of how light or dark the background is?

***

##### Resources

- [W3Schools](http://www.w3schools.com)

- [jQuery Documentation](http://api.jquery.com/)

- [*JavaScript & jQuery: Interactive Front-End Web Development* by Jon Duckett ](https://www.amazon.com/JavaScript-JQuery-Interactive-Front-End-Development/dp/1118531647/)
