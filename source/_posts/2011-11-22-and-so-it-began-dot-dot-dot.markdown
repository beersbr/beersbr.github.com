---
layout: post
title: "Canvas part 1: And so it begins..."
date: 2011-11-22 23:41
comments: true
categories: tutorial javascript programming
---

### The programmers obligatory disclamer

This is the first post of some tutorials and discoveries with HTML5's canvas using javascript. I'm sure I am not doing everything perfect and am certainly open to suggestions and corrections but mostly hope to create a segue from greater canvas noob to lesser canvas noob.

### Starting out with your first canvas

What makes working with canvas so nice is how fast you can get things up and running. You dont need a compiler or a big IDE or knowledge of any complex graphics libraries. All you need is a browser and some javascript. Here is as simple as it gets:

``` html
<html>
<head>
	<script>
		// We will just put our javascript right in the head
	</script>
</head>
<body>
	<canvas id='c' width=640 height=480></canvas>
</body>
</html>
```

That was easy enough right? Now iff you run this you probably wont see anything, as the background of the canvas is probably white. So let's draw some stuff on the screen.

``` javascript yellow_rectangle http://tinkerbin.com/H4Bdbt4B
//<head>

window.onload = function(){
	var cvs = document.getElementById('c');
	var ctx = cvs.getContext('2d');

	ctx.fillStyle = "rgb(255, 255, 0)";
	ctx.fillRect(50, 50, 200, 150);
}

//</head>
```
Now looking at the code, you can probably see everything that is happening. First we grab the canvas element and assign it to variable cvs. Secondly we set the context to 2d and assign it to the variable ctx. Now that we have a context to draw on, we can set the `fillStyle` of the context. The `fillStyle` tells the context what color to fill objects with.
You can use several forms for specifying the color:

``` javascript
	"rgb(255, 255, 255)"; // is white
	"rgba(255, 255, 200, 1.0)"; // is very pale yellow
	"#ffffee"; // is also pale yellow
```
After that we call `fillRect`. This method will just create the rectangle on the canvas. The syntax is:

	fillRect(x, y, width, height)

### There you have it!

Now that you know how to get started with the canvas try drawing some other objects. You can just take a look at [this](http://tinkerbin.com/H4Bdbt4B "tinkerbin") tinkerbin. Look out for the next tutorial on more complex shapes.