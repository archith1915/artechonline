---
{"dg-publish":true,"permalink":"/public/content-folders/html/html-basics/","dgShowToc":true}
---


<center>
<span style="font-size:3.3vh; font-weight: bold;">HTML Basics</span>
<br>
<span>&copy J A Archith</span>
</center>
<br>
<br>

# What is HTML?

- HTML, Hypertext Markup Language is used to create basic structures for web pages.
- It uses tags to demarcate contents on the page. 
- HTML is an interpreted markup language, meaning, it is executed line by line on the client side.

> Note : Client side refers to the user's system or browser. Server side is the remote location where the webpage data is stored and processed.

- Contents written in the HTML structure follow a flow that goes from the top to bottom.
- Anything inside the \<body\> tag is displayed on the webpage. The \<head\> tag is used to store meta information and link CSS and JavaScript files.
- A simple HTML boilerplate looks like this :

```html
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Document</title>

</head>

<body>

    <!-- Webpage content here-->

</body>

</html>
```

- The \<DOCTYPE html\> indicates the version of HTML used in the file. Currently, we are using version 5 of HTML.
- The \<html\> tag with lang="en" denotes the default language used in the webpage. 
- The \<title\> tag is used to display the title of the webpage on the tabs in the browser.
- Every tag used in the HTML code needs to be closed. A '/' after the angle bracket denotes the closing tag. Ex: \</body>, \</head>, etc.



---
*Created : .*
*Last Modified : .*