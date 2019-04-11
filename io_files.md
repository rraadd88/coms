## find

    find . -name "foo*"
    find . -depth -empty >> test

## find and process

    find . -type f -name "*O=A*" | xargs cp/mv/rm

## for loop  
    for line in $(cat test);  
    do  
    mv $line empty_folders;  
    done  

## for loop  
    for line in $(cat test);  do  
        if [[ $f == *.yml ]]; then
            mv $line empty_folders; 
        fi
    done  

## substring

    if [[ $f == *.yml ]]; then 
        action $f ; 
    fi; 

## rename  

    for file in *; do mv "$file" `echo $file | tr ' ' '_'` ; done  
    for file in *; do mv "$file" `echo $file | tr '-' '_'` ; done  
    for file in *; do mv "$file" `echo $file | tr ':' '_'` ; done  

    ls -1 | while read file; do new_file=$(echo $file | sed s/\ //g); mv "$file" "$new_file"; done  


## rename dir and files remove spaces  

    find -name "* *" -type d | rename 's/ /_/g'  
    find -name "* *" -type f | rename 's/ /_/g'  

    find -name "*(*" -type f | rename 's/\(/_/g'  
    find -name "*)*" -type f | rename 's/\)/_/g'  
    find -name "*-*" -type f | rename 's/-/_/g'  
    find -name "*'*" -type f | rename 's/'/_/g'  
    find -name "*,*" -type f | rename 's/,/_/g'  
    find -name "*!*" -type f | rename 's/!/_/g'  
    find -name "*;*" -type f | rename 's/;/_/g'  
    find -name "*"*" -type f | rename 's/"/_/g'  
    find -name "***" -type f | rename 's/*/_/g'  
    find -name "*>*" -type f | rename 's/>/_/g'  
    find -name "*:*" -type f | rename 's/:/_/g'  
  
## replace filenames with numbers  

    ls | cat -n | while read n f; do mv "$f" "$n.extension"; done

    eg. 1st 3 keep chars

## find and delete

    find -name "*:*" -type f -exec rm -rf {} \;

## gzip all files

    gzip *
    ls *.gz | cat -n | while read n f; do mv "$f" ${f:0:3}"$n.gz"; done

## backup: larger than 4.2g files in fat32
    zip -r -s 2g archive.zip FolderName/
    7z a -r -v2g -mx0 /XX.7z backup_081214_data/

## find file >4gb 
    find . -type f -size +3000000k -exec ls -lh {} \; | awk '{ print $9 ": " $5 }'
    7z a -v2g -mx0 file.7z file

## rsync: one-directional forced

    rsync -avv XX/from XX/to

## copy directory structure sans files; to create the list of directories, then

    find . -type d >dirs.txt

## to create the directories on the destination.

    xargs mkdir -p <dirs.txt

## backup

    date=$(date +%Y-%m-%d)
    git_repo='prj'
    git clone ssh://user@ip/path/to/$git_repo
    mv $git_repo $date"_"$git_repo
    du -h -a $date"_"$git_repo > $date"_"$git_repo".log"

## gzip individually
    gzip preffix*
    
## compress folder
    tar -zcvf archive-name.tar.gz directory-name
    Where,
    -z : Compress archive using gzip program
    -c : Create archive
    -v : Verbose i.e display progress while creating archive
    -f : Archive File name

## get the number of file format counts in subdirs

    ls -R . | awk -F . '{print $NF}' | sort | uniq -c | awk '{print $2,$1}' | sort -k2 -n
