# Git Branch Clean-up

Over time people may forget to clean up their old branches that have been
merged. This is an easy way to clean stuff up.

## Local Branches
```
git branch --merged | egrep -v "(^\*|master)" | xargs git branch -d
```

## Remote Branches
```
git branch -r --merged | egrep -v "(^\*|master)" | sed 's/origin\///' | xargs -n 1 git push --delete origin
```

[Source](https://stackoverflow.com/questions/6127328/how-can-i-delete-all-git-branches-which-have-been-merged#6127884)
