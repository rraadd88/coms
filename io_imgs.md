## clipboard (screenshot) to image

	xclip -selection clipboard -t TARGETS -o
	xclip -selection clipboard -t image/png -o > /tmp/avatar.png

	scrot -s test.png

## convert: jpg to pdf

	convert -compress jpeg passbook.jpg passbook.pdf

## compress pdf

	pdfjam --outfile $f --papersize '{80mm,50mm}' $f.resized.pdf
	convert -density 400 $f.resized.pdf -compress JPEG $f.compressed.pdf	

## convert: append images vertically

	convert -append 2.png 1.png out.png

## convert: append images horizontally

	convert +append 2.png 1.png out.png

## convert: make gif  

	convert -delay 100 -loop 0 2016102* output.gif

	for file in 2016102*; do 
	# convert -strip -scale 64%x64% -quality 75 $file "big_"$file;
	# convert -strip -scale 20%x20% -quality 75 $file "sml_"$file;
	convert -crop 2000x1500+600+0 -quality 75 $file "crp_"$file;
	convert -strip -scale 20%x20% -quality 75 "crp_"$file "sml_crp_"$file;
	# convert -crop 2000x1500+600+0 -quality 75
	# convert -strip -scale 20%x20% -crop 600x400 -quality 75 $file "sml_crp_"$file;
	# echo ” ” >> ../html.txt;
	done;

	#ffmpeg: convert
	ffmpeg -i pbs_int5s_z5_001.avi -r 1/1 $pbs%03d.bmp

	#ffmpeg: to images
	ffmpeg -i 160309_sdsd_replicates.xlsx.K23stb.mp4 160309_sdsd_replicates.xlsx.K23stb.mpg

	#ffmpeg: synfig
	ffmpeg -r 15 -i filename.%04d.png -vb 20M -f flv mt.flv

## compress pdf   

	ps2pdf fn.pdf fn.pdf
	for f in med*.pdf; do ps2pdf $f $f.small.pdf; done;

## convert to png

	#!/bin/bash

	fh=$1

	mkdir -p plots/
	#fn=$(basename $fh ".pdf")
	fn=$(basename ${fh%.*}) 

	if [ ! -f "plots/"$fn".png" ]; then
		cp $fh "plots/"
		if [[ "${fh##*.}" != "png" ]]; then
			convert -density 300 -trim $fh -quality 100 "plots/"$fn".png"
		fi
	fi

	# mkdir -p SI_data/
	# -resize 800 
	# -verbose
	
## vector to raster  

## inkscape 

	for f in *.pdf; do inkscape "$f"  -z --export-dpi=600 --export-area-drawing --export-png="${f%%.*}.png"; done
	

## svg to 1000px width, no alpha,

	rsvg -w 1000 fn.svg fn.png
	
## svg to 1000px width, no alpha, loop	

	for f in *.svg; do rsvg -w 1000 "$f" "${f%%.*}.png"; done

## convert to 300dpi, max 2000px width, no alpha,

	for f in *.svg; do convert -density 500 -alpha off -resize '2000' -trim "$f" "${f%%.*}.png"; done

## check the format of the images (NOT RELIABLE, check in gimp to be sure)

	for f in *.tif; do identify -ping -format '%w %h %[channels]\n' "$f"; done

## all details (NOT RELIABLE, check in gimp to be sure)
	
	for f in *.tif; do identify "$f"; done

## for bigger vector files   

	inkscape -z in.svg -e out.png

## TIF (NOT RELIABLE, do in gimp to be sure)  
## compress

	for f in *.svg; do convert -density 300 -alpha off -resize '2000' -compress lzw "$f" "${f%%.*}.tif"; done

## install `rsvg`

	sudo apt install librsvg2-bin
	
## png to ico

	convert -resize x32 -gravity center -crop 32x32+0+0 email.png -flatten -colors 256 -background transparent email.ico

## pdf to image of individual page
	
	convert -density 300 in.pdf page_%04d.svg

## reduce the width of bigger files only
	
	convert -resize 1500\> in out

## pdf to pages
	
	pdftk in.pdf burst output page_%04d.pdf
