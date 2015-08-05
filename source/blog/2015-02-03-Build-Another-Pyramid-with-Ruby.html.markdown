---
title: Build Another Pyramid with Ruby
date: '2015-02-03'
category: coding
tags:
- coding
---

This past week in coding I got my cat bot up to github! You can now make <a href="https://github.com/jdax/twitter_cat_bot" target="_blank">your very own cat bot</a>! I tried to make it as accessible as possible to the non-programmer as possible. Please let me know in some form if you have questions or comments! I guess, if you really wanted to, for some reason I cannot fathom, wanted to make a bunny bot or a dog bot or a ferret bot. I don't know, I guess you could do that.

This past week in class we did if loops, while loops, arrays, hashes and enumeration.

<!--more-->

<strong>If loops/while loops</strong>

If and while loops help you to not repeat code, or to make sure that only specific parts of your code run if certain conditions are met. So 'if this, than that" would be the plain English of an if loop. "While this is going on, or while this is true, keep doing that" is the plain English for a while loop. For our homework we were asked to design pyramids to certain user defined specifications. We had to ask which character the user wanted to build the ASCII pyramid with, how many rows they wanted, and if they wanted it right-side-up, or up-side down. Obviously I had "<a href="https://www.youtube.com/watch?v=qduQyu-Cxgc" target="_blank">Another Pyramid</a>" stuck in my head the whole time I was working on this. This requires that you nest a while loop in an if loop.

In order to keep the "customers" height requirment, you have to keep count of how many times you run the code. So you set up a counter, and /while/ the counter is equal to or less than the customers specified height, you run the code. The if loop is used to determine <em>which </em>type of code you run: the code that will build the pyramid the right way up, or upside down.
<blockquote># getting architectural specifications for the pyramid
puts "Please pick a character with which to build a pyramid"
building_block = gets.chomp

puts "How tall, in rows, would you like this pyramid to be?"
height = gets.chomp.to_i

puts "Do you want to defy gravity? Y/N?"
physics = gets.chomp.upcase
# counter, if loop/while loop

counter = 1

if physics == "N"
while counter &lt;= height
puts " " * (height - counter) + building_block * (counter * 2 - 1)
counter +=1
end
elsif physics == "Y"
while counter &lt;= height
puts " " * (counter + height) + building_block * (2 * (height - counter) + 1)
counter += 1
end
end</blockquote>
<strong>Arrays, Hashes, Ennumeration</strong>

Arrays and hashes are ways of collecting and storing multiple types of data. Both can store <i>strings, numbers, symbols, booleans, </i>and even arrays and hashes. Arrays are ordered lists. When you create one, the order in which you put the data is assigned an index. The index starts at 0.
<blockquote>this_is_my_array = ["string", 1, true]</blockquote>
So in the above array, string is index 0. It can be accessed with array[0].

You can add objects to an array by using the .push method.
<blockquote>this_is_my_array.push("new object")</blockquote>
This will add the "new object" string to the end of the current array, at index 3. You can also insert a new object by assigning it an index that may or may not be currently in use.
<blockquote>this_is_my_array[0] = "Thirteen"</blockquote>
The above would put "Thirteen" at the start, and move everything over by one.

Some other methods you might want to use on an array:
<blockquote>.pop
.uniq
.sample (this is how I built my cat bot!)
.shuffle (yes, like your playlist)
.first
.last
.sort
.reverse
.join
.split</blockquote>
All of the above will make a copy of the array, and then make changes on it. If you want to permanently alter your array, you can add a ! to the end of the method. This is called the bang method.

Hashes are unordered, so there is no index. You access the data in them via keys. Each key is assigned to a value. In some other programming languages they are called "associative arrays" as the data has association to it. Hashes also commonly use symbols. Symbols are like smaller strings, they take less time to run. Instead of being noted "like this" they are notated :like_this. The difference is that symbols are immutable.
<blockquote>this_is_my_hash { :key_one =&gt; "value_one", :key_two =&gt; "value_two"}

hash_of_peoples_favorite_animal { :nikki =&gt; "cat", :liz =&gt; "rabbit", :megan =&gt; "crab" }</blockquote>
The =&gt; is called a hash rocket. Idk why. I guess someone thinks it looks like a rocket.

If you wanted to access information from a hash you would type
<blockquote>hash_of_peoples_favorite_animals[:nikki]</blockquote>
or to put a new key and value into a hash:
<blockquote>hash_of_people_favorite_animals[:hannah] = "dog"</blockquote>
Most of the method's you can call on an array can also use on hash's, save the ones that might require order (such as .first, .last).

We also went over .each and .map, ways in which to sort information into arrays or break out information from an array.

cats = ["Didi", "Tom", "Stormy"]

So say I wanted each of my cats to meow. I could write this:
<blockquote>cats.each do |cat|
puts "#{cat} meows."
end</blockquote>
What this does is temporarily assign each object in the array to the new 'cat' variable then runs it through the code. So it will return:
<blockquote>Didi meows.
Tom meows.
Stormy meows.</blockquote>
But say I wanted to put the results of the .each into an array of it's own. I could use the .map method.
<blockquote>cats_meowing = cats.map do |cat|
puts "#{cat} meows"
end</blockquote>
So cats_meowing will now be an array looking like this:

["Didi meows", "Tom meows", "Stormy meows"]

Leave comments/corrections/critiques/criticisms/compliments in the comments section! Before doing so, you might want to read my <a title="On Comment Policies and Free Speech" href="http://nikkilizmurray.com/2013/05/03/on-comment-policies-and-free-speech/" target="_blank">comment policy.</a> Because I sometimes write about my feminism here, too, and sometimes receive hateful comments, I ask you to keep this in mind. I am learning ruby/programming right now, and do not know all the things there is to know.
