
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

## Adding Classes to a package

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


## Adding functionality to classes

1. **Extending Document class**<br><br>
Let's look at our current definition of Document and talk about how we can improve its functionality. Right now the class is just a container for the user provided text; this doesn't add much value for our user. In order for our Document class to be more useful, we can add more attributes & methods besides __init__. For example, let's say that in our workflow we always want to tokenize our documents as a first step. Tokenization is a common step in text analysis, it is the process of breaking up a document into individual words, also known as tokens.As we've learned, __init__ is what's called when a user wants to create an instance of Document. This would be a convenient location to put a tokenization step. Placing the tokenization process inside of __init__ will ensure our Document is tokenized as soon as it is created, and this will save your user's the trouble of thinking about this step.<br><br>

Our new __init__ method might look something like this. You can see that we added a line that calls self dot underscore tokenize and dumps the output into an attribute named tokens. So where does underscore tokenize come from? and why does it have an underscore in front of it?<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/278afcb3-1c45-46be-95bc-e91a043166e0" width="700"></p><br><br>

2. **Adding _tokenize() method**<br><br>
Let's first answer the question of where the method came from. Since this course isn't focused on teaching text analytics, we aren't going to cover the tokenization function implementation; we'll simply import a function to do it for us. In a way, this demonstrates the beauty of modularity and python's community. Often times there are functions already written by someone in the community, and all you need to do is find out where they are and import them for your own use case. Moving on to the definition of underscore tokenize. We only pass one parameter to the function, the prescribed self convention that will represent an instance of the Document object. Since the tokenize function is already written, all that's left to do is call it on the text attribute. And voila! The tokenization process will now be completed automatically as soon as a user creates a Document instance. So why did we use a leading underscore when naming _tokenize?<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/d9c9f568-ed9b-4884-981c-1b1a2014603b" width="700"></p><br><br>

3. **Non-public methods**<br><br>
The reason we added the tokenization process to the __init__ method is that we wanted tokenization to happen immediately without the user having to think about it. Because of this, the user doesn't need to call underscore tokenize themselves; in other words, this method doesn't need to be 'public' to the user. According to PEP 8, non-public methods should be named with a single leading underscore. This signifies to the user that the method is intended for internal use only. Users can still use non-public methods in their own workflow, but they must do so at their own risk since the developer did not intend for them to do so.<br><br>

4. **The risks of non-public methods**<br><br>
The risks of using a non-public method in your own workflow include: little or no documentation and the function's input or output might change without warning when the developer updates their package.<br><br>

## Classes and the DRY principle

