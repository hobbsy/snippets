# Add current date and time to filename

Use `date`

Reference page on Arch Wiki:  
* https://man.archlinux.org/man/date.1
* https://www.gnu.org/software/coreutils/manual/html_node/date-invocation.html#date-invocation


--

example:

copy current aliases into text file with current date and time in filename

`alias >> $(date +%Y%m%d-%H%M)-alias.txt`

gives: 
20210328-1739-alias.txt

or with seconds:

`alias >> $(date +%Y%m%d-%H%M%S)-alias.txt`

--

Script to append date and time to a filename, from user tatojo on StackOverflow
https://stackoverflow.com/a/64018224
(slightly edited for my needs):

**dateadd.sh**

`nano dateadd.sh`

```
#!/bin/bash

now=$(date +"%Y%m%d-%H%M")
FILE="$1"
name="${FILE%.*}"
ext="${FILE##*.}"

# cp -v $FILE $name-$now.$ext
mv -v $FILE $name-$now.$ext
```

`chmod +x dateadd.sh`

run with

`./dateadd.sh testfilename.txt`

results

`testfilename-20210328-1738.txt`

can move into `.local/bin/` so it is in the PATH to execute from anywhere?

`cp dateadd.sh ~/.local/bin/dateadd`


```
cd
touch testing.txt
dateadd testing.txt
```



