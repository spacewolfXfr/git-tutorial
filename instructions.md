# Git basic training

Initial state of the repo:
- drones.md : list of all drones
- components.md : the components available in the workshop

You can run `git status` between each operations to wtach the state of your local repository.
At first, use the comand line only, then you will be able to use a GUI to make commits.

## Setting up your repo

Clone the repository from Github:
`git clone git@github.com:spacewolfXfr/git-tutorial.git`

Create a branch to work with a mate:
`git branch alice_bob`
`git switch alice_bob`

## The Basic stuff

Add the instructions concerning your new drone. Alice adds a multirotor, and Bob add a fixedwing.
- Add a file for your drone
- Add the name of the drone in `drones.md`

Stage your changes:
`git add drones.md yourNewDrone.md`
Then commit those changes:
`git commit -m "Add my new amazing drone."`

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



