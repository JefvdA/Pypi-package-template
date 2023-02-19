# <u>Pypi package template</u>
This is a template for pypi packages.

Default this comes with a MIT licence.

## <u>Before you start</u>
Add your package's source code to the "src" directory.

Make sure to change your project's info in the [setup](setup.cfg) file!

## <u>Building your package</u>
To build your package you will need to install build with pip.

### Install pip:
#### Windows:
Download the [get-pip.py](https://bootstrap.pypa.io/get-pip.py) file, then execute this python script, which will install pip for you.

#### Linux (apt):
For python3:
```bash
sudo apt update
sudo apt install python3-pip
```

For python2:
```bash
sudo apt update
sudo apt install python-pip
```

### Install build:
Now that pip has been installed, we can use it to install build:

```bash
pip install build
```

Now that build is installed, we can build our package:
```bash
python3 -m build
```
This will generate a source archive (tar.gz) and a build distribution (.whl) in the directory "dist". These are the files we want to upload to the registery.

## <u>Publishing your package</u>
To upload our package to the pypi registery, we will need twine:

```bash
pip install twine
```

Now that twine is installed, we can finally publish our package.

Follow the next steps for uploading your package to PyPi, but it might be smart to try [TestPyPi](#testpypi) first, as this is a registery like PyPi made for testing and experimenting.

### PyPi
As PyPi is twine's default registery, it's a pretty simple command that we need:
```bash
python3 -m twine upload dist/*
```
This command will ask for your credentials (username and password), you need to log in before uploading. You can create an account [here](https://pypi.org/account/register/).

Click [here](#importing-the-package) to see how you can install and use your package in another python project.

### TestPyPi
As TestPyPi is not twine's default registery, we need to specify the registery we want to use in the command:
```bash
python3 -m twine upload --repository testpypi dist/*
```

This command will ask for your credentials (username and password), you need to log in before uploading. Be aware, TestPyPi uses it's own servers, and you need a different account then for PyPi. You can create a TestPyPi account [here](https://test.pypi.org/account/register/).

Click [here](#importing-the-package) to see how you can install and use your package in another python project.

## <u>Importing your package</u>
Now that your package is uploaded to the python registery, you can install it with pip, and use it in other python projects.

### Install from PyPi
As PyPi is pip's default registery, we don't need to specify it, use following command to install a pip package (ofcourse, change [package name] to the name of your own package):
```bash
pip install [package name]
```

### Install from TestPyPi
As TestPyPi is not pip's default registery, we need to specify that we're using it, use following command to install a pip package (ofcourse, change [package name] to the name of your own package):
```bash
pip install -i https://test.pypi.org/simple/ [package name]
```

### Importing the package
Now that we have successfully installed our pip package, we can move on.

If you are not sure, you can get a list of all currently installed pip packages with following command:
```bash
pip list
```

Now you can import the package in another python module like this:
```python
from example_package import example

example.add_one(4) # This will return 5
```
*This example package is used as example on how to import above*

Be aware, after from doesn't come the name of the package, it is the name of a module specified in the [src](./src/) directory.

## <u>Good luck</u>
I don't know who will ever read this, but if you are reading this now, thank you!

I wish you good luck on your next coding adventures, and hope you will one day create an amazing pip package!

@2022 Jef van der Avoirt
