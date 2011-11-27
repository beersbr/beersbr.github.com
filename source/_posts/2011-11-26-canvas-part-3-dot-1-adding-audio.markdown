---
layout: post
title: "Canvas part 3.1: Adding audio"
date: 2011-11-26 21:49
comments: true
categories: programming game-programming javascript html5 canvas
---

### Game programming in canvas

This is just a continuation of what I started in the last post. I covered images, so I though audio would be a good next step. Here we go...

### Audio in javascript

Games aren't really complete without audio most of the time. I have not yet figured out how to gain full control of sound in javascript but here is a good first step -- Similar to the previous post on images we are going to create the element in javascript like so:

``` javascript
	var sound = document.createElement("audio");
	sound.src = "path/to/file.ogg"; // or .wav

	// load the sound
	sound.load();
	sound.play();
```

As said above the sound file has to be either an `.ogg` or `.wav`, at least for now. the `load()` function will make sure the data is in memory or so I have been told. Next you call `play()` and the sound will play to completion. Now looking at a context closer to that of a games; say we have an object we would load and then call `play()` during some collision or some event. 

#### Example (extremetly contrived):
``` javascript
function player(){
	var my_pos = {x, y, w, h}; // some data describing this players position  
	var health = 100;

	//setup sound data
	var collide_sound = document.createElement('audio');
	collide_sound.src = 'some_sound.ogg';
	collide_sound.load();

	this.update = function(close_objects){
		for(var i in close_objects){
			if(this.collides_with(close_objects[i])){

				collide_sound.play();
				health -= 1;
				// do some stuff 
			}
		}
	}

	this.draw = function(){
		// some drawing code here
	}

	this.collides_with = function(an_object){
		// a collision function of some sort
	}
}

// then we create a new player object and use it in our game.

```

Just some psudo code to give you an idea of how it would be used. You can also make a nice tune for the game in the background as you can have multiple audio files loaded and they can even be played at the same time. 

### Some other neat parts to take note of...

* `audioELement.currentTime = 10;` will set the media time to 10 seconds.
* `audioElement.duration;` will return the duration of the media.
* `audioElement.pause();` will pause the media. There is no `stop()` for what ever reason but you can unset the src and reset the src (as an ugly hack) if you need to stop it.

Those are just handy to remember. As always you can check the [MDN docs](hhttps://developer.mozilla.org/En/Using_audio_and_video_in_Firefox). Hope this helps!
