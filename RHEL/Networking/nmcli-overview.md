# NMCLI Overview

### Intro
* Useful for scripts and useful when you do not have GUIs
* `--terse` ugly but useful for scripting
* `--ask` is useful to double check if things are leftout (goes by minimal requirements of the thing)
* `--pretty` makes it prettyish 
* `general` useful to see if we even are connected

### Connections
* A connection is a set of configurations for a Network Interface. You can have multiple connections for any interface but only one connection can be up at a time


### Bridges
When a packet comes into a bridge (Br0), the bridge checks the MAC Addr table to see which port to send the packet over the specific port or blast the packet to all ports other than the receiving port. A bridge is essentially a virtual switch. MAC address checking is done on L2 switches but adding IP Addresses makes it L3. 
