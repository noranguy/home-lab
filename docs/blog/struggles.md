# Errors I ran into
Hopefully, you can avoid the mistakes I made or learn from them!
## DNS/ Cloudflare
- had some 1016 errors due to records being configured wrong which messed with my DNS settings
- ran into port forwarding issue but then came across cloudflare tunneling which fixed them entirely
## Nextcloud
- Ran into simple configuring issues from setting up the external storage drives on the nextcloud webpage. This was due to the fact that netcloud has two tabs for external storage, one for user and one for admin. Use admin
- permission issues that didn't allow me to add files from webpage, but fine in terminal (set permissions for drives as www:data instead of www:root)
- mnt and unmnt during reboot
- losing files during forced shutdown or power outage
- Setting up Nextcloud office. Just dont... I had so many issues and confusion setting up the database and connections to simply open and edit within nextcloud. I ended up using the Only Office plugin and that was much easier
## Reverse Proxy
Setting up NPM was a bit of a time especially due to my prior cloudflare tunneling setup. This was because my VPN and proxy settings kepy getting hijacked my cloudflare because it was going throught the tunnel.
- Make sure to not have other services taking your domain request.
## Jellyfin
Save your config files because if you ever docker compose restart... they'll disappear. Meaning the plugins and metadata you added will need to be added again.


