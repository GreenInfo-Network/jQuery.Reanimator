# jQuery.Reanimator

## Animated image-based movies as you scroll, click, or hover

Reanimator allows you to create image-based slideshow movies. These "movies" are intended to be embedded into larger scrolling content, and will animate as you scroll the page.

This is different than a regular slideshow:
* The image cycling happens on page scrolling and specifically has no transitions so it's super smooth
* This control is designed for use within other content such as as flowing paragraphs of text, and works well with *float:right* and *margin* like images.
* Very slim code for very swift performance.

Some things are better seen than explained, so [check out the demo to see it yourself.](http://greeninfo-network.github.io/jQuery.Reanimator/)


## Basic Usage

It's important to note, that because Reanimator is based on scrolling, there must be page content to scroll. If your page is only one paragraph, there will likely be no scrolling except on very small screens.

```
<div class="reanimator" style="width:300px; height:300px;" data-reanimator-click="true">
    <img src="frames/image01.jpg" />
    <img src="frames/image02.jpg" />
    <img src="frames/image03.jpg" />
    <img src="frames/image04.jpg" />
    <img src="frames/image05.jpg" />
</div>
```

```
$(document).ready(function () {
    $('div.reanimator').reanimator({
        click: false
    });
});
```

## Options

* **debug** -- Enable debugging behavior and logging. Default: *false*
* **above** -- Add to the scrolling area, this much extra space above the image's actual position. Default: *0*
* **below** -- Add to the scrolling area, this much extra space below the image's actual position. Default: *0*
* **scroll** -- Set this to *false* to disable the scrolling behavior. Probably useful if you want to use *mouse* or *click* but the page area and page content won't make for a usable scrolling experience. Default: *true*
* **click** -- If set to *true* then clicking the animation frame, will forward animation by a frame, looping back to the beginning if necessary. This allows one to manually watch the animation without scrolling. Using *click* and *mouse* at the same time, probably doesn't make sense. Default: *false*
* **mouse** -- If set to *true* then moving the mouse cursor over the animation frame, will play the animation. Using *click* and *mouse* at the same time, probably doesn't make sense. Default: *false*

Options can be passed to the constructor, and also by adding a *data-reanimator-**option**="**value**"* attribute to the tag.

The attribute-supplied  options override the constructor-supplied options. In the Basic Usage example above, the *click* feature is set to false for all Reanimator instances, but that specific one overrides it to *true*.



## Scrolling Triggers, Limitations, Above and Below

Reanimator is based on the idea of scrolling the page content to activate the animations. If your page has insufficient content for scrolling, the effect will be greatly diminished. This is largely a function of how much line-wrapping happens: if your site has a fixed width and lot of text, then there will be plenty of scrolling and the images will be at their best.

Reanimator's trigger zone, is the midline of the window's vertical height. As images cross this area, their animations are triggered. The *above* and *below* options can be used to extend this hit box, so that animation starts earlier and ends later. This is particularly useful for an animation that is not particularly "tall" but where you want a larger, more granular area of scrolling animation.

An animation positioned at the very top and very bottom of the page content, can encounter a situation in which one could never scroll it across the midline. An easy option (if it's at the end) is to add empty space so one can scroll further. Alternately, the *above* and *below* options can be used to extend the scrolling area. *Tip: You can even specify negative values for **above** and/or **below** so as to put the hitbox outside the actual position of the animation.*

For these sorts of situations, you will want to enable the *debug* option, which will draw the hit boxes and the midline on-screen.
