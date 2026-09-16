# 1
```
[root@localhost etc]# cut -d ":" -f 1 passwd | sort
```
# 2
```
[root@localhost etc]# /bin/cat /etc/protocols | awk '!/^#/ && NF >= 2 {print $2,
 $1}' | sort -nr | head -5
```
