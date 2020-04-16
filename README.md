# TMED.02-Exercise-CustomizeLayout

## Customizing ExoPlayer UI

We chose to use __SimpleExoPlayerView__ because of its simplicity. 
It can be hooked up to _ExoPlayer_ with a single line of code and greatly simplifies the UI portion of a media application since we don't have to code anything ourselves. 
However, such simplicity usually comes at the cost of customization: 
you might think that we are stuck with the provided UI since it comes ready out of the box. 
Not so with _ExoPlayer_! 

_ExoPlayer_ comes with two notable out of the box UI elements:

- __PlaybackControlView__ is a view for controlling _ExoPlayer_ instances. 
    It displays standard playback controls including a play/pause button, fast-forward and rewind buttons, and a seek bar.

- __SimpleExoPlayerView__ is a high level view for _SimpleExoPlayer_ media playbacks. 
    It displays video (or album art in our case) and displays playback controls using a __PlaybackControlView__.

These _ExoPlayer_ UI components were created with customization in mind, in the following ways:



## Attributes

The XML items support a variety of xml attributes that customize the look of the UI. 
Take a look at the documentation for the UI element to see the list of possible attributes 
(and their corresponding Java methods).


## Overriding layout files

When these views are inflated, they use specific layout files to determine what the UI looks like. 
For __SimpleExoPlayerView__, this file is called: 
[exo_simple_player_view.xml](https://github.com/google/ExoPlayer/blob/release-v2/library/ui/src/main/res/layout/exo_simple_player_view.xml)
. 
This layout file includes a __PlayBackControlView__ 
(once it's inflated, it replaces the exo_controller_placeholder item) 
which also uses its own layout file: 
[exo_playback_control_view.xml](https://github.com/google/ExoPlayer/blob/release-v2/library/ui/src/main/res/layout/exo_playback_control_view.xml)
.

//

If you include any layout files with the same names, _ExoPlayer_ will use them instead of these default ones. 
This allows you to fully customize what the UI looks like.

//

_One caveat:_ 
Use of standard ids (such as exo_play) is required so that child views can be identified, bound to the player and updated in an appropriate way. 
A full list of the standard ids for each view can be found in the ___Javadoc___ for 
[ __PlaybackControlView__ ](http://google.github.io/ExoPlayer/doc/reference/index.html?com/google/android/exoplayer2/ui/PlaybackControlView.html)
and 
[ __SimpleExoPlayerView__ ](http://google.github.io/ExoPlayer/doc/reference/index.html?com/google/android/exoplayer2/ui/SimpleExoPlayerView.html)
. 
Use of each standard id is optional, which is why we’ll be able to omit some of the usual playback controls in our example.


## Custom Layout Files

The issue with the above method is that it customizes the UI for every instance of __SimpleExoPlayerView__ (and/or __PlaybackControlView__). 
For our use case, this doesn't matter since we only have one player view. 
However, if you need to customize individual instances, you can use a combination of the two above methods: use 
 the `player_layout_id` attribute for a custom __SimpleExoPlayerView__, or 
 the `controller_layout_id` for a custom __PlaybackControlView__ and specify a custom layout file to override the layout for that specific instance.

//

We don't need individual instance customization, so 
override the `exo_playback_control_view.xml` layout file for the playback control view (included in our `SimpleExoPlayerView`) and 
remove the skip to next, fastforward and rewind buttons (you can copy the default layout [here](https://github.com/google/ExoPlayer/blob/release-v2/library/ui/src/main/res/layout/exo_playback_control_view.xml)).

//

After completing this, run the app and notice the change in the UI!
