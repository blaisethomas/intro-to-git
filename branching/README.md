

#Git Branches and Github Pages Deployment


####SWBAT:

* Understand how to create, move across and merge branches on local repos

	* `$ git branch`
	* `$ git checkout`
	* `$ git merge`
* Deploy using Github Pages




---

#`$ git branch`


A branch represents an independent line of development. Branches serve as an abstraction for the edit/stage/commit process. You can think of them as a way to request a brand new working directory, staging area, and project history. New commits are recorded in the history for the current branch, which results in a fork in the history of the project.

The git branch command lets you create, list, rename, and delete branches. It doesn’t let you switch between branches or put a forked history back together again. For this reason, git branch is tightly integrated with the git checkout and git merge commands.

Everytime you create a new branch, it duplicates the exisiting code, in the state in which it is in on your current branch. To avoid confusion, working directory and staging area must be clean.


#####Usages

`$ git branch`

List all of the branches in your repository.

`$ git branch <branch>`

Create a new branch called <branch>. This does not check out the new branch. (always try to name your branches after the feature you are trying to implement) 

`$ git branch -d <branch>`

Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.

---


#`$ git checkout`

The git checkout command lets you navigate between the branches created by git branch. Checking out a branch updates the files in the working directory to match the version stored in that branch, and it tells Git to record all new commits on that branch. Think of it as a way to select which line of development you’re working on.


#####Usage

`$ git checkout <existing branch>`

#####Create and checkout a new branch in one command:

`$ git checkout -b footer`

---


### Cool? Easy? 
####There's a catch! - a lightly illogical and nasty one.

NB: You must **always** stage and commit all changes to a branch before checking out to a new branch; else git will see these changes as global and might carry them across branches.

**You must always stage and commit all changes to a branch before checking out** EVEN if you dont want to keep them

**ESPECIALLY** if you don't want to keep them

---

One more note on checkouts : 

We can also checkout to any previous commit. This will put us in a state known as detached head. This is OK if looking but DO NOT do any further development in detached head.




---

#`$ git merge`

Merging is Git's way of putting a forked history back together again. The git merge command lets you take the independent lines of development created by git branch and integrate them into a single branch.

Note that all of the commands presented below merge into the current branch. The current branch will be updated to reflect the merge, but the target branch will be completely unaffected. Again, this means that git merge is often used in conjunction with git checkout for selecting the current branch and git branch -d for deleting the obsolete target branch.

#####Usage

`$ git merge <branch>`

Merge the specified branch into the current branch. Git will determine the merge algorithm automatically.


--- 

Congratulations! You have succesfully branched, checked-out and merged code, across branches. Time to get some practice. There is a lot going on under the hood here. [Atlassian git guide](https://www.atlassian.com/git/tutorials/using-branches) is a fantastic resource for furthuring your understanding. 

----

#Github Pages

###In class lab

Now you have had some good practise at branching and merging - its time to deploy using github pages. 

This will be achieved by following the appropriate [documentation](https://pages.github.com/) 

Its super easy and basically all that needs to happen is the creation of a new branch called `gh-pages` and push it to github. Providing there is an index.html in your root directory, of your gh-pages branch you can then navigate to `http://username.github.io/repository-name` to view the rendered html. You can also point a new domain name to this URL hence giving you a fully deployed project, with custom URL. 

---


#Recommended workflow with branching


`git init`

`git branch <branchname>`
`git checkout <branchname>` 

( or `git checkout -b <branchname>` )

---

Then write your code on that branch. `add` and `commit` as usual on this branch

`git add <as appropriate>`

`git commit -m "<first commit>"`

---

When this feature is built, merge code back to master:

`git checkout master`

`git merge <branchname>`

---

Want to connect up a remote repo?

`git remote add origin <https url>`

`git push -u origin master`










