## retriive lines between

    sed -n '98121,98130 p' test/c1_01_qcd.sam > file

## pattern match @ line
    grep -Hrn pattern file

## sort  
    sort -t, -nk3 user.csv  
    ,: delimiter  
    -n for numbers text nnthing  
    k3: column 3  

## only unique lines  
    sdiff -s file1 file2  

## split a big file to chuncks

    split -a 4 -d -l 10000000 fn fn_

## split large file by line numbers

    split -l 20000000 --numeric-suffixes fp preffix

## replace all occurances in a file
  
    sed -i -e 's/from/to/g' /tmp/file.txt
