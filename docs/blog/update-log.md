# Prior Updates
## 3/20/26
Currently in the bare bones beginning of this setup. Making some steady progress. Nextcloud is configured properly. Want to properly integrate photo backup and access. Access through secure url works!
## 5/20/26 
Added multiple containers and moved services previously implemented to docker containers. Total list of added containers detailed below. Still using the same hardware, but I implemented using the QNAP HDD Enclosure to house a 1 TB HDD I found from a used DVR. Looking to upgrade my desktop to increase overall internal capabilities, acquire more HDDs to implement RAID, and upgrade my older QNAP NAS to a Hardware RAID implemented DAS.
My overall experience with my home server has been really exciting, and I consantly have new things I want to implement/ improve for this system. I understand why people say that home labs are a rabbit hole of learning and information. I look forward to continuing to update this as my progress continues.
## 5/25/26 
Retired the 2TB WD drive with 2 1TB 2.5" WD Blue drives. RAID 1 is configured with both the newer drives. I moved the data that was on the older drive to the newer drives. After that, I conducted a SMART scan on all my currently used drives. I found my other externally mounted drives (3tb and 256gb) are showing signs of age and warning as well. Due to this, I am slowly leaning away from those drives before failure. I recently purchased a 4TB NAS Ironwolf Seagate NAS HDD for $170 (ouch.) I've read that I probably should maximize the storage potential, but I am still a college student and I am sure I'm not going to fill up 4TB immediately. 

I configured Nginx Reverse Proxy Manager! Orignally, I had my services exposed through cloudflare tunneling to allow me to access my services with a nice domain url and when I am not connected to my network; however, I quickly learned that is not the most optimal and secure way to access my services. I sat down and configured the reverse proxy, tailscale, and cloudflare to allow me to securely access my services whether or not I am home. As long as I am connected to my tailscale network through my VPN, I can access my services. This was frustrating to configure at first, but I will note that down in my setup guides and errors I ran into.

I'm backing up my photos to an offsite backup first because... I ran out of google cloud storage (omg shocker right). I don't want to pay the recurring service anymore, so I'm using google takeout to all me to free up storage on my account, but still have my photos in a safe place. Slowly, I'll upload them to immich. 

Current plans are to slow down with the services I am adding.
I do want to implement ad blocking throughout my network and the infamous *arr stack, but I realize I should start actively using my services before I continue to add more.
Additionally, I really wish to upgrade my specs. The drive failure scares were a warning to me that I should look to more suitable options. I plan on replacing my main processing unit with a more suitable and newer device like a Dell optiplex. Afterwards, I want to upgrade my older NAS to a QNAP DAS as I do not need the network capabilities of a NAS when I can connect to my services through my own setup network.

## 5/26/26
The 4TB drive came in today!!
I have spent the past 4 hrs copying over data, and reconfiguring raid. For future reference, if youre running an older system of QTS. Don't move the drives. RAID will be unliked and your share folders will mess up. Thankfully, the data is still all there it is just not easily accessible. I had to SSH into my QTS and initate a transfer to a new shared folder.  
1:26am update so technidally the 27th. Started my ~300gb transfer for my google photos/ meta data. Thankfully, the NVME drive I have that stores the TAR files from google takeout made transfer to my server easy. I had some trouble uploading to immich UI.

The commands i used for a bulk upload are logging into my immich account using my API key
immich login http://localhost:2283 APIKEY

immich upload --recursice /path/to/folder

hashes, checks duplicates, and uploads.
next time, im going to upload directly from a different folder instead of move everything into library admin. Will update on outcome. 

## 6/9/26
Got a new Dell Optiplex 7050 SFF. Currently configuring proxmox on it. I added a 1 TB NVME to it! Im using it as a storage pool for future containers and VMs. Tailscale is configured on nicos-beefy-server. i need to upgrade the ram eventually because it is sitting at 8GBs. Thanks!