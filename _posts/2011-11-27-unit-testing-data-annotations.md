---
layout: post
title:  "Unit Testing Data Annotations"
comments: true
categories: [asp.net,MVC]
---

For home projects done in asp.net I tend to use the DataAnnotations on my models for validation. Of course anyone would want to write a unit test to make sure this is all in order. Let's take some very simple test, I want to check my model is not validating when given nothing:

{% highlight js %}
var controller = new HomeController(guestRepository.Object);
controller.Index(viewModel);
var isValid = controller.ViewData.ModelState.IsValid;

Assert.Equal(isValid, false);
{% endhighlight %}

I've put mocked up my repository and then call the method I want to test, in this case Index. I check the ModelState, but it says everything is fine, all valid and this fails. Damn it!

It's all about context, as a unit test runs in a different context (not the web context), the model binder is never invoked. So it thinks the model is fine and valid.

I have a nice little helper for this which basically calls the model binder so we can test this:

{% highlight js %}
public static void ValidateHelper(Controller controller, T model)
        {
            var validationContext = new ValidationContext(model, null, null);
            var validationResults = new List();
            Validator.TryValidateObject(model, validationContext, validationResults, true);
            foreach (var validationResult in validationResults)
                controller.ModelState.AddModelError(validationResult.MemberNames.First(), validationResult.ErrorMessage);
        }
{% endhighlight %}

(make sure you are using using System.ComponentModel.DataAnnotations and System.Web.Mvc).

I made this generic so I can use different model types. You then just call this method before invoking the Index method, and you should be good.
