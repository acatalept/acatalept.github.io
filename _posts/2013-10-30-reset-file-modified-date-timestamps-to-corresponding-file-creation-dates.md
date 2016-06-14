---
layout: post
title: Reset file modified date / timestamps to corresponding file creation dates
---

I rely on file modification timestamps to quickly indicate when I last worked on a file, particularly when working on multiple revisions to a file.  In some cases I even want to go back and open previous revisions of files to get a sense of what has changed since then.

However, after picking up (the otherwise incredible ;) <a href="http://www.propellerheads.se/products/reason/">Propellerheads Reason 6</a>, I noticed a glaring issue with the new <code>.reason</code> file format: any time I open a file, even if I'm careful to make no changes, <a href="https://www.propellerheads.se/forum/showthread.php?t=153426">the file modification date/timestamp is changed to the current time upon closing the file</a>.  This is apparently "by design", something to do with the new plugin system... or copy protection... or something.

In any case, this makes it very difficult to keep my files sorted by date in Windows Explorer, or even clearly see which revision is the latest, as I often go back and listen to previous revisions, which now has the side effect of updating the timestamps.

But I've thrown together this simple Windows JScript file, which I can run after I'm done with a Reason session to revert all timestamps to their original creation time.  I usually save major changes as a new revision (with a unique filename), so the creation date is usually the same as the last time I edited the file - however, if this is not the case for you (i.e., you often go back and save over the original file multiple times), this may not be an ideal solution for you.

Just drop this file into the same folder as your <code>.reason</code> files are saved, name it <code>reset.js</code> (the <code>.js</code> extension tells Windows it's an executable JScript file), and double-click the file to reset timestamps for all your reason files to each file's corresponding creation timestamp.

<pre class="line-numbers"><code class="language-javascript">var wscript = WScript.CreateObject("WScript.Shell");
var shell = new ActiveXObject("Shell.Application");
var fso = new ActiveXObject("Scripting.FileSystemObject");


// only reset timestamps for these file extensions
var extensions = [".reason"];


// extract file extension from file name for comparison
function GetFileExtension(filename){
  var pieces = filename.split(".");
  if (pieces.length > 1)
    return "." + pieces[pieces.length - 1].toLowerCase();
  else
    return "";
}


// get current folder (where script file was run from)
var folder = shell.NameSpace(wscript.CurrentDirectory);

// get files in current folder
var items = folder.Items();


// loop through files, resetting timestamps for matching extensions
for (var i = 0; i < items.Count; i++){

  var item = items.Item(i);
  
  var thisExt = GetFileExtension(item.Name);
  
  var extMatch = false;
  for (var j = 0; j < extensions.length; j++){
    if (thisExt == extensions[j]){
      extMatch = true;
      break;
    }
  }
  
  // if not file extension we're looking for, skip this file and go to the next
  if (!extMatch){
    continue;
  }

  // otherwise, if this *is* a matching file extension, copy creation timestamp to modified timestamp
  var file = fso.GetFile(item.Path);
  var dateCreated = file.DateCreated;
  item.ModifyDate = dateCreated;
}</code></pre>
