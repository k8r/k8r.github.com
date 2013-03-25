---
layout: post
title: "Template Engine"
description: ""
category: 
tags: []
---
{% include JB/setup %}

When pregnant, food cravings take on a whole new meaning.  If I trusted those cravings, I would have peanut butter for
breakfast, lunch, and dinner (with an occasional helping of chocolate ganache cake).  I'm a little ahead of schedule on
the amount of weight I'm supposed to gain, so I'm regaining control by writing an Android app to solve the problem.  It
helps me plan all my recipes, servings, leftovers, and snacks; and then it emails me a plan for the week.  To generate
the email's html, I used a template engine.

I was familiar with .jsps, .cshtml, etc. for displaying dynamic content on a web-app, but I had never used a template engine to generate HTML content from a standard (non-web) application.  I chose a template engine called [MiniTemplator](http://www.source-code.biz/MiniTemplator/), which worked beautifully on Android.  The documentation and examples were great: after adding a template HTML file, you set the variables, add the "blocks", and call a function to generate output in your Java code.  The syntax is very similar to syntax you might see in a .jsp.  The main difference I noticed is that you put for loops in your Java code, rather than in the template.

{% highlight java %}
for (DayPlan dayPlan : this.dayPlans())
{
    t.setVariable("currentDay", dayPlan.getDayLabel());
    t.setVariable("totalCalories", dayPlan.getTotalCalories());

    t.addBlock("calories");
}
String emailText = t.generateOutput();
{% endhighlight %}

Piece of cake - thank you source-code.biz.  My app is still a work in progress, but it's been helping during the last two weeks.  I still feel like an elephant, but a more comfortable, properly-fed elephant.



