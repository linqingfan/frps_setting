# frps_setting

## server side
### Setting systemd frps service
create a file frps.service in /etc/systemd/system with the content as follows:
```
[Unit]
Description=FRP server service
Wants=network-online.target
After=network-online.target

[Service]
ExecStart=/usr/local/.frp/start_frps.sh
Restart=always
RestartSec=5s

[Install]
WantedBy=multi-user.target
```
### Install frps
```
sudo mkdir /usr/local/.frp
```
copy frps executables into the folder

### create frps.ini
create frps.ini with the content:
```
[common]
bind_port = 80
```
### create start_frps.sh
create start_frps.sh with the content:
```
#!/bin/sh
/usr/local/.frp/frps -c /usr/local/.frp/frps.ini
```
### Firewall Setting
Open the port 443 and 80

For Alicloud it is at Security -> firewall
