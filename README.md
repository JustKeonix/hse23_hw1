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

Обрежем адаптеры:
```platanus_trim R1.fq R2.fq```

```platanus_internal_trim MP_R1.fq MP_R2.fq```

Проверим насколько хорошо обрезались адаптеры с помощью MultiQC:

```fastqc R1.fq.trimmed R2.fq.trimmed MP_R1.fq.int_trimmed MP_R2.fq.int_trimmed```

```multiqc .```

До обрезания адаптеров:

![image](https://github.com/JustKeonix/hse23_hw1/assets/24775932/18708886-4b6a-446a-a7db-fdb4a52cdb41)

После:

![image](https://github.com/JustKeonix/hse23_hw1/assets/24775932/a3ad13fa-6f61-476e-92cb-8cf8eecf7bf4)

Соберём контиги:

```platanus assemble -f R1.fq.trimmed R2.fq.trimmed -o Pxut 2> assemble.log```

По получившейся сборке найдём статистику контигов\
количестов контигов: 608\
длина всез контигов: 3924881\
самы длинный контиг: 179307\
n50 = 47797

Соберём скаффолды:\
```platanus scaffold -o Pxut -c Pxut_contig.fa -b Pxut_contigBubble.fa -IP1 R1.fq.trimmed R2.fq.trimmed -OP2 MP_R1.fq.int_trimmed MP_R2.fq.int_trimmed -t 4```\
По получившейся сборке найдём статистику скаффолдов:\
количестов скаффолдов: 67\
длина всез скаффолдов: 3875453\
самы длинный скаффолд: 3834102\
n50 = 3834102\

Статистика самого длинного скаффолда
число гэпов: 62\
общяя длина гэпов: 5890\

Уменьшим количество гэпов:\
```platanus gap_close -o Pxut -c Pxut_scaffold.fa -IP1 R1.fq.trimmed R2.fq.trimmed -OP2 MP_R1.fq.int_trimmed MP_R2.fq.int_trimmed -t 4```\

Получившаяся статистика:\
количестов скаффолдов: 67\
длина всез скаффолдов: 3922240\
самы длинный скаффолд: 3880490\
n50 = 3880490\

Статистика самого длинного скаффолда
число гэпов: 9\
общяя длина гэпов: 1526\




