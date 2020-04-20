# TMED.04-Exercise-AddMediaSession

[Working with a Media Session](https://developer.android.com/guide/topics/media-apps/working-with-a-media-session.html)

## Quiz Question

In which method should you update the state of the MediaSession?

[&emsp;] &nbsp; `onPlay()`
[&emsp;] &nbsp; `MySessionCallbacks`
[x] &nbsp; `onPlayerStateChanged()`
[&emsp;] &nbsp; `onCreate()`

`onPlayerStateChanged()`, this is an `ExoPlayer.EventListener` and will be called everytime the player state changes, so this is where we update the __Media Session__.
