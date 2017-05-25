# check_zfs
A NRPE/Nagios/Centreon Check for Linux-based ZFS Pools

Configuration:
```
# cat /etc/sudoers.d/nrpe
nrpe ALL= NOPASSWD: /sbin/zpool list *, /sbin/zpool status *

# cat /etc/nrpe.d/check_zfs.cfg
command[check_zfs]=/usr/local/bin/check_zfs $ARG1$ 1
```

Make sure **dont_blame_nrpe=1** in /etc/nagios/nrpe.cfg to be able to use user-defined arguments.

Sample command:
```
/usr/lib/nagios/plugins/check_nrpe -H storage-srv -p 5666 -c check_zfs -a zfspool
```
