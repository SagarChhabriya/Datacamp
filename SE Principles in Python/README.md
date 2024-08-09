
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
<p align="center"><img src="https://github.com/user-attachments/assets/87f10653-5e63-4996-90e4-02092ba8786b" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/bf85677d-c3dd-42b0-a656-f58eb9d28f02" width="1000"></p>

## Adding Functionality to your package

1. **Package structure**<br><br>
To start, let's again look at the file structure we'll be using. Here we've added a file to our package's directory named utils dot py. Again, when we import and work with our resulting package we'll be in the my_script file that's in the same directory as our package. Note that we can choose a different name than utils, but keep in mind that file names should follow the same conventions as package naming. That is, file names should be all lower case and avoid underscores unless it improves readability or if it's a special case such as our package's init file.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/ddb74e12-9243-4f00-8529-e22de3e87f14" width="700"></p><br><br>

2. **Adding functionality**<br><br>
With the right structure in place, the next step is to write some code. Here, in our utils dot py file, we write a function that prints one of two possible statements based on user input. Our utils file is known as a submodule and we can import and with a dot notation syntax of the form: package name dot submodule name dot function name. In this example, we call my_package dot utils dot we_need_to_talk.

<p align="center"><img src="https://github.com/user-attachments/assets/e71f4e84-3f77-44fc-9365-a383c71fa735" width="700"></p>

3. **Importing functionality with __init__.py**<br><br>
Alternatively, we can use our package's init file to make our utils' function more easily accessible by the user. To do this, we import our function in our init file as you see here. The dot notation we use when writing dot utils is known as a relative import and it must be used when packaging in Python versions 3 and above. Importing our function in the init file saves some typing when we want to import and use our function. We're now able to call my_package dot we_need_to_talk without including the additional reference to our utils submodule, importing the function in the init file took care of this reference for us.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/b70b7f2b-4325-4ce2-b361-bc47656db37c" width="700"></p>

3. **Extending package structure**<br><br>
In our example, we added a single file, or submodule, to our package, but we can extend this structure indefinitely to meet our needs. However, when creating larger packages you must be more mindful about organization. When working with multiple submodules should you import them all in init? As a general rule, you should import your package's key functionality in your init file to make it directly and easily accessible. Less central functionality can be accessed by users through the longer submodule dot syntax we saw earlier. The decision of what is 'key' functionality is a gray area, and because of this, there isn't always a clear best way to organize your package. As a package developer, you'll need to use your judgment to decide what you think will give your users the best experience.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/bfae7523-e212-4f4e-b87b-fe007e568d49" width="700"></p><br><br>

In addition to adding additional submodules, you can also build out packages inside your package! These are known as subpackages. Notice how the subpackage still follows the packaging rules of being a directory with an init file. We won't be covering subpackages in depth in this course but exposure to these different structures can be helpful when looking at someone else's code.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/226ea9b4-2f53-47fa-83d7-f60c3b6834a2" width="700"></p>

### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/e3173812-8070-4f7a-b21e-c64f0fbe2c28" width="700"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/95434731-a3b4-4bf1-b057-32f9c7adb32d" width="1000"></p>

## Making your package portable

1.**Steps to portability**<br><br>
The two main steps to sharing a python package are creating setup dot py and requirements dot txt. These two pieces provide information on how to install your package and recreate its required environment. These files list information about what dependencies you've used as well as allowing you to describe your package with additional metadata.Here's how the two files fit into our package structure. They're located at the same level as our package directory. Now let's see what content goes into the files themselves.<br><br>

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/7eebe33d-7d45-4735-b9d7-167f8aaa47e1" width="500"></td>
    <td><img src="https://github.com/user-attachments/assets/044cbefb-aaed-47a0-9397-d533cd328545" width="500"></td>
  </tr>
</table>

2. **Contents of requirements.txt**<br><br>
A requirements file shows how to recreate the environment needed to properly use your package. This includes a list of python packages and optionally the version requirements for each package. Here we see 3 different ways to specify our requirements. If we don't have a reason to specify a version we can just list the package name as you see here for matplotlib. If version is important. We can mark a specific version by using a double equals, or mark a minimum version by using greater than or equal. Since open source packages are constantly evolving, specifying a version can be a big help to your users. To leverage our requirements file we can use this pip install command. This installs all the packages listed with respect the correct version. Note that we didn't actually install our package, we just recreated its environment.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/2ba56f02-3c33-4702-8ab1-c41c64610c4b" width="700"></p>


