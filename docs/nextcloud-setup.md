# Nextcloud Setup
## Install Nextcloud
snap allows for an overall easy install process. Additionally, you can run `hostname -I` to get IP to access nextcloud webpage using http://YOUR_IP_ADDR.
```bash 
sudo snap install nextcloud
```
## Mounting your disks
Mounting/ Unmounting allows for users to manage file systems across multiple drives. 
Mounting attached a drives to a directory which allows you to put files on that drives.
Unmounting disconnects the drive from the computer system.
When mounting, make sure your user has root privileges.
`lsblk` shows all avaliable devices
```bash
lsblk
```
Then, you make the mount point folder & mount the drive
```bash
sudo mkdir /mnt/mydrivedir
sudo mount /dev/drive /mnt/mydrivedir
```
Lastly, I wanted the drives to get mounted everytime my system booted. I configured the /etc/fstab file
```bash
sudo nano /etc/fstab
```
``` bash
# line added to fstab, add per drive
UUID=your-uuid-here  /mnt/mydrivedir  device_format  defaults,nofail  0  2

```
After mounting, make sure you login to nextcloud webpage and properly configure the external storage and mounting through the app. Issues I ran into were making sure I was configuring external storage - ADMIN not external storage - personal. Make sure to download the app for external storage as well. 
## Creating a backup script
For my purposes, I wanted to have a script run weekly to backup my files from my main drive to a backup drive. I setup mnt/backup that holds folders of my nextcloud data & file contents run every sunday at 2am.
```bash
# First I created the script
sudo nano /usr/local/bin/nextcloud-backup.sh
```
Here are my nextclod-backup.sh file contents
```bash
#!/bin/bash
DATE=$(date +%Y-%m-%d)
BACKUP_DIR="/mnt/backup/nextcloud-$DATE"
mkdir -p "$BACKUP_DIR"

echo "Starting Nextcloud backup: $DATE"

# Enable maintenance mode
sudo nextcloud.occ maintenance:mode --on

# Backup data
rsync -avz /mnt/storage/ "$BACKUP_DIR/data/"

# Backup config
rsync -avz /var/snap/nextcloud/common/nextcloud/config/ "$BACKUP_DIR/config/"

# Backup database
sudo nextcloud.export -abc "$BACKUP_DIR/database"

# Disable maintenance mode
sudo nextcloud.occ maintenance:mode --off

echo "Backup complete: $BACKUP_DIR"
```
Finally, I ran a cron exec to allow this script to run on a schedule
```bash
sudo chmod +x /usr/local/bin/nextcloud-backup.sh
# every sunday at 2am
(sudo crontab -l 2>/dev/null; echo "0 2 * * 0 /usr/local/bin/nextcloud-backup.sh >> /var/log/nextcloud-backup.log 2>&1") | sudo crontab -
```
## Configuring Reboot Script
For extra precaution, I want my files to still be accessible when I reboot. I edited my etc/rc.local script to securely rescan my files when my server reboots
```bash
sudo nano /etc/rc.local
```
My rc.local file contents
```bash
#!/bin/bash
# Wait for drives to mount
sleep 10
# mount all drives listed
mount -a
# find and fix all permissions on mounted drives
for d in /mnt/*/; do
        if mountpoint -q "$d"; then
                echo "Setting permissions on $d"
                chown -R root:root "$d"
                chmod -R 775 "$d"
        else
                echo "WARNING: $d is not a mntpt, skipping"
        fi
done

#nextcloud: ensures snap has removeable media access
snap connect nextcloud:removable-media :removable-media

#restore nextcloud ports and restarts
snap set nextcloud ports.http=80 ports.https=443
snap restart nextcloud

#waits for nextcloud to come back
sleep 20
```
I understand there are more efficent ways to run and reboot, but this method works for me. For future implementation, I will look more into improving this.
## Accessing my files outside of my network
To be able to access your files wherever you are, you need to configure your nextcloud webpage with DNS. I did this by using cloudflare and cloudflare tunneling. Check the [cloudflare setup](https://noranguy.github.io/home-lab/cloudflare-setup/) page for the setup. 
# Sources
[Mounting & Unmounting](https://www.geeksforgeeks.org/linux-unix/how-to-mount-and-unmount-drives-on-linux/)