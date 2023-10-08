# hse23_hw1
bioinformatics year 2 homework 1

mkdir hw1
cd hw1

ln -s /usr/share/data-minor-bioinf/assembly/oil_R1.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oil_R2.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R1_001.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R2_001.fastq

mkdir data

seqtk sample -s712 oil_R1.fastq 5000000 > R1.fq
seqtk sample -s712 oil_R2.fastq 5000000 > R2.fq
seqtk sample -s712 oilMP_S4_L001_R1_001.fastq 1500000 > MP_R1.fq
seqtk sample -s712 oilMP_S4_L001_R2_001.fastq 1500000 > MP_R2.fq

fastqc R1.fq R2.fq MP_R1.fq MP_R2.fq
