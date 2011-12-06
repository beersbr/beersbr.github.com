---
layout: post
title: "Canvas part 4: A game loop"
date: 2011-12-06 13:36
comments: true
categories: tutorial javascript programming
---

### A game loop in javascript

A game loop is pretty pivotal in any game taking on a common format of update() -> draw(). Meaning that you update() all of your game objects and data for the current frame and then draw that frame to the screen. We do this over and over at a fixed framerate (usually 30 or 60 frames per second) and we get an animation. Things like user input and system changes would go into the update() section, while all your drawing calls would go into the draw() section. Here is a quick example:

``` javascript moving_box http://tinkerbin.com/pP0suTI6
//...

var cvs = document.getElementById('c');
var ctx = cvs.getContext('2d');
var interval = 0;

// get the canvas width and height
var scr_w = cvs.width;
var scr_h = cvs.height;

function Rect(){
	this.x = 200;
	this.y = 200;
}

var urect = new Rect();

function Update(){
	urect.x = (urect.x + 1)%scr_w;
	urect.y = (urect.y + 1)%scr_h;
}

function Draw(){
	ctx.save(); // save the context state so we don't disrupt any other draw calls
	ctx.fillStyle = "rgb(100, 200, 100)";
	ctx.fillRect(urect.x - 10, urect.y - 10, 20, 20);
	ctx.restore(); // restore the context state to whatever it was before
}

function Loop(){
	Update();
	ctx.clearRect(0, 0, scr_w, scr_h);
	Draw();	
}

window.onload = function(){
	var interval = setInterval(Loop, 1000/30); // run it at 30 fps
}

//...
```

Ok I haven't done anything completely new except for the use of `setInterval`. We are using it to repeat the game loop at a fixed amount of time. It's somewhat crude but for now it will work perfectly. The sytax for `setInterval` is as follows: 

	integer_id setInterval(function_pointer, time_interval_mili);

It returns an id that can be used by a sister function `clearInterval(id)` to stop the interval. Then you pass a function pointer or a string of code. Lastly you give it the time interval at which to execute the function or code passed to `setInterval`. 1000 miliseconcs is a second. So if we divide by the desired framerate we will be given the amount of miliseconds it takes to achieve that.

### Stepping through the rest of the code

Now to iterate over the rest of the code we do the usual stuff by getting the canvas and context into variables. Secondly we create an object named `Rect` which is just a container for holding some values. We instanciate a `Rect` as `urect`. Then there is a funciton for updating the state of `urect`. It takes the current x position, `urect.x`, and increses it by 1 and the mod operator makes sure that we never go over the max screen width. It does the same with `urect.y`. We grave the max screen width `scr_w` and `scr_h` right from the canvas.

Next we have the `Draw()` function which takes our object instace and handles drawing a rectangle at the position of our `urect`. We use `save()` and `restore()` in this function so that if we have another method that is drawing stuff we dont interupt its drawing. Think of it as saving a set attributes onto a stack similar to openGl, for anyone who has used openGl. The `save()` function saves all the current canvas attributes. While `restore()` pops the last save off the "stack" and the attributes go back to whatever they were before the last `save()` call.

Lastly we have the `Loop()` function which is used in `setInterval()` to update the game objects and draw them to the canvas. All that loop does is act as a container for `setInterval()`. We call `Update()` then we clear the canvas so you don't have multiple images on the screen. Then it call `Draw()` which draws the rectangle on the canvas.

### And a game loop is made...

While this example was simple it's not entirely unrealistic. Things will get more interesting after some of the simple parts are covered. Have fun!
