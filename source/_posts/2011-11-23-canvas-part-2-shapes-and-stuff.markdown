---
layout: post
title: "Canvas part 2: Shapes and stuff"
date: 2011-11-23 13:41
comments: true
categories: tutorial javascript programming
---

### A little more interesting

The last tutorial I just showed how to get the canvas up on a page and into a state that something could be done with it. But drawing rectangles is kinda boring. So now I'll show you something a little more interesting.

### Shapes!

Shapes are made by using paths to vertecies. For this we use the `moveTo(x, y)` and `lineTo(x, y)` methods. 

* `moveTo(x, y)` will move you to a point (x, y) without tracing the path to that point (x and y are pixel units). You usually use it for the start of your path. 

* `lineTo(x, y)` will move you to a point (x, y) and trace the path there. So when we call `fill()` or `stroke()` (we will discuss them shortly ) we have something to draw.

Let's have a look at the javascript:

``` javascript paths http://tinkerbin.com/J92xNsA6
window.onload = function(){
  var cvs = document.getElementById('c');
  var ctx = cvs.getContext('2d');
  
  ctx.moveTo(50, 50);
  ctx.lineTo(250, 50);
  ctx.lineTo(150, 150);
  ctx.lineTo(50, 50);
  ctx.strokeStyle = "rgb(0, 255, 0)";
  ctx.stroke();
}
```

We do a few things here. First we grab the canvas element. Then we `moveTo(50, 50)` which moves our invisible cursor to point 50, 50 on the canvas where the positive Y moves down instead of up. The next thing we do is use `lineTo(250, 50)` which will make a line from (50, 50), the previous point, to (250, 50) on the canvas. We do this several time till we close the shape with the `lineTo(50, 50)` from (150, 150).

Finally we draw the shape by calling `stroke()`. Shapes like this wont be drawn unless you call either stroke, drawing only the outline of the shape, or fill which will fill the shape in for you. You can call both to get a stroke and fill. Check out the [link](http://tinkerbin.com/J92xNsA6) to play around with it.