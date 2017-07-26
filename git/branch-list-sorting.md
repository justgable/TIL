# Git Branch List Sorting

## By Committer Date
```
// or using git branch (since version 2.7.0)
git branch --sort=-committerdate  # DESC
git branch --sort=committerdate  # ASC

// alternative (and supports older versions of git)
git for-each-ref --sort=-committerdate refs/heads/
```

### Advanced/Prettified Sort by Committer Date

```
git for-each-ref --sort=committerdate refs/heads/ --format='%(HEAD) %(color:yellow)%(refname:short)%(color:reset) - %(color:red)%(objectname:short)%(color:reset) - %(contents:subject) - %(authorname) (%(color:green)%(committerdate:relative)%(color:reset))'
```

[Source](https://stackoverflow.com/a/5188364) | 
[List of sort keys](https://www.kernel.org/pub/software/scm/git/docs/git-for-each-ref.html#_field_names)
