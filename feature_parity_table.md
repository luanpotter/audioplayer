# Feature Parity Table

Not every feature is available on every platform yet. Use this table to keep track of our work and progress, and please help if you want :)

Note: LLM means Low Latency Mode.

## Main Features

<table width="70%">
    <thead style="font-size: 1.5em">
        <th>Feature/Platform</th>
        <th>Android</th>
        <th>iOS</th>
        <th>macOS</th>
        <th>web</th>
    </thead>
    <tbody>
        <tr><td colspan="5"><strong>Audio Source</strong></td></tr>
        <tr><td>local file on device</td><td>yes</td><td>yes</td><td>yes</td><td>no</td></tr>
        <tr><td>local asset</td><td>yes</td><td>yes</td><td>yes</td><td>yes</td></tr>
        <tr><td>external URL file</td><td>yes</td><td>yes</td><td>yes</td><td>yes</td></tr>
        <tr><td>URL file with http headers</td><td>yes</td><td>no</td><td>no</td><td>no</td></tr>
        <tr><td>external URL stream</td><td>yes</td><td>yes</td><td>yes</td><td>yes</td></tr>
        <tr><td>byte array</td><td>SDK >=23</td><td>not yet</td><td>not yet</td><td>not yet</td></tr>
        <tr><td colspan="5"><strong>Audio Config</strong></td></tr>
        <tr><td>set url</td><td>yes</td><td>yes</td><td>yes</td><td>yes</td></tr>
        <tr><td>pre-load</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td>audio cache</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td>low latency mode</td><td>yes</td><td>no</td><td>no</td><td>no</td></tr>
        <tr><td colspan="5"><strong>Audio Control Commands</strong></td></tr>
        <tr><td>resume / pause / stop</td><td>yes</td><td>yes</td><td>yes</td><td>yes</td></tr>
        <tr><td>release / release mode</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td>volume</td><td>yes</td><td>yes</td><td>yes</td><td>yes</td></tr>
        <tr><td>seek</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td colspan="5"><strong>Advanced Audio Control Commands</strong></td></tr>
        <tr><td>playback rate</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td>duck audio</td><td>yes (except LLM)</td><td>no</td><td>no</td><td>no</td></tr>
        <tr><td>respect silence</td><td>yes (except LLM)</td><td>yes</td><td>no</td><td>no</td></tr>
        <tr><td>stay awake</td><td>yes (except LLM)</td><td>yes</td><td>no</td><td>no</td></tr>
        <tr><td>recording active</td><td>not yet</td><td>yes</td><td>no</td><td>no</td></tr>
        <tr><td>playing route</td><td>yes (except LLM)</td><td>yes</td><td>no</td><td>no</td></tr>
        <tr><td colspan="5"><strong>Streams</strong></td></tr>
        <tr><td>duration event</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td>position event</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td>state event</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td>completion event</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
        <tr><td>error event</td><td>yes</td><td>yes</td><td>yes</td><td>not yet</td></tr>
    </tbody>
</table>

<br />

## Notifications

Apart from the main features for playing audio, some unrelated features to notification and lock screen management were added to audioplayers.

This is not the best home for them though. We are working with @ryanheise to eventually extract the existing notification related code from audioplayers and either:

 * create a new package, audioplayers_notifications for it
 * merge this code into the existing audio_service package

audio_service is already a package that provides much more advanced notification/lock screen controls.

So please do not send any PRs or additions to the notifications/lock screen for now, unless it's part of our separation effort.

I will update this file as we move forward with this.

## Other Features

Some features are totally out of scope for the `audioplayers` package. The goal  of this library is to provide a unified place to play audio media, be it songs, background musics, sound effects, etc, from different sources, and providing an array of advanced controls and listeners to control it via code.

Non-goals: if the existing solutions proposed below are not good or do not work well with audioplayers, I am happy to collaborate to create an `audioplayers_x` separated package (eg `audioplayers_recorder`).

 * notifications/locks screen: see section above, use this for now or audio_service;
 * interfaces: nothing related to interface building concerns audioplayers; you can use Flutter to build your interfaces;
 * audio recording: recording audio from the microphone into audio files and streams; there is already a package for this called [audio_recorder](https://github.com/ZaraclaJ/audio_recorder).
 * playlist: you can implement playlists as you wish by playing multiple audios or songs in sequence. Doesn't make sense for this package to have any builtin playlist mechanism.
 * music metadata: some file formats include music metadata, like MP3 files that have author, track. This is a library dedicated for playing audio. It is a non-goal to provide this functionality.
