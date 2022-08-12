10

#!/bin/bash
echo "give me a number or string"
read a
i=$((${#a}-1))
echo ${a:$i:1}
------------------------------------------------

13

#!/bin/bash
echo "Chess Board"

for (( i=1; i<=8; i++))
do
        for (( j=1; j<=8; j++))
        do
                total=$(($i+$j))
                temp=$(($total%2))
                # for alternative blocks
                if [ $temp -eq 0 ]
                then
                        echo -e -n "\033[47m" " "  #white
                else
                        echo -e -n "\033[40m" " " #black
                fi
        done
        echo -e -n "\033[0m" " "
        echo ' '
done
-------------------------------------

nouser=`who | wc -l`
echo -e "User name: $USER (Login name: $LOGNAME)" >> /tmp/info.tmp.01.$$$
echo -e "Current Shell: $SHELL"  >> /tmp/info.tmp.01.$$$
echo -e "Home Directory: $HOME" >> /tmp/info.tmp.01.$$$
echo -e "Your O/s Type: $OSTYPE" >> /tmp/info.tmp.01.$$$
echo -e "PATH: $PATH" >> /tmp/info.tmp.01.$$$
echo -e "Current directory: `pwd`" >> /tmp/info.tmp.01.$$$
echo -e "Currently Logged: $nouser user(s)" >> /tmp/info.tmp.01.$$$
if [ -f /etc/redhat-release ]
then
    echo -e "OS: `cat /etc/redhat-release`" >> /tmp/info.tmp.01.$$$
fi

if [ -f /etc/shells ]
then
    echo -e "Available Shells: " >> /tmp/info.tmp.01.$$$
    echo -e "`cat /etc/shells`"  >> /tmp/info.tmp.01.$$$
fi
echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
echo -e "Computer CPU Information:" >> /tmp/info.tmp.01.$$$ 
echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
cat /proc/cpuinfo >> /tmp/info.tmp.01.$$$

echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
echo -e "Computer Memory Information:" >> /tmp/info.tmp.01.$$$
if [ -f /etc/sysconfig/mouse ]
then
    echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
    echo -e "Computer Mouse Information: " >> /tmp/info.tmp.01.$$$
    echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
    echo -e "`cat 
echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
echo -e "Computer CPU Information:" >> /tmp/info.tmp.01.$$$ 
echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
cat /proc/cpuinfo >> /tmp/info.tmp.01.$$$

echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
echo -e "Computer Memory Information:" >> /tmp/info.tmp.01.$$$ 
echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
cat /proc/meminfo >> /tmp/info.tmp.01.$$$
if [ -d /proc/ide/hda ]
then
    echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
    echo -e "Hard disk information:" >> /tmp/info.tmp.01.$$$ 
    echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
    echo -e "Model: `cat /proc/ide/hda/model` " >> /tmp/info.tmp.01.$$$    
    echo -e "Driver: `cat /proc/ide/hda/driver` " >> /tmp/info.tmp.01.$$$    
    echo -e "Cache size: `cat 
echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
echo -e "File System (Mount):" >> /tmp/info.tmp.01.$$$ 
echo -e "--------------------------------------------------------------------" >> /tmp/info.tmp.01.$$$ 
cat /proc/mounts >> /tmp/info.tmp.01.$$$

if which dialog > /dev/null
then
    dialog  --backtitle "Linux Software Diagnostics (LSD) Shell Script Ver.1.0" --title "Press Up/Down Keys to move" --textbox  /tmp/info.tmp.01.$$$ 21 70
else
    cat /tmp/info.tmp.01.$$$ |more
fi
