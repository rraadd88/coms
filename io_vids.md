## download youtube

## list formats
    youtube-dl -F lnk

## choose format
    youtube-dl -f <18> lnk

## list subtitles
    youtube-dl -list-subs lnk

## get subtitles
    youtube-dl --all-subs --skip-download lnk

## get audio only  
    youtube-dl -f 140 link

## translate subtitles
    trans -b file:///home/->file.vtt > file.en.vtt
    
## update ydl
    sudo youtube-dl -U
