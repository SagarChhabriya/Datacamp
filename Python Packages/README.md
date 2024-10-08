# Datacamp


## Packages
version = major.minor.patch <br>
patch: bug fixes, issues, or code fix<br>
minor: for add new features such as class or functions<br>
major: for a really big change<br><br>

`setup.py`
To make the package installable, you need to add a new file to the package the setup.py file. The setup script is part of the package but not the source code. To add the setup script, we need to restructure our directory slightly. Therefore we create a new folder inside the package directory to keep the source code. It's very common to name the inner and outer folders the same thing. Here the outer package directory is called my-sklearn, and inside this directory there is the directory of source code, also called my-sklearn.<br>

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/224d2e0e-436d-4620-adc0-cb25640601b4" alt="Image 1" width="400" /></td>
    <td><img src="https://github.com/user-attachments/assets/d699d351-1451-4410-8872-a62c1147c551" alt="Image 2" width="400" /></td>
  </tr>
</table>


- Once you have written the setup script you can install the package. You should navigate to the directory containing the setup file, and then you can use pip to install the package like this. `pip install -e .` Pip runs the setup-dot-py script for you. The dot at the end of this command means install the package in the current directory. The dash-e means to install this package in an editable mode. This means when you make changes to the source code, like fixing a bug or adding new features, these changes are included when you import the package. If you didn't do this, you would need to reinstall the package each time you make a change.<br><br><br>

- Being a good package developer means not reinventing packages that already exist. These extra packages that you use inside yours are the dependencies of your package. When someone else, or just you, tries to install your package, you need to make sure that they have these packages installed too.<br><br>

- To ensure that your users have the right packages installed, you can set the install-requires parameter inside the setup function of the setup script. Here you list the packages which your package depends on. Then when someone uses pip to install your package, pip will install these extra packages as well, unless the user already has them. These dependencies are updated often, and the version number changes. In this example, any version number of these packages is allowed.

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/30a1502d-355d-46ac-9c16-1c80d221b018" alt="setup.py" width="400"></td>
    <td><img src="https://github.com/user-attachments/assets/2c0b8199-d5cc-428d-8ce6-0e721fd27826" alt="setup.py" width="400"></td>
    <td><img src="https://github.com/user-attachments/assets/91e1c996-0a94-4a2a-bf48-4f9976ea9d21" alt="setup.py" width="400"></td>
  </tr>
</table>


## Including licences and writing READMEs
1. **Why do I need a license?** <br><br>
The license is a really important file for code you want to share online. If you host your package online, but do not include a license, then you are not giving permission to other people to share, modify or even use the code! Many great packages are open source and may be freely modified and shared by other users. This openness has led to the success of many of these packages as they have attracted developers to work on them.<br><br>

1. **Open source licenses**<br><br>
There are lots of different licenses you might include, and we can't go into all of these in this course. If you would like to open source your package, then I thoroughly recommend you to find out information about these license choices here. All of the open source licenses on this popular website allow individuals to use your package themselves, and to modify and share it. Some licenses might require modified versions of the package to be open sourced, and shared with the same license you used. [Click Here](https://choosealicense.com)<br><br>


1. **What to include in a README** <br><br>
What you include is mostly up to you, but a good README will have the `package title`; a `description of the package` including its most important features; instructions on how to install the package; some example uses to get started; a section on how to contribute to the package code; and a brief note on the type of license used.<br><br>

1. **README format**<br><br>
Just like there are multiple formats for documentation, there are two formats used for READMEs - `reStructuredText` and `markdown`. In this course, you'll use markdown to write your README. It is slightly simpler than reStructuredText and is a common choice in the wild. Most of what you write in markdown will be easy to convert to reStructuredText if you ever need a more complex README.<br><br>

1. **Commonmark** <br><br>
There are some slightly different versions of markdown out there. But the version for READMEs is called `commonmark`. Commonmark is a file format like HTML, but is much much simpler.<br><br>

1. The license and README files should be added to the top directory, alongside the setup script and the requirements file.<br><br>

1. **MANIFEST.in** <br><br>
There is one last file you will need to create before you can release your package to the world. This is the manifest-dot-in file. This file is used to list all of the extra files that you want to distribute along with your package. This manifest file is important because by default your license will not be included when someone downloads your package, and neither<br><br>
  *MANIFEST.in*
  ```manifest.in
  include LICENSE
  include README
  ```
<br><br>

## **Publishing Your Packages**<br><br>
When you install packages using pip, you are normally downloading them from the python package index, known as PyPI. This is an online code repository, and anyone anywhere can upload packages to it. You just need to register for a free account. It can be tempting to wait until your package is fully finished and polished before releasing it. But releasing early, just as soon as it might be useful to someone, means you can get feedback and you might attract other people to help you develop it.<br><br>

