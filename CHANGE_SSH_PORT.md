### Change SSH port 
---

#### Before update chack the curret port
```bash
ss -tuln
```
You will get like this output

```txt
Netid   State    Recv-Q   Send-Q           Local Address:Port       Peer Address:Port   Process   
udp     UNCONN   0        0                   127.0.0.54:53              0.0.0.0:*                
udp     UNCONN   0        0                127.0.0.53%lo:53              0.0.0.0:*                
udp     UNCONN   0        0          192.168.64.7%enp0s1:68              0.0.0.0:*                
tcp     LISTEN   0        4096                127.0.0.54:53              0.0.0.0:*                
tcp     LISTEN   0        4096             127.0.0.53%lo:53              0.0.0.0:*                
tcp     LISTEN   0        4096                   0.0.0.0:22              0.0.0.0:*                
tcp     LISTEN   0        4096                      [::]:22                 [::]:*
```

#### Edit ssh configaration file
```bash
nano /etc/ssh/sshd_config
```
Change it to:

```txt
Port 2211
```
#### Restart daemon and services to effect the changes
```bash
sudo systemctl daemon-reload
systemctl restart ssh
systemctl restart ssh.socket
```

#### Now chack the curret port
```bash
ss -tuln
```
You will get like this output

```txt
Netid   State    Recv-Q   Send-Q           Local Address:Port       Peer Address:Port   Process   
udp     UNCONN   0        0                   127.0.0.54:53              0.0.0.0:*                
udp     UNCONN   0        0                127.0.0.53%lo:53              0.0.0.0:*                
udp     UNCONN   0        0          192.168.64.7%enp0s1:68              0.0.0.0:*                
tcp     LISTEN   0        4096                127.0.0.54:53              0.0.0.0:*                
tcp     LISTEN   0        4096             127.0.0.53%lo:53              0.0.0.0:*                
tcp     LISTEN   0        4096                   0.0.0.0:2211            0.0.0.0:*                
tcp     LISTEN   0        4096                      [::]:2211               [::]:*
```

#### Now login by ssh with 2211 port
```bash
ssh root@<SERVER_IP> -p 2211
```