1. **Creating a SocialMedia Class**<br><br>
To do this let's make a SocialMedia class that performs the same functions as the Document class, but can additionally analyze social media specific things like hashtags. However, when making this SocialMedia class we want to preserve the Document class as is to be used for more general analysis. So, how can we do this? A first guess might be to copy-paste the contents of the Document class. This violates what is known as the DRY principle in Software Engineering.The DRY principle is a great rule that, if followed, can help you write modular, readable code. `DRY stands for: Don't Repeat Yourself`.<br><br>

2. **DRY**<br><br>
There are many ways to follow this rule such as writing re-usable functions, classes, and packages. The benefits of staying DRY are not only saving time by reusing code, but also if you copy-paste code, and later find a bug, you have to remember everywhere you've pasted the buggy code and fix each instance individually. If you stay DRY you only need to fix the bug once.<br><br>

3. **Intro to inheritance**<br><br>
In the case of extending the Document class to be a SocialMedia class, we can stay DRY by using the Object Oriented Programming concept of inheritance. With inheritance, we start with a parent class and we pass on it's functionality to a child class. The child class inherits all the methods and attributes of its parent, and we're able to add additional functionality without affecting the parent class.<br><br>

4. **Inheritance in Python**<br><br>
So how do we leverage inheritance in Python? To start let's see how the child SocialMedia class fits into the package structure. It will live as a single file named after the SocialMedia class at the same level as the rest of the package's code.

<p align="center"><img src="https://github.com/user-attachments/assets/08c6025b-c96a-4469-a2a3-5418244a4fee" width="700"></p><br><br>

5. **Generic Example**<br><br>
Now let's see how to actually write a child class that uses inheritance. You'll be writing the code for the SocialMedia class, so we'll stick to a generic example. First, we import the ParentClass for use in defining our ChildClass. To let Python know we're using inheritance, we pass the ParentClass as an argument in our class statement. Last, we call our ParentClass's __init__ method. Remember, __init__ builds an instance of a class and it also accepts self as its first argument. With this call, we're building an instance of ParentClass and storing it right back into self. This means that self now has all the methods and attributes that an instance of ParentClass would. We can now use self as normal to build in additional functionality unique to ChildClass. Here, we just add an attribute. With our definitions, we can now create an instance of our new ChildClass as we've seen before, and then access attributes from both the parent and the child. Using inheritance like this can lead to short, easy to read definitions of children classes that are jam-packed with the functionality of their parents.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/a3b14e41-d27c-4996-b6db-c0d421471dc5" width="700"></p><br><br>

### Exercises

<p align="center"><img src="https://github.com/user-attachments/assets/abe1f8c4-6de8-4141-9b10-7208185ce64e" width="700"></p><br><br>

`Note: The call to the constructor of parent class with the parameters same as the child class.`

## Multilevel Inheritance

1. **Creating a Tweet Class**<br><br>
Great job on creating the SocialMedia class for your package. Thanks to the Document class and inheritance you were able to quickly build up the class for a more specific task, but what if we wanted to go even more specific.The SocialMedia class has some general functionality dealing with hashtags and mentions that works across multiple social media platforms. If we wanted to include functionality about retweets, it wouldn't be appropriate to include in the general class; instead, we can create a Tweet class. So how can we do this without losing the benefits of both the Document and SocialMedia classes? `With inheritance again of course!`. <br><br>

2. **Multilevel inheritance**<br><br>
We've seen before that a child class can inherit from a parent class. We can continue the family tree again with inheritance. With multilevel inheritance, our child class is all grown up and can its functionality onto its children.Thanks to inheritance we pass along the traits of all prior classes in the family tree. Note, that in the graphic we only have one inheriting class at each level, but we are by no means limited to this. Multiple classes can inherit from the same parent.In fact, one child class can inherit from multiple parents. This more advanced OOP concept is known as `multiple inheritance`. We won't be covering it in this course, but it's good to familiarize yourself with the definition in case you hear of it out in the wild.

<table>
  <tr>
    <td><p align="center"><img src="https://github.com/user-attachments/assets/b437c2ce-bae5-4b55-a367-940fa4b36a4e" width="500"></p><br><br></td>
    <td><p align="center"><img src="https://github.com/user-attachments/assets/afbb318e-b1be-44fd-8372-1f8a174492b8" width="500"></p><br><br></td>
  </tr>
</table>


3. **Multilevel inheritance and super** <br><br>
Let's code up an example of multilevel inheritance. We'll start with the inheritance pattern we've seen before. Here we define a Parent and Child class that inherits from the Parent. We could do this differently, by using the super function. Instead, of directly calling the __init__ method of Parent we use the super function. This makes no functional difference in our code here but it has some advantages in maintainability and when implementing multiple inheritance. However, there are some `gotchas` that can arise with super and multiple inheritance; you can check out [Learn more about multiple inheritence & super()](https://www.datacamp.com/community/tutorials/super-multiple-inheritance-diamond-problem) companion DataCamp tutorial to learn more about it.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/c9299a10-3c69-443d-ad7f-4b5087312640" width="700"></p><br><br>

Let's continue the family tree, to create a Grandchild class that inherits from SuperChild we use the same super syntax in its __init__ method, and voila. If we create an instance of Grandchild we can see from the output that each __init__ method in the family tree was called.

<p align="center"><img src="https://github.com/user-attachments/assets/88b1c390-851a-4387-884d-9759eaeeb56c" width="700"></p><br><br>


4. **Keeping track of inherited attributes**<br><br>
If you're using inheritance it's sometimes hard to remember what attributes and methods your class has at the end of it all. If you're using an IDE, then generally you can use tab complete to get a list of suggestions. However, if you want to get the info from the console, you can use either help or the dir function. help is a good option in most cases, but it will only include public methods in it's output. Using dir will print a fairly exhaustive list of what your class has under the covers. The list includes methods that come with our class object by default. Near the end of the list, you see all the methods and attributes that you personally programmed into the SocialMedia class. dir can definitely come in handy, but a warning from the documentation, "dir is supplied primarily as a convenience for use at an interactive prompt." So it's not advised to use it in your scripts.<br><br>

### Exercises

<p align="center"><img src="https://github.com/user-attachments/assets/725555e4-911e-4e53-9d56-a594c2f9cb82" width="1000"></p><br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/0276b961-c5f9-4f81-96c2-e4a33c2f5f02" width="1000"></p><br><br>

# Chapter 4: Maintainability

## Documentation

1. **Documentation**<br><br>
One of the big Software Engineering concepts that all python users benefit from is Documentation.Documentation in python can take the form of comments. Comments in python are led by the pound symbol as you see here. They can sprinkle in information about your code for future collaborators. Another way of documenting code is to use docstrings. Docstrings are invoked by the use of triple quotation marks like you see here. They are typically used to document functions, classes, and scripts for your users. Let's look at both these in a little more detail.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/3a949171-c659-47da-acc6-315947ce02c2" width="700"></p><br><br>

2. **Comments**<br><br>
Comments are used inline to document what a particular line of code is doing and why. They can appear on their own line or a the end of a line of code. A big difference between docstrings and comments is that comments will not be seen by your users unless they are looking into your source code. The goal of comments is to make your code more readable for both yourself and collaborators.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/e8e883f9-90f8-4569-b6f1-3648139e4731" width="700"></p><br><br>


3. **Effective comments**<br><br>
There is some debate on the usefulness of comments. Take a moment to look at these comments. As you can see, they don't add much value; unless the code is trying to teach someone about Python basics, then these could be useful comments. So it's important to know your audience when commenting. However, a good rule is that comments should explain why a line of code is doing something and not what the line of code is doing. Here is the same code with different comments to explain the why of the code. In my opinion, over-commented code isn't nearly as big of a headache as under-commented code. If you ever question whether or not a comment is useful I would suggest adding the comment.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/24171eb7-f390-45d5-9581-16843066d9f2" width="700"></p><br><br>


4. **Docstrings**<br><br>
Comments are documentation for yourself and collaborators, docstrings are documentation for your users. Docstrings are what python outputs whenever a user calls help on your functions and classes. Let's look at the anatomy of a docstring. The first sections describe the functionality of what we're documenting.Next, we document the parameters and return value of our function. We use this particular syntax with the colons by convention so that downstream tools can take our docstrings and convert them into website based documentation. You can see an example of a webpage generated from a docstring formatted like ours at this link which show's the documentation for the popular Flask package.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/72a50733-09a3-4a15-8125-295085e31d06" width="700"></p><br><br>

[Example webpage generated from a docstring in the Flask package.](https://flask.palletsprojects.com/en/3.0.x/api/#application-object)

5. **Example docstring**<br><br>
Here we see a docstring actually filled out to describe a function and its usage. It contains a brief description, information on the parameter & return values, and an example showing how the function is used. In the case of this simple function, the optional details section wouldn't add much value so it's been omitted. In addition to the docstring, we see comments explaining why the code was written a certain way, as opposed to what the code is doing.Now that we've written the docstring for the square function, users can access it by calling help. When they do they'll see this print out showing all the information they'd need to understand what it does and use it properly. Note, as mentioned before, the user's don't see our comments that describe our implementation details to future colaborators.<br><br>


<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/25eae1ce-674b-46a9-b4bc-baa6d3e68764" width="500"></td>
    <td><img src="https://github.com/user-attachments/assets/15535bb3-6b82-4dd7-aa79-7333ce2c29b9" width="500"></td>
    <td><img src="https://github.com/user-attachments/assets/419290f4-5011-427c-8c02-9ff430c62361" width="500"></td>
  </tr>
</table>


## Readability Counts

1. **Readability counts**<br><br>
Another important step to writing a maintainable project is readable code.<br><br>

2. **The Zen of Python**<br><br>
Luckily, Python has a big focus on readability, and it comes with a list of guidelines to help write good code. These guidelines are known as the 'Zen of Python', and you can view them through the command 'import this'. Here we see an abridged version. Notice the item stating, 'readability counts', and the rest of the items can guide us in this quest for readability.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/becd4f1c-5307-4656-83c6-b551a4049185" width="700"></p><br><br>

3. **Descriptive naming**<br><br>
One way to aid in readability is with good naming. Look at these 2 functions. Both implement the same logic. However, if we believe 'readability counts', then the is_boiling function is a better option. The is_boiling function describes what it's doing thanks to descriptive naming. This is known as self-documenting code. However, remember that under-commented is a bigger issue than over-commented code; if you're ever in doubt, add comments. A warning about descriptive names. It's possible to go too far. Modern IDEs have auto-complete so it might not seem like a burden to type long names, but long names can make code hard to read, as you see here. Note, even if your code is self-documenting, your users will appreciate the ability to call help and see all the good information a docstring can provide.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/3a0c26cb-9bcd-4193-8c11-18fa9eecd909" width="700"></p><br><br>

4. **Keep it simple**<br><br>
Another way to keep your project readable is by writing in simple maintainable units of code. Let's take a look at an example by writing a function to make a pizza.


5. **Making a pizza - complex**<br><br>
Take a look at this code to make a pizza. Notice that the full definition doesn't fit on the slide. Although we're working with a small screen, not being able to fit your function on the screen is a sign that it maybe should be refactored. A less obvious issue is that we have a few different processes happening that could stand on their own. We're making dough and then making a sauce; we might want to be able to make dough outside of the pizza process. Let's do some refactoring.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/b268f804-c6f6-46c9-8b87-04afb1f0d05f" width="700"></p><br><br>

6. **Making a pizza - simple**<br><br>
Take a second to look at this refactored function. It's easier to see what's happening, in both a functional sense and a literal one since we were able to fully fit it on the screen. By breaking processes out into their own descriptively named functions we can see the high-level process of making a pizza at a glance. An additional benefit of defining these smaller functions is that we now have more modular code that we can easily plug into different recipes that might call for our homemade marinara. These also make writing tests easier, which we'll soon be covering.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/90d9d84c-d945-4bce-8c91-cce9e1610fb7" width="700"></p><br><br>


7. **When to refactor**<br><br>
Our rewrites came about thanks to a couple warning signs. They were that our function was a bit long and we had separate processes happening. You should strive for your functions to accomplish one and only one thing. In our pizza example, we were using comments as 'section headers' to denote different processes; if you're ever doing that then it's a good bet that your code should be split into smaller functions. Another warning sign that your function is doing too much is if it's hard to think of a good meaningful name for it. Unfortunately, you might not notice your code is hard to read until trying to read it the next day. Just strive to do your best, and to repeat once more: document your code with comments and docstrings.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/933a12d3-0bd6-4ffe-8b62-f7cced9793d6" width="700"></p><br><br>

## Unit testing

1. **Unit testing**<br><br>
Even well-documented, readable code isn't very useful if doesn't work correctly. That's where testing can come in handy.<br><br>

2. **Why testing?**<br><br>
With testing, you can confirm your code is working as intended. You probably already run some manual tests. Instead of writing these tests in the console, you could add much more value to your project by adding these to your test suite. A written test can be re-run after you make changes to check if there were any unexpected effects. Also, changes in dependencies can sometimes break your code. Automated tests can alert you problems like this and more. So how do we test in Python? We'll cover 2 easy to use options: doctest & pytest.<br><br>

3. **Using doctest**<br><br>
Thanks to writing informative docstrings with examples included you've already written tests that can be run with doctest! Let's look at an example with this square function. To use doctest we need to import it and run the testmod command to test our module's examples. When we run the tests we see that it failed. Looks like there was a typo in the docstring that was caught thanks to doctest. If there were no failed tests the output from testmod would be blank.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/d2ed7803-6bae-46fc-837d-8d24d9f03c31" width="700"></p><br><br>

4. **pytest structure**<br><br>
doctests are great for smaller examples, but you often can't cover every case you want to test in a docstring. For example, if your function returns a large pandas DataFrame this could be hard to include as a doctest. For larger cases, there's pytest. To use pytest, I recommend a tests directory at the same level as your package's directory.Due to pytest's flexibility, there are other options. For example, if developing a larger package it might be useful to break out subpackage tests into their own folders.<br><br>

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/8003fa29-cef4-40df-8bfb-1b441d47957c" width="700"></td>
    <td><img src="https://github.com/user-attachments/assets/fa131cac-767b-4f0a-819b-911727bd6432" width="700"></td>
  </tr>
</table>

5. **Writing unit tests**<br><br>
Let's write some tests for our Document class. First, notice the test underscore prefix. pytest searches for tests by first looking for files that start or end with the word test, and then pytest runs all the functions in these files who's name follow the same pattern. Within our test method, we've then created an instance of document as our test case. Last, we run the actual test with the assert keyword. As long as the assertion is True, our test passes. When testing, it's also a good idea to test for the 'edge cases' that you can think of. For example, here we could test the expected attributes of a blank Document.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/96b49af5-932e-4b0d-b4e3-5e41653c4922" width="700"></p><br><br>

6. **Writing unit tests**<br><br>
Note that when testing class objects, it's not wise to compare two objects with double equals. Here we create two identical Document objects and test equality. Our test shows the objects are not the same. Instead, to compare objects we can compare attributes as we see here.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/2f4530bc-526b-4842-8355-3a08b4175dcf" width="700"></p><br><br>

7. **Running pytest**<br><br>
To run our tests we head to the terminal in our work_dir directory, run the command "pytest", and wait for our output. We see that all of our tests passed and our code is running as expected [1].If we just wanted to run the tests in one file our command might look like this and we'd only get the results for that file's tests.So far all of our tests have passed.[2] Let's look at some output of when things go wrong. In the output, we see exactly which test failed and even how it failed. This information can be a lifesaver when your projects grow and tracking down bugs becomes a more time-consuming process.[3]<br><br>

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/b563a043-4939-4173-81bf-54662ffccbcf" width="700"></td>
    <td><img src="https://github.com/user-attachments/assets/ca35f182-e29c-4bfe-8067-31b34dfbcb2b" width="700"></td>
    <td><img src="https://github.com/user-attachments/assets/f26b08ec-4f1f-4933-a58a-b110882dd2df" width="700"></td>
  </tr>
</table>


## Documentation & testing practice

1. **Documenting projects with Sphinx**<br><br>
Sphinx was mentioned earlier as a tool that transforms docstrings into beautiful documentation. Here we see an example of what your Document class might look like as an HTML page generated by Sphinx. All of this benefit just from writing complete docstrings! If you're managing your project with GitHub or GitLab then you can even host your Sphinx-built documentation for free using the products' services. That way users can search the web to find your helpful documentation.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/50d534cb-fa1a-4c68-8cb0-11abd84693a4" width="700"></p><br><br>


2. **Documenting classes**<br><br>
You might have noticed that the example Sphinx page showed documentation for a class and included information on attributes. Let's take a quick aside to look at the docstring that was used to build the page. This docstring should look mostly familiar, but here are a couple of things to note. We document the parameters for the init method in the class docstring. This way users can see how to initialize a new instance by calling help on the class itself. Next, we document attributes using the 'ivar' keyword. This abbreviation stands for 'instance variable'. With this documentation in place, users can easily see how to use your class.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/e1fc50c7-a9f0-4ac7-95bf-a3256dc1e4ad" width="700"></p><br><br>

3. **Continuous integration testing**<br><br>
By using pytest extensively you'll be able to have most, if not all, of your project's code being tested, but it can be a bit of a bother to have to always run the tests repeatedly from the command line. This is where tools like Travis CI come in. The CI stands for continuous integration, and it just means that you are continually adding new code to your project. When adding this new code, Travis can automatically run your tests for you and alert you if your changes broke something [1]. Then when you push a fix, Travis CI will run your tests again to double check that your fix was successful. Another great aspect of Travis CI and other CI testing tools is scheduled builds. By scheduling a build your tests can be run periodically even without you adding new code. Scheduled tests are a great way to catch bugs introduced by updates in one of your dependencies [2].<br><br>


<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/3ee3b26b-9296-486e-87b2-f40990426133" width="700"></td>
    <td><img src="https://github.com/user-attachments/assets/bf0f65a3-228b-477f-8f98-675d6a9f3663" width="700"></td>
  </tr>
</table>

4. **Links and additional tools**<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/f339e421-4d11-4327-ae45-9016d662763a" width="700"></p><br><br>

[Sphinx](https://www.sphinx-doc.org/en/stable/)
[Tarvis CI](https://travis-ci.org/)
[GitHub](https://github.com/)
[GitLab](https://github.com/)
[Codecov](https://codecov.io/)
[Code Climate](https://codeclimate.com/)



### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/89392904-a316-45c2-a668-1c4aeeebd1bd" width="1000"></p><br><br>

