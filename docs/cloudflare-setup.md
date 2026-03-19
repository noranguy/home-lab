# commands ran in order and descriptions
## installed cloudflared
```Bash
curl -L https://pkg.cloudflare.com/cloudflare-main.gpg | sudo tee /usr/share/keyrings/cloudflare-main.gpg
sudo apt install cloudflared 
```

## logged in
``` Bash
cloudflared tunnel login
```

## created tunnel
``` Bash
cloudflared tunnel create nextcloud
# this gave me a tunnel id i used to configure the config file
```

## edit and create config file
``` Bash
sudo nano /etc/cloudflared/config.yml
```
### config.yml file contents
```yml
tunnel: YOUR_TUNNEL_ID
credentials-file: /etc/cloudflared/YOUR_TUNNEL_ID.json

ingress:
  - hostname: YOUR_DOMAIN.org
    service: http://localhost:80
  - service: http_status:404
//
```
## create record
Allows domain to be routed to the tunnel which is connected to my home-server
``` Bash
cloudflared tunnel route dns nextcloud YOUR_DOMAIN.org
# created a CNAME record in your Cloudflare DNS pointing your domain to the tunnel.
```


## running tunnel as a service
Starts automatically on a boot
``` bash
sudo cloudflared service install
sudo systemctl start cloudflared
sudo systemctl enable cloudflared
```
## checking status
``` bash
sudo systemctl status cloudflared
# tells user if tunneling and connection was successful
```