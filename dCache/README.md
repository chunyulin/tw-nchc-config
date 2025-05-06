# dCache SE config

### Packages:
```
# yum list installed | grep dcache
dcache.noarch                                                     10.2.12-1                     @@commandline
dcache-plugin-xrootd-monitor.noarch                               7.0.0-0                       @@commandline

# yum list installed | grep xrootd
dcache-plugin-xrootd-monitor.noarch                               7.0.0-0                       @@commandline
xrootd.x86_64                                                     1:5.8.1-1.el9                 @epel
xrootd-client-libs.x86_64                                         1:5.8.1-1.el9                 @epel
xrootd-devel.x86_64                                               1:5.8.1-1.el9                 @epel
xrootd-libs.x86_64                                                1:5.8.1-1.el9                 @epel
xrootd-scitokens.x86_64                                           1:5.8.1-1.el9                 @epel
xrootd-selinux.noarch                                             1:5.8.1-1.el9                 @epel
xrootd-server.x86_64                                              1:5.8.1-1.el9                 @epel
xrootd-server-libs.x86_64                                         1:5.8.1-1.el9                 @epel
xrootd-voms.x86_64                                                1:5.8.1-1.el9                 @epel
xrootd4j-cms-plugin.noarch                                        4.0.4-1                       @@commandline
```
Note that the cmstfc was built from https://github.com/CMSCompOps/xrootd-cmstfc in /usr/local


### dCache/Chimera mounting point: 
```
# mount localhost:/ /pnfs

# ls /pnfs -al
ls: /pnfs/upload: Permission denied
total 5
drwxrwxr-x    9 root  root  512 May  3 01:30 .
dr-xr-xr-x.  19 root  root  271 May  3 13:30 ..
lrwxrwxrwx    1 root  root   29 Apr 19  2023 cms -> dpm/grid.nchc.org.tw/home/cms
drwxrwxr-x+   3 root  root  512 Feb  7  2023 dpm
drwxrwxr-x+   4 dteam dteam 512 May  3 14:09 dteam
drwxrwxr-x    2 kagra kagra 512 May 20  2024 kagra
drwxrwxr-x+ 940 ops   ops   512 May  6 10:42 ops
drwxrwxr-x+   3 root  root  512 May  1 20:33 SRR
drwx--x--x   14 root  root  512 Feb 19  2023 upload
drwxr-xr-x    2 wlcg  wlcg  512 May  9  2024 wlcg
```

### Start dCache and SLAC xrootd server:
```
# systemctl start dcacge.target
# systemctl start xrootd@clusterd
# systemctl start cmsd@clusterd
```
