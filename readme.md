# HTML & CSS

## Learning Objectives
- Review the roles of HTML and CSS in web pages
- Identify the parts and roles of HTML boiler plate
- Identify the parts of an HTML element
- Distinguish in-line styles, style tags, and linked style sheets
- Break down the syntax of a CSS declatation and a CSS rule(set)
- Distinguish the components of the box model
- Practice

## Overview (5 minutes / 0:05)

This lesson will be a refresher on the fundamentals of HTML and CSS.
All material is review from the pre-work and so will move quickly and potentially glosses over material.
For a much more robust treatment, please see [the Mozilla Developer Network Learning Area](https://developer.mozilla.org/en-US/docs/Learn).

## HTML (Hyper Text Markup Language) (5 minutes / 0:10)

HTML exists to solve the problem of how a rich document can be expressed in plain text.
That is to say what are the parts of the document, what role does each part serve (e.g. heading, image list, emphasized text, link etc.), and how to they relate to one another.

HTML expresses the **structure and semantics** of a document in plain text.

### Elements (10 minutes / 0:20)

The parts of an HTML document are called **elements** and they are denoted with **tags**.
Tags come at the beginning and end of an element's content.

Extra information about elements can be added using **attributes** which are added to the opening tag.
A ubiquitous element which always needs an attribute is the `a` (for *anchor*) element.
The `a` element creates a link to another location, frequently another page.

We express the structure of an HTML document by nesting.
For example, we can take a paragraph:

```html
<p>The easiest way to learn HTML is to use it!</p>
```

and we can empasize part of the sentence using `em` tags:

```html
<p>The easiest way to learn HTML </em>is to use it!</em></p>
```

We can add a link to the word `HTML` that goes to the MDN HTML page (https://developer.mozilla.org/en-US/docs/Web/HTML)

```html
<p>
  The easiest way to learn
  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML">
    HTML
  </a>
  </em>is to use it!</em>
</p>
```

Notice the use of whitespace (linebreaks and indentation) here.
The whitespace makes no difference to the browser but is significantly more readable.

An element can be the child of another element (contained within its parents tags) but can never strattle another element.

```html
<!-- Don't do this! -->
<p>The easiest way to learn HTML </em>is to use it!</p></em>
```

Similarly, do not omit closing tags.
Every element needs a closing tag (with the exception of **empty elements** which we'll discuss momentarily).

```html
<!-- Also, don't do this! -->
<p>The easiest way to learn HTML </em>is to use it!</em>
```

Browsers are extremely accomidating and so will likely display something but this behavior can't and shouldn't be depended upon.

Because the browser can be uninformatively accomidating, we want to double check our work with an [HTML validator](https://validator.w3.org/).
Even our valid example above (with the anchor tag) won't validate just yet as we are missing some required boiler plate.

### HTML Boilerplate (20 minutes / 0:40)

When a client's browser gets an HTML file from the server, it begins building a document that will be displayed to the user.

Consider the following HTML boilerplate (conveniently available as a snippet in your text editor by typing `html` then hitting **tab**)

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>

  </body>
</html>
```

This is very nearly valid HTML.
The only missing requirement is content in the `title` tag.

The first line `<!DOCTYPE html>` declares that the document is an HTML document.
This is largely vestigial but necessary and not worth worrying about at the moment beyond knowing it is necessary.

The next line opens the top level element, `html` which represents the entire document.
This is the only top level element and spans the whole document.
The closing `html` tag should be the last line of the page.

The `html` element has two children, `head` and `body`.
Both `head` and `body` are required and they are the only two valid children of `html`.

#### Head

The `head` element holds **metadata** about the document that is to say extra information about the document beyond the content of the document.
One required piece of metadata is the `title` element.
Every page is required to have a title; without one the HTML document is invalid.

The `meta` element declares the *charset* or set of characters to be used in this document to be **utf-8** which includes most characters from all known human languages.
This is not required but can avoid some

Other examples of metadata include linking of external stylesheets (more later) and importing of scripts to run on the page.

#### Body

The `body` element contains the information actually presented to the user; it represents the content of the document.

### Valid HTML in a file (10 minutes / 0:50)

Before we start adding content to the body lets create a file localy for our work so we can open it.

Create a directory in you sandbox called `html-and-css`

```bash
cd ~/wdi/sandbox
mkdir html-and-css
cd html-and-css
```

Create a file `index.html` and open it with atom

```bash
touch index.html
atom index.html
```

Note: All code for this lesson is available in [this repo](https://github.com/ga-wdi-exercises/html-css-in-class/tree/master) with branches for each step.

In `index.html` type `html` and hit **tab**.
You will see the same boilerplate from above.
Add the paragraph we used as an example to the page body and give the page a title.
`index.html` should look like this:

```hmtl
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>HTML Practice</title>
</head>
<body>
  <p>
    The easiest way to learn
    <a href="https://developer.mozilla.org/en-US/docs/Web/HTML">
      HTML
    </a>
    <em>is to use it!</em>
  </p>
</body>
</html>
```

This is valid HTML.
We can confirm this by copying and pasting the code into an [HTML validator](https://validator.w3.org/#validate_by_input).

We can also open this file in the browser by running from the command line:

```bash
open index.html
```

Wow!
Super dull!
We'll work on making this more lively shortly but first some practice fixing invalid HTML.

#### Exercise: [HTML Fixit](https://github.com/ga-wdi-exercises/html_fixit) (15 minutes / 1:05)

- 10 minutes working / 5 minutes review
- Work with a partner and write out plain English answers
- If you finish early, add additional HTML trying to provoke various error messages

### More Elements (20 minutes / 1:25)

There are tons of different HTML elements and memorizing them is impracticle.
Instead, it is better to start using 20 percent of the building blocks that get you 80 percent of the way there.
Among these are headings, paragraphs, lists, and images.

#### Headings

The `h1` - `h6` tags are for headings and subheadings.
It's rare to use past 3 or 4.

```html
<h1>I'm most important! There should really only be one of me on a page.</h1>
<h2>I'm still quite important! I'm fine being on the page a few times though</h2>
<h3>I'm pretty common!</h3>
<h4>I'm quite detailed</h4>
<h5>I'm probably deep in a menu</h5>
<h6>Wow, that's very detailed</h6>
```

#### Paragraphs

The `p` tag is used for paragraphs

```html
<p>Not a ton going on here...</p>
```

#### Lists

People love lists.
There are two types of HTML lists, ordered and unordered.

```html
<ol>
  <li>I'm first</li>
  <li>I'm second</li>
  <li>I'm third</li>
</ol>
<ul>
  <li>red</li>
  <li>green</li>
  <li>blue</li>
</ul>
```

#### Images

If there's anything people like more than lists it's pictures.
Pictures are **empty elements** meaning that they cannot logically have children and so are represented in HTML with a single self closing element.
Some people put a slash at the end of empty elements but it is unecessary.

```html
<img src="" alt="" />
<!-- is the same as -->
<img src="" alt="">
```

Images require two attributes, a `src` with a URL for an image, and an `alt` tag for screen readers and when something breaks and the image doesn't show up.
The url can be any address but generally we want to manage our own assets.

Right click the picture and click **Save image as...** and give the file a shorter name and make sure you save it to Downloads.
I've gone with `html5logo.png`.

![HTML5 Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/HTML5_logo_and_wordmark.svg/1024px-HTML5_logo_and_wordmark.svg.png)

Move the file from your Downloads folder to the `css-and-html` directory.

```bash
mv ~/Downloads/html5logo.png ~/wdi/sandbox/css-and-html/
```

We tell the browser to request an image and load it into the page by giving an image tag's source attribute a path to the image.

```html
<img src="html5logo.png" al="html5 logo" >
```

### Wire Framing (5 minutes / 1:30)

It is good practice to sketch up an approximation of what you'd like your end product to look like.
It's alright if it's a rough approximation.

TODO: Wireframe picture

The text and links:

```
Good Strategies
===============
Imitation
Repition
Inspection
Reflection

Good Links
==========
MDN HTML Tutorials (https://developer.mozilla.org/en-US/docs/Learn/HTML)
MDN list of inline HTML elements (https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)
MDN list of block level HTML elements (https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)
```

### Build Out Wireframe (10 minutes / 1:40)

- 5 minutes working / 5 minutes discussing

## Break (10 minutes / 1:50)

## CSS (Cascading Style Sheets)

We use CSS to tell browsers how we would like for them to **paint** or display the elements of our document.

### Websites without CSS (5 minutes / 1:55)

### CSS File (5 minutes / 2:00)

To get started writting styles we will create a new file.

```bash
touch ~/wdi/sandbox/css-and-html/style.css
```
> notice, this is an absolute path, if you're in the `css-and-html` directory you can just `touch style.css`

Then we will add a line to our HTML linking the stylesheet.

```html
<link rel="stylesheet" href="style.css">
```

### CSS Rules (5 minutes / 2:05)

CSS styles are a series of **rules** or **rulesets**.
A rule is a combination of a **selector** and a set of **declarations**.

![Anatomy of a CSS Ruleset](https://mdn.mozillademos.org/files/9461/css-declaration-small.png)

## Selector (15 minutes / 2:20)

A rule used to match element to which the rule should apply.
As shown this can be an element.
Very commonly we add `class` or `id` attributes to elements mark for targeting by a specific rule.
Selectors can be combined and related and there are many more types of [selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors).
Especially interesting are [pseudo class selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements).

### Exercise: [CSS Diner](http://flukeout.github.io/)
- 7 minutes working / 3 minutes review

## Declaration (5 minutes / 2:25)

### Property
- There are tons of properties
- Again we're looking for 20% that gets us 80% of the way
  - color
  - background
  - font-size
  - line-height
  - align
  - layout properties (box model)

### Property Value

## Box Model (5 minutes / 2:30)
![Box Model](https://upload.wikimedia.org/wikipedia/commons/5/53/Css_box_model.svg)
- display
- width and height
- padding
- margin
- border

## Fonts (Bonus)


## Style Learning HTML and CSS page
- 10 minutes / 5 review

## [Hippie Portfolio](https://github.com/ga-wdi-exercises/hippy-portfolio)

## Exercise: [Fashion Blog](https://github.com/ga-wdi-exercises/fashion-blog)

## Homework: [Wendy Bite](https://github.com/ga-wdi-exercises/wendy_bite)
