# Utilizing Github Pages to host a static site/app

This is a quick guide to hosting your site or app on Github Pages. Mostly, it covers getting started with git. It's by no means a complete guide to using git or a workflow for developing an app, just the bare minimum to take an html/css/js project and get it hosted, for free, on Github Pages.

If you're already familiar with git, here's the TL;DR:

* create a gh-pages branch
* push it to github
* your app is now live at `http://username.github.io/repo-name`

## install git

### windows

* Download from [http://git-scm.com/downloads](http://git-scm.com/downloads)

### mac

* install [homebrew ](http://brew.sh/) (scroll to bottom for install instructions)
* open terminal
* run `brew install git`

From here out, when i say 'command line', for mac I mean Terminal, for windows I mean Git Bash (which will have been installed along with git). I'll put commands like so:

```
> some command
> another command
```

The `>` represents the prompt, don't type that. Each `>` starts a new command. You type the command, then hit enter. For the above you would type `some command`, hit enter, type `another command`, hit enter.

## set up ssh keys

This helps authenticate you when pushing to or pulling from github.

* follow these instructions for your OS: [https://help.github.com/articles/generating-ssh-keys](https://help.github.com/articles/generating-ssh-keys)
* ignore the bit about using github's native app

## set up your code

### create a directory for your code

Name it something to do with the app or site you're creating. If it's a Todo list app, could just be 'todo'

### add some files

Add an `index.html` and put some boilerplate in it (doctype, head, body, some simple content)

Add a file name `.gitignore` with the following contents:

```
.DS_Store
tmp
*.log
```

There are some files you don't want or need committed to your git repo. This ensures they are ignored by git.

### on the command line, go to the directory using the `cd` command:

On windows, this might look like:

```
> cd C:\Users\username\Dev\my-app
```

On a mac, it might look like:

```
> cd ~/Dev/my-app
```

### run the following on the command line:

```
> git init
> git checkout -b gh-pages
> git add .
> git commit -m "initial commit"
```

## set up a git repo on github and push your code to it

* Log into github, click the `+` in the top right and choose 'New Repository'.
* Make the repository name the same as the directory you created for your code.
* Ignore the rest of the options and click the 'Create repository' button.

## send your code to github

Run the following, but change `username` and `my-app`:

```
> git remote add origin https://github.com/username/my-app.git
> git push -u origin gh-pages
```

## your app is live!

You should be able to go to `http://username.github.io/my-app` and see your app live and public on the internet. It may take a minute between pushing and seeing it live.


## continue working on your app

Add files and code to your project. After you've made a change you want to deploy to github, run the following:

```
> git add .
> git commit -m "message about what i changed"
> git push
```