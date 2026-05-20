# Current Implementations
## Nextcloud File Storage\
[Github Link](https://github.com/nextcloud/server)
**Nextcloud** goal is regain control over data. It is an open source google drive alternative which allows for selfhosting.  It gives the user full control over files without sending data to 3rd parties.

Additionally, it allows for **file sync** and **file sharing** between other clients.

I mainly use it for file storage but it includes integrated apps for calendars, contacts, calls, etc.

For my setup, I mounted external drives to my server to allow for me to practice with mounting, expansion, and backups

For more detail & setup, go to [Nextcloud Setup](https://noranguy.github.io/home-lab/nextcloud-setup/)
## Proxy Managing & Cloudflare
To increase security (HTTPS) and setup access outside of my local network, I purchased a domain from cloudflare.

To allow for connecting my server/devices to my domain, I used **cloudflare tunnel**. This allowed me to securely expose my local devices to the internet, without public IP, to cloudflare. cloudflare tunnel allowed me to connect my devices to cloudflare that allows me to access my server apps through an https link and not exposing my ip.

This was the route I choose because my main router is unreachable. Additionally, I struggled with traditional port forwarding setup.

For more detail & setup, go to [Cloudflare Tunneling Setup](https://noranguy.github.io/home-lab/cloudflare-setup/)
## Audiobookshelf - Audiobook library
[Github Link](https://github.com/advplyr/audiobookshelf)
A selfhosted audiobook and podcast server.

## Calibre-Web - Ebook Library
[Github Link](https://github.com/janeczku/calibre-web)
Web application that provides a interface for browsing, reading, and downloading ebooks using a Calibre database. 

## Glance - Home Page & Dashboard
[Github Link](https://github.com/glanceapp/glance)
Customizable Dashboard to display feeds and monitor nicos-home-lab
## Immich - Photo & Video Management
## Jellyfin - Media Server
# General Achievements
- Connected/ mounted external storage devices to access through nextcloud
- Setup up backup drives and back up scripts
- Reboot script to ensure security and precautions for power outages