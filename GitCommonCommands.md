# Git Common Codes

## Download repository from github:

    git clone https://github.com/bpmc-group/<project name>.git

Your clone of the repository doesn't affect anyone else's work and you can delete your clone at any time without affecting the repository. You can even have multiple clones of the repository as long as their folders are under different folders. For example: c:\python\AAA\bpmc vs c:\python\BBB\bpmc 

## Check status of your clone
Find out which files you have changed locally and if any of the files in your local clone are out of date compared to the repository (you must be in your cloned folder):

    git status

See Resolving Differences section if your local clone is out of date with the repository.

If this command shows files that you don't want included in the main repository, such as db.sqlite3 or temp files, look for the hidden file .gitignore (create it if required). This file specifies intentionally untracked files that Git should ignore. Each line in a gitignore file specifies a pattern, such as 

    db.sqlite3
    *.pyc 

You may have to modify the settings in Windows Explorer to have it display hidden files.

## Update the Repository

### Stage your changes
When you have changes you might want to save retain, to prepare for a commit:

`git add .` or `git add <filename>`

Doing `git add .` will get every changed file starting with the local folder ('.'). If you only want to stage one or several files, do `git add <filename [filenames]>`.

### Unstage your changes

You can "un-stage" files and **keep** your changes (you weren't ready to stage a file or accidentally added a file you don't want in the repository) with:

    git restore --staged <filename>

### Commit your changes
When you are ready to keep your changes,you need to commit them as follows:

`git commit -m "<Description of changes>`

The description of the changes should be exactly as long and as detailed as you feel is necessary. It can be short ("bug 123") or it can be long ("Interaction of module 1 and module 2 failed intermittently when accessed under the following conditions...."). Just be sure to enclose the description in double-quotes.

### Push your changes into the Repository
When you are ready to insert your changes back into the repository, do the following:

`git status`   (to verify that your changes are made against an up to date local version of the repository. See Resolving below).

`git push`   (to insert your changes in the main branch of the repository).

In advanced repositories with multiple branches, the push command can use many additional options and settings, but to get started `git push` should be enough.

## Resolving Differences
If you discover that your local repository is out of date, you can do one of two commands: `git fetch` and `git pull`. 

*   Fetch is supposed to be lighter weight and only copies the changes from the repository. Fetch is perfect if some other modules have been changed than those you are working on.
*   Pull is appropriate if the remote changes affect the code you have been working on. Pull acts like a combination of `git merge` and `git fetch`. In the merge process, git will incorporate the changes anywhere that it believes that it can do the changes safely. When it can't, git stops and tells you where it is having problem and requires you to resolve the differences manually.
*   Always rerun your tests with the incorporated changes to verify correct operation of the project.

## How Often to Update the Repository
There are many opinions about how often to push your changes, ranging from several times a day to rarely (when completely finished polishing the code). Probably the most pragmatic option is to push any time your code is good enough that if your local system died at that moment you would have to **work** to recreate the changes. 

For example, if you just ran a formatter that set all of your tabs to 8 spaces or added a couple of comments, etc, if you had to do those over again, it probably wouldn't be a big problems. However, if you just created a new function or figured out a tricky bug fix, those are probably worth pushing to the repository.

It's also important to remember that changes can be rolled back in the repository to previous versions. A repository is a living thing that changes over time.

## Git Branches
When a project gets relatively stable or in production or during a code/feature freeze, someone might want to add a new feature or improve functionality. Instead of incorporating the changes directly into the main branch, a new branch might be added to handle all of the changes and additions. Typically branch changes are all interconnected and should all go in at once.

One example might be a new ways of accessing the database (or a different database). A new branch can hold all of these changes away from the main branch until the changes are all worked out. When the branch is ready for use, the whole branch can be merged into main.

## Git Review Processes
When a project is fairly mature or there are more than a handful of developers, it is time to consider implementing a formal review process. 

The standard git review process is done as follows: 

1.  A user will "fork" the repository 
2.  The user makes a pull request against that fork
3.  The user makes all of their changes to their fork
4.  When the user has made all of their changes, they are pushed to their fork.
1.  The forked repository must be reviewed and accepted by someone with the proper privileges. 

This method is commonly used on public repositories when someone outside of the project wants to make an update to the code. The developers inside the project can decide if the forked changes are appropriate for their project.