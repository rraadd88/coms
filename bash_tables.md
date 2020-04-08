## Read delimeted tables

    awk -F'\t' 

    - `-F'\t'` : field separator, eg. -F, for comma separated files

## Grep by column values

    awk -F'\t' '{if(int($5) >= 1 && int($5) != 255){print}}' little.sam
    
    - get only the reads for which column #5 values (int) are greater than 1 and not equal to 255  

## Use shell variable in awk

    name="sam"

    awk -v var="$name" 'BEGIN {name,$1,$2}' little.sam 

## Get unique values in a column

## 1. `Awk`ward

    awk '!a[$1]++' <file


## 2. Using `sort`

    sort -u -t, -k1,1 file

    -u for unique
    -t, so comma is the delimiter
    -k1,1 for the key field 1
