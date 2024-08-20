# Zsh-Cheatsheet

### View disk usage
```
df -h
```

### Monitor output, interval 1 sec
```
watch -n 1 <command-here>
```

### Move large directory with progress bar
Don't need to define new folder name in new path
```
sudo rsync -r --progress /source/large-directory /destination/new-folder-name/
```
