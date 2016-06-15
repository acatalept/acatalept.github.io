---
layout: post
title: "Cubrick: a minimal, meditative, 3D puzzle/platformer game"
---

[In development for Android, Windows (with Oculus Rift support), Linux, and the web (and eventually Mac OSX / iPhone / iPad when I get my hands on a Mac to compile it)]

*Follow the [devlog on TIGSource](http://forums.tigsource.com/index.php?topic=38797)*

<a href="http://acatalept.com/cubrick" target="_blank" class="imgLink"><img src="http://acatalept.com/cubrick/images/cubrick-logo-square-360.png" alt="Cubrick title image" /></a>

Playable Prototype
------------------

A playable prototype is available to <a href="http://acatalept.com/cubrick" target="_blank">play directly on the website</a> (if your browser supports the Unity plugin), or to <a href="http://acatalept.com/cubrick/#download" target="_blank">download for Windows, Linux, and Android</a>.

I welcome feedback, please let me know if anything breaks, or if you have any questions/suggestions!

![Cubrick gameplay animation](http://acatalept.com/cubrick/images/cubrick-2014-02-12-22-16-15-101_700x394_30fps.gif)

![Cubrick gameplay animation](http://acatalept.com/cubrick/images/cubrick-2014-02-15-00-34-19-410_700x394_30fps.gif)

Features
--------

#### An "un-platformer"
I call it a "platformer" with some reservation, since there's no jumping, no accidentally rolling off the edge and dying, and although there is a small element of timing certain movements, it doesn't require any real manual skill or dexterity - I'm trying to focus on testing your mind and perception, not your twitch button mashing ability.

#### Motion / feel / "flow"
Movement, control, and animation as fluid, natural, and intuitive as possible, to avoid high-level "interface" frustrations that take the player out of the game.  Strangely I'm influenced by old skateboarding games where you could just ride around effortlessly, ollie-ing off everything you came across...  On another level, I'm trying to reduce/eliminate as many "speedbumps" in the experience as possible: no loading screens (you can even start moving before each level is completely loaded), no "wait and read" title/credit/legal screens... so from beginning to end the entire experience "flows".

#### Mood / visuals / sound
Stark, thoughtful, meditative, generally peaceful, but occasionally some tension or "darkness" as the story progresses.  Picture a virtual space inside the mind of an artificial intelligence.  This is supported by the sound design, from cubrick's movements (a simple pentatonic piano "plink"), to other complimentary sounds in the environment, all overlaying and harmonizing with the ambient soundtrack.

#### Story
Cubrick's backstory ties into some other things I'm working on, and will be hinted at in that greater context, but never really spelled out.  I'm trying to keep human language out of the game as much as possible, and to a minimum in the menu/GUI, to give an almost "machine perspective" on what's taking place.  You may meet other cubricks, they may be a part of you, or completely independent, and you may not even stay the same cubrick for long...

#### Cross-platform / cross-play
Cubrick is made with Unity, making it easy to deploy cross-platform (though I won't be able to release an OSX/iOS version until I get my hands on a Mac).  But while most cross-platform games live in their isolated ecosystems (Windows/Linux/Mac games can sync to any other PC using Steam, Android games can sync to any other Android device using Google Play, iOS games can sync to other iOS devices, etc.), I've developed a simple way to save your progress on one platform, and pick up where you left off on a different platform whenever you like, without any extra effort on the part of the player (aside from creating a unique profile on the game server - you don't even need to supply an email address).  This is an opt-in service, so you play offline by default, but it will allow you to (for example):

start a game on a Windows PC...

... resume that game later on your Android phone/tablet...

... resume *that* game even later on your Linux PC...

... resume *that* game in a web browser on your work computer (or any public/shared computer where you may not be able or want to install games)...

... and so on

#### In-game level editor
I'm creating all the game's levels *in* the game, and making the creation process seamlessly integrated into the game, so that you can literally start creating/destroying/modifying without "stepping out" of the game (see "flow" above).  It will be easy to share your levels with any other players who have profiles on the server, or by simply copying level files (saved as JSON format in plain text) from your save folder into theirs.

#### Oculus Rift support!
Optional Oculus Rift VR support is working nicely (coming soon to Windows prototype) through Unity's Oculus SDK integration.  The VR experience works really well with the minimal aesthetic - the objects and environment feel like little blocks that you can almost reach out and touch ;)

## Progress

I've been working on Cubrick on and off as time allows since June 2013.  I hope to have a complete product ready sometime in the first half of 2014.

**Done:** Movement & controls (including "clones"), graphics, animation, sound effects, dynamic ambient soundtrack, a handful of sample levels for the prototype

**To Do:** Minimalist GUI icons (reduce/remove text), more soundtrack work, finishing some deeper puzzles and gameplay elements that will be revealed when they're ready ;)


Thanks for looking!