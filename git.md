## create git repo
    # bare because can be collaboratavely edited over eg. ssh
    git init --bare myrepo.git 

## if master exists
    git pull link

## if master is empty

    git init
    git remote add origin ../myrepo.git
    #do stuff
    git add .

## if any problem

    git status

## commit
    
    git commit -m "tag" fn
    
## push    
    git push origin master

## gui
     gitk

## check origin master
     git remote show origin

## check older versions
    git checkout abcde file/to/restore

## update fork
    git remote -v
    git remote add upstream https://github.com/rraadd88/dms2dfe.git
    git fetch upstream;git rebase upstream/master
    git push origin master

## update fork with github UI

    Step 1: New PR
    Go to your own fork’s UI, and click the “New Pull Request” button:

    New Pull Request Button

    This will take you to a screen not too different from this one:

    PR create screen

    Step 2: Base Switch
    If the option to try “switching the base” is there, click that.

    Switching the base option

    If the option isn’t there, switch the bases manually by using the provided dropdowns, and set them up so that your fork is on the left, and the original is on the right, like so:

    Switched sources

    Step 3: Send and Merge
    Click the green “Create Pull Request” button. In the input fields that appear, give it a title like “Syncing from original”. Optionally, add a description.

    Create a new pull request

    Again, click the “Create Pull Request” button to actually send the PR. The result should be a typical PR screen:

    PR screen with Merge button

    Feel free to merge it with the “Merge Pull Request” button (and “Confirm Merge” afterwards), and you’re done!

    Merged PR

    Done!

## update branch
    git pull

## gitignore 
    *.ext #to remove all files with ext
    docs/* # to remove everything under docs

## remove gitignore files
    git rm -r --cached .
    git add .
    git commit -m "fixed untracked files"

## add but ignore changes
    git update-index --assume-unchanged fh

## reverse
    git update-index --no-assume-unchanged fh

## over ssh
    git clone --bare XX@192.168.XX.XX:/XX/XX.git
    git clone dms2dfe.git

## github: one time on a comp
    git config --global --add user.name "rraadd88"
    git config --global --add user.email rraadd_8@hotmail.com

    git config --global credential.helper cache
    git config --global credential.helper "cache --timeout=3600"
    git config credential.helper store

## github: make repo on site
    git clone https://github.com/rraadd88/XX.git
    cd XX
    git push

## github: working flow
    git add *
    git commit -a -m "progs added"
    git status

## github: force mirror a fork

    git fetch upstream
    git rebase upstream/master
    git push

## tagging:1. bump version no. in the setup.py

    git commit -am "version bump";git push origin master
    git tag -a v$(python setup.py --version) -m "Update";git push --tags

## rewrite old tags
    git tag new old
    git tag -d old
    git push origin :refs/tags/old
    git push --tags

## remove tag from remote

    git push --delete origin old

## undo last commit
    git reset --hard HEAD~

## ignore tmp files
    git update-index --assume-unchanged FILE_NAME

## grep before commit!
    git grep 'pw' .

## local/ssh remote origin master

### at remote origin master branch 

    repon=prj
    mkdir $repon.git;cd $repon.git;git init --bare
    # get the full path
    pwd

### at downstream branch

### to add link
    
    usr=
    host=
    path=
    git remote add origin ssh://$usr@$host:/$path
    git push origin master

### to change link

    path=
    git remote set-url origin ssh://$usr@$host:/$path
    git push origin master

## merge in a direction

    git checkout --{ours/theirs} path/to/conflict-file
