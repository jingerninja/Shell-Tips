## AWK OPERATORS
### AND
```bash
# any order
awk '/pattern1/ && /pattern2/' PATH
# specific order
awk '/pattern1.*pattern2/' PATH			
```

### OR
```bash
awk '/pattern1|pattern2/' PATH
```

### NOT
```bash
awk '!/pattern/' PATH
```

##Examples
* Find all php files whose CONTENTS have changed in the last seven days and look for any strings that don't contain "nextend"
```bash
find -type f -name "*.php" -ctime -7 | sed -n '/nextend/!p'
find -type f -name '*.php' -ctime -7 | awk '!/nextend/'
```

* Actively watch the access log and show all lines containing "POST" but not "404"
```bash
tail -f access_log | sed -n '/POST/!d; /404/!p'
tail -f access_log | awk '/POST/ && !/404/'
```
