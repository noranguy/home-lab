# Cloudflare Setup
## Installed cloudflared
```Bash
curl -L https://pkg.cloudflare.com/cloudflare-main.gpg | sudo tee /usr/share/keyrings/cloudflare-main.gpg
sudo apt install cloudflared 
```

## Logged in
``` Bash
cloudflared tunnel login
```

## Created tunnel
``` Bash
cloudflared tunnel create nextcloud
# this gave me a tunnel id i used to configure the config file
```

## Edit and Create Config file
``` Bash
sudo nano /etc/cloudflared/config.yml
```
### Config.yml file contents
```yml
tunnel: YOUR_TUNNEL_ID
credentials-file: /etc/cloudflared/YOUR_TUNNEL_ID.json

ingress:
  - hostname: YOUR_DOMAIN.org
    service: http://localhost:80
  - service: http_status:404
//
```
## Create record
Allows domain to be routed to the tunnel which is connected to my home-server
``` Bash
cloudflared tunnel route dns nextcloud YOUR_DOMAIN.org
# created a CNAME record in your Cloudflare DNS pointing your domain to the tunnel.
```


## Running tunnel as a service
Starts automatically on a boot
``` bash
sudo cloudflared service install
sudo systemctl start cloudflared
sudo systemctl enable cloudflared
```
## Checking status
``` bash
sudo systemctl status cloudflared
# tells user if tunneling and connection was successful
```