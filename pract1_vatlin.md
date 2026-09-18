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
nano reg

#!/bin/sh

if [ $# -ne 1 ]; then
    echo "Использование: $0 имя_команды"
    exit 1
fi

if [ ! -f "$1" ]; then
    echo "Ошибка: файл $1 не найден"
    exit 1
fi

chmod 755 "$1"
cp "$1" /usr/local/bin/

echo "Команда $1 зарегистрирована"

chmod +x reg
./reg banner
ls -l banner
ls -l /usr/local/bin/banner
/usr/local/bin/banner "Hello"
```
# Task 6
```

```
