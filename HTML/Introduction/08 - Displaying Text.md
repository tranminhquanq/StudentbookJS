# Displaying Text

If you want to display text in HTML, you can use a *paragraph or span*:

* *Paragraphs* (`<p>`) contain a block of plain text.
* `<span>` contains short pieces of text or other HTML. They are used to separate small pieces of content that are on the same line as other content.

Take a look at each of these elements in action below:

``` HTML
    <div>
        <h1>Technology</h1>
    </div>
    <div>
        <p><span>Self-driving cars</span> are anticipated to replace up to 2 million jobs over the next two decades.</p>
    </div>
```
In the example above, there are two different `<div>`. The second `<div>` contains a `<p>` with `<span>Self-driving cars</span>`. This `<span>` element separates “Self-driving cars” from the rest of the text in the paragraph.

It’s best to use a `<span>` element when you want to target a specific piece of content that is *inline*, or on the same line as other text. If you want to divide your content into blocks, it’s better to use a `<div>`.

### Instructions

``` HTML
    <body>
        <h1>The Brown Bear</h1>
        <div id="introduction">
            <h2>About Brown Bears</h2>
            <h3>Species</h3>
            <h3>Features</h3>
        </div>
        <div id="habitat">
            <h2>Habitat</h2>
            <h3>Countries with Large Brown Bear Populations</h3>
            <h3>Countries with Small Brown Bear Populations</h3>
        </div>
        <div id= "media">
            <h2>Media</h2>
        </div>
    </body>
```

1. Below the `<h2>` element that says `About Brown Bears`, add `<p>` opening and closing tags, and inside of the tags put the following text:

    > *“The brown bear (Ursus arctos) is native to parts of northern Eurasia and North America. Its conservation status is currently Least Concern. There are many subspecies within the brown bear species, including the Atlas bear and the Himalayan brown bear.”*

    Remember to always add two spaces of indentation when you nest elements inside of `<div>`s for better readability.

2. Below the `<h3>` element that says `Features`, add a paragraph with the following text:

    > *“Brown bears are not always completely brown. Some can be reddish or yellowish. They have very large, curved claws and huge paws. Male brown bears are often 30% larger than female brown bears. They can range from 5 feet to 9 feet from head to toe.”*

3. Under the `<h3>` element that says: `Countries with Small Brown Bear Populations`.

    Add a paragraph with the following text:

    > *“Some countries with smaller brown bear populations include Armenia, Belarus, Bulgaria, China, Finland, France, Greece, India, Japan, Nepal, Poland, Romania, Slovenia, Turkmenistan, and Uzbekistan.”*