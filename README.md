This README file serves as a landing page for the git-cmd-ref repository

This repo was created as a reference guide on using "git" written in a more user friendly way.
There's COMMAND --help for a more formal display of information of git.
Right now all the information added is from the Coursera course "Introduction to Git and GitHub".
All of this is done to become more familiar and remember the various commands on the journey to 
become a better programmer/coder.

********************
The online reference website for GIT can be found at:
www.git-scm.com/docs

For using GitHub
https://docs.github.com/en

For Markdown file types like this README.md:
https://guides.github.com/features/mastering-markdown/
https://docs.github.com/en/github/writing-on-github

********************


# PLAN OF ACTION

1. Make records and references of git.
2. Create an interactive Python script or program that displays information for the relevant 
   commands.
3. Organise the repo on the go


# CURRENT CONFIGURATION

    git config --global --add user.email juliantjw@gmail.com
    git config --global --add user.name Sti11itS
    git config --global --add color.ui auto


# LOCATION OF GIT CONFIG FILES AND THEIR PURPOSE

### Git System Config File
| Linux | Windows |
|:-----:|:-------:|
| `[path]/etc/gitconfig` | `C:/Program Files/Git/etc/gitconfig` |

### Git Global Config File
| Linux | Windows |
|:-----:|:-------:|
| `~/.gitconfig` | `C:/Users/Julian` |

### Git Global Local File
| Linux | Windows |
|:-----:|:-------:|
| `<repo_dir>/.git/config` | `<repo_dir>/.git/config` |

### The .gitignore file
`<repo_dir>/.gitignore`

echo \<file> > .gitignore

- The .gitignore file specitifes intentionally untracked files that Git should ignore.
- Files already tracked by Git are not affected
- see online documentation


# BRANCHES AND MERGING

## Branch

### Basic Level Description

- A pointer (the `HEAD`) to a particular commit
- Represents an independent line of development of a repo project
- The default branch initialised for new repo is usually called
  "master". But now preferred to be called "main"

- Creating branches of the `Main` is for experimenting with different ideas
  and untested solutions before incorporating them into the Main branch
- This is to reduce the messiness and to keep the commit history and logs tidy
  and organised.
- By creating sub-branches new code and be written and tested before merging
  back into the Main branch.

- `git add` and `git commit` works as per normal to the current selected working branch
  which is selected by `HEAD`.
- When switching branches, the `HEAD` updates the working directory/tree and the commit log 
  history to reflect the snapshot of the new selected branch
- This means that if there were new files saved in the commit of the new branch, those 
  files and commit will disappear from the working directory/tree when the `HEAD` switches 
  to an old branch. When switching back to the new branch, they will be restored, or more
  accurately, to reflect the new branch's snapshot


## Merging

- To combine branched data and history together
- Pull / Merge / Push workflow
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

###### SAMPLE Merge Conflict

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


## Rebasing Your Changes

- In a large project with a large team of developers, naturally there will be multiple
  repo branches containing changes or additions of code. 
- Use `git rebase <ref_branch>` to update the `<current_branch>` to have the latest commit possible
  from `<ref_branch>`.
  - Change the base of the `<current_branch>` to be `<ref_branch>`.
- Helps to make debugging easier and prevents three-way merges by transferring completed work
  from one branch to another
- Rather than using `git merge` and performing a three-way merge, rebasing rewrites commit history
  and maintains linearity, making for cleaner code.
  - Fetch / Rebase / Push workflow


```
          A---B---C topic
         /
    D---E---F---G master
```
```
git rebase master
git rebase master topic
```
```
                  A'--B'--C' topic
                 /
    D---E---F---G master
```

### Git Rebase Interactive `git rebase -i <branch>`

- Shows a list of possible actions to commits made if edits are required
- Use this command to combine commits. There are two methods to combine
  - Squash: use commit, but meld into previous commit
  - Fixup: like 'squash' but discard this commit's log message
  - Both operate the same but the difference is the commit message


## Best Practices for Collaboration

- Synchronize your branches before starting any work on your own.
- Try and avoid having very large changes that modify a lot of different things.
- When working on a big change, it makes sense to have a separate feature branch.
- Regularly merge changes made on the master branch back onto the feature branch.
- Have the latest version of the project in the master branch and a stable version of the 
  project on a separate branch.
- You shouldn't rebase changes that have been pushed to remote repos.
- Having good commit messages is important.


# GITHUB INTERACTIONS

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

1. Create blank `<repo>` on GitHub
2. git remote add origin `https://github.com/Sti11itS/<repo>`.git
3. git branch -M main
4. git push -u origin main

## Forking and Pull Request

### Forking
- A way of creating a copy of the given repository so that it belongs to our user on GitHub.

### Pull Request
- A commit or series of commits that you send to the owner of the repository so that they
  incorporate it into their tree.
- Repositories belong to other people are usually commit-protected to prevent unwanted commit
  changes. Reasons are obvious
- Any commit changes performed on the forked repo are saved on a new branch 
  "patch-#" automatically created by GitHub.
- Only then the Pull Request on the original repository can be performed. This informs 
  the original repo owner about the proposed changes

## Code Review

- Request, or create, a style guide for the project.
- Respond to Pull Requests ASAP when possible, especially when making comments.
- If you're a project maintainer, it's important that you are reply promptly to pull 
  requests and don't let them stagnate. The more time that passes until a pull request 
  gets reviewed, the more likely it is that there's a new commit that causes a conflict 
  when you try to merge in the change.
- if it's an open source project that volunteers are contributing to is that it's 
  important that you understand any changes you accept. You never know if the other person 
  is going to stick around to maintain the code after you merge it in so you better make 
  sure you can do that.

### Tracking Issues

- When it comes to coordinating who does what and when, a common strategy for active 
  software projects is to use an issue tracker (or bug tracker).
- It's built-in at GitHub. Third-party examples include Bugzilla.

### Continuous Integration / Continuous Delivery System (CI/CD)

- We can write automated tests to test the code for us and then use a continuous 
  integration or CI system to run those tests automatically.
- Will build and test our code everytime there's a change.
- Once we have our code automatically built and tested, the next automation step 
  is continuous deployment which is sometimes called Continuous Delivery or CD. 
- **Pipeline** - Specify the steps that need to run to get the result you want.
- **Artifacts** - The name used to describe any files that are generated as part of
  the pipeline.

- Make sure the authorized entities for the test servers are not the same entities 
  authorized to deploy on the production servers.
- Always have a plan to recover your access in case your pipeline gets compromised.
