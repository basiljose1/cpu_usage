# SCRIPT TO MONITOR CPU, MEMORY AND DISK USAGE.

This bash/shell script is going to output a table with four columns showing date and the percentages of Memory, Disk and CPU used on our machine. The script is going to run for a certain amount of time every 1 second and save the date to a log file in a table form. Later on, the data file can then be imported into an Microsoft Excel sheet for analysis and graphing.

Let’s get started!

The script is basically made up of three main parts:

#1- Memory:

free -m | awk 'NR==2{printf "%.2f%%\t\t", $3*100/$2 }'
9.24%

#2- Disk:

df -h | awk '$NF=="/"{printf "%s\t\t", $5}'
7%

#3- CPU

top -bn1 | grep load | awk '{printf "%.2f%%\t\t\n", $(NF-2)}'

You can always output the data to a log file:


[root@localhost]# ./cpu_usage.sh >> log.txt

Once the data is ready, you can use Microsoft Excel to import the data into a table and use Excel’s graphing capabilities to view the changes.

