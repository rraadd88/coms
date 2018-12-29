# Add the signing key 
## for the CRAN repositories 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
If that fails, this way may work:

gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys E084DAB9
gpg -a --export E084DAB9 | sudo apt-key add -
```
To activate the new software sources configuration, run:

sudo apt-get update

# read xls

> library(gdata)                   # load gdata package 
> help(read.xls)                   # documentation 
> mydata = read.xls("mydata.xls")  # read from first sheet

# script

--start--

# # USAGE	:	source("XX/com_qpcR.R")
# # INPTS	:	data 	: col 1 cycle no. rest samples
# # 		:			: row 1 sample id rest values 
# # 		: import to workspace by 
data <- read.delim("XX/test2")
data <- read.delim("path2trmd.csv")

library(qpcR)
otpt=0
# for(i in names(data)){
for(i in 2:ncol(data)){
#  df[[paste(i, 'length', sep="_")]] <- str_length(df[[i]])
# make pcrfit obj
objpcrfit <- pcrfit(data, cyc = 1, i, model = l4, start = NULL,offset = 0, weights = NULL, verbose = TRUE)
# calc cp
objefficiency <- efficiency(objpcrfit, plot = FALSE)
# get only cpD2 
otpt[i]=objefficiency['cpD2']
}
write.csv(otpt, file = "XX/otpt_cpvals.csv")

--end--

# plotting

library("png")
# read a sample file (R logo)
img <- readPNG(system.file("img", "Rlogo.png", package="png"))
# img2 <- readPNG(system.file("img", "Rlogo.png", package="png"))
img2 <- readPNG("hand.png", TRUE) # here import a different image 
if (exists("rasterImage")) { 
  plot(1:1000, type='n')
  rasterImage(img, 100, 100, 200, 200)
  rasterImage(img2, 300, 300, 400, 400)
}

# imshow

png("test.png",height = 4, units = 'in', res = 300)
library(png); library(grid); img <- readPNG("../plots/fig1.png");  grid.raster(img)
dev.off()
