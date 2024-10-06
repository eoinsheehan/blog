# Git

https://levelup.gitconnected.com/git-rebase-never-mess-up-merge-conflicts-again-460890a269d4

the above kind of walks through what is going on when you rebase

- set up to inspect commit messages
    - more than likely using conventional commits or something like that
- need to set up git config with naming for signing commits and all that and prevent issues being raised every time you push to a repo

in bashrc or zshrc should probably add some aliases for commonly used commands like:

bundle exec or whatever

look at proper naming conventions 

- in relation to branches
- in  relation to commits

remove any local branches that have been deleted on the remote

- git fetch prune
    - this will only delete all the origin referenced branches locally

doesn’t seem to be a means of deleting all merged branches locally

- could potentially look at creating a script to do this

Automatically create upstream branch on push

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

To revert file to a previous version

git log — path/to/file

find the last time git knows about it and revert to that version of the file

git checkout SHA — path/to/file

git commit the reversion of this change

good article [here](https://www.notion.so/SuperGold-Team-Development-Docs-391fa6e4dfde4c958945b39db84cfaae?pvs=21) from atlassian about undoing in git

I believe checkout and commit is the way to do it at the file level

git revert can only be done to a complete commit?

git reset is a misrepresentation and should probably not be done on public branches?

Untracked files

- git clean -n does a dry run of what would be removed

git clean -f actually forces the command

git clean -fd to force clean directories

how to bring bring back local changes

- git reset HEAD~
    - brings the most recent things back in

good atlassian stuff on undoing

https://www.atlassian.com/git/tutorials/undoing-changes/git-reset

Git stash

- push with -m to set a message to each of the stashes
- git stash list to list all of the current stashes

need to look into how to get the count of commits that are on a branch for like interactively rebasing the entire branch

git ls-files

- to list all of the files

# **What is a Git tag?**

A [tag](https://book.git-scm.com/docs/git-tag) is an object referencing a specific commit within the project history, similar to chapter markers in a book. You can create tags to point to a new version release, a significant codebase change, or any other event development teams may want to reference. Many development teams use [semantic versioning](https://semver.org/) to communicate the types of changes that occur between one tag and another.

need to look up the git blame command as well

also need to look at my git config in general

- git status -sb should maybe be my default to have it like more readable
    - but need to look into these alias options in a littler more detail
- just generally need to lookk at the git config to improve my experience

in semantic versioning rc stands for release candidate and they are generally more stable than beta releases

Question?

- when I git checkout to a specific commit without specifying a file I ended up in a detached head state
- a state which I am still not comfortable in being in at all
- so need to look into that

git show-ref —tags

- displays all refs that are available in git

Github specific logic perhaps that would be good to chat about:

- tags and releases
- tags are natively included in git
- actions and all of that jazz
    - a workflow is made up of a bunch of actions/jobs?
        - need to clarify the terminology on this really

nice image from this article on code review

https://medium.com/the-crazy-coder/best-practices-for-writing-code-review-comments-d3667eb95aa0

to do:

should probably look into conventional comments here:

https://conventionalcomments.org/

To better understand how `git fetch` works let us discuss how Git organizes and stores commits. Behind the scenes, in the repository's `./.git/objects` directory, Git stores all commits, local and remote. Git keeps remote and local branch commits distinctly separate through the use of branch refs. The refs for local branches are stored in the `./.git/refs/heads/`. Executing the [git branch](https://www.atlassian.com/git/tutorials/using-branches) command will output a list of the local branch refs. The following is an example of `git branch` output with some demo branch names.

Remote branches are just like local branches, except they map to commits from somebody else’s repository

git fetch —prune will delete remote refs that are no longer in use on the repo

- only deletes remote refs as you need to keep the ones that don’t have a remote just yet
- also will only do the ones that are no longer in use
    - think this means branches that have been deleted as they are merged

OK so git blame seems to be like a great tool

- must ask Gus about how he has his tooling set up to inspect spec

Ok so it seems like you can use git add -p to add partials of a file to a specific commit

- these seem to be known as hunks for some reason

[`git push --force-with-lease`](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease) is a safer alternative to `git push --force`. It allows you to push changes to the remote branch only if the remote branch is at the same commit as the one you have locally. If the remote branch has been updated by someone else, the push will be rejected, preventing accidental overwrites

By adding the `--dry-run` option, you can check if the push would succeed without actually pushing the changes. This can help you avoid potential conflicts and overwrites.

| Command | Overwrites Remote Branch | Safety | Use Cases |
| --- | --- | --- | --- |
| `git push --force` | Yes | Low | Undoing a mistaken push, cleaning up messy commit history, updating a feature branch |
| `git push --force-with-lease` | No, only if the remote branch is at the same commit as the local branch | High | Collaborative work, rebasing or squashing commits, updating a feature branch with additional safety |

The above is a good table for using git push —force and git push —force-with-lease

First, make sure nobody’s pulled down your branch and done local work off of it. If they have, your force push may make it difficult for them to reconcile their changes with yours.

there branch would be completely out of whack

I think there could be an issue around if you do git fetch and then somehow git push —force-with-lease without merging those remote changes or something like that.

question

- what is git churn

to add file to last commit

git commit —amend —no-edit

if you want to like trigger a workflow you can do git commit —allow-empty

to do

- [ ]  would be good to add a git pre commit hook that would check commit message against the one I have tried to add
- [ ]  ideally would do some auto correction or whatever eventually but to begin with it would be good to just reject them with some sort of message

how to tag a commit in github

how to delete an existing tag on the remote

`git push origin :refs/tags/<tagname>`

You can look at git rebase as a way to perform multiple cherry-picks one after the other

Indeed, Git can simply perform a fast-forward merge, as the history is completely linear 

But on a rebase, we switch side because the first thing a rebase does is to checkout the upstream branch! (to replay the current commits on top of it)

good article on mergetool switching here
https://stackoverflow.com/questions/3051461/git-rebase-keeping-track-of-local-and-remote
