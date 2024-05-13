# dCache SE config

### Packages:
```
# yum list installed | grep dcache
dcache.noarch                         9.2.19-1                 @/dcache-9.2.19-1.noarch
dcache-plugin-xrootd-monitor.noarch   7.0.0-0                  @/dcache-plugin-xrootd-monitor-7.0.0-0.noarch

# yum list installed | grep xrootd
dcache-plugin-xrootd-monitor.noarch   7.0.0-0                  @/dcache-plugin-xrootd-monitor-7.0.0-0.noarch
gfal2-plugin-xrootd.x86_64            2.22.2-1.el7             @epel
xrootd.x86_64                         1:5.6.9-1.el7            @epel
xrootd-client-libs.x86_64             1:5.6.9-1.el7            @epel
xrootd-cmstfc.x86_64                  1.5.2-6.osgup.el7        @/xrootd-cmstfc-1.5.2-6.osgup.el7.x86_64
xrootd-libs.x86_64                    1:5.6.9-1.el7            @epel
xrootd-scitokens.x86_64               1:5.6.9-1.el7            @epel
xrootd-selinux.noarch                 1:5.6.9-1.el7            @epel
xrootd-server.x86_64                  1:5.6.9-1.el7            @epel
xrootd-server-libs.x86_64             1:5.6.9-1.el7            @epel
xrootd-voms.x86_64                    1:5.6.9-1.el7            @epel
xrootd4j-cms-plugin.noarch            4.0.4-1                  @/xrootd4j-cms-plugin-4.0.4-1.noarch
```

### dCache/Chimera mounting point: 
```
# mount localhost:/ /pnfs
# ls /pnfs -l
total 10
drwxrwxr-x  11 root       root     512 Apr 20 23:59 .
dr-xr-xr-x. 24 root       root    4096 Apr 20 00:00 ..
lrwxrwxrwx   1 root       root      29 Apr 19 23:04 cms -> dpm/grid.nchc.org.tw/home/cms
drwxrwxr-x   3 root       root     512 Feb  7 17:11 dpm
drwxrwxr-x   2 dteam001   dteam    512 Jan 19 14:29 dteam
drwxrwxr-x   2 enmr001    enmr     512 Jan 16 15:24 enmr.eu
drwxrwxr-x   2 kagra001   kagra    512 Feb  8 14:41 kagra
drwxrwxr-x   4 ops001     ops      512 Apr 24 16:11 ops
drwxrwxr-x   3 root       root     512 Apr 24 10:57 SRR
drwx--x--x  14 root       root     512 Feb 19 23:43 upload
drwxrwxr-x   2 neugrid001 neugrid  512 Jan 22 21:33 vo.neugrid.eu
drwxr-xr-x   2      10000   10000  512 Apr 20 23:56 wlcg
```

### Start dCache and SLAC xrootd server:
```
# systemctl start dcache.target
# systemctl start xrootd@clusterd
# systemctl start cmsd@clusterd
```
