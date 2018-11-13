## Read delimeted tables

```
awk -F'\t' 
```

- `-F'\t'` : field separator, eg. -F, for comma separated files

## Grep by column values

```
awk -F'\t' '{if(int($5) >= 1 && int($5) != 255){print}}' little.sam
```

- get only the reads for which column #5 values (int) are greater than 1 and not equal to 255  

