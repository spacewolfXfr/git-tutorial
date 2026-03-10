# Git basic training

You have here the instructions for our tutorial.

All Git commands are of the form `git <verb> <arguments>`. We will see in this tutorial the main verbs (or sub-commands).
The first you should learn is `help`: typing `git help` will give you an overview of the main Git commands. Typing `git help <verb>` (or `git <verb> --help`) will give you specific details about the associated sub-command.

If it is your first time ever using Git, you will have to configure your identity by running the following commands:

```sh
git config --global user.name "Your Name Comes Here"
git config --global user.email you@yourdomain.example.com
```

They respectively register your name and email, which are required when making changes: one must know who is responsible for adding great content ! (or screwing everything up...)

Now that you are ready, lets clone the repository we will use for this tutorial.

## Getting the repo

Clone the repository from GitHub:
```sh
git clone git@github.com:spacewolfXfr/git-tutorial.git
```
Check that everything is alright by typing
```sh
git status
```
You should do that regularly to inspect the state of your *working directory*, *staging area* and *repository*.

The file you will be working on are in the `Lab` folder. Initially, it contains:

- `drones.md` : list of all drones
- `components.md` : the components available in the workshop
- `cobra.md`,`zagi.md` : two drones we have here at the lab

You can also take a look at what changes were done up to this point by typing:
```sh
git log
```
(This is mostly to show what can be done from the command line... A GUI is way more practical to take a quick look at a repository history.)

## Setting up your branch

You will set up a branch with your mate. This will allow you to make your changes without being bothered by everyone else in the room, only your mate :)

Chose a name with your mate, as you will work together on a set of changes. Create your own branch by:
```sh
git branch our_beautiful_branch
```
By typing `git branch` alone, you should have a list of branches, looking like:
```
* main
  our_beautiful_branch
```
The star (*) means that you are currently on branch `main` (the default) one. You now have to switch on your newly created one by typing:
```sh
git switch our_beautiful_branch
```
(You can simultaneously create and switch to a new branch by typing `git switch -c a_brand_new_branch`)

## The Basic stuff

Let's create a new drone ! We will do this very simply: pick a name and decide its type (fixed wing, rotorcraft, or any kind of hybrid). Once this is done:

- Add a new file `<my_drone_name>.md` in `Lab`, containing the drone name (and a short description if you are inspired)
- Modify the file `drones.md` to add your new drone to the list (create a new category if needed).

Stage your changes by using the `add` verb and listing the changed/new files:
```sh
git add drones.md <my_drone_name>.md
```
You can go faster by adding directly a folder; Git will add all changes in the said folder. Be cautious,
this way you may add more than you initially intended...

Then commit those changes (saving them to the repository). If you write `git commit`,
a command line text editor will open, asking you to save a message describing the changes you made.
It is traditionally made from a short title on one line, and if needed a longer paragraph below
describing in more details. Since you made only small changes, you can do everything in one line:
```sh
git commit -m "Add my new amazing drone."
```

You can do that multiple time to be as ease with the process.

## Working collaboratively

Alice and Bob push:
`git push`

The second to push will fail to push: your repo is not up to date !
`git pull`

There are a few strategies to merge changes with your own, just configure this one, its the easiest to work with:
`git config pull.rebase false`

Run git pull again:
`git pull`

Git automaticaly merge your changes with the others, just validate the merge commit message (you can change it if you like).

You can now push:
`git push`

The other one can `git pull` to get your changes


## Managing conflicts

Add 5 components to `components.md`, then commit your changes.
Push your changes.
On the pull you will have a conflict:

```
Auto-merging composants.md
CONFLICT (content): Merge conflict in composants.md
Automatic merge failed; fix conflicts and then commit the result.
```

Resolve the conflict by editing the file, then commit your changes.
You can now push.

Everyone pull to be up-to-date.


## Branches

Create your own branch:
`git branch my_awesome_stuff`
And switch on it:
`git switch my_awesome_stuff`

Make some commits

Push you branch to the remote:
`git push --set-upstream origin my_awesome_stuff`

Make some more commits, and push them:
`git push`

Now, you will integrate your branch to the common branch.
Switch to the common branch:
`git switch alice_bob`

Pull the latest changes:
`git pull`

Merge your branch to alice_bob:
`git merge my_awesome_stuff`

You can now push your new changes.

## Some bonus commands

### Restore

Restore a file to its state at the latest commit:

`git restore my_file`

### Reset

Go back to a commit, keeping all changes (unstaged):
`git reset <commit>`


Go back to a commit, removing all changes:
`git reset <commit> --hard`

### Putting aside some unstaged changes

You can put  aside some unstaged changes:
`git stash`

Then restoring them:
`git stash apply`

And finally remove the entry:
`git stash drop`



