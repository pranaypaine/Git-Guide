# Git-Guide For Open Source Contributions

A collection of commands needed while working on git

##Common Terms
Some of the basic terms used while working with git are:
* *Fork*: This is how you make a copy of a project owned by someone else. A person or organisation. Apart from the owner of the repository, no one is allowed to make direct changes to the project. So fork is used to make a copy of the project that is owned by you.
* *Clone*: You got the project in your account, now what? A clone is just that, a copy. It does not care about ownership. It is aimed to bring the copy of the project hosted on github or any other VCS system in your machine. This is where you will make the changes and later update your remote project
* *Pull Request (PR)*: Pull Request or PR as it is generally known, is a method to contribute to open development projects by including bug fixes or adding new features. Its a way of contributing by asking the owner of project to include changes made in the external/forked repository.

##Set Up
In order to set up the user through terminal:

`git config --global user.name <name>` 

`git config --global user.email <email>` 

This is the user your commits and PR will be shown through.

##Fork, Clone, Add, Commit and Push
In order to work on an existing project that is not owned by you, follow the following steps:

1. `Fork` the project from the respective repository. This will redirect you to your fork of the project which is basically a copy of the original project but you are its owner.
2. Copy the HTTPS link of the project and go to the location through terminal or command prompt where you want to have the repository locally
3. Run `git clone <link to your fork>`. This will give you a local copy of the project which you can work with.
4. Any changes in the local repository can be tracked by running `git status` in that directory. Files in red will be the ones that have been modified, added or deleted.
5. To have your remote repository(the one hosted online also referred to as *origin*) reflect the changes, do 
`git add <file-path>` for all the files who's changes you wish to see in the remote. You can also run `git add .` to add all the files that have been changed (not advisable though).
6. Run `git status` once again and you will see the files that you have added in green.
7. In case you need to un-add any file, run `git reset HEAD -- <file path>`
8. To commit the changes (equivalent to locking down the changes you have made), run `git commit -m "Your commit message"`
9. So far you have made and saved the changes in your local repository, to send the changes to your fork in github, run
`git push` which will ask for your username and password. Fill and you are ready to go. 

  NOTE: This by default pushes all your local branches to remote with the same name. We will go through branching later.


##Setting up Upstream
When a repository is cloned, it has a default remote called `origin` that points to your fork on GitHub, not the original repository it was forked from. To keep track of the original repository, you should add another remote named `upstream`:

1. Open terminal or git bash in your local repository and type:

   `git remote add upstream <url of original project>`
  
1. Run `git remote -v` to check the status, you should see something like the following:

  > origin    https://github.com/YOUR_USERNAME/project-name.git (fetch)
  
  > origin    https://github.com/YOUR_USERNAME/project-name.git (push)
  
  > upstream  https://github.com/OWNER_USERNAME/project-name.git (fetch)
  
  > upstream  https://github.com/OWNER_USERNAME/project-name.git (push)

1. To update your local copy with remote changes, run the following:

   `git fetch upstream`

   `git merge upstream/master`

   This will give you an exact copy of the current remote, make sure you don't have any local changes.


##All About Branching

Branches exist in github to enable you to work on different features simultaneously without they interfering with each other and also to preserve the master branch. Usually the master branch of your project should be kept clean and no feature should be developed directly in the master branch.  Follow the following steps to create branches and be able to sync them:

1. Make sure you are in the master branch `git checkout master`.

2. Sync your copy `git pull`

3. Create a new branch with a meaningful name `git checkout -b branch_name`

4. Add the files you changed `git add file_name` (avoid using `git add .`)

5. Commit your changes `git commit -m "Message briefly explaining the feature"`

6. Push to your repo `git push origin branch-name`

This will push the changes you made to your fork on github under the branch name you gave. To have the owner of the original project review your changes, create a Pull Request explaining the changes you made. If it is satisfactory, it will be merged with the original project.

###Common Branch Commands:

  `git branch` will give you all the branches your local repository has.

  `git branch -a` will give you all the branches your local and remote repositories have

  `git branch -d the_local_branch` will delete a local branch that you had by the given name. Make sure you dont have any lose    ends in the branch or a delte won't be allowed.
   After deleting the local branch, if you wish to delete the remote branch of the same name, use:

  `git push origin :the_remote_branch` but be careful while using this.
  
##Squashing Commits

Often it is required while contributing that your entire feature change is in the form of one single commit.

##Disclaimer:
This guide is aimed particularly at people starting open source contribution for the first time and aims to familiarise them with required patterns and expected contribution behaviour.
