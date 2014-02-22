---
layout: post
title:  "Date Validation (check user age)"
comments: true
categories: [Javascript,Javascript,validation]
---

I'm going to admit now that I have issues with validating date formats. Not so much the format itself, but finding whether user x is a certain age. Working on some alcohol projects in the past, it has caused a bit of pain whichever language. The main issue comes from trying to see a date as a number. In C# it is quite easy (I will write a separate post on this eventually), but in javascript I found it a bit fiddly.

Why would one use Javascript to check for age? Facebook! Facebook apps reply on Javascript for validation etc. So after looking round the internets, I found this useful function:

function checkdate(input){
     var validformat=/^d{2}/d{2}/d{4}$/ //Basic check for format validity
     if (!validformat.test(input))
         alert("Invalid Date Format. Please correct and submit again.");
     else{ //Detailed check for valid date ranges
         var monthfield=input.split("/")[0];
         var dayfield=input.split("/")[1];
         var yearfield=input.split("/")[2];
         var dayobj = new Date(yearfield, monthfield-1, dayfield);

         if ((dayobj.getMonth()+1!=monthfield)||(dayobj.getDate()!=dayfield)||(dayobj.getFullYear()!=yearfield))
               alert("Invalid Day, Month, or Year range detected. Please correct and submit again.")
         else
          alert("valid");
     }
}

Still fiddly, but it works. Enjoy. Any feedback welcome as usual.
