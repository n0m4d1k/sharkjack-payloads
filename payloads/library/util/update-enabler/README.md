# Title: Update enabler
### Author: n0m4d1k
### Version: 2.0

### Description:

This payload sets the shark jack to DHCP_CLIENT mode toallow access to the internet and then enables SSH on the shark jack allowing you to SSH into the device an perform updates or download additional tools. It also automatically updates the distfeeds.conf and customfeeds.conf file to fix update errors.

Note: 
As of 07/27/2023 the /etc/opkg/distfeeds.conf file that comes with the stock shark jack is incorrect and will error out. I have also included the corrected files in this directory. To fix this manually remove the original text and add the below.

```
src/gz openwrt_core http://downloads.openwrt.org/releases/18.06.0/targets/ramips/mt76x8/packages
src/gz openwrt_base http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/base
src/gz openwrt_luci http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/luci
src/gz openwrt_packages http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/packages
src/gz openwrt_routing http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/routing
src/gz openwrt_telephony http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/telephony
```

Additionally, there is currently nothing in the Hak5 packages repo so this will also throw and error.
to fix this you can simply comment out the second line in the /etc/opkg/customfeeds.conf

Keep in mind that the shark jack will most likely have a 10.42.0.0/24 IP address and you will need to SSH to that. You can find the new IP using nmap by running the below command.

`nmap -sn 10.42.0.0/24`

#### LED Key:

LED SETUP (Magenta)... Setting NETMODE to DHCP_CLIENT and starting SSH

LED Green... Ready