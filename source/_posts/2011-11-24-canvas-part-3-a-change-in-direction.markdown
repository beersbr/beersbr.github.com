---
layout: post
title: "Canvas Part 3: A change in direction"
date: 2011-11-24 00:00
comments: true
categories: programming game-programming javascript html5 canvas
---

### Game programming in canvas

Hopefully by know you have played with some of the drawing functions I used in the last two tutorials. I am sort of changing directions because I love programming games and canvas gives you a quick platform to use. But first we need to discuss how we are going to get certain things on the browser. Things like images, sounds, key events, etc etc. 

### Images in canvas

As it turns out drawing images on the screen is actually very simple:

``` javascript
	var image = new Image();
	i.src = "/some/path/to/an.img";
```

Easy, right? Now all we have to do is draw it to the canvas. As luck would have it, that is super easy too!

``` javascript
	var cvs = document.getElementById('c');
	var ctx = cvs.getContext('2d');

	var i = new Image();
	i.src = "/some/path/to/an.img";

	ctx.drawImage(i, 100, 100);
```

Now that loads an image and draws it on the canvas at (100, 100). There are several `drawImage()` functions. They are all similar but are good to know so lets go ver them now.

* `drawImage(image, x, y)` Draws an image from the top left corner at (x, y). This is the function I used above.
* `drawImage(image, x, y, width, height)` Draws an image to (x, y), as the size width, and height. It is basically a way to scale your images in canvas.
* `drawImage(image, source_x, source_y, source_height, source_width, destination_x, destination_y, destination_width, destination_height)` This one is a bit more complex in that it allows you to slice your image. This is useful for tile-sheets or sprite-maps. Source_* creates a rectangle you want to grab from the original image and destination is where  you are going to put that rectangle. You can tinker around with that by use the code above and playing with each function. I will put up some code as well in the very near future.

One thing to note is that you can't grab coordinates that are not in the image. For example if you have an image with a width of 100 and height of 100, you can grab coordinates (-1, -1) to (500, 500). From my experience that will produce javascript image read errors.

### Splitting this section

In an effort to keep these posts at a readable length I am going to split this part into sub parts. This was the image section and I will go over audio and then key events. You can find more information by checking out the [MDN docs](https://developer.mozilla.org/en/HTML/Canvas). You can also just send me a message with any thing you might have. Thank you!