1. **Distributions**
When you upload your package to PyPI you actually upload a package distribution. A distribution is just a bundled version of your code which is ready to be installed. There are two important kinds of distributions in Python. `Source distributions and wheel distributions`.
  - Source distributions are basically just the Python files you have written. To install this distribution the files must be downloaded and then the setup script is run.
  - A wheel distribution is a version of your package in a slightly processed format. It can be installed without running the setup script and so is faster for the user to install and is     usually smaller in size, so is faster to download as well. `The wheel distribution is the preferred Python distribution`, and pip will install a package using this when it is             available. However, when you upload distributions to PyPI, it is good practice to upload both the wheel and the source distribution.

1. **How to build distributions** <br><br>
You can build source and wheel distributions from the terminal using this command. `python setup.py sdist bdist_wheel`. You run the setup script and pass sdist to make the source distribution and bdist-wheel to make the wheel distribution. This will create a dist directory and add wheel and source distributions inside. It will also create build and egg-info directories, but you can ignore these.
<p align="center"><img src="https://github.com/user-attachments/assets/0d84fda3-7a93-4d44-83a9-48f367432d09" alt="dist" width="300"></p>

1. **Getting your package out there**<br><br>
Now that you have built your distributions the only thing left to do is upload them. You can do this from the terminal using twine. Twine is a tool specifically made for uploading packages to PyPI. Upload your distribution to PyPI `twine upload dist/*`. Upload your distribution to TestPyPI `twine upload -r testpypi dist/*`. Here we upload all the distributions in the dist directory. You can also upload your distributions to the Test-PyPI repository, which is a version of the PyPI repository made for testing. It's a good place to start. In order to upload, you'll first have to go to either PyPI or Test-PyPI to register for an account.<br><br>

1. **How other people can install your package**<br><br>
Once you've done this, your package is live and anyone can install it using PIP. It is also possible to install your package from Test-PyPI using a longer command. You specify the index-url which is where the package is downloaded from, and the extra-index-url which is where PIP can search for your dependency packages.<br><br>


## Testing Your Package

You have completed every step required to transform some loose code into a package hosted on PyPI. In this chapter we are going to focus on bringing your code up to an even higher standard. And the first step on this journey is testing.<br><br>

1. **The art and discipline of testing**<br><br>
When you are writing code, you will probably be performing small tests along the way to make sure it's working. Imagine you are writing this function to return the first and last element in a list. You might test it like this. This is the basic idea of testing, but in a good package, instead of just running this test once, you would save the code used to run this test. This means every time you make changes you can run all your tests again, to make sure your changes haven't broken anything.<br><br>

<p align="center"> <img src="https://github.com/user-attachments/assets/6c0f1a42-8725-489c-9643-52d6428f0cb0" alt="test" width="700"></p><br>

2. **Writing tests** <br><br>
Each function in your package should have a test function. Here the test function for get-ends is defined. It runs the get-ends function on a list and makes sure get-ends returns the correct answer. If get-ends returns the correct answer then the test function passes. If something is wrong with get-ends, then this test function raises an assertion error. You can also include multiple assert statements to test your function in different ways.<br><br>

  <table>
    <tr>
      <td><img src="https://github.com/user-attachments/assets/afb4a9e3-b2c1-4075-b2e2-0b6208060c5b" alt="test" width="400" /></td>
      <td><img src="https://github.com/user-attachments/assets/7598894e-e60d-436a-8b8d-ada76f4ef2a3" alt="test" width="400" /></td>
    </tr>
  </table>
  <br><br>

3. **Organizing tests inside your package** <br><br>
You should keep these tests in their own directory which is in the top folder of the package. The best way to lay out the tests directory is to copy the structure of the code directory. The test directory has an empty init file and the preprocessing subdirectory. Inside this subdirectory is the test-normalize module. The test-normalize module should contain all the tests for functions in the normalize module. Every other module in the code directory should have its own test module in the test directory.

<p align="center"> <img src="https://github.com/user-attachments/assets/8bad6a1d-b72c-4ea8-9391-7818a457ba2f" alt="organizing-directories" width="700"></p><br><br>

4. **Organizing a test module** <br><br>
Inside the test module, there should be a test function for each function defined in the source module. Remember that you will need to import the functions you are testing from the main package. This should be done using an absolute import. In this course we are only going to use these simple assert statements for testing, but if your package has more complex functions you will need more complex tests. If you'd like to learn more, you can take this great course on writing more complex tests here on DataCamp.

