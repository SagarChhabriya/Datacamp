
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
