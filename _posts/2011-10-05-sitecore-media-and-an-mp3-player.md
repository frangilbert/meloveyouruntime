---
layout: post
title:  "Sitecore media and an mp3 player"
comments: true
categories: [CMS,media,Sitecore,Sitecore]
---

Recently, I had a bit of a pain with adding an mp3 player to pages for playing files held in Sitecore. Here's a bit of background to the issue: the client wanted an mp3 player like a sister site of theirs has on their site. The sister site does have a player, but the mp3s are served by their Wordpress blog. In our client's case, they will be uploading mp3s to the Sitecore Media Library.
 
The task was simple. Search for any link with a class of "audio" or where the extension is .mp3. Whack in the player over that. All done in 30 minutes. Testing in Firefox, it worked fine. In IE, Chrome, Opera and Safari it would play the mp3, but the display would say "Connecting..." and stick with this while playing. I used the standalone version of [WP Audio Player](http://wpaudioplayer.com/standalone/)
 
I ended up comparing all the headers with a working version and noticed that requesting from Sitecore gave no content-length. Apparently Sitecore (up to 6.4.1 update 1) does not include this essential header.
 
I wrote to Sitecore who replied with:
To add the "Content-Length" header to the "Response" headers, please perform the following steps:
 
1. Compile the “CustomMediaRequestHandler.cs” file (the file is attached) and copy DLL to the “bin” folder.
2. Change the old handlers in the "configurationsystem.webhandlers" and "configurationsystem.webhttpHandlers" with the new ones:
 
For example:

<handlers>
…
<add verb="*" path="sitecore_media.ashx" type="Sitecore.Customization.CustomMediaRequestHandler, Sitecore.Customization" name="CustomMediaRequestHandler" />
…
</handlers>
<httpHandlers>
…
<add verb="*" path="sitecore_media.ashx" type="Sitecore.Customization.CustomMediaRequestHandler, Sitecore.Customization " />
…
</httpHandlers>

 
I have attached the Sitecore.Customization.dll I created for this which is the compiled CustomMediaMediaRequestHandler.cs ([Download Sitecore.Customization.dll here](http://files.meloveyouruntime.com/Sitecore.Customization.dll) or [the zip here](http://files.meloveyouruntime.com/Sitecore.Customization.zip)). Clear cache and BINGO! All good.
 
One other thing to this little tale. Make sure, if you are searching through Mime types in Sitecore (in web.config and MimeTypes.config), that mp3 is set to audio/mpeg, not audio/mp3 which they seem to have done.
 
I hope this helps someone.
