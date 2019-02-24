---
layout: post
title:      "Need Some Data?"
date:       2019-02-24 21:52:18 +0000
permalink:  need_some_data
---



Here's a form that creates a new activity, or what my app refers to as a *Drop*.


![](https://i.imgur.com/8CtSDkdl.jpg)

---

See that dropdown menu? Here a user can choose an object’s category. 



![](https://i.imgur.com/B09NqfGl.jpg)

---

Then imagine I need to take the values collected from my user’s selection in order to compose a post request using said values. With that data, I'll insert into the DOM, amongst other things, the selected category’s name to be displayed.

---

#### **The Problem: ** 

*The value provided is the category’s id, not it's name. *

---
If I checkout the params sent to the server after I harvest the form, I'll see: 

```

raise params.inspect => {"activity"=>{"title"=>"Party Hard", "category_id"=>"3", "description"=>"Party the hardest!", "due_date"=>"2019-02-27"}
```

I'm missing the category name, but I do have a category_id. So if the user selected *lifestyle*,  the lifestyle category (category_id: 3) is provided to the controller action.

---

When I allow the post request to run its course in its basic form, after having rendered the newly created activity as JSON for my controller to serve up, and insert the returned data into the DOM, *undefined* will be displayed via the DOM. 

![](https://i.imgur.com/PJ1PCkQl.jpg)

But I want to see the category's *name*.


---


#### **The Solution:**
**Create some data!**
Insert ‘custom’ data within the controller action’s JSON response. Below you'll see I used the attribute name, *activity_category*.


```
if @activity.save
	category = Category.find(params[:activity][:category_id])
		respond_to do |format|
			format.json { render json: {
				"activity": @activity,
				"activity_category": category.name
		}
	}
end
```

The returned data now looks like this:

```
{activity: {…}, activity_category: "Lifestyle"}
activity:
category_id: 3
complete: false
created_at: "2019-02-24T21:37:33.159Z"
description: "Party the hardest!"
due_date: "2019-02-27T00:00:00.000Z"
id: 13
title: "Party Hard"
updated_at: "2019-02-24T21:37:33.159Z"
user_id: 1
__proto__: Object
activity_category: "Lifestyle"
```

Check out that *activity_category* attribute!

Now when the DOM is updated, here's what a user will see:

![](https://i.imgur.com/GwvTIZOl.jpg)

---

![](http://southparkstudios.mtvnimages.com/shared/characters/alter-egos/the-grand-wizard.png?height=165)

Having the power to determine so explicitly which data would be returned in response to a request makes me feel like a wizard.
