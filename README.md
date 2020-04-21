# TMED.07-Exercise-AddExtras

## Android Media Framework Extras

### Audio Focus

This is how the Android framework knows about different applications using audio. 
If you want your app to fade out when other important notifications _(such as navigation)_ occur, 
 you'll need to learn how your app can _"hop in line"_ to be the one in charge of audio playback, 
  until another app requests __focus__.
  


### Noisy Intent

There are certain conditions that you will want to check for. 
For example, imagine you are blasting your favorite song at full volume. 
Little does anyone know, but your favorite song is _"Itsy Bitsy Spider"_. 
Right when it's about to get to the best part, you trip and yank out the headphones from the audio port. 
Suddenly the whole world knows your secret. 
_Not the best experience right?_ 
Luckily the android framework sends out the [__ACTION_AUDIO_BECOMING_NOISY__](https://developer.android.com/reference/android/media/AudioManager.html#ACTION_AUDIO_BECOMING_NOISY) intent when this occurs. 
This allows you to register a broadcast receiver and take a specific action when this occurs 
_(like pausing the music and saving yourself of embarrassment)_. 



### Audio Stream

Android uses separate audio streams for
 - playing music, 
 - alarms, 
 - notifications, 
 - the incoming call ringer, 
 - system sounds, in-call volume, and 
 - DTMF tones. 
 
This allows users to control the volume of each stream independently.

&nbsp;&nbsp;

By default, pressing the volume control modifies the volume of the active audio stream. 
If your app isn't currently playing anything, hitting the volume keys adjusts the ringer volume. 
To ensure that volume controls adjust the correct stream, you should call [__`setVolumeControlStream()`__](https://developer.android.com/reference/android/app/Activity.html#setVolumeControlStream(int)
 passing in [__`AudioManager.STREAM_MUSIC`__](https://developer.android.com/reference/android/media/AudioManager.html#STREAM_MUSIC).
 
 
 
 
 ## ExoPlayer Extras
 
 ### Subtitle Side Loading
 
 Given a video file and a separate subtitle file, MergingMediaSource can be used to merge them into a single source for playback.
 ```
MediaSource videoSource = new ExtractorMediaSource(videoUri, ...);
MediaSource subtitleSource = new SingleSampleMediaSource(subtitleUri, ...);
// Plays the video with the sideloaded subtitle.
MergingMediaSource mergedSource = new MergingMediaSource(videoSource, subtitleSource);
```


### Looping a video

A video can be seamlessly looped using a __`LoopingMediaSource`__. 
The following example loops a video indefinitely. 
It’s also possible to specify a finite loop count when creating a __`LoopingMediaSource`__. 
```
MediaSource source = new ExtractorMediaSource(videoUri, ...);
// Loops the video indefinitely.
LoopingMediaSource loopingSource = new LoopingMediaSource(source);
```
