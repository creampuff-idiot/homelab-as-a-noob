# homelab-as-a-noob
Trying.
## Hardware

### beepboop (primary server — Proxmox VE)
- CPU: Intel Core Ultra 5 225
- Motherboard: ASRock B860I WiFi (mini-ITX)
- RAM: Corsair Vengeance DDR5-6000 32GB
- Cooler: Noctua NH-D9L
- PSU: SilverStone Extreme 550Rz SFX Gold
- Case: Jonsbo N3
- Storage: 2x Seagate IronWolf Pro 8TB (ZFS mirror), + NVMe boot SSD

### gregory (legacy server)
- Secondhand HP desktop, i5 vPro 2nd Gen
- OS: Debian + Docker
- Running: Samba, Jellyfin, Immich, Tailscale
- Status: being phased out / replaced by beepboop

## Network
- Adding V-Lan to iot devices, and a vpn down the line.


## Software stack

| Service   | Host     | Status      |
|-----------|----------|-------------|
| Proxmox VE| beepboop | Installed   |
| ZFS pool  | beepboop | Configured  |

So far.

## ZFS Pool
2x 8tb Iron Wolf Pro NAS, named the pool icarus mirror, ashift 12, lz4, addtional storage ticked status is healthy.

## Progress log

- [x] Sourced beepboop hardware
- [x] Installed Proxmox VE
- [x] Disabled enterprise repo, added no-subscription
- [x] Created ZFS mirror (`icarus`, RAID1, ashift 12, lz4, additonal storage)
- [ ] Create non-root admin user
- [ ] Set up backups
- [ ] Migrate services from gregory (LXC vs Docker VM — TBD)
- [ ] iGPU passthrough for Quick Sync transcoding
- [ ] VLANs + OPNsense

## Decisions

- **Proxmox over bare Debian/Docker for beepboop**: wanted proper VM/container management and snapshots as the lab grows.
- **ZFS mirror over single disk**: redundancy for the 8TB drives holding media/photos.
- **Fresh Proxmox build rather than migrating gregory directly**: cleaner slate, avoid carrying over Debian-specific config and gregory never fully had all the data just a test bed. 
