## tablet
    scp -P XX XX.png tablet@192.168.XX.XX:/XX/

## wget ftp to a directory 
    wget -x -nH ftp://ftp -P destination

## wget folder only 
    wget -r -np -nH /path/


## download all subpages 
    wget --mirror -p --convert-links -P ./LOCAL-DIR WEBSITE-URL

## download directory ignoring robot.txt
    wget -r -e robots=off link

    –mirror : turn on options suitable for mirroring.

    -p : download all files that are necessary to properly display a given HTML page.

    –convert-links : after the download, convert the links in document for local viewing.

    -P ./LOCAL-DIR : save all the files and directories to the specified directory.

