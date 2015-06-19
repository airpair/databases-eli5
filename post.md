Explain Like I'm 5 years old - **databases**. This article is intended for complete beginners or even people without a technical background. If you're just curious about what a database is, or what the word 'data' means, this article is for you.
___
![Rubber Ducky NoSunglasses](http://www.saintpetersblog.com/wp-content/uploads/2014/08/rubber-duck.jpg)

![Rubber Ducky Sunglasses](http://ecx.images-amazon.com/images/I/61YHf5GsARL._SL1024_.jpg)

Look at these two rubber duckies. Can you spot the difference? This is the Duckerson family. The ducky with sunglasses is named Ricky. His brother is named Jim.

Now both of these ducks want to buy a hat. **You have a hat store for ducks**, and Ricky and Jim are interested in buying a hat. They log in to your hat store website and they fill out their personal information.

Ricky enters:

1. First name: Ricky
2. Last name: Duckerson
3. Interested in: Hats
4. Owns sunglasses: Yes
5. Age: 5

Jim enters:

1. First name: Jim
2. Last name: Duckerson
3. Interested in: Hats
4. Owns sunglasses: No
5. Age: 3

When they enter this information, it has to be stored somewhere. The website will remember their names, what they are interested in, and if they own sunglasses. The website stores this information in a **database**. 
___
**Data** is just another word for information. So think of a database as a home base for all that information. If we look at Ricky's data, we see that he owns sunglasses! Data is used all the time in websites, for many many reasons. 

Now that Jim and Ricky are logged into the website, the website looks at this data to suggest products for them. The website has a section "Reccommended Products", you've probably seen a website with this exact feature before: amazon, newegg, almost every website that sells products has a "Reccommended for you" section.

We're going to look at the structure of a database briefly, then I'm going to explain how the website gets the data *only* for Jim when Jim logs in, and *only* the data for Ricky when Ricky logs in.
___
# Structure of a database
On a piece of paper, write down Ricky's information horizontally, seperated by some space. You've got his first name, last name, interests, and sunglasses. Now, below that, write Jim's information in the same way. Draw some vertical and horizontal lines between the information. Above each column put the title of that column. This probably looks a lot like a spreadsheet, if you've ever used one of those.

That's pretty much what some databases look like. The piece of paper itself is called a **Table**. That table stores information about the Duckys, or customers, or products, or anything you could imagine. The vertical lines seperate the **Columns**, in which each row is the same data-type. The horizontal lines seperate **Rows**.

> Within columns, all rows must be the same data type.

Take for example, the First Name column. Every entry will be someone's Name, which is going to be a string. **Strings** are like those bracelets with alphabet letters strung together. They form words and sentences. Databases called this data type **varchar** -- think of variable characters. Each character varies, so you can have "J" + "i" + "m", or "Jim" as the value, each character can be anything.

Now look at the Age column, these are all numbers. In math, numbers are called **Integers**, and in programming they are also called integers. Databases shorten that and call them **int**. Why do there have to be different data types? Well, a computer can compare integers like this: "Is Jim's age greater than Rickys age?". But a computer cannot (logically) compare strings: think about this: "Is Jims name greater than Rickys name?" A computer cannot figure that out, and if it did it might not be the same answer you come up with (I'm looking at you, Jim).

There are other datatypes but lets skip them because we didn't get any other data from Jim or Ricky when they signed up for our hat store. I'll include some extra links at the bottom of this article for you to explore more.
___
##How do you get the data back out of the database?

There is something called a **database query** which pulls specific information out of a database. I like to think of queries as just questions. You say "Give me all the duckys". That would be a very simple query, let's take a look.

    SELECT * FROM Ducky_Table

This is going to return all columns and all rows from the Ducky_Table table. I capitalized the keywords, SELECT, and FROM. Each keyword is the beginning of a clause. Clause just means a part of a sentence, you can see why I think of queries as questions. SELECT * means SELECT EVERYTHING. Anything after SELECT will determine which columns are selected, for example, we just want a list of first names.

    SELECT first_name FROM Ducky_Table

The FROM clause specifies which table (remember piece of paper) to grab the data from. Not much to explain there, as the keyword is actually FROM. SELECT and FROM are the two clauses that must be present in every query. What if we want to only select Jim's name?

    SELECT first_name FROM Ducky_Table WHERE first_name = "Jim"

This is going to return just Jim. That's not a very useful query, we already know Jims name. How about, We know Jim's name but we want to know what he is interested in?

    SELECT interests FROM Ducky_Table WHERE first_name = "Jim"
    
That's a useful query! "In the Ducky table, where Jim is the first name, give me his interests." This is how reccommended products are figured out. The database knowns the customer and their interests. So you just ask the database for the interests of Jim with that query. What about if we want to get all the duckies that own Sunglasses, and also what their interests are

    SELECT first_name, interests FROM Ducky_Table WHERE owns_sunglasses = "Yes"

This is great, it returns Jim and his interests (Hats), because he's the only Ducky with sunglasses.

Theres a lot of online resources to learn further, but I believe practice makes perfect. **[Here's a sandbox](http://sqlfiddle.com/#!9/36e504/1)** where you can play with this Ducky database. Try out some of these queries (you can copy the ones from this article exactly, and watch them execute in your browser!) and make some of your own!

[Here's more reading material](http://www.techonthenet.com/mysql/datatypes.php) about data types. Can you see a better data type for the owns_sunglasses column? Maybe one that has to do with true and false?

I hope this was a gentle enough introduction to databases for you. Often when I talk to my non-technical friends, as soon as I say the word "Data" they stop following what I'm saying completely. I think people need to know that pretty much everything can be explained with rubber duckies.