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
    git fetch upstream
    git rebase upstream/master

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

    git add setup.py
    git commit -m "version bump"
    git push origin master
    git tag -a v$(python setup.py --version) -m "Update"
    git push --tags

## rewrite old tags
    git tag new old
    git tag -d old
    git push origin :refs/tags/old
    git push --tags

## undo last commit
    git reset --hard HEAD~

## ignore tmp files
    git update-index --assume-unchanged FILE_NAME

## grep before commit!
    git grep 'pw' .

## local/ssh remote origin master

## at remote origin master branch 

    repon=prj
    mkdir $repon.git;cd $repon.git;git init --bare

## at downstream branch

## to add link

    usr=usr;host=host;path=path;
    git remote add origin ssh://$usr@$host:/$path/$repon.git

## to change link

    git remote set-url origin ssh://usr@host:/path/prj.git
    git push origin master