<p align="center"><img src="https://github.com/user-attachments/assets/fb2726b3-0312-4b16-991e-58ca45879f10" alt="assert-image" width="700"></p><br><br>

5. **Running tests with pytest** <br><br>
Once you have written these tests you can run them all at once using pytest. From the terminal all you need to do is navigate to the top of your directory, and then run the pytest command. Pytest will look inside the test directory, and search for all modules that start with test-underscore. Inside those modules it will look for all functions that start with test-underscore, and it will run these functions.If a test fails then pytest will highlight this so you can fix it.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/d94f0588-b83e-4888-b87e-cb4f6236c84a" alt="running-tests-with-pytest" width="700"></p>

## Testing your package with different environments
1. **Testing multiple versions of Python** <br><br>
But if you are trying to write a package which will work with multiple versions of Python, then you will need to test each version separately. This means `you will need to install the versions of Python you would like to support`, install your package and all of its dependencies within each Python version and run pytest. An easier way to test multiple Python versions, and the most common way, is to use a tool called tox.<br><br>
<P align="center"><img src="https://github.com/user-attachments/assets/9dbed3dc-4158-43ba-8645-578c54762bb2" alt="setup-tools" width="700"></P><br><br>

2. **What is tox?**<br><br>
Tox is a tool specifically built to run package tests with multiple versions of Python. You can run tox from the terminal, just like pytest.<br><br>

3. **Configure tox**<br><br>
In order to use tox, you need to create a configuration file telling tox what to run in each environment and also which Python versions to use. The configuration file must be named tox-dot-ini and needs to be placed in the top level of the package, alongside the setup-dot-py file.<br>
<p align="center"> <img src="https://github.com/user-attachments/assets/fb58dbfd-ddb8-43c3-b16e-8e8f7c955e4f" alt="config-tox" width="700"></p><br><br>


Inside the file you need to create the tox heading like this. You will then specify the versions of Python you want to test using the envlist parameter. Here we are testing python 2.7, 3.5, 3.6 and 3.7. You need to have these versions of Python already installed on your computer. Tox won't install new python versions. Using each of these versions of Python, tox will install your package and its dependencies. Under the testenv heading you need to tell tox what you want it to do once it has installed your package. You use the commands parameter to tell tox to run pytest. However, pytest isn't installed by your package dependencies, so you need to specify pytest as a tox dependency. You could actually add any commands you like to the commands list and tox will run them all. These need to be shell commands, which you could run from the terminal.<br>
<p align='center'><img src='https://github.com/user-attachments/assets/c8589511-3659-4501-9ccf-497692241d98' alt='tox.ini' width='700'></p><br><br>

4. **Running tox** <br><br>
To run tox, all you need to do is navigate to the top of your package and run the `tox` command.<br><br>
<p align='center'><img src='https://github.com/user-attachments/assets/7279d686-3ffd-4bd7-8241-3ede1f249fde' alt='running-tox' width='1000'></p>

<p align='center'><img src='https://github.com/user-attachments/assets/34019bb5-c4b5-42fd-b351-ddd8ebd3d728' alt='exercise' width='1000'></p>

<p align='center'><img src='https://github.com/user-attachments/assets/d6d5af41-275c-48d0-a400-4b5cfba1c80e' alt='exercise' width='1000'></p>

### Now, Run the `tox` command.

## Introducing flake8
Good code is read many more times than it is written, and so to help the reader, and yourself, we use the standard Python style guide, PEP8. This covers how variables and functions should be named, and generally how your code should be laid out. Following these conventions makes your code easier for others to understand and use. When developing code, it can be hard to spot bugs when you are writing it; that's why we use pytest. Similarly, it can be hard to spot every place where you have deviated in style; for this we use flake8.<br><br>

1. **Running flake8**<br><br>
Flake8 is a static code checker, which means it reads through your code without actually running it. Here we run flake8 from the terminal, passing it one of our modules to evaluate. It prints a series of style improvement suggestions. The output includes the file name, then the line number, then the character number of the violation, and a problem code and description.<br><br>

<table style="width:100%; text-align:center;">
  <tr>
    <td><img src="https://github.com/user-attachments/assets/539b952f-70c5-49b8-87fb-e43afd107aef" alt="flake8" width="700" height='250'></td>
    <td><img src="https://github.com/user-attachments/assets/9acf3d04-580d-4311-82f4-323eddfc9bfb" alt="flake8" width="700" height='250'></td>
  </tr>
</table>

If we make the suggested changes and run flake8 again, it prints nothing, meaning our code is stylish.

