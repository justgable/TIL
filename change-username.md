# Change Username (Not current user) 

```
killall -u oldname
sudo usermod -md /home/newname -l newname oldname
sudo groupmod -n newname oldname
```

Create another temporary user account to change your own username.

[Source](https://askubuntu.com/a/912978)
