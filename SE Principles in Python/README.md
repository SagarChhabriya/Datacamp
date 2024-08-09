![image](https://github.com/user-attachments/assets/4aae289d-0510-49ab-ada9-30a023b66bf3)
# Software Engineering Principles in Python

## Table of Contents

## Chapter 1: Software Engineering & Data Science
1. [Conventions and PEP8](#conventions-and-pep8)

## Chapter 2: Writing a Python Module
1. [Write your first package](#write-your-first-package)
2. [Adding Functionality to your package](#adding-functionality-to-your-package)
3. [Making your package portable](#making-your-package-portable)

## Chapter 3: Utilizing Classes
1. [Adding Classes to a package](#adding-classes-to-a-package)
2. [Adding functionality to classes](#adding-functionality-to-classes)
3. [Classes and the DRY principle](#classes-and-the-dry-principle)
4. [Multilevel Inheritance](#multilevel-inheritance)

## Chapter 4: Maintainability
1. [Documentation](#documentation)
2. [Readability Counts](#readability-counts)
3. [Unit testing](#unit-testing)
4. [Documentation & testing practice](#documentation-testing-practice)

# Chapter 1: Software Engineering & Data Science

## Conventions and PEP8

1. **What are conventions?**<br><br>
Something you probably know from real life is that different cultures and communities follow different guidelines that help them run smoothly. For example, this can be seen in different greetings, depending on which community setting you're in it might make sense to say hello by shaking hands, bowing, or bumping fists. These unwritten rules are known as social conventions. The world of software engineering also has conventions that differ based on the language and community.<br><br>

2. **Introducing PEP 8**<br><br>
Luckily for Pythonistas, these conventions aren't unwritten. We can turn to `Python Enhancement Protocol 8`, or PEP 8. PEP 8 is the defacto Style Guide for Python Code. It lets us know how to format our code to be as readable as possible, and to quote PEP 8, `code is read much more often than it is written`. So readability is not something that should be overlooked.
Let's see an example. Here we have some code that violates PEP 8 best practices. To put it simply, the code here is hard to the read. A few problems are: The module import isn't at the top of the file, the spacing and indentation is inconsistent, and the lack of line breaks makes it difficult to tell when one idea finishes and the next begins. Even without knowing the specific PEP 8 rules being broken, you can probably tell this isn't the most readable chunk of code.<br><br>
<P align="center"><img src="https://github.com/user-attachments/assets/52541a74-0f0c-4637-ba0a-8b442799c218" alt="breaking-pep8-rules" width="700"></P>

3. **Following PEP 8**<br><br>
Let's see what the same chunk of code looks like after being rewritten to conform to PEP 8. Much better. By following the agreed-upon rules in PEP 8 and using whitespace appropriately, this code became much more readable despite accomplishing the same exact task.<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/cc4fced4-ba0a-4cd7-917f-8df7d2ddc20a" width="700"></p>

4. **PEP 8 Tools**<br><br>
So how is it possible to keep up with the many rules defined in PEP 8? Thankfully for you and me, there are tools that can check your code for you just like a spellchecker. Personally, I use an IDE that flags violations as soon as I write a bad line of code, but there are other options. One in particular that you'll be exposed to in this course is the `pycodestyle package`. `pycodestyle` can check code in multiple files at once and it outputs descriptions of the violations along with information to let you know exactly where you need to go to fix the issue. Here is some example code on how to install and use `pycodestyle` from the shell. As you'll see in the exercises later you can also run `pycodestyle` from a python script. Here we use the command line interface to check the contents of the file dict to array dot py that contains our poorly formatted code from before. Note that the output we see on this slide has been truncated.<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/c7ef969a-413e-43d7-bfad-85306b50defb" width="700"></p><br><br>

The output shows us the exact location of any violations by showing the file name, line number, and column number where the problem occurred. Note that the output does not use zero based indexing. Additionally, pycodestyle outputs a human readable description of the PEP 8 violation and an error code. A complete list of pycodestyle's possible error codes can be seen in the package's documentation.<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/b227eb5a-2ceb-495a-a525-31e1a1e84773" width="700"></p>

### Exercises
<p align="center"> <img src="https://github.com/user-attachments/assets/de971778-8dc4-4bec-aba2-0e54edd15ebb" width="1000"></p>
<p align="center"> <img src="https://github.com/user-attachments/assets/9f41dd32-dbad-4779-bbe1-67afb343a5cb" width="1000"></p>
<p align="center"> <img src="https://github.com/user-attachments/assets/7f97c311-5494-4eff-b7d4-78a55acac66d" width="1000"></p>



# Chapter 2: Writing a Python Module

## Write your first package

1. **Package structure**<br><br>
A minimal python package consists of 2 elements: a directory and a python file. You can see the basic structure here. The name of the directory will be the name of the package, but how should you name it? We can turn to PEP 8 again for some guidance.To paraphrase, PEP 8 states that packages should have short, all-lowercase names. The use of underscores in a package name is discouraged, but you can and should use them if it improves readability. Outside of this, you have the freedom to brand as you'd like. I'd suggest picking a name that conveys the functionality of the package.<br><br>

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/92446052-cd30-4f70-a706-b61de916eed3" width="500"></td>
    <td><img src="https://github.com/user-attachments/assets/91ca61f1-8af5-4f20-a06a-9e78a85eda45" width="500"></td>
  </tr>
</table>
<br><br>

The file in our newly branded directory doesn't have any flexibility in naming. We must name it underscore underscore init underscore underscore dot py. This file lets python know that the directory we created is a package. And that's it! With this structure we've created a package that we can import just like we would import numpy or any other package. Note that as of Python version 3-point-3 any directory can be imported as if it were a package without error even if it doesn't follow this structure. Earlier versions of Python would throw an error if you tried to import an improperly formatted package. Even though a directory might import without error, you will run into issues if you do not follow this structure.<br><br>

2. **Importing a local package**<br><br>
So how do we import our package? Before we look at some code let's establish where our script is relative to our new package. We'll be working in the my_script dot py file that's in the same location as our package directory.<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/e5d49ebe-5406-4fc6-a1e6-3fa2af11ed27" width="700"></p><br><br>

With all the setup we've done so far, importing the package is a breeze. At the top of our script, we can use import my_package. Just for an added bonus, let's check out what happens if we try to call help on our package. We get some minimal information with python letting us know that it is indeed a package and additionally we see the location of our __init__ dot py file. As we previously covered, it's up to the developer to add in useful documentation to be printed whenever a user calls help. Later we will be going over how we can add this documentation as well as implementing some functionality to make our package more useful.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/801e31e8-2b41-4ebf-9011-111e4d2bf3f8" width="700"></p>

### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/87f10653-5e63-4996-90e4-02092ba8786b" width="700"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/bf85677d-c3dd-42b0-a656-f58eb9d28f02" width="700"></p>

## Adding Functionality to your package

## Making your package portable

# Chapter 3: Utilizing Classes

## Adding Classes to a package

## Adding functionality to classes

## Classes and the DRY principle

## Multilevel Inheritance

# Chapter 4: Maintainability

## Documentation

## Readability Counts

## Unit testing

## Documentation & testing practice
