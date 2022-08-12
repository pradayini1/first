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

15

#!/bin/bash
<<COMMENT
Print Informations:
1. Currently logged user
2. Your shell directory
3. Home directory
4. OS name and version
5. Current working directory
6. Number of users logged in
7. Show all available shells in your system
8. Hard disk information
9. CPU information
10. Memory information
11. file system information
12. Currently running process
COMMENT

echo "Enter the option from 1-13 to get the particular information:
1. Currently logged user
2. Your shell directory
3. Home directory
4. OS name and version
5. Current working directory
6. Number of users logged in
7. Show all available shells in your system
8. Hard disk information
9. CPU information
10. Memory information
11. file system information
12. Currently running process"

echo -n "Choice: " ; read option

case $option in
	1) # prints the names of the users currently logged in to the current host without showing any information about source, login time, or any other relevant information 
	   echo "Currently logged user:"; users;
	   ;;
	2) #gives shell name relative to root
	   echo "Your shell directory: $SHELL"
	   ;;
	3) echo "Home directory: $HOME"
	   ;;
	4) echo -n "operating system name is:  "; uname -s ; #uname
  	   echo -n "operating system version is:  "; uname -v
	   echo -n "operating system release is:  "; uname -r
        #echo -n network hostname: ; uname -n
	   #echo -n hardware name: ; uname -m
     	   ;; 
	5) echo "Current working directory: $PWD"
   	   ;;
	6) echo -n "Number of users logged in is: "
   	   who -u | wc -l
	   #who -q
	   ;;
	7) cat /etc/shells | grep -v "#"
	   ;;
	8) echo "Hard disk information:"
        diskutil list #in MAC
        #for further detailed information of each physical disk
        diskutil info disk0
        diskutil info disk1

        #sudo lshw -short
	    #sudo hdparm -I /dev/sda
	   ;; 
	9) echo "CPU information:"
        #in MAC
        echo "Chip Brand – Processor Type and Chip Model – CPU Speed"
        sysctl -n machdep.cpu.brand_string

        #CPU details
        sysctl -a | grep machdep.cpu
        #CPU Processor Details of a Mac with system_profiler
        #system_profiler

        #sudo lscpu
	   #cat /proc/cpuinfo
	   ;;
	10)echo "Memory information:"
        #in MAC
        sysctl -a | grep mem

        #cat /proc/meminfo
	   ;;
	11)echo "file system information:"
	   df -H
	   #fdisk -1 ; mount
	   ;;
	12)echo "Currently running process:"
	   ps
 	   #gives currently running process dynamically
	   #top 
	   ;; 
	*)echo "Invalid option:"
	   ;;
esac
------------------------------------------------
	  14
	  
	  #!/bin/bash
echo "give 5 number and orderd or underderd array"
read a b c d e f g

arr=($a $b $c $d $e)

echo "Array in original order"
echo ${arr[*]}

for ((i = 0; i<5; i++))
do

    for((j = 0; j<5-i-1; j++))
    do

        if [ ${arr[j]} -gt ${arr[$((j+1))]} ]
        then
            # swap
            temp=${arr[j]}
            arr[$j]=${arr[$((j+1))]}
            arr[$((j+1))]=$temp
        fi
    done
done

echo "Array in sorted order :"
echo ${arr[*]}

echo "Array in sorted order :"
echo ${arr[*]} | rev
------------------------------------------------------------
21

#!/bin/bash

hour=`date +%c | tr -s " " | cut -d " " -f4 | cut -d ":" -f1`   
day=`date +%A`  
mon=`date +%B`  
dte=`date +%d`  
year=`date +%Y`  
tf=`date +%r`    
if [ $hour -ge 5 -a $hour -lt 12 ]  
then
        echo -e "Good morning `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
elif [ $hour -ge 12 -a $hour -le 13 ]   
then
        echo -e "Good noon `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
elif [ $hour -ge 14 -a $hour -lt 17 ]  
then
        echo -e "Good afternoon `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
elif [ $hour -ge 17 -a $hour -lt 21 ]   
then
        echo -e "Good evening `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
elif [ $hour -ge 21 -o $hour -lt 5 ]   
then
        echo -e "Good night `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
fi

