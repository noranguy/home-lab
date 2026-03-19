# nicos-home-lab
Documentation of my progress building my personal server/ home lab. 

# Current Status
Currently in the bare bones beginning of this setup. 

# Setup
- 2017 HP Pavilion All-In-One Desktop
  - Intel Core i5
  - 1TB HDD
  - Windows 10
  - Using Ubuntu Server OS
- 3TB HD HDD
  -  USB connected
- 256 SSD
    - USB connected
- GL. inet ac1300 Travel Router
- NetGear GS605 LAN Switch
- QNAP HDD SATA enclosure (not in use)
   - No drives yet

# Current Implementations
## Physical Implementations
- Connected external drives to USB
- Setup Ubuntu OS flashed through a CD
- Configured SFTP & SSH
## Nextcloud File Storage
### General Achievements
- Connected/ mounted external storage devices to access through nextcloud
- Setup up backup drives and back up scripts
- Reboot script to ensure security and precautions for power outages
### Proxy Managing & Cloudflare
To increase security (HTTPS) and setup access outside of my local network, I purchased a domain from cloudflare.

To allow for connecting my server/devices to my domain, I used **cloudflare tunnel**. This allowed me to securely expose my local devices to the internet, without public IP, to cloudflare. cloudflare tunnel allowed me to connect my devices to cloudflare that allows me to access my server apps through an https link and not exposing my ip.

This was the route I choose because my main router is unreachable. Additionally, I struggled with traditional port forwarding setup.

for more detail & setup, go to [cloudflare tunneling setup](https://noranguy.github.io/home-lab/Cloudflare-Setup)

# Planned Implementations
1. Jellyfin Media Server
2. Photo Galleries
    - replacement for google photos
3. BookLore
    - host and manage books

# Sources/ Resources
[awesome-selfhosted](https://awesome-selfhosted.net/)
[configuring-mkdocs-w/-github-pages](https://www.youtube.com/watch?v=pFG7Mpccgqk)
[cloudflare](https://developers.cloudflare.com/tunnel/)