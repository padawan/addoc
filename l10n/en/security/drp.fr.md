+++
url = "/security/pca/"
title = "Activity Continuity Plan"
layout = "faq"
weight = 50
tags = [ "security", "start", "backup" ]
+++

Our architecture is concise in a way that gives you the maximum guarantee on the reservation of your data, in the event of a major incident on our production units.

These guarantees are _not_ optional: they are shipped by default on the platform and all our offerings in bonus.

## Data & Backups

Your user account data is automatically backed up every day, without action from you. [According to the chosen offer](backups), they are kept for up to 30 slippery days.

### Are my data backed up?

Your user account data is automatically backed up every day, without action from you. They are kept for 30 slippery days.

### What data is involved?

All of your user account data is related to the backup:

- files
- databases
- Emails

### Or are these backups located?

These backups are hosted in a datacenter located at several kilometres from the production units. This concept is [contractuelle](https://www.alwaysdata.com/fr/mentions-legales/) (point 4.6 of the hosting conditions).

This datacenter is operated by [Interxion](https://www.digitalrealty.fr/data-centers), while production datacenters are managed by [Equinix](https://www.equinix.com/).

### How can you guarantee access to backups from the user account file system?

Backups can be accessed from your user account file system (via [SSH](remote-access/ssh), [SFTP](remote-access/sftp)…) thanks to the NFS protocol, which allows us to mount read-only, through the network, your access to your backups.

### How can I recover these backups?

You can make a copy of your backups from your user account file system (via [SSH](remote-access/ssh), [SFTP](remote-access/sftp)… by copying the directories located in `$HOME/admin/backup/`.

The `latest` directory is a shortcut to the last available backup.

### How do I restore these backups?

To restore your backups, [check the available documentation](backups).

## Network

### How is access to the network guaranteed?

Each server has two network arrivals. If the main link is broken, the secondary link is automatically activated to keep the connection active.

We set up our network within the datacenters.

### How is Internet access guaranteed?

Our Internet access is guaranteed by four independent access providers.

We are also members of RIPE, have [our own AS60362 number](https://bgpview.io/asn/60362), and our own IP beaches.

## Management Infrastructure

### How are server berries distributed?

Our production servers are divided into several datacenters, several berries, and several rooms.

### What happens in the event of a power cut/failure?

Each server has two power supplies each on fully autonomous circuits (2N), allowing it to remain supplied in the event of a breakdown.

Our datacenters are also equipped with emergency handlers capable of providing several days of power to the infrastructure in the event of a failure of the main network.

### How is the service restored in the event of damage to the boat?

Other servers are available in security, allowing us to quickly switch your services. If necessary, we can also switch to a partner host by redeploying a backup infrastructure with your latest data.

### Are servers redundant?

The data on each server is duplicated on two RAID1 disks, to overcome a failure.

We have a [Gold offer(accounts/billing/private-cloud-prices#serveurs-gold-infogérés) offering synchronized redundancy of servers in sealed data centers to ensure continuity of service.

### Is access to servers secured?

Our datacenters are managed by partners applying strict standards regarding access to the sailor, based on access and biometric authentication permissions.

### What are the guarantees of data centers?

Our production units are hosted by [Equinix](https://www.equinix.com/data-centers/colocation/), the world leader in the International Business Exchange (IBX®️). These datacenters are [certified by many standards](https://www.equinix.com/data-centers/design/standards-compliance/) in quality and security.
