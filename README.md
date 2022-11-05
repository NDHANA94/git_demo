# git_demo

## $${\color{green}{SSH \ Keys}}$$
In order to push files to your github account, you have to prove to github that you are the owner of your account.
The way this is done is using SSH Keys.

- you need to start by generating a key in your local machine: \
    `ssh-keygen -t rsa -b 4096 -C "nipun.dhananjaya@gmail.com"`
- give a name to key
- give a passphrase or leave it blank pressing Enter
- repeat the passphrase if u have entered in previous step, else leave it blank pressink Enter
- After key is generated, find it using `ls | grep the_name_u_gave_to_key`
- you will see there are two. *.pub is the key you have to upload in github interface. pub stands for public, It's okay others to see this key.
The other key is the private key you have to keep secure on ur local machine, you don't share this key with anybody.

    How it work is that the public key you put in github, and then every time you want to connect to github or push your code on github or use account via your local machine, you use your private key to show github that you are the one that generated .pub key. It's a methamatical proof that only this private key could have generated the public key. 

- Print out the public key using: `cat KEY_NAME.pub`
- Copy the key.
- On github: settings -> SSH and GPG keys -> New SSH key ; give a title and paste the copied public key


## $${\color{green}{git \ commands}}$$

### git init:
- `git init` : for initializing git for a folder in your local machine

### git clone: 
Bring a reository that is hosted somwhere like Github into a folder on your local machine.
- `cd` in to the folder on ur local machine that you want to clone the repo.
- then, `git clone URL`

### git status:
- to see the current git status: `git status`

### git add:
Track your files and changes in Git.
- `git add .` for tracking all the files and folders in directory
- `git add FILE_NAME` for tracking a specific file

### git commit:
save your files in Git.
- `git commit -m "YOUR MESSAGE"` 
    `-m` stands for message. There should be a message in order to commit your files.

### git remote:
- set s new remote: `git remote add origin git@github.com:ACCOUNT_NAME/REPOSITORY_NAME`
- verify new remote: `git remote -v`
- changing a remote repo's URL: 
    `git remote set-url origin git@github.com:ACCOUNT_NAME/NEW_REPOSITORY_NAME`

### git push:
Upload git commits to a remote repo, like github.
`git push origin BRANCH_NAME`
- origin: an option set for us. It's basically a word that stands for the location of our git repo. 
- BRANCH_NAME: the branch that we want to push to.

### git pull:
Download changes from remote repo to your local machine, the oppesite of push.



## $${\color{green}{starting \ git \ from \ github \ repo:}}$$
- `git clone` -> edit/add files/folders -> `git add` -> `git commit -m "MESSAGE"` -> `git push origin BRANCH_NAME`

## $${\color{green}{starting  \ git \ from \ local \ machine:}}$$
- make a new empty repository in your github account giving the same name as the folder you want to upload(push)
- copy the repository ssh address. (ex: git@github.com:ACCOUNT_NAME/REPOSITORY_NAME)
- cd into folder you want to push to git
- `git init` -> `git add .` -> `git commit -m "MESSAGE"` 
- add remote origin(only for the first time): \
    `git remote add origin git@github.com:ACCOUNT_NAME/REPOSITORY_NAME` 
- use: `git remote -v` to see any remote repository that u've connected to the repo.
- `git push origin BARNCH_NAME` : to push the folder contains to the repo. 
<br />

- set upstream just only to use `git push`: \
    `git push -u origin BRANCH_NAME` \
    now you can use just use `git push` to push the files to repo.

## $${\color{green}{git \ \ branching:}}$$
- To see the available branches:        `git branch`
- Switch to another branch:             `git checkout BRANCH_NAME`
- Add a new brance and switch to it:    `git checkout -b NEW_BRANCH_NAME`
- Check and see the code that merging with: `git diff BRANCH_NAME`
- Merge another branch to current branch: `git merge ANOTHER_BRANCH_NAME_TO_MERGE`

## $${\color{green}{pull \ request \ (PR):}}$$
- A request to have your code pulled into another branch.
- Once we have made a PR, anyone can review our code, comment on it, ask us to make changes or updates. 
- After u make a PR, u can also update the code just by making additional commit and pushing them up to github, as long as it's on the same branch that you're making the PR with.
- Once the PR is merged, you will generally delete your feature or source brance, And to switch back to the master branch. Then when you want to make additional coding changes, you will create another new branch, and start the process over make your commits; make your commits, make a PR and then merge again. 
- to delete feature branch: `git branch -d BRANCH_NAME`


## $${\color{green}{merge \ complex \ (PR):}}$$
- When you are building your own code writing a bunch of code on your own branch, maybe other people are are writing their code in their branches. And master/main/default branch is getting updated from multiple different places. So it's possible for multiple people to change the same files. And so sometimes Git doesn't know which code you want to keep, or which code is redundant, or which code you want to get rid of. So you have to manually do that.
- EX:
    - create another branch: `git checkout -b quick-test`
    - modify the code.
    - use `git diff` to see modifications or `git status` to see curent status
    - add modified file to git: `git commit -am "updated index.html"` 
        here `-a` stands for add and `m` stands for message. This is a shortcut to add and commit using one command only for modifed files, not for newly created file.
    - switch to main/master/default branch : `git checkout main`
    - modify differently the same line in the file as you modified before in quick-test branch.
    - now seperate two branches has different code. 
    - if u try to switch to quick-test branch again, u will get an error now. bcz u have local changes that line to that u added in main/master/default branch.  So, its says it's going to be over written if u change branches.
    - So it's asking u to commit before you change. This way that line two will be saved to get in the master branch, and won't be lost when you change the branch.
    - after u commit the master branch, now u can switch to other branch. 
    - befor u merge master in to quick-test branch, try `git diff main`. it will show u the changes.
    - merge: `git merge main` in man branch. now you will get a merge complex error.
    - fixing merge complex: 
        - if u use vs code, you will see in the file where merge complex happens. and vs code allows you to resolve it (resolve in merge editer).
        - after resolving the merge complex, see `git status`.  It will show u that u have to commit again the feature (quick-test) branch.


