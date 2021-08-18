---
title: Nginx CLI
---

# Nginx CLI comamnds (tested on ubuntu linux 20.04)

## Info

### Show Version

```
nginx -v 
```

### Show Version and Config Options

```
nginx -V
```

### Check Config Syntax

```
sudo nginx -t
```

### Check Config Syntax and Dump the Configuration File

```
sudo nginx -T
```

### Check Nginx Service Status

```
sudo systemctl status nginx #systemd
OR
sudo service nginx status   #sysvinit
```

### Show Nginx's Command Help

```
systemctl -h nginx
```

## Running Nginx

### Start Nginx

```
sudo systemctl start nginx #systemd
OR
sudo service nginx start   #sysvinit
```

### Enable Nginx

```
sudo systemctl enable nginx #systemd
OR
sudo service nginx enable   #sysv init
```

### Restart Nginx

```
sudo systemctl restart nginx #systemd
OR
sudo service nginx restart   #sysv init
```

### Reload Nginx's Configurations

```
sudo systemctl reload nginx #systemd
OR
sudo service nginx reload   #sysvinit
```

### Stop Nginx

```
sudo systemctl stop nginx #systemd
OR
sudo service nginx stop   #sysvinit
```
