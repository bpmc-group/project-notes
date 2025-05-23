# Python Virtual Environments

## Intro

Python includes the capability to create Virtual Environments (venv). This feature allows you to specify configurations without impacting other environments. The most common reason for doing this is allow you to set up different projects differntly. For example, "old-project" could be setup to run on python v3.8 with django v4.8 and "new-project" setup to run on python v3.13 with django v5.11. Another good use would be to verify that your code is compatible with the python versions your code should support.

## Creating Virtual Env's Using Anaconda

Anaconda is a front end for 'conda', a config system management system. Anaconda Navigator displays a variety of tools that you can use, including Jupyter Notebook and Jupyter Labs(a multi-tabbed version of Jupyter Notebook). It also includes PyCharm and it's own AI interface plus lots more. For the CV project, more importantly, it provides simpler access to virtual envs. You name an environment and then switch to its terminal view, and then use pip to install the desired python software libraries. The biggest advantage over python's venv is that each env that you create in Anaconda automatically lists all of the libraries and their versions. This means that you don't have to worry that you forgot to install Ultralytics or numpy - you can just look at the list to verify it is installed. It also displays the version of each library, so you can tell if one is out of date.

### Creating Anaconda's Virtual Env and Installing Libraries

Anaconda seems to automatically tell VS Code that Code's terminal window should come up in the (base) env. The (base) env is huge, ready for almost everything except CV. And you cannot clone it and use it as a baseline for your env. Instead, set up a new env for OpenCV, do as follows:

1. Click on the Environments button on the left side of the screen. 
1. Click on the Create button at the bottom of the screen.
1. Select the desired version of Python. Either version 3.12 or 3.13 are probably best; if some libraries are lagging behind you may have select an older version for compatibility.
1. When it is done grinding away creating the new env, click on the Rt-Arrow thingie and select "Terminal Window".
1. In the terminal window, type `pip install opencv-contrib-python`
1. Next type `pip install ultralytics`
1. Next type `pip install matplotlib`
1. Next type `pip install pandas`
1. Install any other libraries that are needed by an app that you are creating or using in your env.

### Using Anaconda's Virtual Env

1. If your VS Code terminal opens with a different env declared, type the following: `deactivate`  This will deactivate the unwanted env.
1. If your VS Code terminal window opens with (base) declared, type the following: `conda deactivate`  This will deactivate the (base) env.
1. Type `conda activate <desired env name>` This will load the desired env. 

It may seem like just telling the terminal to activate the desired env is good enough, but there has been some evidence that the envs will just stack on top of previous ones, meaning that the combined envs may not always be the same, leading to unpredictable results. For reliable results, it is best to deactivate any previous envs before activating the desired env.

## Creating Virtual Env's Using venv

The basic procedure to create a virtual environment is as follows:

1.  Change to the project-related folder where you want to create the new environment
1.  Type in `python -m venv <name of virtual environment to make>`
1.  It will process for a few moments while it creates the necessary folders and copies in the files needed for the virtual environment.
1.  You need to activate the virtual environment before you can use it. In Windows, the command is as follows:
    1.  PowerShell: `<new virt env name>\Scripts\Activate.ps1`
    1.  DOS CMD: `<new virt env name>\Scripts\activate`
1.  The terminal/CMD window will now have the name of your environment at the beginning of each command line.  ![Virtual Enviroment (py312) shows on command line](img/VirtualEnvironmentActive.png)
1.  Use python and django as you normally would.
1.  When you are done with the virtual environment, you should deactivate it by typing `deactivate` (no path required)

## Using Virtual Environments and VS Code

VS Code with Python extensions installed seems very aware of virtual environments and **may** open the desired when you open a terminal window. There are probably configuration options or config scripts buried inside VS Code that can affect which venv is installed.

However the following procedure can be used to ensure the desired venv is used by VS Code terminal windows.

1.  Exit all terminal windows in VS Code
1.  Exit VS Code
1.  In a windows PowerShell terminal or Windows CMD window, activate the desired venv
1.  Once it has been activated, start VS Code the way you normally start it.
1.  Open a new terminal window and verify the desired venv is active by running the appropriate version commands. For example:

```
py --version
    
django-admin --version
```

Use other commands as necessary to verify that the desired venv has been activated.
