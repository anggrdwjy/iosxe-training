## Overview

## Information

## Basic Configuration

## Routing Configuration

## MPLS (Multi Protocol Labeling Switching)

## MPLS L2VPN Configuration

## VPLS Configuration

## Interior-BGP Route Reflector

## MPLS L3VPN Configuration

## LACP (Link Aggregation Control Protocol)

* LACP Configuration
```
interface Port-channel1
ip address 192.168.1.1 255.255.255.0
```

* Port Interface
```
interface GigabitEthernet0/1
switchport
switchport mode trunk
channel-group 1 mode active
```
```
interface GigabitEthernet0/2
switchport
switchport mode trunk
channel-group 1 mode active
```

## Switch Configuration

#### VLAN Configuration
* VLAN
```
vlan [VLAN_ID]
vlan name [VLAN_NAME]
```

* Interface VLAN
```
interface vlan [VLAN_ID]
description [SERVICE_NAME]
ip address [IP_ADDRESS] [NETMASK]
no shutdown
```

#### Port Trunk
* Port Trunk
```
interface GigabitEthernet [PORT_TRUNK]
description Trunk to 11-CE
switchport trunk allowed vlan 111,444,666
switchport trunk encapsulation dot1q
switchport mode trunk
```

* Advanced Port Trunk
```
interface GigabitEthernet [PORT_TRUNK]
description Trunk to 11-CE
switchport trunk allowed vlan 111,444,666
switchport trunk encapsulation dot1q
switchport mode trunk
cdp enable
mtu 1900
load-interval 30
negotiation auto
udld port disable
spanning-tree bpdufilter enable
ip dhcp snooping trust -> Optional
```

* Spanning-Tree
```
spanning-tree bpdufilter enable
```

* DHCP Snooping
```
ip dhcp snooping trust
```

#### Port Access
* Port Access
```
interface GigabitEthernet [PORT_ACCESS]
description Access to A-CPE
switchport access vlan 444
switchport mode access
```

* Advanced Port Access
```
interface GigabitEthernet [PORT_ACCESS]
description Access to A-CPE
switchport access vlan 444
switchport mode access
cdp enable
mtu 1900
load-interval 30
negotiation auto
udld port disable
spanning-tree bpdufilter enable
ip dhcp snooping trust -> Optional
```

* Spanning-Tree
```
spanning-tree bpdufilter enable
```

* DHCP Snooping
```
ip dhcp snooping trust
```

#### Static Routing
```
router(config)# ip route 0.0.0.0 0.0.0.0 [GATEWAY]
router(config)# ip route [NETWORK_NEIGHBOR] [PREFIX] [GATEWAY]
```

## Support

* [:octocat: Follow me on GitHub](https://github.com/anggrdwjy)
* [🔔 Subscribe me on Youtube](https://www.youtube.com/@anggarda.wijaya)


#### Bugs

Please open an issue on GitHub with as much information as possible if you found a bug.
* Your IOS-XE and Software Update
* All the logs and message outputted
* etc