2. **Breaking the rules on purpose**<br><br>
Remember that PEP8 is only a guide, so you might bend these rules occasionally. For example, PEP8 says that after an equals sign, you should have only one space, but you might find that these two expressions. Become clearer if you add an additional space. If you made this choice, flake8 would notify you about it every time, which could get annoying. You can stop this by placing a noqa comment on the line. This stands for no quality-assurance. Now flake8 won't evaluate this line of code. If we include a violation code after noqa, then flake8 will evaluate the line but ignore this particular type of violation.<br>

<table style="width:100%; text-align:center;">
  <tr>
    <td><img src="https://github.com/user-attachments/assets/469a3a09-ca18-4376-88fc-dcd5b2ce765a" alt="image1" width="300"></td>
    <td><img src="https://github.com/user-attachments/assets/df25a1cb-4c05-48d2-aae7-7f1392ece332" alt="image2" width="300"></td>
    <td><img src="https://github.com/user-attachments/assets/7424d059-1d2d-4425-866f-61aaf34bcdc4" alt="image3" width="300"></td>

  </tr>
</table>
Blank Space before 6.

3. **flake8 settings**<br><br>
It is possible to ignore specific errors using flake8 without adding comments. For the previous case, we could use flake8's ignore flag and pass it a list of violation codes to ignore. Or if we only want to search for a specific set of violations, we can select those. Here we search for unused imports and variables.<br><br>


4. **Choosing package settings using `setup.cfg`** <br><br>
We can save these settings for flake8 by creating a setup-dot-cfg file in the package directory. In this config file, we create a section header for flake8 and then define the settings we want. For example, we'll ignore line spacing in all modules, and we will exclude setup-dot-py from being evaluated. We can also tell flake8 to ignore specific violations in particular files. Here we tell it to ignore extra spaces, but only in the main module of this example package. When we use flake8 inside our package, these settings will be used without us having to specify them.<br><br>

<table style="width:100%; text-align:center;">
  <tr>
    <td><img src="https://github.com/user-attachments/assets/4d2f7db1-9e6d-4010-835c-406d4dab61ea" alt="image1" width="500" height="300"></td>
    <td><img src="https://github.com/user-attachments/assets/68caf11f-c78e-448a-b01b-22470d16ea82" alt="image2" width="500" height="300"></td>
  </tr>
</table>


You can run flake8 on the whole package at once by navigating to the top of the package, and running flake8 from the terminal. You can run flake8 on the whole package at once by navigating to the top of the package, and running flake8 from the terminal.
<p align='center'><img src='https://github.com/user-attachments/assets/a10fe7fa-0551-4ec4-9b5f-ff329e7eb75c' alt='running-tox' width='1000'></p>


## Faster package development with templates
1. **Templates** <br><br>
As you've seen in earlier chapters, a Python package has a lot of additional files you need to write. Which means when starting from scratch there is a lot to remember, and fill in. Fortunately, you can use templates to do a lot of this work for you.<br><br>

2. **cookiecutter** <br><br>
Cookiecutter is a command line tool which creates projects from templates. You can use it to create a basic, empty Python package, like this one. These templates can create all of the additional files which your package needs, so you can focus more on the code, and won't need to worry you have forgotten something. You run cookiecutter from the terminal, and pass it the URL of the template you would like to use. The standard template for Python packages is this one. But there are lots more templates you can use choose from.<br><br>

