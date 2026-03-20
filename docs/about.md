# About 
Mainly just playing with homelab/ server hosting! A personal project started 3/14/26!
# What I learned
A journel of sorts of my process
## DNS/ Cloudflare
DNS or domain name system is distributed naming system that takes domain names to ip addresses. 

1. user requests
2. host files are checked
3. query is run and searhed to find dns if not found locally
4. returns ip to computer
## Nextcloud
Make sure to test without having much files in the server yet. A lot of trial and error with some random test files were lost, but it allowed me to feel more confident building a server where I won't lose my files.
I learned about mounting and unmounting. Additionally, I learned about creating scripts and execs to run. Finally, I learned nextcloud is an overall all-in-one jack of all trades, master of none. After more research, I might consider switching to seafile.
# Errors I ran into
## DNS/ Cloudflare
- had some 1016 errors due to records being configured wrong which messed with my DNS settings
- ran into port forwarding issue but then came across cloudflare tunneling which fixed them entirely
## Nextcloud
- Ran into simple configuring issues from setting up the external storage drives on the nextcloud webpage
- permission issues that didn't allow me to add files from webpage, but fine in terminal (set permissions for drives as www:data instead of www:root)
- mnt and unmnt during reboot
- losing files during forced shutdown or power outage
