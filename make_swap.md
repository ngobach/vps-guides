Check the System for Swap Information
====

```
sudo swapon -s
```

Result should be

```
Filename                Type        Size    Used    Priority
```

Making swap file
====

```
# Double of memory size :)
sudo fallocate -l 2G /swapfile
```

Enabling the Swap File
====

```
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

Check the result

```
sudo swapon -s
```
```
free -m
```

Make the Swap File Permanent
====

```
sudo nano /etc/fstab
```

At the bottom of the file, you need to add a line that will tell the operating system to automatically use the file you created:

```
/swapfile   none    swap    sw    0   0
```

Tweak your Swap Settings
====

```
sudo nano /etc/sysctl.conf
```

At the bottom, you can add:

```
vm.swappiness=10
vm.vfs_cache_pressure = 50
```

[Original](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
