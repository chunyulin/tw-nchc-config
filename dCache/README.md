# dCache SE config

### Packages:
```
# yum list installed | grep dcache
dcache.noarch                                                     11.2.2-1                    @@commandline
dcache-plugin-xrootd-monitor.noarch                               7.0.0-0                     @@commandline

# yum list installed | grep xrootd
dcache-plugin-xrootd-monitor.noarch                               7.0.0-0                     @@commandline
xrootd.x86_64                                                     1:5.9.1-1.el9               @epel
xrootd-client-libs.x86_64                                         1:5.9.1-1.el9               @epel
xrootd-devel.x86_64                                               1:5.9.1-1.el9               @epel
xrootd-libs.x86_64                                                1:5.9.1-1.el9               @epel
xrootd-scitokens.x86_64                                           1:5.9.1-1.el9               @epel
xrootd-selinux.noarch                                             1:5.9.1-1.el9               @epel
xrootd-server.x86_64                                              1:5.9.1-1.el9               @epel
xrootd-server-libs.x86_64                                         1:5.9.1-1.el9               @epel
xrootd-voms.x86_64                                                1:5.9.1-1.el9               @epel
xrootd4j-cms-plugin.noarch                                        4.0.4-1                     @@commandline
```
Note that the cmstfc was built from https://github.com/CMSCompOps/xrootd-cmstfc in /usr/local


### dCache/Chimera mounting point: 
```
# mount localhost:/ /pnfs

# ls /pnfs -al
total 4
drwxrwxr-x    8 root  root  512 Mar 22 11:57 .
dr-xr-xr-x.  20 root  root  286 May 16  2025 ..
lrwxrwxrwx    1 root  root   29 Apr 19  2023 cms -> dpm/grid.nchc.org.tw/home/cms
drwxrwxr-x+   3 root  root  512 Feb  7  2023 dpm
drwxrwxr-x+   3 dteam dteam 512 Mar 14 00:41 dteam
drwxrwxr-x+ 940 ops   ops   512 Mar 27 14:34 ops
drwxrwxr-x+   3 root  root  512 Jan 24 18:57 SRR
drwx--x--x   14 root  root  512 Mar 22 11:25 upload
drwxr-xr-x    2 wlcg  wlcg  512 Mar 22 11:44 wlcg
```

### Start dCache and SLAC xrootd server:
```
# systemctl start dcacge.target
# systemctl start xrootd@clusterd
# systemctl start cmsd@clusterd
```
