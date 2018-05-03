---
title: Using Databases!
date: '2015-05-05'
blog: blog
published: false
---

If you are trying to run an application, you will probably need to store data somewhere. A database helps you do this. If you've used a computer with Microsoft Office on it, you might have some passing familiarity with Excel. Excel is a database that has a graphical user interface, and can do some of it's own programming. You might have used it to create tables, or to balance your budget. If you want to create Rails apps, you will want to use a database that you can access in the terminal or console. Rails, by default, will run with SQLite. There are other options, such as postgresql, MongoDB, and MySQL. Each has their own pro's and con's, and each has had moments of extreme popularity that lead to shops still using them years later.

SQL - pronounced like sequel, as in the second thing in what should never have been more than one thing in the first place, stands for Structured Query Language. Learning SQL is a lot like learning a new language. This post is for people that do want to learn that new language. If you want to skip this post, check back later and I will be explaining how to totally get around learning SQL and just write out stuff directly into your app.

<!--more-->

SQL is a database that has rows and columns. You can perform CRUD on them. CRUD isn't as bad as it sounds. It stands for "Create, Read, Update, Destroy." Those are the actions you can perform in a database. You can create data, read it, update it, and destroy it.

Using ActiveRecord you can connect your database to your program, and use your terminal to CRUD your data via the database or via your program. Postgres and other databases you might use in doing Ruby programming are tabular databases, meaning it has rows and columns. Each record in that database is given a primary key that is unique.

For example, you might have a table in a datbase that looks like this:

id | name         | color
1  | gryffindor | red
2  | hufflepuff | yellow

Once you'ce installed postgres, you can open it by typing 'psql' in your command line. Once you open postgres you can view all the databases you have by using \l and connect to one using \c databasename. To exit you type \q. Each database can have multiple tables, so once you are connected to the database you can see the tables you have. This is a bit like having one excel doc with multiple sheets.

To create a database you would type (do you have your cap locks ready?) CREATE DATABASE databasename; and enter/return. Also, like CSS, ; are super important here. Once you've created it, you will connect to it using "\c databasename;" and then the command line prompt will change to reflect the database you are in. Once you are in the database, you can create all the tables you need. You create a table in roughly this format:
<pre><code>CREATE TABLE cats (
  id    SERIAL PRIMARY KEY,
  name  VARCHAR(50) NOT NULL,
  owner VARCHAR(150) UNIQUE,
  age   INTEGER DEFAULT 0
);</code></pre>
VARCHAR means variable characters, and the number that comes after it is the limit on those characters. NOT NULL means that it can't be left blank, UNIQUE means only one can exist in the database (good for things like emails, but, well, cats don't have emails), INTEGER is for number, and DEFAULT 0 in the above example means that if a value isn't given, it will automatically be assigned to '0'. SERIAL PRIMARY KEY means that a key will be assigned automatically in incremental increases. ALSO: NOTE THE SEMI COLON.

Now that you've created your table, you need some data in it. To add a cat to the cats table you would type

INSERT INTO cats (name, owner, age) VALUES ('Didi', 'Nikki", 4);

DO NOT FORGET THE SEMI COLON. There is nothing worse than forgetting that semicolon. Now that you have some information in your table, you need to be able to search it and select from it. If you want to see all rows you can type:

SELECT * FROM cats;

Again. Semi-colon.  To select just certain data you can specify which you want:

SELECT * FROM cats WHERE age &lt; 1;
SELECT * FROM cats WHERE owner = "Nikki";

You can combine them with the AND operator. Also. Do. Not. Forget. The. Semicolon.

If you made a typo and need to update or something's changed, you can type:

UPDATE cats SET age = 5 WHERE name="Didi";

If you need to delete a record you can type:

DELETE FROM cats WHERE name = "Didi";

But please don't actually delete Didi. She's a very good cat.

Now that we can do some simple SQL, we can get into Active Record, and, soon be able to create all this stuff without writing any SQL!

You can access the information you have in your databases via ActiveRecord. Active Record is a model, or a piece of data in Rails. Rails is like a house, with walls and floors and windows and support beams; it has many parts and they all have different functions. Active Record is like a piece of the house. It's able to function on it's own outside of it's purpose in a house, though. So it's a bit like a sink, you can use a sink or might need a sink at times when you aren't in a house.

Make sure you have the Active Record gem installed, which you should if you have Rails. Otherwise "gem install 'active_record'" in your command line. You must also require it in your Ruby file. At the top of your Ruby file, add "require 'active_record'" and you should be set! You should also make sure that you have the right adapter. An adapter is like those things you buy when you are going to other countries and need to still use electricity. Active Record can talk to any database, but it will need a different adapter for each. Figure out which database you are using and install the right adapter.

If everything is all set up, the complicated part starts now. To connect your database to Active Record you're going to need to type in:

ActiveRecord::Base.establish_connection("postgres://user:password/database_name")

Very tricky, I know. Now, how do we use this to talk to a database? You do so by creating a model in your Ruby file and having it linked to ActiveRecord. Like this:

class Cat &lt; ActiveRecord::Base
end

Because Ruby is based on convention, it will do what people lovingly/hatingly call "Ruby Magic". It will see that there is a table called cats and assign it's contents to the Cat class.  The convention is that the table will be plural, and snake case, while the model will be capitalized and camel case. Active Record is about 99% capable of figuring out irregular plurals like wolf and wolves.

Now that you have everything hooked up you can use pry or irb console to add data, edit it, and delete it. You can run your Ruby program and use the following methods:

Model.all
Model.count
Model.find(&lt;id&gt;)
Model.destroy(&lt;id&gt;)
Model.where(:field =&gt; "value")
Model.order()

Using these methods, you can easily search your database in the console, or write methods to display your data!
