# Task 1
```
[root@localhost etc]# cut -d ":" -f 1 passwd | sort
```
# Task 2
```
[root@localhost etc]# /bin/cat /etc/protocols | awk '!/^#/ && NF >= 2 {print $2,
 $1}' | sort -nr | head -5
```
# Task 3
```
nano banner

#!/bin/sh

string="$1"
length=${#string}
echo -n "+"
i=0
while [ $i -lt $((length + 2)) ]
do
        echo -n "-"
        i=$((i + 1))
done
echo "+"

echo "| $string |"

echo -n "+"

i=0
while [ $i -lt $((length + 2)) ]
do
        echo -n "-"
        i=$((i + 1))
done
echo "+"

chmod +x banner
./banner "Hello from RTU MIREA!"
```
# Task 4
```
nano identifiers

#!/bin/sh

file="$1"
sed '/\/\*/,/\*\//d' "$file" |
grep -oE '[A-Za-z_][A-Za-z0-9_]*' | sort -u | xargs

./identifiers hello.c
```
# Task 5
```

```
