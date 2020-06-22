---
layout: post
title: "Learning Python with Zed Shaw"
date: 2018-01-08
---

Posting my notes from the Python learn-along I did a few weeks back. I used multiple books during my learning sessions, however, the one I completed was <a href="https://learnpythonthehardway.org/python3/">'Learn Python the Hard Way'</a> by <a href="https://twitter.com/zedshaw">Zed Shaw</a>. I found it to be an incredible resource that took me straight to the application of code instead of talking about theory. In all my past experiences with learning new stuff, I have found that the initial few sessions which just talk about theory drive me away and lead me from completing any tutorial.

Starting off with a screenshot of my setup, with one of the first exercises done from the LPTHW book:

<a href="/images/posts/python1.PNG"><img src="/images/posts/python1.PNG"></a>

It is worth noting that Python considers any text with a " or ' around it as a **string**. If you want to put a variable into a string, the way to do it is **f"some stuff here {a variable}**. Here's an example code to demonstrate this:

*code:*<br>
1 types = 10
2 x = f"there are {types} types of people"

*results in:*<br>
PS C:\Users\Rajat Bhatia\lpthw> python ex6.py <br>
there are 10 types of people

Another way of doing this is by using .format() like the following code:

*code:*<br>
1 print("Its fleece was white as {}.".format('snow'))

*results in:*<br>
PS C:\Users\Rajat Bhatia\lpthw> python ex7.py <br>
Its fleece was white as snow.

More formatting with strings below. This is useful when we want to repeat an action with different text but similar format:

*code:*<br>
1 formatter = "{} {} {} {}" <br>
2 print(formatter.format(1, 2, 3, 4))

*results in:*<br>
PS C:\Users\Rajat Bhatia\lpthw> python ex8.py <br>
1 2 3 4

Getting user input through code.:

*code:*<br>
1 print("How old are you?", end=' ') <br>
2 age = input() <br>
3 print("How tall are you?", end=' ') <br>
4 height = input() <br>
5 <br>
6 print(f"So, you're {age} old and {height} tall.")

*results in:*<br>
PS C:\Users\Rajat Bhatia\lpthw> python ex11.py <br>
How old are you? 29 <br>
How tall are you? 5'9 <br>
So, you're 29 old and 5'9 tall.

The same could also done this way:

*code:*<br>
1 age = input("How old are you? ")
2 print(f"So, you're {age} years old.")

