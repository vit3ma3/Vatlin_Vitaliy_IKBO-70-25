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
    echo "Usage: $0 command_name"
    exit 1
fi

if [ ! -f "$1" ]; then
    echo "Error: file $1 not found"
    exit 1
fi

chmod 755 "$1"
cp "$1" /usr/local/bin/

echo "Command $1 is registered"

chmod +x reg
./reg banner
ls -l banner
ls -l /usr/local/bin/banner
/usr/local/bin/banner "Hello"
```
# Task 6
```
nano check_comments

#!/bin/sh

find . -type f \( -name "*.c" -o -name "*.js" -o -name "*.py" \) | while read file
do
    first=$(head -n 1 "$file")

    case "$file" in
        *.py)
            echo "$first" | grep -q '^[[:space:]]*#'
            ;;
        *.c|*.js)
            echo "$first" | grep -q '^[[:space:]]*\(//\|/\*\)'
            ;;
    esac

    if [ $? -eq 0 ]; then
        echo "$file: there is a comment"
    else
        echo "$file: no comment"
    fi
done

chmod +x check_comments
./check_comments
```
# Task 7
```
nano duplicates

#!/bin/sh

find "$1" -type f -exec md5sum {} \; |
sort |
awk '
{
    files[$1] = files[$1] "\n" $2
}
END {
    for (hash in files) {
        n = split(files[hash], a, "\n")
        if (n > 1) {
            print "Duplicates:"
            for (i = 2; i <= n; i++)
                print a[i]
            print ""
        }
    }
}'

chmod +x duplicates
./duplicates
```
# Task 8
```
nano archive_files

#!/bin/sh

if [ $# -ne 1 ]; then
    echo "Usage: $0 extencions"
    exit 1
fi

ext="$1"
archive="files.tar"

find . -type f -name "*.$ext" > filelist

if [ ! -s filelist ]; then
    echo "Files with extencions .$ext not found"
    rm -f filelist
    exit 1
fi

tar -cf "$archive" -T filelist

rm -f filelist

echo "Files .$ext added to $archive"

chmod +x archive_files
./archive_files txt
tar -tf files.tar
```
# Task 9
```
nano spaces_to_tabs

#!/bin/sh

if [ $# -ne 2 ]; then
    echo "Usage: $0 input_file output_file"
    exit 1
fi

sed 's/    /\t/g' "$1" > "$2"
```
#Task 10
```
nano empty_files

#!/bin/sh

if [ $# -ne 1 ]; then
    echo "Использование: $0 директория"
    exit 1
fi

find "$1" -type f -size 0 -print

chmod +x empty_files
./empty_files .
```
