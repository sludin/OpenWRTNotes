```
config interface 'loopback'
	option device 'lo'
	option proto 'static'
	option ipaddr '127.0.0.1'
	option netmask '255.0.0.0'

config globals 'globals'
	option ula_prefix 'fdef:1a4e:5873::/48'

config device
	option name 'br-lan'
	option type 'bridge'
	list ports 'lan1'
	list ports 'lan2'
	list ports 'lan3'
	list ports 'lan4'

config interface 'lan'
	option proto 'static'
	option ipaddr '192.168.1.1'
	option netmask '255.255.255.0'
	option ip6assign '60'
	option device 'br-lan.1'

config device
	option name 'wan'
	option macaddr 'ea:9f:80:1b:88:d0'

config interface 'wan'
	option device 'wan'
	option proto 'dhcp'

config interface 'wan6'
	option device 'wan'
	option proto 'dhcpv6'

config bridge-vlan
	option device 'br-lan'
	option vlan '1'
	list ports 'lan1'
	list ports 'lan4:t*'

config bridge-vlan
	option device 'br-lan'
	list ports 'lan2'
	list ports 'lan4:t'
	option vlan '10'

config interface 'IOT'
	option device 'br-lan.20'
	option proto 'static'
	option netmask '255.255.255.0'
	option gateway '192.168.1.1'
	option ipaddr '192.168.20.1'

config bridge-vlan
	option device 'br-lan'
	list ports 'lan3'
	list ports 'lan4:t'
	option vlan '20'

config bridge-vlan
	option device 'br-lan'
	option vlan '30'
	list ports 'lan4:t'

config interface 'GUEST'
	option proto 'static'
	option device 'br-lan.30'
	option ipaddr '192.168.30.1'
	option netmask '255.255.255.0'
	option gateway '192.168.1.1'

config interface 'INTERNAL'
	option proto 'static'
	option device 'br-lan.10'
	option ipaddr '192.168.10.1'
	option netmask '255.255.255.0'
	option gateway '192.168.1.1'
```
