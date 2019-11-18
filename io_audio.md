### get legth of mp3s 
  for f in *.mp3; do mp3info -p "$f\t%m\n" "$f"; done
