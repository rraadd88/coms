## merge pdfs
  
  qpdf --empty --pages *.pdf -- out.pdf
  
## remove watermarks

  pdftk $f output $f.uncompressed.pdf uncompress 
  sed -e "s/watermarktextstring/ /" $f.uncompressed.pdf > $f.unwatermarked.pdf
  pdftk $f.unwatermarked.pdf output $f.fixed.pdf compress
