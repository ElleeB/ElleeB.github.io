---
layout: post
title:      "Process Makes Perfect"
date:       2018-04-11 09:59:35 -0400
permalink:  process_makes_perfect
---


I remember thinking, at 15-years-old, that if my father would just get out of the car, I’d be a great driver. Like my 15-year-old self, I’ve recently been feeling that if I could just be released to create my own site/app from bottom to top, I’d be good-to-go. 

For this project, I was most excited for the planning phase. My background in art and design is just one indicator that I love a creative process - building something from nothing. Additionally, I work best with written outlines and visuals. My goal was to create an app for teachers and students through which teachers apply positive feedback to students. At this point, the app only permits teachers to create accounts.

Once a teacher creates an account, they can add, edit, and delete students to/from their roster, and they can add and delete comments to/from a student.

I began by organizing my models and tables. Below is my initial outline, which needed tweaking when it came to the belongs_to/has_many relationships. I fixed those later as the issues presented themselves while developing (I later added a join table and has_many, through: relationships).

---

**Original Class/Table Outline**

```
Classes

Teacher

has_many :students

:username
:email
:password
:quote
:subject


Student
belongs_to :teacher
has_many :positivity_marks

:name
:grade
:teacher_id

Positive_Marks
has_many :students

:description
:todays_date
```

---

Then I was on to my most anticipated part of the process: Adobe XD. I used the Adobe XD software to organize my erb files/pages and their routes. Here is a snippet:

![image](https://i.imgur.com/kpI3iMP.jpg)

---

Then I organized the directory structure:

```
|——  app
|	|——  controllers
|		|——  application_controller
|		|——  teachers_controller
|		|——  students_controller
|		|——  comments_controllers
|	|——  models
|		|——  teacher.rb
|		|——  student.rb
|		|——  comment.rb
|	|——  views
|		|——  index.erb
|		|——  layout.erb
|		|——  teachers
|			|——  teacher_index.erb
|			|——  create_teacher.erb
|			|——  login.erb
|			|——  new_teacher_view.erb
|			|——  existing_teacher_view.erb
|			|——  show.erb
|			|——  edit.erb*
|		|——  students
|			|——  student_index.erb
|			|——  new.erb
|			|——  show.erb
|			|——  edit.erb*
|		|——  comments
|			|——  new.erb
|			|——  edit.erb*
|			|——  comments.erb
```

---

By the time I opened Atom, I had the entire app planned out. This is not to say that I didn’t run into some great coding challenges, like using checkboxes as add OR remove based on checked or unchecked. It all came together quickly, which reminds me how important the process is, as always. This was my favorite experience in my learning thus far.
