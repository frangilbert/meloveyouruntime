---
layout: post
title:  "ByteArray to file"
comments: true
categories: [Uncategorized]
---

I work a lot with Flash developers (or actionscripters) and most of the time Flash will need to post a form to the server to process or something similar. A server side developer will then write some services to receive or return data to the Flash. Sometimes the data isn't that standard. Sometimes the Flash will generate an image and will want to save it to the server. It will post a ByteArray to the server, this term scares some developers for some reason. It is just a raw file in a load of bytes. But it needs to be processed to become an image or other file again to be saved. This is how easy it is:

//Read byte array into
byte[] byteArray = [the byte array from the flash];
MemoryStream mStream = new MemoryStream();
mStream.Write(byteArray , 0, byteArray.Length);

//Save as PNG
Image image = Image.FromStream(mStream);
image.Save([Location to save file to], ImageFormat.Png);


In this example I take the byte array posted by the Flash and convert it into an image (PNG formatted). It takes the byte array and writes it to a MemoryStream. The image object then reads the MemoryStream object and saves it. Of course, the necessary checks will need to be done to make sure no nasties or malicious files are uploaded etc. but this is the crux of it and very simple.
