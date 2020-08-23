# Videos

In addition to images, HTML also supports displaying videos. Like the `<img>` tag, the `<video>` tag requires a src attribute with a link to the video source. Unlike the `<img>` tag however, the `<video>` element requires an opening and a closing tag.

``` HTML
    <video src="myVideo.mp4" width="320" height="240" controls>
        Video not supported
    </video>
```

In this example, the video source (`src`) is `myVideo.mp4` The source can be a video file that is hosted alongside your webpage, or a URL that points to a video file hosted on another webpage.

After the `src` attribute, the `width` and `height` attributes are used to set the size of the video displayed in the browser. The `controls` attribute instructs the browser to include basic video controls: pause, play and skip.

The text, “Video not supported”, between the opening and closing video tags will only be displayed if the browser is unable to load the video.

### Instructions

1. Under the image, create a `<video>` tag and add the following video url as the source:
    > https://content.codecademy.com/courses/freelance-1/unit-1/lesson-2/htmlcss1-vid_brown-bear.mp4

    Be sure to create a closing tag as well with `</video>`.

2. Define the `width` of the video as `"320"` and the height as `"240"`. Make sure to also include the `controls` attribute.

3. In between the `opening` and `closing` `<video>` tags, add the phrase `Video not supported`, which will be displayed if the browser is unable to load your video.