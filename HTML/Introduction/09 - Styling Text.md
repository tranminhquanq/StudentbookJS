# Styling Text

You can also style text using HTML tags. The `<em>` tag emphasizes text, while the `<strong>` tag highlights important text.

Later, when you begin to style websites, you will decide how you want browsers to display content within `<em>` and `<strong>` tags. Browsers, however, have built-in style sheets that will generally style these tags in the following ways:

* The `<em>` tag will generally render as *italic emphasis*.
* The `<strong>` will generally render as bold emphasis.

Take a look at each style in action:

``` HTML
    <p><strong>The Nile River</strong> is the <em>longest</em> river in the world, measuring over 6,850 kilometers long (approximately 4,260 miles).</p>
```
In this example, the `<strong>` and `<em>` tags are used to emphasize the text to produce the following:

### Instructions

``` HTML
    <body>
        <h1>The Brown Bear</h1>
        <div id="introduction">
            <h2>About Brown Bears</h2>
            <p>The brown bear (Ursus arctos) is native to parts of northern Eurasia and North America. Its conservation status is currently Least Concern. There are many subspecies within the brown bear species, including the Atlas bear and the Himalayan brown bear.</p>
            <h3>Species</h3>
            <h3>Features</h3>
            <p>Brown bears are not always completely brown. Some can be reddish or yellowish. They have very large, curved claws and huge paws. Male brown bears are often 30% larger than female brown bears. They can range from 5 feet to 9 feet from head to toe.</p>
        </div>
        <div id="habitat">
            <h2>Habitat</h2>
            <h3>Countries with Large Brown Bear Populations</h3>
            <h3>Countries with Small Brown Bear Populations</h3>
            <p>Some countries with smaller brown bear populations include Armenia, Belarus, Bulgaria, China, Finland, France, Greece, India, Japan, Nepal, Poland, Romania, Slovenia, Turkmenistan, and Uzbekistan.</p>
        </div>
        <div id="media">
            <h2>Media</h2>
        </div>
    </body>
```

1. In the first paragraph that starts “`The brown bear…`”, emphasize `Ursus arctos` using the `<em>` tag.

2. In the paragraph under `About Brown Bears`, make the words `Least Concern` strong using the `<strong>` tag.