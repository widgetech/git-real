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