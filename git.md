3 stages: Working Directory(local machine) -> Staging Area(commit) -> Repository(pushed to store)





Commit authorship — Git needs to know who made each change
---------------------------------------------------------------
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

Initializes a new Git repository in your current folder(track everything, need once per project)
------------------------------------------------------------------------------------------------------
git init

Checks the status of your files(tells you which files are new, modified, or staged)
----------------------------------------------------------------------------------------
git status

Adds a file from your working directory to the staging area(Include the changes in this file in my next commit)
-------------------------------------------------------------------------------------------------------------------
git add <file-name> or/ git add .

Commits the files from the staging area to your local repository(before push thing)
---------------------------------------------------------------------------------------
git commit -m "Your descriptive message"

