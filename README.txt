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

after you add the file, run status
git status

and u will see the files that have been added and ready to be commited

to commit the changes
git commit -m "<comment>"

run status and should show nothing to commit

