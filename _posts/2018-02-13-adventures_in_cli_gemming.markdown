---
layout: post
title:      "Adventures in CLI Gemming"
date:       2018-02-13 22:31:48 -0500
permalink:  adventures_in_cli_gemming
---


Creating something from nothing produces, for me, is one of my most rewarding experiences. Like creating a painting or a photograph, designing not only the structure and user experience of an application, but the structure and readability of the code is like an art, no matter how simple. I just completed my first something-from-nothing Ruby gem. The process was challenging, frustrating, and entirely fun. The problem-solving, testing, pattern recognition can be likened, again, to creating a piece of art or design. It's become clear that patterns are key in every single stage of development. Patterns must be consciously and purposefully set up immediately during planning. For instance, when creating objects, one must consider in what way the object will be instantiated, saved, and related to other objects. Given that there are a million and one ways to accomplish any given method/function, it's essential for a developer to determine which structure, or solution is most effective (even if a more effective and/or efficient means is discovered later), and then cut and paste! Example:
```
class FindaPark::Park

  attr_accessor :name, :state, :city, :contact, :blurb, :url, :catch_phrase, :season_info, :hours

  @@all_parks

  def initialize
    # assign attributes
    # save
  end

  def self.create_from_collection
    # use collection of parks to instantiate instances of parks
    # assign designation, name, city, blurb, url
  end
	...
```
