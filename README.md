# OpenZiti
```
sudo apt update && apt upgrade
```
```
sudo timedatectl set-timezone America/Chicago
```
```
sudo apt install net-tools
```
```
sudo apt install plocate
```
```
sudo apt install plocate
```
```
resolvectl status
```
```
vi /etc/hosts
```
```
vi /etc/hostname
```
```
route -n
```
```
vi /etc/netplan/50-cloud-init.yaml
```
```
sudo netplan try
```
```
sudo netplan apply
```
```
reboot
```

### Open Ports

8440/tcp: edge controller providing router control plane

8441/tcp: edge controller providing client sessions

8442/tcp: edge router providing client connections

8443/tcp: Ziti Admin Console (ZAC) [optional]

Change directory

```
cd /tmp
```
```
curl -sS https://get.openziti.io/install.bash | sudo bash -s openziti
```
```
curl -sSLf https://get.openziti.io/tun/scripts/install-ubuntu.bash | bash
```
```
sudo systemctl enable --now ziti-edge-tunnel.service
```
```
sudo systemctl restart  ziti-edge-tunnel.service
```
```
sudo systemctl status  ziti-edge-tunnel.service
```
### expressInstall Setup

```
export EXTERNAL_DNS="openziti.hungry-howard.com"
```
```
export EXTERNAL_IP="$(curl -s eth0.me)"
```
``` 
export ZITI_CTRL_EDGE_IP_OVERRIDE="${EXTERNAL_IP}"
```
```
export ZITI_ROUTER_IP_OVERRIDE="${EXTERNAL_IP}"
```
```
export ZITI_CTRL_EDGE_ADVERTISED_ADDRESS="${EXTERNAL_DNS:-${EXTERNAL_IP}}"
```
```
export ZITI_ROUTER_ADVERTISED_ADDRESS="${EXTERNAL_DNS:-${EXTERNAL_IP}}"
```
```
export ZITI_CTRL_ADVERTISED_PORT=8440
```
```
export ZITI_CTRL_EDGE_ADVERTISED_PORT=8441
```
```
export ZITI_ROUTER_PORT=8442
```
```
source /dev/stdin <<< "$(wget -qO- https://get.openziti.io/ziti-cli-functions.sh)"; expressInstall
```
```
startController
```
```
startRouter
```
```
createControllerSystemdFile
```
```
createRouterSystemdFile "${ZITI_ROUTER_NAME}"
```
```
stopRouter
```
```
stopController
```
```
sudo cp "${ZITI_HOME}/${ZITI_CTRL_NAME}.service" /etc/systemd/system/ziti-controller.service
```
```
sudo cp "${ZITI_HOME}/${ZITI_ROUTER_NAME}.service" /etc/systemd/system/ziti-router.service
```
```
sudo systemctl daemon-reload
```
```
sudo systemctl enable --now ziti-controller
```
```
sudo systemctl enable --now ziti-router
```
```
sudo systemctl -q status ziti-controller --lines=0 --no-pager
```
```
sudo systemctl -q status ziti-router --lines=0 --no-pager
```

```
echo $ZITI_HOME
```

### Ziti Admin Console
```
wget https://github.com/openziti/ziti-console/releases/latest/download/ziti-console.zip
```
```
echo $ZITI_HOME
```
```
source ${HOME}/.ziti/quickstart/$(hostname)/$(hostname).env
```
```
export ZITI_HOME
```
```
apt install unzip
```
```
unzip -d ${ZITI_HOME}/zac ./ziti-console.zip
```
```
cd /root/.ziti/quickstart/openziti.hungry-howard.com
```
```
vi openziti.hungry-howard.com.yaml
```

# add the following lines 

Thi would be under  the section called - binding: edge-management
	     
```
      - binding: zac
        options:
          location: ./zac
          indexFile: index.html
```
```
sudo systemctl restart ziti-controller.service
```
```
sudo systemctl status  ziti-controller.service
```   
   

