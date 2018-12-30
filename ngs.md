## forward strand
    samtools view -F 0x10 XX.sam.s.bam
## rev strand
    samtools view -F 0x10 XX.sam.s.bam
## count total reads
    samtools view -c XX.sam.s.bam

    samtools view -bS test/XX.sam | samtools sort - test/XX.sam.s
    samtools index test/XX.sam.s.bam

    samtools faidx NC_012967.1.fasta
    samtools view -b -S -o bowtie/XX.bam bowtie/XX.sam
    samtools sort bowtie/XX.bam bowtie/XX.sorted
    samtools index bowtie/XX.sorted.bam

    bowtie2-build [options]* <reference_in> <bt2_base>

## get consensus
    samtools mpileup -uf index/XX.fasta XX.sam.s..bam | bcftools view -cg - | perl /usr/share/samtools/vcfutils.pl vcf2fq > test5

    for file in $(cat $1);
    do echo "$file" ;
    bowtie2 -p 12 --very-sensitive $bt2 -q $file -S $file.sam
    bowtie2 -p 12 --very-sensitive-local $bt2 -q $file -S $file.sam
    done
    samtools view -bS -T $fasta $file > $file.bam
    samtools sort $file.bam $file.s
    samtools index $file.s.bam
    perl sam2mat1_v21_branch3_shortreads.pl $fasta $file.s.bam 2>> $file.s2mp1log;
    fasta='XX.fasta';
    bt2='XX';

    awk '{split($17,NM,":");if (NM[3]<5) {print }}' $file._globalsam

## bcl2fastq
    ./bcl2fastq  --ignore-missing-bcl --ignore-missing-control -i XX/Data/Intensities/BaseCalls -R XX --interop-dir XX/InterOp 

## fa2fq
    python fa2fq.py XX.fasta XX.fastq

## QC:  prinseq

    perl prinseq-lite.pl -verbose -fastq $file -graph_data $file.gd -out_good null -out_bad null -graph_stats ld,gc,qd
    perl prinseq-graphs.pl -i $file.gd -png_all -o $file
    perl prinseq-graphs.pl -i $file.gd -html_all -o $file

    files=$(ls /XX/*fastq)
    for file in $files; do 
    perl prinseq-lite.pl -verbose -fastq $file -graph_data $file.gd -out_good null -out_bad null -graph_stats ld,gc,qd ;
    perl prinseq-graphs.pl -i $file.gd -png_all -o $file
    perl prinseq-graphs.pl -i $file.gd -html_all -o $file
    done
