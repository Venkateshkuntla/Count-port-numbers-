# Count-port-numbers-
This code can be used to count and save number of ports open and save to one file and closed ports to another file. 
#!/bin/sh
for port in 22
do
lsof -t -i tcp:$port > pid
count=`wc -l pid | awk -F" " '{print $1}'`
if [ ${count} -gt 1 ]
then
echo $port >>listeningports.txt
else echo $port >> freeport.txt
fi
done
