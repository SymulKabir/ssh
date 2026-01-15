### Install and configare SSH in ubuntu
---
#### Clear previous installation

```bash
sudo apt purge openssh-server
sudo apt purge openssh-client
```

#### Install openssh-server

```bash
sudo apt install openssh-server
```
#### Install openssh-client

```bash
sudo apt install openssh-server
```

#### Allow root login

```bash
sudo nano /etc/ssh/sshd_config
```
Find `PermitRootLogin`

```txt
PermitRootLogin yes
```

#### Restart SSH
```bash
sudo systemctl restart ssh
```