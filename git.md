#git init in master dir
# bare because can be collaboratavely edited over eg. ssh
git init --bare myrepo.git 
# go to working dir
# if master exists
# git pull link
# if master is empty
git init
git remote add origin ../myrepo.git
#do stuff
git add .
# if any problem
# git status
git commit -m "tag" fn
git push origin master
gitk
# username pass
# check origin master
git remote show origin
# trouble?
# gitk &
# check older versions
# git checkout abcde file/to/restore

# update fork
git remote -v
git remote add upstream https://github.com/rraadd88/dms2dfe.git
git fetch upstream
git rebase upstream/master

# update branch
git pull

#gitignore 
*.ext #to remove all files with ext
docs/* # to remove everything under docs

#remove gitignore files
git rm -r --cached .
git add .
git commit -m "fixed untracked files"

# add but ignore changes
git update-index --assume-unchanged fh
#reverse
git update-index --no-assume-unchanged fh

#over ssh
git clone --bare XX@192.168.XX.XX:/XX/XX.git
git clone dms2dfe.git

# github: one time on a comp
git config --global --add user.name "rraadd88"
git config --global --add user.email rraadd_8@hotmail.com

git config --global credential.helper cache
git config --global credential.helper "cache --timeout=3600"
git config credential.helper store

# github: make a repo
# github: make repo on site
git clone https://github.com/rraadd88/XX.git
cd XX
git push

# github: working flow
git add *
git commit -a -m "progs added"
git status

# github: force mirror a fork

git fetch upstream
git rebase upstream/master
git push

# tagging

##make tags
##bump version no. in the setup.py
git add setup.py
git commit -m "version bump"
git push
git tag -a v$(python setup.py --version) -m "http://kc-lab.github.io/dms2dfe/v1.0.6/html/"
git push --tags

##rewrite old tags
git tag new old
git tag -d old
git push origin :refs/tags/old
git push --tags

#undo last commit
git reset --hard HEAD~

## ignore tmp files
git update-index --assume-unchanged FILE_NAME
