# Small File Offenders
This perl script helps to inform you of the users that have the most "small files". 
If you are on HDP 2.5+, you do not need a script like this. Why? 
Because HDP 2.5 has a Zeppelin notebook that will help you identify 
what users are contributing to small file volume. This is part of [SmartSense](https://docs.hortonworks.com/HDPDocuments/SS1/SmartSense-1.4.0/index.html).
 Read more 
[here] (https://docs.hortonworks.com/HDPDocuments/SS1/SmartSense-1.3.0/bk_installation/content/activity_analysis.html) on that. 
If you are on an older HDP version, you 

# Why Worry About Small Files?
The HDFS NameNode architecture, explained [here](https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html) mentions that 
"the NameNode keeps an image of the entire file system namespace and file Blockmap in memory." What this means is that 
every file in HDFS adds some pressure to the memory capacity for the NameNode process. Therefore, a larger max heap for 
the NameNode Java process will be required as the files system

# How to use this script
Before beginning, process the image file into TSV format, as shown in this example command:
hadoop oiv -i /hadoop/hdfs/namesecondary/current/fsimage_0000000000003951761 -o fsimage-delimited.tsv -p Delimited
then pipe the output file (fsimage-delimited.tsv) into this program, eg. cat fsimage-delimited.tsv | fsimage_users.pl