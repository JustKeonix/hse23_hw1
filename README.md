# hse23_hw1
bioinformatics year 2 homework 1

```mkdir hw1```

```cd hw1```

```ln -s /usr/share/data-minor-bioinf/assembly/oil_R1.fastq```

```ln -s /usr/share/data-minor-bioinf/assembly/oil_R2.fastq```

```ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R1_001.fastq```

```ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R2_001.fastq```

```mkdir data```

```seqtk sample -s712 oil_R1.fastq 5000000 > R1.fq```

```seqtk sample -s712 oil_R2.fastq 5000000 > R2.fq```

```seqtk sample -s712 oilMP_S4_L001_R1_001.fastq 1500000 > MP_R1.fq```

```seqtk sample -s712 oilMP_S4_L001_R2_001.fastq 1500000 > MP_R2.fq```

```fastqc R1.fq R2.fq MP_R1.fq MP_R2.fq```

paired-end:

![image](https://github.com/JustKeonix/hse23_hw1/assets/24775932/eb2e304d-b7b5-4456-a963-606a3b6c7bc0)
![image](https://github.com/JustKeonix/hse23_hw1/assets/24775932/fde338f3-e500-4af7-a9ed-e7454e5f76e0)

mate-pairs:

![image](https://github.com/JustKeonix/hse23_hw1/assets/24775932/f58b119b-c88d-48ca-a2ed-f2df85b37dca)
![image](https://github.com/JustKeonix/hse23_hw1/assets/24775932/4b799fcf-1c74-4373-ba7f-e84e466e9e0a)

MultiQC:

![image](https://github.com/JustKeonix/hse23_hw1/assets/24775932/e760ca05-d105-4cbb-ac3e-218c493593c1)