```python
pip install cookiecutter https://github.com/audreyfeldroy/cookiecutter-pypackage.git
```
When you run this, it will ask you to fill in some details about the package you are creating. { *We also don't use a command-line interface, so we enter 3 to pick this option. We will include an author file, which is just a list of the package authors.* } cookiecutter creates a new directory with your package name, and fills it with all the files we have covered. Each of these files has good default content. Even the setup-dot-py file has been completely filled out. However, you may still want to make some edits. For example, here the README is a restructured text file rather than markdown. It also adds some extra files we will cover later, like the AUTHORS file, which lists the authors of the package and their contact details.
 


## Version numbers and history
1. **Final files**<br><br>
In the last lesson you saw that cookiecutter created these two new files, contributing and history.<br>

- The contributing file is either a markdown or reStructured-text file. This is your call out to other developers for help, and is the first place another developer will look if they are interested in assisting with your package. It is up to you what information you choose to include in this file. You might ask potential developers to join a mailing list, or to email you, or how they can get involved via Github. The standard contributing file which cookiecutter creates, is a great place to start, but you can change it if you'd like to send out a different message to potential collaborators.<br><br>
- The history file is really important for your users. In chapter two, we said that a package's history file is used to figure out which versions of a package will work with your package. There are different terms for this file, you might hear it being called the `history`, `change-log` or `release notes`, but they are all the same thing. The history file will tell your users the important things that have changed between the previous and new releases. This allows them to figure out which versions of your package they should use. <br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/be39f1f8-3100-4f3b-887d-51cbc7551eaf" alt="history" width="700"></p>

When you make changes, and are ready to make a new release, you will need to increase the version number. Only one copy of the package can be associated with each version number. So PyPI won't let you upload a copy with a version number you have used before. There are two places in the package where you must update the version number. The setup-dot-py file and the top level init-dot-py file.The version number in the setup file is used by pip and PyPI. The version number in the init file is included for the user, and it is best-practices to include this. It allows them to print and use the package version.

<p align="center"><img src="https://github.com/user-attachments/assets/f7d289f8-5eb6-462f-bcb3-6f1bc48946ee" alt="histroy" width="700"></p>

2. **bumpversion** <br><br>
These version numbers can be updated simultaneously using the simple bump-version tool. This tool is used from the terminal and will search through your package and increase the version number in appropriate places. You simply need to navigate to the top of your package and run bump-version with the argument major, minor or patch, and it will increase the major, minor or patch number.
`bump major` `bump minor` `bump patch`


3. **Makefiles and Classifiers**<br><br>
There are two last things you should know about before you start developing packages in the wild. Makefiles which will speed up your development, and classifiers which will help people find your package. Inside the setup-dot-py file you will notice that cookiecutter has filled in the classifiers parameter. This is a list of categories for each release of your package. Users on PyPI can search through packages, and filter based on classifiers. Like if they are looking for packages for Python 2, or with a particular license type. Here we have classified that the mysklearn package is currently intended for developers, and is in pre-alpha stage, meaning it's not ready to be used by general users. We state the type of license, the language used in the package, and the versions of Python it is compatible with. This package is for Python 3, so we add this classifier. We also add classifiers for the minor versions 3.6 to 3.8, since these are the specific versions of Python 3 that the package works with. There are lots more classifiers you can use for your package, but you should always include these as a minimum. You can see a full list of classifiers here.

<p align="center"><img src="https://github.com/user-attachments/assets/832cb9fa-e284-4336-8158-3719e908c9ff" alt="classifier" width="700"></p>

4. **What are Makefiles for?**<br><br>
You will notice that cookiecutter also created a Makefile from the template. Throughout this course you were using a lot of terminal commands. Sometimes these commands can be very repetitive, and sometimes hard to remember. Can you remember exactly what terminal commands you used to upload your distributions to PyPI? This is where the Makefile comes in. Makefiles are kind of like Python modules. You can write functions inside them, but these functions are used from the terminal. Inside the Makefile, cookiecutter has added a bunch of functions like this dist function. This function runs the setup-dot-py file to build source and wheel distributions for your package. There is also a clean-build function, which deletes the old distribution files so you can safely create new ones for a new release. There is also the test function, which simply runs pytest, and the release function which uploads your newest distributions to PyPI.

<p align="center"><img src="https://github.com/user-attachments/assets/532b5858-84e6-46f4-827a-0894ce973a5a" alt="makefile" width="700"></p>

5. **How do I use the Makefile?** <br><br>
You can use the makefile functions by navigating to the top of your package and using the command make followed by the function name.So to build new source and wheel distributions, you would type make dist into the terminal and run this.<br>

<p align="center"><img src="https://github.com/user-attachments/assets/33097568-416f-47c1-ae8e-2570d30d64f4" alt="makefile" width="700"></p><br><br>

You can also get a summary of the commands available in the Makefile by using the make `help command`. This lists the functions in the makefile as well as what they do.

### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/cf79d355-a78c-4c84-b05a-97adb2281a49" alt="exercise" width="1000"></p><br><br>

commands: `make clean` `make test` `make dist` <br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/9ceed602-a756-4c74-a502-d71b07ca1104" alt="recap" width="700"></p>

6. **Further topics**<br><br>
You already have the skills you need to start creating great packages, but at some point you will need to start writing more complex tests for your package. And for this, there is a great course right here on DataCamp that goes more in-depth than we could here. You also might want to create a website for your package documentation. Thanks to tools like sphinx and websites like read-the-docs, this is easy and free. You can find out more about this here.<br><br>

  - Advanced `pytest`
    -[Unit Testing for Data Science in Python](https://learn.datacamp.com/courses/unit-testing-for-data-science-in-python) 
  - Package Website
    -[ReadDocs and Sphinx](https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html) 
