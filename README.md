10
#!/bin/bash
echo "give me a number or string"
read a
i=$((${#a}-1))
echo ${a:$i:1}
