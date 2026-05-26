# Current Implementations
All stored in docker container and seperate docker-compose.yml files for organization, functionality, and my personal sanity.
## Nextcloud File Storage
[Github Link](https://github.com/nextcloud/server)  
**Nextcloud** goal is regain control over data. It is an open source google drive alternative which allows for selfhosting.  It gives the user full control over files without sending data to 3rd parties.

For more detail & setup, go to [Nextcloud Setup](https://noranguy.github.io/home-lab/nextcloud-setup/)

## Audiobookshelf
[Github Link](https://github.com/advplyr/audiobookshelf)  
A selfhosted audiobook and podcast server.

## Calibre-Web
[Github Link](https://github.com/janeczku/calibre-web)  
Web application that provides a interface for browsing, reading, and downloading ebooks using a Calibre database. 

## Glance
[Github Link](https://github.com/glanceapp/glance)  
Customizable Dashboard to display feeds and monitor nicos-home-lab

## Immich
[Github Link](https://github.com/immich-app/immich)  
Self-hosted photo and video management

## Jellyfin
[Github Link](https://github.com/jellyfin/jellyfin)  
Media manager and streamer

## Nginx Proxy Manager
[Github Link](https://github.com/NginxProxyManager/nginx-proxy-manager)  
Manager of reverse proxies with SSL termination

# External Services
## Tailscale
[Service Link](https://tailscale.com/)  
Configuring a VPN for all my devices.
Allows me to securely access my server and services no matter where I am.  
## Cloudflare
[Service Link](https://www.cloudflare.com/)  
Powers 20% of the internet. Bought and configure my DNS records through their dashboard.

To increase security (HTTPS) and setup access outside of my local network, I purchased a domain from cloudflare.

Orignally, I used **cloudflare tunnel**. This allowed me to securely expose my local devices to the internet, without public IP, to cloudflare. cloudflare tunnel allowed me to connect my devices to cloudflare that allows me to access my server apps through an https link and not exposing my ip. This does exposes your domain to the internet which could leave you vulnerable. 

For more detail & setup, go to [Cloudflare Tunneling Setup](https://noranguy.github.io/home-lab/cloudflare-setup/)
# General Achievements
- Connected/ mounted external storage devices to access through nextcloud
- Setup up backup drives and back up scripts
- Reboot script to ensure security and precautions for power outages