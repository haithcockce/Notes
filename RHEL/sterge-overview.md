# Overview

### Concepts
* A fc switch is like a net switch for fc
* H:B:T:L - Host, Bus, Target, LUN
* _WWID_ World Wide Unique ID, identifies the LUNs (disks)
 

### Troubleshooting Steps

##### Bottom of the stack
* Where my LUNs at? Rescan and still doesn't show up?
* Check `/proc/scsi/scsi`. Ask what they are expecting. If a scan still doesn't allow stuff to show there, then it is external to the OS. 
  * For fibre channel, a rescan is an echo to something in /sys/class
  * LUNz is a place holder LUN. This means that the system does not have permissions. 
* If the LUNs show up but we can not access them, check for what is being presented: 
  * `sos_commands/devicemapper/ls_-laR_.dev`

##### Device Mapper
* /proc/patitions to map major:minor numbers 

##### Multipath
* logically aggregting devices. 
* `mpath` devices are created on boot with the `dm_multipath` module. To completely remove `mpath` devices, you will need to blacklist that module and rebuild the initramfs/initrd. 
* You can use `# multipath -ll` to see if paths are missing in the path configurations
 
##### LVM
* `/etc/lvm/lvm.conf`
* `pvs` shows devices and what they belong to. You should use this (specifically with `/dev/mapper/*`) to create lvm filters. 
* `/etc/lvm/backup` contains the last backups. `/etc/lvm/archive` contains historical data
  * May need to check here for prior lvm activity for a can't boot

##### Boot from SAN
* may need to check thr grub menu
 
##### Resize FS
* Always work in sectors `# fdisk -u <dev>`
* Grab the starting sector of the old partition via fdisk
* Then set the start and end sectors. 
* The supported way is to extend via LVM, but you can manually set them

rport: blocked FC remote port time out: means a port outside of the system is having an issue
