# Github Foundations Certification Study Guide
In this repository, we are going to review important Git and Github concepts and commands in order to prepare for the Github Foundations Certification exam. The content was extracted from [Linkedin Prepare for the GitHub Foundations Certification Course](https://www.linkedin.com/learning/paths/prepare-for-the-github-foundations-certification).

## Configuring your Git locally
First thing to do I to define your username and email.
```bash
git config --global user.name "YourUserName"
git config --global user.email "youremail@email.com"
```
Next, it's a convetion to use `main` as the name of your production repository branch, replacing the previous `master`.
```bash
git config --global init.defaultBranch main
```
## Initializing a Git Repository
To start a Git repository you simply use the `init` command.
```bash
git init
```
After this command you can find a `.git` folder inside your reopository with all the tracking files used by Git.

## Staging files and pushing changes
Whenever you create, change or delete a file you can track it by commiting it to your branch history.
```bash
git add --all
git add --A
git add .
```
By adding the file(s) you can then write a checkout message for it.
```bash
git commit -m "Adding README file to repo"
```
Finally, whenever you wan't to push the files to a remote repository like Github you can define it with the following command.
```bash
git remote add origin https://github.com/YourUserName/your_repo_name
git push -u origin main
```
Make sure you create your Github repository before trying to push the changes to it.

## Understanding Git environments
One important command to use to have a better understanding of the status of your Git repository `git log`. For a simpler view, use `git log --oneline`. This gives the view of your current branch, it's relation to remote repository and commits recorded.<br>
Another command is `git status`, which describe the status of the files in your current working branch.
Another powerful command is `restore`. It can restore the state of tracked files to previous states. For example, `git restore --staged .` would unstage all files that were added to staging, and `git restore .` would remove all the changes made to tracked files. In case you deleted a tracked file, if you run `restore` command, it would appear back in your repository folder.

## Ignoring files
Software projects usually need settings files that are not supposed to be versioned, as it may carry sensitive data. To prevent Git to track these types of files you can create `.gitignore` file inside your repository.

## Deleting and renaming files
Whenever you delete a tracked file from your Git repository, it's marked for deletion, an you need to add and commit it, in order to formalize the deletion. You can also use the `git rm <file>` to delete and stage a file in one step. <br>
In case of renaming, you can use `git mv <file>` in order to avoid having to track a deletion and creation of files.

## Differences
Another interesting command for checking the differences made on your track files is `git diff`, as it displays changes made to each line on altered files. You can also check a specific commit from your `git log --oneline` and copy the id to inspect the changes made to that specific commit with `git diff 9723453` (for commit id 9723453).

## Changing history
### Amend
There a few ways for your to make changes to your Git history. The first one is amend, which offers you the possibility to modify the last commit made. Instead of creating a new commit, you simply use `git commit --amend`, to replace the last one. 

### Reset
If you want to reset changes made to a specific point in time you can use `git reset <commit id>`. The reset command actually moves the `HEAD` to a specific past commit. If you specify the `git reset --hard <commit id>` parameter it will delete all the changes made between the original `HEAD` commit and the past commit id, while if you don't specify the files will keep the changes, but it won't be staged.

### Rebase
Rebase allows you to take the changes from one branch and apply it to another branch. You have a few ways to use rebase, like the interactive, which opens your default text editor in order for you to organize your current branch history.
```bash
git rebase -i --root
```

## Branching
Branching allows you to create alternative versions of your Git project in order to develope and test new features. To have check the available branches from your repository you can use `git branch`. Whenever you want to create a new branch, keeping the history of the current branch you can use `git switch -c <NEW BRANCH NAME>` (or older command `git checkout -b <NEW BRANCH NAME>`).