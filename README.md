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

