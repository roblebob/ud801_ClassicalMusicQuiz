# TMED.03-Exercise-EventListening

## Introduction

Now we have a customized media player that works perfectly for our app. 
The last step is to make it play well with external clients and other apps. 
But before we can set up a __Media Session__, we need to find out what the state of _ExoPlayer_ is so that we can keep our __Media Session__ in sync. 
We learned that state changes happen automatically with our ```SimpleExoPlayerView```, but how are we going to get that information over to the __Media Session__? 
Go to the next video to find out!

## ___ExoPlayer___ Event Listening

In this exercise, you'll monitor the state changes of the _ExoPlayer_ using an `EventListener`, and log the state every time it changes.


## Quiz Question

In which method should you update the state of the __MediaSession__ ?

[&emsp;] `onPlay()`

[&emsp;] `MySessionCallbacks`

[&emsp;] `onPlayerStateChanged()`

[&emsp;] `onCreate()`