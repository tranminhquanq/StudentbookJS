# Images

The `<img>` tag allows you to add an image to a web page. Most elements require both opening and closing tags, but the `<img>` tag is a *self-closing* tag. Note that the end of the `<img>` tag has a forward slash `/`. Self-closing tags may include or omit the final slash — both will render properly.

``` HTML
    <img src="image-location.jpg" />
```

The `<img>` tag has a required *attribute* called ***src***. The `src` attribute must be set to the image’s *source*, or the location of the image. In this case, the value of src must be the *uniform resource locator* (URL) of the image. A URL is the web address or local address where a file is stored.

# Image Alts

The ***alt*** `attribute`, which means alternative text, brings meaning to the images on our sites. The `alt` attribute can be added to the image tag just like the `src` attribute. The value of `alt` should be a description of the image.

``` HTML
    <img src="#" alt="A field of yellow sunflowers" />
```

### Instructions

1. Under the `Media` `<h2>` heading, add an image. Use the following URL as the source (`src`) for the image:
    > https://s3.amazonaws.com/codecademy-content/courses/web-101/web101-image_brownbear.jpg

2. Add the ***alt*** attribute to the image and include a description. Make sure the description accurately describes the image.