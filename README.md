This README file serves as a landing page for the git-cmd-ref repository

This repo was created as a reference guide on using "git" written in a more user friendly way.
There's COMMAND --help for a more formal display of information of git.
Right now all the information added is from the Coursera course "Introduction to Git and GitHub".
All of this is done to become more familiar and remember the various commands on the journey to 
become a better programmer/coder.

********************
The online reference website can be found at:

www.git-scm.com/docs

********************


# PLAN OF ACTION
----------------

1 - Make records and references of git.

2 - Create an interactive Python script or program that displays information for the relevant 
    commands.
 
3 - Organise the repo on the go



# CURRENT CONFIGURATION
-----------------------

`git config --global --add user.email juliantjw@gmail.com`
`git config --global --add user.name Sti11itS`
`git config --global --add color.ui auto`



# LOCATION OF GIT CONFIG FILES AND THEIR PURPOSE
------------------------------------------------


### Git System Config File
`C:/Program Files/Git/etc/gitconfig`

### Git Global Config File
`C:/Users/Julian`

### Git Global Local File
`<repo_dir>/.git/config`

### The .gitignore file
`<repo_dir>/.gitignore`

echo <file> > .gitignore

- The .gitignore file specitifes intentionally untracked files that Git should ignore.
- Files already tracked by Git are not affected
- see online documentation


# BRANCHES AND MERGING
----------------------

### Branch

#### Basic Level Description

- A pointer (the HEAD) to a particular commit
- Represents an independent line of development of a repo project
- The default branch initialised for new repo is usually called
  "master". But now preferred to be called "main"

- Creating branches of the Main is for experimenting with different ideas
  and untested solutions before incorporating them into the Main branch
- This is to reduce the messiness and to keep the commit history and logs tidy
  and organised.
- By creating sub-branches new code and be written and tested before merging
  back into the Main branch.

- git add and git commit works as per normal to the current selected working branch
  which is selected by HEAD.
- When switching branches, the HEAD updates the working directory/tree and the commit log 
  history to reflect the snapshot of the new selected branch
- This means that if there were new files saved in the commit of the new branch, those 
  files and commit will disappear from the working directory/tree when the HEAD switches 
  to an old branch. When switching back to the new branch, they will be restored, or more
  accurately, to reflect the new branch's snapshot


### Merging

- To combine branched data and history together

- Uses two different algorithms to perform a merge:
  Fast-Forward and Three-way Merge

### Fast-Forward Merge

- All commits in the check-out branch are also in the branch that's 
  being merged. Meaning: The commit history does not diverge

### Three-way Merge

- Happens when the merging branches have diverged in someway
- Occurs when both branches have additional commits after the split
- To resolve, Git ties the branch histories together in a new commit. And merge
  the snapshots at the two branch tips with the most recent ancestor, the commit before
  the divergence. 
- Git will figure out how to combine both snapshots. If the difference is unique, all changes
  will be put together in the result.
- If changes in the same portion of "data" of both branches are detected, merge conflict
  will result.

- To resolve, the conflicted file will contain the code from both branches surrounded by merger 
  markers and you will need to edit the file and decide which lines of code to keep.
- Once done, git add the resolved file to mark the conflict has been resolved and git commit
  to wrap up the merge.
- The commit message will contain a description that it is merging the other branch.

SAMPLE Merge Conflict

```
def main():
<<<<<<< HEAD
    print("Start of program>>>>>>>")
=======
    print("End of program!")
>>>>>>> improvement-to-the-code

main()
```

- git log --graph --oneline to visually see the commit history of the branches



# GITHUB INTERACTIONS
---------------------

***************************************************************************
- New remote repositories can ONLY be made on GitHub itself
- Only then can push the local to the remote by following the instructions
***************************************************************************

- In Git, "origin" is a shorthand name for the remote repository that a project was originally
 cloned from. More precisely, it is used instead of that original repository's URL - and thereby 
 makes referencing much easier.
- Note that origin is by no means a "magical" name, but just a standard convention. Although it 
 makes sense to leave this convention untouched, you could perfectly rename it without 
 losing any functionality.

1 - Create blank <repo> on GitHub
2 - git remote add origin https://github.com/Sti11itS/<repo>.git
3 - git branch -M main
4 - git push -u origin main

