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

- Being a good package developer means not reinventing packages that already exist. These extra packages that you use inside yours are the dependencies of your package. When someone else, or just you, tries to install your package, you need to make sure that they have these packages installed too.<br>

- To ensure that your users have the right packages installed, you can set the install-requires parameter inside the setup function of the setup script. Here you list the packages which your package depends on. Then when someone uses pip to install your package, pip will install these extra packages as well, unless the user already has them. These dependencies are updated often, and the version number changes. In this example, any version number of these packages is allowed.

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/30a1502d-355d-46ac-9c16-1c80d221b018" alt="setup.py" width="400"></td>
    <td><img src="https://github.com/user-attachments/assets/2c0b8199-d5cc-428d-8ce6-0e721fd27826" alt="setup.py" width="400"></td>
    <td><img src="https://github.com/user-attachments/assets/91e1c996-0a94-4a2a-bf48-4f9976ea9d21" alt="setup.py" width="400"></td>
  </tr>
</table>

