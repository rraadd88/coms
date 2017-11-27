# clipboard (screenshot) to image
xclip -selection clipboard -t TARGETS -o
xclip -selection clipboard -t image/png -o > /tmp/avatar.png

scrot -s test.png

# convert: jpg to pdf
convert -compress jpeg passbook.jpg passbook.pdf

# convert: append images
convert -append 2.png 1.png out.png

# convert: make gif
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

# compress pdf 
pdf2ps 12th.pdf 12th.ps
ps2pdf 12th.ps 12th.pdf
