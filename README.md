# OpenZiti
    1  sudo apt update && apt upgrade
    2  clear
    3  sudo timedatectl set-timezone America/Chicago
    4  sudo apt install net-tools
    5  sudo apt install mlocate
    6  sudo apt install plocate
    8  resolvectl status
    9  vi /etc/hosts
   10  vi /etc/hostname 
   11  route -n
   12  vi /etc/netplan/50-cloud-init.yaml
   13  sudo netplan try
   14  sudo netplan apply
   15  reboot
   17  cd /tmp
   18  curl -sS https://get.openziti.io/install.bash | sudo bash -s openziti
   19  curl -sSLf https://get.openziti.io/tun/scripts/install-ubuntu.bash | bash
   20  sudo systemctl enable --now ziti-edge-tunnel.service
   21  sudo systemctl restart  ziti-edge-tunnel.service
   22  sudo systemctl status  ziti-edge-tunnel.service
   24  export EXTERNAL_DNS="openziti.hungry-howard.com"
   25  export EXTERNAL_IP="$(curl -s eth0.me)" 
   26  export ZITI_CTRL_EDGE_IP_OVERRIDE="${EXTERNAL_IP}"
   27  export ZITI_ROUTER_IP_OVERRIDE="${EXTERNAL_IP}"
   28  export ZITI_CTRL_EDGE_ADVERTISED_ADDRESS="${EXTERNAL_DNS:-${EXTERNAL_IP}}"
   29  export ZITI_ROUTER_ADVERTISED_ADDRESS="${EXTERNAL_DNS:-${EXTERNAL_IP}}"
   30  export ZITI_CTRL_ADVERTISED_PORT=8440
   31  export ZITI_CTRL_EDGE_ADVERTISED_PORT=8441
   32  export ZITI_ROUTER_PORT=8442
   33  source /dev/stdin <<< "$(wget -qO- https://get.openziti.io/ziti-cli-functions.sh)"; expressInstall
   34  startController
   35  startRouter
   36  createControllerSystemdFile
   37  createRouterSystemdFile "${ZITI_ROUTER_NAME}"
   38  stopRouter 
   39  stopController 
   40  sudo cp "${ZITI_HOME}/${ZITI_CTRL_NAME}.service" /etc/systemd/system/ziti-controller.service
   41  sudo cp "${ZITI_HOME}/${ZITI_ROUTER_NAME}.service" /etc/systemd/system/ziti-router.service
   42  sudo systemctl daemon-reload
   43  sudo systemctl enable --now ziti-controller
   44  sudo systemctl enable --now ziti-router
   45  sudo systemctl -q status ziti-controller --lines=0 --no-pager
   46  sudo systemctl -q status ziti-router --lines=0 --no-pager
   47  source ~/.ziti/quickstart/$(hostname -s)/$(hostname -s).env
   48  echo $ZITI_HOME
   49  wget https://github.com/openziti/ziti-console/releases/latest/download/ziti-console.zip
   50  echo $ZITI_HOME
   51  source ${HOME}/.ziti/quickstart/$(hostname)/$(hostname).env
   52  export ZITI_HOME
       apt install unzip
   53  unzip -d ${ZITI_HOME}/zac ./ziti-console.zip  
   57  cd /root/.ziti/quickstart/openziti.hungry-howard.com
   59  vi openziti.hungry-howard.com.yaml
       add the following lines
	     apis:
      # binding - required
      # Specifies an API to bind to this webListener. Built-in APIs are
      #- edge-management
      #- binding: zac
      #   options:
      #     location: ./zac
      #     indexFile: index.html
      #   - edge-client
      #   - fabric-management
      - binding: edge-management
        # options - arg optional/required
        # This section is used to define values that are specified by the API they are associated with.
        # These settings are per API. The example below is for the 'edge-api' and contains both optional values and
        # required values.
        options: { }
      - binding: edge-client
        options: { }
      - binding: fabric
        options: { }
      - binding: zac
        options:
          location: ./zac
          indexFile: index.html
   60  sudo systemctl restart ziti-controller.service
   61  sudo systemctl status  ziti-controller.service      
   

