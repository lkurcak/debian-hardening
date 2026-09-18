# debian-hardening

## sudo

as root:
```
apt install sudo
usermod -aG sudo alice
```

## ssh

### client

```
ssh-keygen
```

add the public key to the server's `~/.ssh/authorized_keys`

### server

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

```
sudo vi /etc/ssh/sshd_config.d/10-hardening.conf
```

```
PasswordAuthentication no
KbdInteractiveAuthentication no
PubkeyAuthentication yes
PermitRootLogin no

# AllowUsers alice@192.168.1.*
```

```
sudo sshd -t
```

```
sudo systemctl reload ssh
```

## unattended-upgrades

```
apt update
apt install unattended-upgrades
```

```
dpkg-reconfigure unattended-upgrades
```

## docker

https://docs.docker.com/engine/install/debian/

```
sudo usermod -aG docker alice
```
