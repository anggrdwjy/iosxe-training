## Overview

## Information

## Basic Configuration

## Routing Configuration

## MPLS (Multi Protocol Labeling Switching)

## MPLS L2VPN Configuration

#### Far End
* Service Instance
```
interface GigabitEthernet2
service instance 666 ethernet
description MPLS_L2VPN
encapsulation dot1q 666
rewrite ingress tag pop 1 symmetric
bridge-domain 666
xconnect 11.11.11.11 666 encapsulation mpls
```

* Verification
```
show mpls l2transport vc [L2VPN-ID]
show bridge-domain [L2VPN_ID]
show mac-address-table dynamic vlan [VLAN_ID]
```

#### Near End
* Service Instance
```
interface GigabitEthernet2
service instance 666 ethernet
description MPLS_L2VPN
encapsulation dot1q 666
rewrite ingress tag pop 1 symmetric
bridge-domain 666
xconnect 12.12.12.12 666 encapsulation mpls
```

* Verification
```
show mpls l2transport vc [L2VPN-ID]
show bridge-domain [L2VPN_ID]
show mac-address-table dynamic vlan [VLAN_ID]
```

## VPLS Configuration

#### Far End
* VPLS Configuration
```
l2 vfi VFI-444 manual
vpn id 444
bridge-domain 444
mtu 1900
neighbor 21.21.21.21 encapsulation mpls
```

* Service Instance
```
interface GigabitEthernet2
service instance 444 ethernet
description VPLS_SERVICE
encapsulation dot1q 444
rewrite ingress tag pop 1 symmetric
bridge-domain 444
```

* Verification
```
show mpls l2transport vc [VPLS-ID]
show bridge-domain [VPLS_ID]
show vfi [VPLS-ID]
show mac-address-table dynamic vlan [VLAN_ID]
```

#### Near End
* VPLS Configuration
```
l2 vfi VFI-444 manual
vpn id 444
bridge-domain 444
mtu 1900
neighbor 12.12.12.12 encapsulation mpls
```

* Service Instance
```
interface GigabitEthernet2
service instance 444 ethernet
description VPLS_SERVICE
encapsulation dot1q 444
rewrite ingress tag pop 1 symmetric
bridge-domain 444
```

* Verification
```
show mpls l2transport vc [VPLS-ID]
show bridge-domain [VPLS_ID]
show vfi [VPLS-ID]
show mac-address-table dynamic vlan [VLAN_ID]
```

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

* Verification
```
show running interface [PORT]
show running interface [Port-Channel]
show etherchannel summary
show mac-address-table dynamic vlan [VLAN_ID]
```

## Switch Configuration (IOS-L)

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

* Verification
```
show running interface [vlan]
show vlan
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

* Verification
```
show running interface [PORT]
show vlan
show mac-address-table dynamic vlan [VLAN_ID]
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

* Verification
```
show running interface [PORT]
show vlan
show mac-address-table dynamic vlan [VLAN_ID]
```

#### Static Routing
* Static Route
```
router(config)# ip route 0.0.0.0 0.0.0.0 [GATEWAY]
router(config)# ip route [NETWORK_NEIGHBOR] [PREFIX] [GATEWAY]
```

* Verification
```
show route table
```

## Support

* [:octocat: Follow me on GitHub](https://github.com/anggrdwjy)
* [🔔 Subscribe me on Youtube](https://www.youtube.com/@anggarda.wijaya)


#### Bugs

Please open an issue on GitHub with as much information as possible if you found a bug.
* Your IOS-XE and Software Update
* All the logs and message outputted
* etc
