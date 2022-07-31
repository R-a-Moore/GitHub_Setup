# GitHub_Setup
[Writing in .md Files](https://github.com/R-a-Moore/Writing_In_md)
![github logo](https://www.netmatters.co.uk/uploads/article/636/github-NVKO.png)
## GitHub
GitHub is an open source version control framework which allows for locally available data to be made available globally. This allowing teams to work on a single product/system simultaneously in an organised, collaborative manner.


### GitHub Account
In order to utilise github, you mist first have a github account: [github login page](https://github.com/)

Once you've done that you're ready to start setting up git.
## Setting Up Git
Git is the software you use to communicate between github and your local host (your personal machine).

Start by following these steps:
- download git bash from [here](https://gitforwindows.org/)
- run the executable and follow through its steps.

With that done, you should be ready to start up Git Bash in your windows browser, run it as an administrator so that it has full permisions to operate on your machine...

![git bash in browser](https://user-images.githubusercontent.com/47668244/181805670-e543161e-7deb-495c-8220-c4ae665f7df2.png)

It should look like this when you start it up

![git bash started](https://user-images.githubusercontent.com/47668244/181805721-8c80c55e-9e8b-4d34-ad58-fb905bbe5af4.png)

## Using HTTPs
Now that you have git and a github account set up, you are ready to start work.

On github, in the ripositories tab press 'new'. this creates a new repository for you to send all of your work. it should look like this: 
 
![create new repo](https://user-images.githubusercontent.com/47668244/181805754-27727057-7221-4117-a082-06d026502b0e.png)

- Name the repository as you like
- give it whatever description you like
- you can choose whether it is public or private to you
- For now we will leave the 'Add a READEME.md file' option unticked, however you can tick this for other repos.

Now click 'Create repository'

### Creating a README.md & Pushing to your repo
Now that the repo has been made, we will want to access versions for out local machines, and put work in there.

First, Open up git bash. and follow these commands:

`mkdir "new_repo"` this creates a file for us to work in. Name it what you like, i've called it "new_repo".

`cd new_repo` this navigates the git bash into the new_repo file.

`ls -a` this provides a list of all the files in this file.

`git init` this will initialise git int this file you have made

`nano README.md` this will create a new file called 'README.md' which will immediately allow you to write into it.
Write whatever you like in here, instructions or descritpions may be a useful idea. If you don't know the useful tools for writing in .md files follow [this link!](https://github.com/R-a-Moore/Writing_In_md)
Once you are done press `CTRL + X` then when the prompt appears press `y` and finally `ENTER` which should take you back onto the git bash proper.

![git bash nano command](https://user-images.githubusercontent.com/47668244/182022514-2e112575-6ab8-4f80-b6f0-901296e1126d.png)

`git add .` this adds all of the work you've done to a commit.

`git add -u README.md` this adds the specific file you've added/altered to a commit.

`git commit -m ""` this commits the work you've done, now ready to be pushed up into your repo on github.

`git remote add origin https://github.com/"your username"/"your repo".git` this adds the work you've done, into your online repo.

`git branch -M main` this moves you onto the main branch of your repo work

`git push -u origin main` this pushes all of the work you've done onto the main branch of your repo. It should now be on there when you view it in your github.

![github pushed](https://user-images.githubusercontent.com/47668244/182022630-33e44635-2d30-42b9-9b14-c667a7d24d1a.png)

This is what all of the code should look like together

![git bash code all](https://user-images.githubusercontent.com/47668244/182022500-17aef7e5-536a-47bb-8495-0e3ccde4f219.png)

If you want to pull down work from a repo the code for this (after you have `git init`) is this; `git pull "your repo link"`.

Note that you must delete the .git file using `rm -rf .git` in order to leave the branch you are in, and the connection to git all together. You can re-initialize with `git init` in the file you were using, again, when you come back to it.

### Authentication
It may be the case that git bash is not allowing you to run the code due to you not being authenticated. Try loging in using your github account.

```commandline
git config --global user.name "myname"
git config --global user.email myemail@example.com
```

## SSH

Secure Shell [(SSH)](https://en.wikipedia.org/wiki/Secure_Shell), is a public-key cryptographic protocol for securing communications on a network. In this case, it allows us to securely send our work to and from github.

### Creating an SSH Key
The first thing you need to do in order to use git with SSH, is make the repo use it. You can do this in the creation;

![making repo SSH](https://user-images.githubusercontent.com/47668244/181997207-ad44fff9-956a-420e-99aa-83a62ec1548d.png)

Next, you will need to creat an .SSH file in your local host (if you do not have one already), with `mkdir .ssh` and then navigating into that new file using `cd .ssh`.

Now we can make the keys wit this command: `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

- You will then be prompted to name the key
- you will then be prompted to provide a passphrase for the key (just press `ENTER` to leave it blank)

With that your key should be generated (both your public - .pub - and private key files, which you can find in your .ssh folder). Use the `ls -a` command to see it within your directory.

### Using SSH

`cat "your key"` this command will read out the cotent of a file. In this case you should be able to see what your key looks like. Select the key's content (in it's entirety), and copy it. You will need it for later.

Next, go to github and go into settings > SSH and GPG keys. Then create a new SSH key, naming/titling it and pasting the copy of the key into the key field. Then finishing by pressing 'Add SSH key'.

Then go into your repo in github. Get the SSH link copy. 

![repo SSH link copy](https://user-images.githubusercontent.com/47668244/181997196-1b4db931-c527-4d1b-a8a8-1da585b24c5e.png)

### ssh-agent & keys
You may need to 

`eval "$(ssh-agent -s)"` this gets your agent pid which should looks something like `Agent pid "your number"`.

Add your ssh private key to the ssh-agent; `ssh-add ~/.ssh/"your private key name"`

With all of this done, you should be able to pull/push, your work as normal with the previous steps in the 'creating a README.md' section above. Enjoy!
