# retriive lines between
sed -n '98121,98130 p' test/c1_01_qcd.sam > file

# pattern match @ line
grep -Hrn pattern file


# find

find . -name "foo*"
find . -depth -empty >> test

# find and process

find . -type f -name "*O=A*" | xargs cp/mv/rm

# for loop  
for line in $(cat test);  
do  
mv $line empty_folders;  
done  

# sort  
sort -t, -nk3 user.csv  
,: delimiter  
-n for numbers text nnthing  
k3: column 3  

# only unique lines  
sdiff -s file1 file2  

# rename  

for file in *; do mv "$file" `echo $file | tr ' ' '_'` ; done  
for file in *; do mv "$file" `echo $file | tr '-' '_'` ; done  
for file in *; do mv "$file" `echo $file | tr ':' '_'` ; done  

ls -1 | while read file; do new_file=$(echo $file | sed s/\ //g); mv "$file" "$new_file"; done  


# rename dir and files   
## remove spaces  

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

# find and delete

  find -name "*:*" -type f | -exec rm -rf {} \;

# gzip *
ls *.gz | cat -n | while read n f; do mv "$f" ${f:0:3}"$n.gz"; done

# backup

# larger than 4.2g files in fat32
zip -r -s 2g archive.zip FolderName/
7z a -r -v2g -mx0 /XX.7z backup_081214_data/

# find file >4gb 
find . -type f -size +3000000k -exec ls -lh {} \; | awk '{ print $9 ": " $5 }'
7z a -v2g -mx0 file.7z file

# rsync: one-directional forced

rsync -avv XX/from XX/to

# copy directory structure sans files

find . -type d >dirs.txt
to create the list of directories, then

xargs mkdir -p <dirs.txt
to create the directories on the destination.

# split a big file to chuncks

split -a 4 -d -l 10000000 fn fn_