3. **Contents of setup.py**<br><br>
setup dot py is what tells pip how to install our actual package. Additionally, its info will be used by PyPi if you decide to publish. The contents of this in our case contains a single call to the setup function from the setuptools package. There are other options, but setuptools is one of the most common and powerful choices. Here we use just a few of the possible setup arguments. There are many more options available that you can read more about in the setuptools documentation. The argument's names make them fairly self-explanatory; for example, your package's name is assigned to name and so on. Some less obvious arguments in our example are install_requires and packages. packages in essence lists the location of all the init files in our package. Our package has a single init file and it's in the directory 'my_package'. As we saw before, more complex packages might include subpackages with their own init files, if this was the case we would also list their locations here. Until you start writing more complex packages, the contents of the packages list will likely be the same as the name argument. install_requires might look familiar, in the case of our package, the contents are the same as our requirements file.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/8c02d2a4-a985-43a1-bc37-9a994734d2ab" width="700"></p><br><br>

4. **install_requires vs requirements.txt**<br><br>
An example of when install_requires can differ is if you want to specify where pip should download packages from. This can be specified in the requirements file as you see here. We won't go into much detail here since this advanced option is not often needed in everyday use. To read up more on the differences you can see the documentation linked [here](https://packaging.python.org/discussions/install-requires-vs-requirements/#requirements-files)<br><br>




# Chapter 3: Utilizing Classes

1. **Object oriented programming** <br><br>
We'll now look at how you can use classes to strengthen your package's functionality. Object Oriented Programming, or OOP, is a great way to write modular code, and reap the benefits of modularity such as easily understood and extensible code. We'll cover some aspects of OOP, but if you want a deeper dive I recommend the dedicated DataCamp courses. Let's jump into some code.

2. **Anatomy of a class** <br><br>
In python, OOP can be utilized by writing classes. Here we see a minimal class implementation. To start we use the keyword class followed by the name of our class. According to PEP8, our class name should be written in camel case, that is, our name should start with a capital letter and every word in the name should have a capital letter as well. Unlike function and package names, class names should never contain underscores. Next, is some documentation that will appear when a user calls help on our class. We'll cover the details of this particular documentation formatting later in the course. Last, we see a function with a familiar name, __init__. Similarly to your package's __init__.py file, this will initialize everything when a user wants to leverage your class. You might have noticed we use a variable named self, we'll get back to this in a couple slides.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/34d255de-37f1-4c55-bad4-3917aca0408c" width="700"></p><br><br>

3. **Using a class in a package**<br><br>
To make our class easily accessible we can add it to our init file just like we've done with functions before. We use relative import syntax to import MyClass from the 'my class' dot py file in the same directory, we can now import the package and access MyClass easily. Now let's create what's known as an instance of MyClass. To do this we call MyClass like a function and supply a string to the value parameter. Calling our class like this tells Python that we want to create an instance of our class by using the init method. Recall that MyClass's init method set the contents of value to a variable we referenced as self dot attribute. Users can access this attribute by referencing my underscore instance dot attribute. Note, nowhere in this script do we see the self-object that we used when defining our class.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/986fd7e5-065e-49ee-bb09-ac7b8d1a49eb" width="700"></p><br><br>

4. **The self convention**<br><br>
Let's look more in depth at the use of self in our class's init method. Self is, in essence, a way to refer to a class instance even though we don't know what the user is actually going to name their instance. When defining typical class instance methods, like __init__, self is the first argument. However, if you recall creating an instance of MyClass, when using __init__, the user doesn't need to pass a value to this self argument; this is done automatically behind the scenes. Once in the method body, we can use self to access or define attributes. The user can then access these attributes by using their class's name in place of self, like we did in our script. Technically we can use a different word than self, but this a very strong PEP8 convention and not abiding by it will make your code very hard to read by your collaborators.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/3fe06abd-a817-4b31-b241-57b5da447eb6" width="700"></p><br><br>




## Adding Classes to a package

## Adding functionality to classes

## Classes and the DRY principle

## Multilevel Inheritance

# Chapter 4: Maintainability

## Documentation

## Readability Counts

## Unit testing

## Documentation & testing practice
