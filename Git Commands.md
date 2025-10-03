
*Tags:-*
1. System - for all users
2. Global - for all repos of current user
3. Local - for current repo only


*Configurations:-* [Can see this](https://git-scm.com/docs/git-config)
1. git config --global user.name "*your_name*" (quotes used because space in between name)
2. git config --global user.email *your_email*
3. git config --global core.editor *nano* (or any editor of your choice)
4. git config --global core.autocrlf input (or true) (to handle end of lines)
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


-> the local repo can be stored on a remote repository as well(like GitHub).You can then push the changes of the local to the remote. To do this :-
```
git remote add origin https://github.com/your-username/your-repository.git
git push -u origin <branch_name>
```
you can set branch name as :-
```
git branch -M <branch_name>
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
git rm --cached something.bin(only removes from staging area)
```
