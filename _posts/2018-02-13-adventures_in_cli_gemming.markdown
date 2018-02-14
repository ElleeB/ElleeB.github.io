---
layout: post
title:      "Adventures in CLI Gemming"
date:       2018-02-13 22:31:48 -0500
permalink:  adventures_in_cli_gemming
---


Creating something from nothing produces, for me, is one of my most rewarding experiences. Like creating a painting or a photograph, designing not only the structure and user experience of an application, but the structure and readability of the code is like an art, no matter how simple.

I just completed my first something-from-nothing Ruby gem. The process was challenging, frustrating, and entirely fun. The problem-solving, testing, pattern recognition can be likened, again, to creating a piece of art or design. It's become clear that patterns are key in every single stage of development.

Patterns must be consciously and purposefully set up immediately during planning. For instance, when creating objects, one must consider in what way the object will be instantiated, saved, and related to other objects. Given that there are a million-and-one ways to accomplish any given method/function, it's essential for a developer to determine which structure, or solution is most effective -- even if a more effective and/or efficient means is discovered later -- and then cut and paste! 

Example: my Park and State classes in their earliest stages are identical in their structure.

```
class FindaPark::Park

  attr_accessor :name, :state, :city, :contact, :blurb, :url, :catch_phrase, :season_info, :hours

  @@all_parks = []

  def initialize
    # assign attributes
    # save
  end

  def self.create_from_collection
    # use collection of parks to instantiate park
    # assign designation, name, city, blurb, url
  end



class FindaPark::State

  attr_accessor :name, :url, :parks

  @@all_states = []

  def initialize
    # assign attributes
    # save
  end

  def self.create_from_collection
    # use collection of states to instantiate state
    # assign name, url
  end
	```
	
	
Here is a snapshot of how the  methods evolved together, maintaining equivalent patterns.
	

```
class FindaPark::Park

  attr_accessor :name, :state, :designation, :city, :park_url, :contact, :blurb, :info_url...

  @@all_parks = []

  def initialize(park_hash)
    @name = park_hash[:name]
    @state = park_hash[:state]
    @designation = park_hash[:designation]
    @city = park_hash[:city] # !!! city return is odd !!! #
    @park_url = park_hash[:park_url]
    @contact = park_hash[:contact]
    @blurb = park_hash[:blurb]
    @info_url = park_hash[:info_url]
    @catch_phrase = park_hash[:catch_phrase]
    @season_info = nil
    @hours = nil
    self.save
  end

  def self.create_from_collection(parks_array)
    parks_array.each do |park_hash|
      FindaPark::Park.new(park_hash)
    end
  end


	
class FindaPark::State

  attr_accessor :name, :url, :park

  @@all_states = []
  @parks = []

  def initialize(state_hash)
    @name = state_hash[:name]
    @url = state_hash[:url]
    @park = nil
    self.save
  end

  def self.create_from_collection(states_array)
    states_array.each do |state_hash|
      FindaPark::State.new(state_hash)
    end
  end
```
	
	
As the code becomes more abstract, the already established patterns/structure make it easy to move between classes and objects, easily accessing the code, and  easily making adjustments and improvements, because really, if you figure it out for one, you've figured it out for both. Just cut and paste!


Final Park and State initialize example:


```  
def initialize(park_hash)
    park_hash.each do |key, value|
      self.send("#{key}=", value)
    end
    self.save
  end



  def initialize(state_hash)
    state_hash.each do |key, value|
      self.send("#{key}=", value)
    end
    self.save
  end
```

My project can be found [here](https://github.com/ElleeB/nps-finda-park-cli-app).

