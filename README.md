# Git/Github Tutorial
Download Git: [http://git-scm.com/downloads](http://git-scm.com/downloads)

Set up Git: [https://help.github.com/articles/set-up-git/](http://git-scm.com/downloads)

Use `cd` to navigate to your project’s directory 

Copy **git-publish** a place that is accessible via your path. Run `echo $PATH` to see a list of all folders in your path. You only need to place the git-publish script in one of them.
I like to use ~/bin (“~” means my home directory).

#### On Windows
You can create a folder called “bin” in your **%HOMEPATH%** and copy the git-publish script there.

Now restart your bash console (close it and re-open it).

Type `git publish` to see if it runs. You should get a message like “Error - You do not appear to be on a branch to publish from, please check with 'git branch’”. That’s fine for now.

## Our first project
Lets make our first git project. Make a new folder called **firstgit** and use `cd` to navigate to it in your bash shell.

Run `git init` to initialize git in the current directory.

Make a new file, make a new branch, commit the file to the new branch. Go back to **master**, and the file has disappeared! 

## Publish a Git Project to GitHub

To publish a folder to github, you have to tell git where you want to publish to. You need to [add a remote branch](https://help.github.com/articles/adding-a-remote/).

Now make your commit and simply run `git publish` to publish your files to GitHub.


## Simple Git Workflow

Work on a branch that’s not **master**. Add your changed files. Commit some things. Then  when you’re happy, publish your branch.

```git checkout -b dev # go to branch (**-b** = create one if it doesn’t exist).
#git add . # add all files in the current directory
git add README.md # add README.md to be committed
git commit -m “my commit message” # commit your file state
git publish
```

## Helpful links
* [Interactive Git Tutorial](http://pcottle.github.io/learnGitBranching/) - A great visualization of what is happening as you work with git

#### A note on git publish for the curious
What git publish does is simplify a few common tasks in a typical git workflow.
Really git publish is doing the following from your current branch, say **dev** in this example:
```git checkout master # go to master branch
git fetch # get the latest updates from the server
git checkout dev # go back to dev
git rebase master # rebase with master
git checkout master
git merge dev
git push
```
However, `git fetch` is instead a combination of `git remote update -p` and `git merge --ff-only @{u}` written as fetch here for simplicity of understanding. These two commands used together helps keep the commit history clean of “Merge branch ‘master’ of ….”
