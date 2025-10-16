
*Tags:-*
1. System - for all users
2. Global - for all repos of current user
3. Local - for current repo only


*Configurations:-* [Can see this](https://git-scm.com/docs/git-config)
1. git config --global user.name "*your_name*" (quotes used because space in between name)
2. git config --global user.email *your_email*
3. git config --global core.editor *nano* (or any editor of your choice)
4. git config --global core.autocrlf input (or true) (to handle end of lines)
5. git config --list (to see changes to config in terminal)
6. git config --global diff.tool <diff_tool_name>
7. git config --global difftool.<diff_tool_name>.cmd "nano --wait --diff $LOCAL $REMOTE"

can do -> _git config --help / git config -h_


-> Initialise a local git repository :-
```
git init
```
creates a .git directory in the current working directory which stores local config, version history, etc.


-> Git uses a staging area which is sort of a middle ground between the folder and the repository. You add files to staging area and when you are happy with the state of the staging area, you can commit the changes to the repository which is basically just taking the snapshot of the current staging area.
```
git add file1.txt file2.txt
git commit -m "any message you want to associate with this snapshot"
```
If there is a file in staging area any changes are made to that file in folder, we will have to add that file again before committing to make sure the changes have been committed.


-> the local repo can be stored on a remote repository as well(like GitHub).You can then push the changes of the local to the remote. To do this ('origin' is remote name) :-
```
git remote add origin https://github.com/your-username/your-repository.git
git push -u origin {branch_name}
```
-u flag used to set upstream. if we don't use -u then we will have to type "git push origin main" everytime.
you can set branch name as :-
```
git branch -M {branch_name}
```


-> each commit has some info associated with it
- ID
- Message
- Date/Time
- Author
- Snapshot


-> Check the status of files(which files need to be added to staging area and which need to be committed) using :-
```
git status / git status -s (for short status)
```


-> We don't need to always stage changes before committing. To skip staging area :-
```
git commit -am "any message you want to associate with this snapshot"
```
Here -a represents all changed files.


-> To remove files from repo :-
```
#this will remove file1 from directory
rm file1.txt

#check files in staging area using this
git ls-files

#to reflect the deletion of file1 in staging area
git add file1.txt

#to combine these steps
git rm file2.txt
```


-> To rename :-
```
#delete file1 and copy its contents to new file main.js
mv file1.txt main.js

#add both these changes to staging area
git add file1.txt main.js

#to combine steps
git mv file1.txt main.js
```


-> We don't want to include all files in repo as some are created by other files as a step like executing a code. To ignore these we create a new file called .gitignore
```
echo useless.txt >> .gitignore
git add .gitignore
git commit -m "added gitignore"
```
If a file or folder has already been committed then adding it to .gitignore will not make git ignore it. To fix it, remove it from staging area.
```
git rm --cached something.bin (only removes from staging area)
```


-> To check what all has been changed in files in directory or staging area :-
```
git diff #check folder files
git diff --staged #check staged files
```
for a visual diff tool, set configs 6 and 7 and then do this :-
```
git difftool
git difftool --staged
```


-> Check commit history :-
```
git log #flags like --oneline and --reverse can be added
```
HEAD -> <current_working_branch>


-> To view contents of a commit or file in that commit :-
```
git show {commit id} #can see commit id using log
git show HEAD~n #contents of commit n commits before head 
git show HEAD~n:{any_file}
```
and to view files stored in a commit :-
```
git ls-tree HEAD~n #gives files with their unique id
git show {fileunique_id}
```


-> To unstage files :-
```
git restore --staged {file_name} #takes version of file in last commit and copies it to staging area
```
and to discard local changes in directory :-
```
git restore {file_name} #takes version of file in staging area and copies it to directory
```
if file is not in staging area then remove it using git clean. use git clean -h for help.
*The restore cmd takes version in next environment and copies it to current env. for directory, next env is staging area and for staging area, next env is last commit/snapshot.*


-> If you accidentally deleted a file from both directory and staging area, you can restore that file :-
```
git restore --source=HEAD~n {file_name}
```
HEAD~n defines the version of file you want to restore. To restore the version of file 4 commits before head, do HEAD~4.


-> Branch commands :-
```
git branch #to check all branches and current branch
git branch -M {branch_name} #to rename branch
git checkout {branch_name} #to move from one branch to another
git checkout -b {branch_name} #to create new branch
git checkout -d {branch_name} #to delete a branch

git push origin {branch_name} #to push to a specific branch
```


-> Merging branches :-
```
git diff {other_branch} #compare commits, files and more b/w current and other
git merge {other_branch}
```
branches can also be merged on GitHub via Pull Requests. When using this method, we also need to pull changes from remote to local to update remote using "git pull origin main"


-> Merge Conflicts :-
Conflicts occur when git is unable to resolve differences in code automatically
ex: file1 in main - this is a button
    file1 in somebranch - this is a checkbox
Both branches have different text in same place.
You can:
- keep both changes
- accept current change
- accept incoming change
When you do "git merge {other branch}", it shows conflict error.
To solve this use PR(pull requests) or just manually commit changes to both branches locally.


-> Undoing Changes :-
1. Staged changes
```
	git reset {filename}
```
2. Committed Changes
```
	git reset HEAD~n
	git reset <commit hash>
	git reset --hard <commit hash> #removes chages in file as well
```