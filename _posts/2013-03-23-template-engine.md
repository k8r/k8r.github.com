---
layout: post
tagline: {{ page.date | date_to_string }}
tags: [Android, Java, HTML]
---
{% include JB/setup %}
When pregnant, food cravings take on a whole new meaning.  If I trusted those cravings, I would have peanut butter for
breakfast, lunch, and dinner (with an occasional helping of chocolate ganache cake).  I'm a little ahead of schedule on
the amount of weight I'm supposed to gain, so I'm regaining control by writing an Android app to solve the problem.  It
helps me plan all my recipes, servings, leftovers, and snacks; and then it emails me a plan for the week.  To generate
the email content, I used a template engine.

I was familiar with .jsps (Java code and certain pre-defined actions are mixed with HTML, and compiled / served up as a static document),
.cshtml (similar to .jsps, but used by Razor, an ASP.NET view engine), etc. for displaying dynamic content on a web-app, but I had never used a template engine
to generate HTML content from a standard (non-web) application.

I chose a template engine called [MiniTemplator](http://www.source-code.biz/MiniTemplator/),
which worked beautifully on Android.  The documentation and examples were great: after adding a template HTML file, you set the variables, add the "blocks"
(see example below), and call a function to generate output in your Java code.  At first glance, the syntax is
similar to syntax you might see in a .jsp.  One difference I noticed is that .jsps allow you to insert actual Java
code for loops in the template; while MiniTemplator has you place them in your Java source code.

{% highlight java %}
for (DayPlan dayPlan : this.dayPlans())
{
    t.setVariable("currentDay", dayPlan.getDayLabel());
    t.setVariable("totalCalories", dayPlan.getTotalCalories());

    t.addBlock("calories");
}
String emailText = t.generateOutput();
{% endhighlight %}

{% highlight html %}
<!-- $BeginBlock calories -->
${currentDay} / Total Calories: ${totalCalories}
<!-- $EndBlock calories -->
{% endhighlight %}

Piece of cake - thank you [source-code.biz](http://www.source-code.biz).  My app is still a work in progress, but it's been helping during the last two weeks.
I still feel like a hippo, but a more comfortable, properly-fed hippo.



