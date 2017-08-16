# `automysqlbackup` Large DB Fix

One of our databases would refuse to backup due to its size. Unfortunately, it wasn't throwing any errors to indicate that the backup wasn't completing. It wasn't until we needed the backup that this was discovered.

The fix was adding the flag `--skip-add-lock` to the `mysqldump` command that `automysqlbackup` initiates. It took some digging to figure out how to add the flag without modifying the script directly as the configuration file didn't have a spot for modifying the command flags. I discovered there was a variable in the shell script that held the default flags named `OPT` so I added that line to my configuration file along with the `--skip-add-lock` flag and it worked!

```
# /etc/default/automysqlbackup
OPT="--quote-names --events --skip-add-locks"
```

*Note: This fix applies to the automysqlbackup package installed through Ubuntu's `apt-get` command*
