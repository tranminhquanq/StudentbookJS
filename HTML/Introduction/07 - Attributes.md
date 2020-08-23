# Attributes

If we want to expand an element’s tag, we can do so using an ***attribute***. Attributes are content added to the opening tag of an element and can be used in several different ways, from providing information to changing styling. Attributes are made up of the following two parts:

* The `name` of the attribute.
* The `value` of the attribute.

One commonly used attribute is the `id`. We can use the `id` attribute to specify different content (such as `<div>`s) and is really helpful when you use an element more than once. `id`s have several different purposes in HTML, but for now, we’ll focus on how they can help us identify content on our page.

When we add an `id` to a `<div>`, we place it in the opening tag:

``` HTML
    <div id="intro">
        <h1>Introduction</h1>
    </div>
```

### Instructions

``` HTML
    <body>
        <h1>The Brown Bear</h1>
        <div>
            <h2>About Brown Bears</h2>
            <h3>Species</h3>
            <h3>Features</h3>
        </div>
        <div>
            <h2>Habitat</h2>
            <h3>Countries with Large Brown Bear Populations</h3>
            <h3>Countries with Small Brown Bear Populations</h3>
        </div>
        <div>
            <h2>Media</h2>
        </div>
    </body>
```

1. Add an `id` attribute with the value `"introduction"` to the `<div>` tag that’s below the The Brown Bear `<h1>` heading.

2. Add an `id` attribute with the value `"habitat"` to the opening `<div>` tag that has the `Habitat` `<h2>` heading as a child.

3. Add an id attribute with the value `"media"` to the opening `<div>` tag that has the `Media` `<h2>` heading as a child.