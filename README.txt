Will list global configurations
git config --list

First step in tracking files
Move to the directory where the files will be stored and from the 
	git shell prompt
git init

create files the directory, but will need to add them before git will do anything with them
	and take different snapshots
	confirm by
git status

The above will tell you want files have been changed/modified, what files have been added to be
	staged

To add the file so git will monitor
git add <filename>
git add .  - will add all files in dir
git add some*.txt   - will add all files that meet that name criteria
git add --all  - will add all files
git add file1 file2 file3   - will add listed files
git add docs/*.txt   - add all txt files in the docs directory
git add /docs  - add all files in docs directory and below
git add "*.txt"   - add all txt files in project


after you add the file, run status
git status

and u will see the files that have been added and ready to be commited

to commit the changes
git commit -m "<comment>"

run status and should show nothing to commit

To show what has been done
git log

will show changes made to the file

Level 2
staging and remote

to see differences between unstaged files and staged files
git diff

Level 6 Rebasing

git fetch ;; retrieves information but does not merge changes

git rebase
1. Move all changes to  master which are not in  origin/maaster to a temporayr area
2. Run all origin/master commits
3. Run all commits in the temporary area, one at a time

Does automatically, does nto ask to merge commit

by running 
git add <file>

and then run git diff, nothing will return because all changes have been promoted

to show differences with staged files
git diff --staged

will move back prior to the previous stage
git reset HEAD <file>

blow away all changes since last commit
git checkout -- <file>

to add changes and commit in same step
git commit -a -m "<comment>"

will only do a commit on files that are currently being tracked

Reset the last commit and put it back into staging
git reset --soft HEAD^

to add a file to the last commit statment
git commit --amend -m "modify readme and add todo.txt"

undolast commit and all changes
git reset --hard HEAD^

undo last 2 commits and all changes
git reset --hard HEAD^^

Staging and remote
First step is to create a remote repository

on github.com
create the repository
back in the git shell, to add the repository
git remote add origin https://github.com/widgetech/git-real.git

origin - name for repository on my pc
web address of the repository

to show remote repositories
git remote -v

To push to the remote
git push -u origin master
origin - our name of what is being pushed
master - the branch we want pushed

to pull the information down from the remote repsitory
git pull

;; Cloning and branching

to clone an existing repository
created a second user widgetech-2
git clone https://github.com/widgetech/git-real.git

to change the name of the repository
git clone https://github.com/widgetech/git-real.git git-demo

move the cloned git repository on local pc
git remote -v

to list out the repoistories 
and sets the branch to master

going to do some work on the local repository and should create a branch to make the changes
git branch cat

to see what branchs are available
git branch

to move to a branch
git checkout branch

changing to a different time line in that changes to the files i make on branch "cat" are only
	good on branch cat. None of the changes are seen on master

when done with work on branch and want to merge to master

git branch -r   ;; will show all of the remote branchs
move to master
git merge cat - which is branch name

after done with merge and done with cat, get rid of the branch
git branch -d cat

to create a new branch and move to the branch
git checkout -b admin

making whatever changes on this branch and when i change to another branck will not move them to branch
i move to. so

git checkout master

perform what i need to do
git pull - will update the master with latest and greatest from the repository

git push  - will push the changes from the branch i am on (master in this case) up to the repository

git checkout <branch>  - will move t the other branch i was working on and my changes should still be there

to create a branch and move to it in one command
git checkout -b <branch>

Start again at #3 and watch videos. Missing something at video #5
Cloning and Branching

git clone <url provided by github>
will create a directory by that name and will download all files into the directory
can also do the below and change the name of what GitHub has
git clone <url> <wanted name>

before making any changes to a clone repository, good idea to create a branch and then perform 
merges
git branch <branch_name>

Will then need to move to the branch
git checkout <branch_name>

This changes times lines or actually it allows us to modify the files without modifying the original
on the master branch

Create a file on the new branch like
echo "Some text" > test.txt

do an ls and the file will be present
move back to the master branch and the file will not be there

after the changes have been made move back to master
git checkout master

now merge all changes from the branch to the master branch
git merge <branch_name>

After done with branch should delete the branch
git branch -d <branch_name>

Shortcut to create a branch and to move into the branch
git checkout -b admin

and this change for lesson #3

Move to level 4
Collaboration basics

adding a comment the book asked fo
this is anothe comment

Level 5
git checkout -b shopping_cart  ;; create a branch on the local PC

git push origin shopping_cart  ;; will create a remote branch and link to local branch to track

command was rejected by git and needed to
git push --set-upstream origin shopping_cart

git remote show origin   ;; will show status of a branches and remote branchs n status of branches

To delete a remote branch
git push origin :<branch name>

if other people have the remote the branch it will show as stale when they do a 
git remote show origin

if another user does a
git pull
it will show the new branch

git branch - shows local branchs
git branch -r  - shows all remote branches

git push origin :<remotebranch>  - to delete the remote branch

this shows the branches on the remote
C:\temp\gitreal [master]> git branch -r
  origin/master
  origin/shopping_cart
C:\temp\gitreal [master]> git push orgin:shopping_cart
fatal: You are pushing to remote 'orgin:shopping_cart', which is not the upstrea
m of
your current branch 'master', without telling me what to push
to update which remote branch.

The command needs the space betwee the origin and :
C:\temp\gitreal [master]> git push origin :shopping_cart
To https://github.com/widgetech/git-real.git
 - [deleted]         shopping_cart
C:\temp\gitreal [master]>

After done with remote branch need to delete
git remote show origin  -- this will show the branch as stale if someone else deleted the remote branch

to get rid of that
git remote prune origin  -- this will clean up deleted remote branches

A tag is a reference to a commit used mostley for release versioning

git tag  ; list of all tages
git check out <tag>  ;; check out the code at the commit
git tag -a <tag name> -m "<comment>"
git push --tags  ;; to push the tags to the remote

git tag
git checkout v0.0.1
git tag -a v0.0.3 -m "version 0.0.3"
git push --tags  ;; pushs the tags to the remote server, looks like it bundles the files up being
	monitored under that tag. Not sure what that will do for me
git push --tags

Git real 7
git log - to show log of chagnes

git log --pretty=oneline
git log --pretty=format:"%h $ad- %s [%an]"
git log --pretty -p ;; will show changes made
git log --pretty --start   ;; shows insertions and deletions
git log --oneline -- graph  ;; shows branches graphically
git log --until=1.minute.ago
git log --since=1.day.ago
git log --since=1.hour.ago
git log --since=1.month.ago --until=2.weeks.ago
git log --since=2000-01-01 --until=2015-07-21
git diff  ;; will show diffrences since last commit
git diff HEAD  ;; does the same as gid diff
git diff HEAD^  ;; parent of latest commit
git diff HEAD^^  ;; grandparent of latest commit
git diff HEAD~5  ;; five commits ago
git diff HEAD^..HEAD  ;; second most recent commit vs most recent
git diff <hash>..<hash>  ;; first hash to compare to other hash. Only need first few characters of the hash
git diff <branch> <branch>  ;; to compare different branches
git diff --since=1.week.ago --until=1.minute.ago
git blame <file> --date short  ;; will show person responsible for changes/commits to the file in question


to exculde files from being monitored or uploaded to the repository us
.git/info/exclude
	tutorial.mpt
	*.mp4

Should not monitor log files
in the .gitignore add any log files

to remove a file from git

git rm <file.name>

git status

git commit -m "Remove <filename>"

