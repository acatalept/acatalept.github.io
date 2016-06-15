---
layout: post
title: "Unity3D Android keystore problems (and workarounds)"
---

I use two different computers to work on my Unity project, syncing and version-tracking source code and assets with Git (but this situation could just as easily apply to multiple developers on a team working on a shared code base).  As a result, I ran into **two problems deploying my builds, both related to the keystore used to sign Android builds**:

## Problem 1: Different debug keys on different computers cause ["conflicting signature" error](http://stackoverflow.com/questions/19959890/android-app-not-install-an-existing-package-by-the-same-name-with-a-conflicting) on install

Before preparing my build for publishing on the Google Play store and before manually creating a keystore (see Problem 2 below), my app appeared to be signed with a default debug key - this was created and used transparently behind the scenes on each computer independently, resulting in a different unique key for each development system.

When deploying these "debug" builds for testing on my device, I was unable to overwrite/upgrade a previous revision built on one computer with a build from the other computer, due to the different keys.  This forced me to uninstall from the device whenever I switched to a build made on a different computer, which also wiped out any created files in <code>PersistentDataPath</code> (where I'm saving a logfile and locally caching preferences, savegames, and screenshots).

**Solution 1:** This problem was magically solved by creating a keystore (see Problem 2 below), allowing me to sign builds on both computers with the same shared key...

## Problem 2: Absolute keystore path not found if project resides on different drive/folder hierarchy on different computers

When I decided to start preparing to deploy the app to Google Play for distribution, I discovered one of the first things I needed to do was to [create a protected keystore to sign the app](http://www.youtube.com/watch?feature=player_detailpage&v=BMGGwjqQRns#t=74), giving it a unique fingerprint allowing the Google store and Android devices to verify the app's authenticity.  But by default, the absolute path to this keystore is saved in the project settings, even though Unity supports paths relative to the project folder as of version 3.5.

**Solution 2:** However, you can't simply type directly in the keystore path field in the Unity editor to change/remove the path info, you can only click the Browse button to select another absolute path.  To change this to a relative path (to make your project more portable), you must manually edit the project settings asset file:

1. In the Unity editor, go into <code>Project Settings -> Editor</code>
2. Change the <code>Asset Serialization</code> value to <code>Force text</code>
3. Close the Unity editor (or at least close your project)
4. Under your project folder, in the <code>ProjectSettings</code> folder, open the file <code>ProjectSettings.asset</code> in a text editor
5. Find the value named <code>AndroidKeystoreName</code>, and remove all path info up to and including the project folder name and leading slash, leaving only the keystore file name and any path info inside the project folder (if you have your keystore in a subfolder)
6. Reopen Unity, build your project to confirm the keystore is found with the new path, then try building the project with the modified <code>ProjectSettings.asset</code> file on your other computer(s) (commit/push/pull using Git/SVN/etc, or however your normally sync your project files) - you should now be able to build on all systems (even if the project resides under different drives/hierarchies on each system) without further modifications.

Good luck!
