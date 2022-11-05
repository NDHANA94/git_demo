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

