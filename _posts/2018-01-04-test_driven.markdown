---
layout: post
title:      "Test Driven"
date:       2018-01-04 13:23:47 -0500
permalink:  test_driven
---


After 13 years as an educator, I know that one of the most important questions one can ask while preparing a lesson is:
## What do I want my students to know and be able to do as a result of my instruction?

I’ve learned quickly that, as a programmer,  this same question is essential, though I’ll reword it: 
## What do I want my program to know and be able to do as a result of my code?
As I learn more and more about Test Driven Development (TDD), I wonder how anyone ever went through, or still goes through the process of developing in any other way.

Like scaffolding (an awesome education term for beginning at the beginning (you might think, “duh!”, but you’d be surprised), you begin slowly, in small, digestible chunks, building students’ understanding and skills.

Formative assessments check for understanding, informing the teacher of the class’s overall grasp of the concepts. If students don’t pass, the instruction is improved and the understanding tested again, and so on. This process mirrors the debugging process. Keep units small, test frequently, and consider failure an essential part of the learning/programming process.

As I work on my own programs, I include my test goals as comments. Just as a teacher should always be sure her/his students know exactly what goal they are attempting to reach at any moment, I keep myself reminded and focused. Likewise, writing out steps in pseudo code accomplishes the same: answering, “what the heck am I trying to do, or what questions am I trying to answer?”.

Below is an example of one method belonging to an Artist Class. It may be  visually abbrasive, but I remove it as I go, or at least when I'm done and store the process in a separate file.
```
class Artist

  def add_song(song)
  # assigns the current artist to the song's 'artist' property
  # does not assign the artist if the song already has an artist
  # adds the song to the current artist's 'songs' collection
  # does not add the song to the current artist's collection of songs if it already exists therein

    # does the song have an artist?
		# if no...
    if song.artist == nil
      # assign artist's self to song
      song.artist = self
        # does the song exist in the artist's collection of songs?
        # yes? do nothing
        # no? add it
        self.songs.detect{|s| s == song} ? nil : @songs << song
    else
      # does the song have an artist? yes?
      self.songs.detect{|s| s == song} ? nil : @songs << song
    end
    
  end
  
end
```
