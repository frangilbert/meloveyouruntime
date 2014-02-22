---
layout: post
title:  "Setting up SSH and Git on PC"
comments: true
categories: [Git,Github,PC,Putty,SSH,Version Control,Windows]
---

Today at lunch, the tech team at work sat down for a lunch at learn to work out Git, which we are currently migrating to. We had a few learning issues with setting up SSH keys within Git Extensions, so I thought I'd write my findings down here.

For this, you'll need to download Pageant and PuTTYGen from the [PuTTY download page](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

Once done with that, open PuTTYGen and click "Generate". You'll then need to run your mouse around until you have a random key. After this is done, click "Save private key" and save the file somewhere. At the top, there will be a Public key you can copy starting with ssh-rsa, copy all of this string.

Open Pageant (it may open in the System Tray, so if it doesn't appear, just search for it there). Click to Add Key and select the private key you saved earlier.

Now log into your Github account and go to your account settings. In the account overview, you should find "SSH Public Keys". Add a new public key, you can call the title anything. Then paste the public key you copied earlier into the "Key" field. You should now be set up to go with SSH.
