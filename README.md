# git_demo

## git commands
- `clone`: Bring a reository that is hosted somwhere like Github into a folder on your local machine.
- `add`: Track your files and changes in Git.
- `commit`: save your files in Git.
- `push`: Upload git commits to a remote repo, like github.
- `pull`: Download changes from remote repo to your local machine, the oppesite of push.


## SSH Keys
In order to push files to your github account, you have to prove to github that you are the owner of your account.
The way this is done is using SSH Keys.

- you need to start by generating a key in your local machine:
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

## git push:
`git push origin BRANCH_NAME`
- origin: an option set for us. It's basically a word that stands for the location of our git repo. 
- BRANCH_NAME: the branch that we want to push to.