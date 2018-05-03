---
title: There's a method for that!
date: '2015-02-11'
blog: blog
published: false
---

Sorry for the long pause in the coding related content! The reason is that I moved my blog from wordpress.com to self-hosted and running on wordpress.org.  The move has allowed for a lot more customization and a lot more control over my content, including the ability to create my own themes. I'm still using my old one while I design the new theme, but be on the lookout!

<!--more-->

For those of you unfamiliar with Ruby, but familar with other languages, a<strong> method</strong> is like a function in some other languages like JavaScript. A method is a re-usable block of code. You might have already used a standard Ruby method like .upcase. A big concept in Ruby is "DRY" which means "don't repeat yourself."  You create a method that you can use on an object by doing the following:

def method_name(arguments)
#code that you want to run
end

So for example, say you have an object  cat:

cat = gets.chomp

and you want it to meow. You can create a method for that.

def meow    return "meow's"
end

So now you can go cat.meow and it should return the cat meowing.  You can now use this piece of code you wrote elsewhere.  You can also create a method with arguments.

def cat(name, toy)
return "#{name} plays with #{toy}. Meow!"
end

This bit of code won't run if you don't give it both of the arguments, though. If you forget to put in a toy argument, Ruby will tell you there is an argument error. To avoid this, you can set defaults.

def cat(name, toy="yarn")
return "#{name} plays with #{toy}. Meow!"
end

So now even if someone doesn't specify the toy, Ruby will put "yarn" as the toy automatically!

You might have noticed I'm using "return" instead of "puts." Return ends the method and breaks out of it, puts does not. Return sends us something from our code, whereas puts does not affect our code, and is more like a message to ourselves in the console.  This is important when you are working with numbers, if you wanted a method that adds to numbers and returns the results.

One thing to keep in mind is that method's are like black boxes. If you've worked in other programming languages, you might know about a concept called scope. <strong>Scope</strong> is a way of talking about who knows what and where in your code. If you create a variable on line 12, does the code you are running on line 45 know about that variable?  If you create a variable in a method, that variable is not accessible outside of running that method. On the flip side of that, a method cannot reference variables outside of it. However, a method CAN reference another method, but since Ruby runs line by line, that method must have been defined before it can be referenced in another method.

Questions, comments, critiques in the comments!
