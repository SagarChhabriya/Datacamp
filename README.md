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
