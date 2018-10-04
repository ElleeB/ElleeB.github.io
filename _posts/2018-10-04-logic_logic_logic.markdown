---
layout: post
title:      "Logic Logic Logic"
date:       2018-10-04 15:44:23 +0000
permalink:  logic_logic_logic
---


Having just completed my Rails project, I'm looking back and wondering what my most poignant process theme was. Welp, it was definitely, "Where the #^$% do I put this logic?"

I spent quite a bit of time trying to dry up and beautify my code. This is one of my favorite parts. It's like cleaning a messy bedroom and the result is utterly satisfying. This was the first time, however, where I was really faced with some horribly unnattractive view code and devoted much effort into researching where to put view logic and how to break it up appropriately so that the HTML actually functions as it should.

But, I'm going to step off this path because ultimately, the real question is, where do I put my stuff (and this is just the tip of the ruby iceberg)? 

<br>

**MODELS**

[  ]  existing AR object logic

[  ]  if related to non-existing object

[  ]  if requires calling a non-display method? create a helper method

[  ]  need a method available to all models? create a helper method in application_record.rb

<br>

**VIEWS**

[   ]   html

[   ]   variables that turn into html

[   ]   calls to helper methods

[   ]   if requires a conditional - create a helper method

[   ]   if requires a lengthy loop - create a helper method

[   ]   if requires calling a non-display method - create a helper method

<br>

**CONTROLLER**

[   ]   handle requests and routing

[   ]   logic encapsulated in model methods

[   ]   logic related to sessions/searching database for matching records -  put in application_controller.rb

[   ]   optional: define a single instance variable per controller action





