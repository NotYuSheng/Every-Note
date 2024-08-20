# VMware Notes

### Adding Storage (Linux)
1. **Clean machine with no snapshot required**

2. **VM > Settings > Hard Disk (SCSI) > Expand ...**

3. **Install Partition Tool**
```
sudo apt-get update
sudo apt-get install gparted
```

4. **Partition**
```
sudo gparted
```

### Install Windows 11 Without Logging In
1. **Turn Off Internet**
   - VM > Settings > Network Adapter

2. **Boot ISO**
   - Use `Shift + F10` to open Command Prompt.

3. **Bypass Login**
   - Enter the following command:
     ```cmd
     oobe\bypassnro
     ```
