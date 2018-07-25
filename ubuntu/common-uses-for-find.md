# Common Uses for `find` (Unix)

Find is an very useful command to find files based on a set of criteria. It can also be used to perform mass deletions of files without spawning another task for each result. These are just some of the basic ways I've been using it recently. `man find` obviously has a lot more detailed information than what I've included, this is primarily just for me.

## Finding files

### By name
```
find . -name '.DS_Store'
find . -iname '.ds_store'
```

### By size
```
# Files over 5MB
find . -size +5M

# Files under 100KB
find . -size -100k
```

### By date

```
# find all files and directories in current directory that have an inode change
# time within the last 10 days
find . -newerct '10 days ago' -print -depth 1

# find all files that have a newer created date than myfile.txt 2 levels deep
find . -newer myfile.txt -depth 2
```

## Extras with `find`

### Delete

```
find . -name '.DS_Store' -delete
```
**Warning:** omit the `-delete` flag and run `find` command to verify what
files will ultimately be deleted.

### Custom commands
```
# Find all files over 5MB and run `ls -lah` with results
find . -size +5M -exec ls -lah {} \;

# Similar to using -delete but less performant
find . -name '.DS_Store' -exec rm {} \;
```
