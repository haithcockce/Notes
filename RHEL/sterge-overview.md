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
