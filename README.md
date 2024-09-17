# projectnotes
This "repository" contains helps, hints, and guides for working together on this project.

## VS Code To Access Remote Hosts
Your local copy of VS Code can be used to access remote hosts. After installing the Remote SSH extension, you can click on the >< blue icon button in the lower left corner of the screen and log into servers. This is useful if you need to edit a file on the remote system, for example, a config file or, using the terminal window, to stop a running app or restart one.

Once the Remote SSH extension pack is installed:

1.  Click on >< button in lower left corner.
1.  From the pop-up list, click on the "Connect to Host . . . Remote-SSH"
1.  Type in <username>@<host-name> and press Enter
1.  The first time it will ask what kind of system it is and give you a few options. Mark's non-google system will usually be Linux. 
1.  A new VS Code window will popup over the original VS Code window.
1.  When it asks, type in your <password>
1.  At this point you are connected to the remote server. You can open files, edit them, and save them on the remote server.
1.  If you open a new terminal window, the terminal will be inside the host that you connected to. This is where you could issue commands to start or stop a process on the host computer.

1.  WHEN DONE:
1.  Click the >< button in lower left
1.  From the popup list, select Close Remote Connection at the bottom
1.  VS Code returns to local mode.

NOTE: When the remote VS Code window is opened, you can close the original VS Code window.


## Github
### Download repository from github:

`git clone https://github.com/bpmc-group/<project name>.git`

Your clone of the repository doesn't affect anyone else's work and you can delete it at any time without affecting the repository. You can even have multiple clones of the repository as long as their folders are under different folders. For example: c:\python\AAA\bpmc vs c:\python\BBB\bpmc 

### Check status of your clone
Find out which files you have changed locally and if any of the files in your local clone are out of date compared to the repository (you must be in your cloned folder):

`git status`

### Update the Repository
#### Stage your changes
When you have changes you might want to save retain, to prepare for a commit:

`git add .` or `git add <filename>`

Doing `git add .` will get every changed file starting with the local folder ('.'). If you only want to stage one or several files, do `git add <filename>`.

You can "un-stage" files and DISCARD your changes, do:

`git restore <filename>`

#### Commit your changes
When you are ready to keep your changes,you need to commit them as follows:

`git commit -m "<Description of changes>`

The description of the changes should be exactly as long and as detailed as you feel is necessary. It can be short ("bug 123") or it can be long ("Interaction of module 1 and module 2 failed intermittently when accessed under the following conditions...."). Just be sure to enclose the description in double-quotes.
#### Push your changes into the Repository
When you are ready to insert your changes back into the repository, do the following:

`git status`   (to verify that your changes are made against an up to date local version of the repository. See Resolving below).

`git push`   (to insert your changes in the main branch of the repository).

In advanced repositories with multiple branches, the push command can use many additional options and settings, but to get started `git push` should be enough.

#### Resolving Differences
If you discover that your local repository is out of date, you can do one of two commands: `git fetch` and `git pull`. 

*   Fetch is supposed to be lighter weight and only copies the changes from the repository. Fetch is perfect if some other modules have been changed than those you are working on.
*   Pull is appropriate if the remote changes affect the code you have been working on. Pull acts like a combination of `git merge` and `git fetch`. In the merge process, git will incorporate the changes anywhere that it believes that it can do the changes safely. When it can't it stops and tells you where it is having problem and requires you to resolve the differences manually.
*   Always rerun your tests with the incorporated changes to verify correct operation of the project.

### How Often to Update the Repository
There are many opinions about how often to push your changes, ranging from several times a day to rarely (when completely finished polishing the code). Probably the most pragmatic option is to push any time your code is good enough that if your local system died at that moment you would have to *work* to recreate the changes. 

For example, if you just ran a formatter that set all of your tabs to 8 spaces or added a couple of comments, etc, if you had to do those over again, it probably wouldn't be a big problems. However, if you just created a new function or figured out a tricky bug fix, those are probably worth pushing to the repository.

It's also important to remember that changes can be rolled back in the repository to previous versions. A repository is a living thing that changes over time.

### Git Branches
When a project gets relatively stable or in production or during a code/feature freeze, someone might want to add a new feature or improve functionality. Instead of incorporating the changes into the main branch, a new branch might be added to handle all of the changes and additions. Typically branch changes are all interconnected and should all go in at once.

One example might be a new ways of accessing the database (or a different database). A new branch can hold all of these changes away from the main branch until the changes are all worked out. When the branch is ready for use, the whole branch can be merged into main.

### Git Review Processes
When a project is fairly mature or there are more than a handful of developers, it is time to consider implementing a formal review process. 

GitHub offers a workflow that could be incorporated. 

Another method is for a user to "fork" the repository and make a pull request against that fork. Next, make all their changes to their fork. Then, when their changes are pushed to the repository, they have to be reviewed and accepted by someone with the proper privileges. This method is commonly used on public repositories when someone outside of the project wants to make an update to the code. The developers inside the project can decide if the forked changes are appropriate for their project.