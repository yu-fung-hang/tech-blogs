# CentOS 7

### Set Network 
1. `vi /etc/sysconfig/network-scripts/ifcfg-ens33`;
2. set `BOOTPROTO` = `dhcp`, and `ONBOOT` = `yes`;
3. `service network restart`;
4. `ip addr` to check.