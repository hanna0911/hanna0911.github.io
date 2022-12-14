---
layout: post
title:  "生信 Week 2 上机任务"
date:   2022-09-23 14:45:25 +0800
categories: [posts, bioinformatics]
tags: [blog]
author: hanna0911
toc: true
comments: true
comments: true
pin: true
---

写出一个bash脚本，可以使它自动读取一个文件夹（例如bash_homework/）的内容，将该文件夹下文件的名字输出到filenames.txt，子文件夹的名字输出到 dirname.txt。

> 下载bash_homework.zip并解压。（该文件位于[该链接]()中**Files needed by this Tutorial**中的清华云Bioinformatics Tutorial / Files路径下的相应文件夹中。）
>
> 将bash脚本，filename.txt，dirname.txt 写到同一个文件中上交。格式建议： word, pdf, txt.

bash脚本：

```bash
#!/bin/bash

# 提示用户输入待查看文件夹的路径（绝对路径/相对路径）
echo -n "Please input the path of the directory you want to check: "

# 保存用户输入的文件夹路径到check_path中
read check_path

# 输出文件路径
output_file="filenames.txt"
output_directory="dirname.txt"

for item in ${check_path}/*;do
    item_name=`basename $item` # 去除目录文件夹前缀${check_path}/
    # 若item是文件，则输出该文件名到filenames.txt中
    if [ -f $item ];then
        echo "$item_name" >> "$output_file"
    # 若item是子文件夹，则输出该子文件夹的名字到dirname.txt中
    elif [ -d $item ];then
        echo "$item_name" >> "$output_directory"
    fi 
done

exit 0
```

filename.txt：

```
a.txt
a1.txt
b.filter_random.pl
b1.txt
bam_wig.sh
c.txt
c1.txt
chrom.size
d1.txt
dir.txt
e1.txt
f1.txt
human_geneExp.txt
if.sh
image
insitiue.txt
mouse_geneExp.txt
name.txt
number.sh
out.bw
random.sh
read.sh
test.sh
test.txt
test3.sh
test4.sh
wigToBigWig
```

dirname.txt：

```
RBP_map
a-docker
app
backup
bin
biosoft
c1-RBPanno
datatable
db
download
e-annotation
exRNA
genome
git
highcharts
home
hub29
ibme
l-lwl
map2
mljs
module
mogproject
node_modules
perl5
postar.docker
postar2
postar_app
rout
script
script_backup
software
tcga
test
tmp
tmp_script
var
x-rbp
```
