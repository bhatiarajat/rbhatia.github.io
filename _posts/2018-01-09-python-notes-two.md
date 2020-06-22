---
layout: post
title: "Python: Arguments & Functions"
date: 2018-01-09
---

Apart from the direct methods of getting user inputs (where we ask user to enter values while the code is running), another way to do the same thing is by passing variables to a script. Let's look at the following code:

*code:*<br>
1 from sys import argv <br>
2 ex, name, age, weight = argv <br>
3 <br>
4 print("this is exercise:", ex) <br>
5 print("your name is:", name) <br>
6 print("your age is:", age) <br>
7 print("your weight is:", weight) <br>

In the above code, in line1, we are importing the argument variable 'argv', which basically holds the arguments that are passed during the run command. Line2 unpacks the argv, and assigns the values that are entered by the user to 4 variables named ex, name, age and weight. The result of this is below. It is worth noting how the code is being run. The values entered along with the script name (ex13.py) could be anything, and they would simply get assigned to the variables that have been called within the code.

*result*<br>
PS C:\Users\Rajat Bhatia\lpthw> python ex13.py rajat 29 144 <br>
this is exercise: ex13.py<br>
your name is: rajat<br>
your age is: 29 <br>
your weight is: 144

Arguments can also be used to open other files, by simply calling the filename (with extension) as shown in following code:

*code:*<br>
1 from sys import argv <br>
2 script, filename = argv <br>
3 txt = open(filename) <br>
4 print(f"Here's your file {filename}:") <br>
5 print(txt.read()) <br>

*result:*<br>
PS C:\Users\Rajat Bhatia\lpthw> python ex15.py ex15_sample.txt <br>
Here's your file ex15_sample.txt: <br>
This is a sample file that will be read in my other code.

Similar to txt.read(), there are a number of other actions that can be done on the file, such as:

filename.truncate(): deletes the contents of a file named 'filename'
filename.write('sample text'): writes 'sample text' to the file named 'filename' 
filename.close(): closes the file

**Functions** allow you to create mini-scripts by defining commands that can be used multiple times. An example:

*code:* <br>
1 def fullname (first_name, second_name): <br>
2    print(f"Your given name is {first_name}") <br>
3    print(f"Your family name is {second_name}") <br>
4 <br>
5 first_name = input("What's your first name: ") <br>
6 second_name = input("What's your last name: ") <br>
 <br>
7 fullname(first_name, second_name) <br>

*result:* <br>
PS C:\Users\Rajat Bhatia\lpthw> python ex19.py <br>
What's your first name: rajat <br>
What's your last name: bhatia <br>
Your given name is rajat <br>
Your family name is bhatia <br>

The inputs for function 'fullname' need not necessarily come from an input() call. They can be defined from within the script too.

