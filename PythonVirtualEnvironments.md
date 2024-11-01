= Python Virtual Environments

== Intro

Python includes the capability to create Virtual Environments (venv). This feature allows you to specify configurations without impacting other environments. The most common reason for doing this is allow you to set up different projects differntly. For example, "old-project" could be setup to run on python v3.8 with django v4.8 and "new-project" setup to run on python v3.13 with django v5.11. Another good use would be to verify that your code is compatible with the python versions your code should support.

== Creating and Using venv

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

== Using Virtual Environments and VS Code

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
