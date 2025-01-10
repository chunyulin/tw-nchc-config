# dCache SE config

### Packages:
```
# yum list installed | grep dcache
dcache.noarch                         9.2.32-1                 @/dcache-9.2.32-1.noarch
dcache-plugin-xrootd-monitor.noarch   7.0.0-0                  @/dcache-plugin-xrootd-monitor-7.0.0-0.noarch

# yum list installed | grep xrootd
dcache-plugin-xrootd-monitor.noarch   7.0.0-0                  @/dcache-plugin-xrootd-monitor-7.0.0-0.noarch
gfal2-plugin-xrootd.x86_64            2.22.2-1.el7             @epel
xrootd.x86_64                         1:5.6.9-1.el7            @epel
xrootd-client.x86_64                  1:5.6.9-1.el7            @epel
xrootd-client-devel.x86_64            1:5.6.9-1.el7            @epel
xrootd-client-libs.x86_64             1:5.6.9-1.el7            @epel
xrootd-cmstfc.x86_64                  1.5.2-6.osgup.el7        @/xrootd-cmstfc-1.5.2-6.osgup.el7.x86_64
xrootd-devel.x86_64                   1:5.6.9-1.el7            @epel
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
# ls /pnfs -al
total 9
drwxrwxr-x   10 root     root   512 Jun 27  2024 .
dr-xr-xr-x.  23 root     root  4096 Nov  7 22:18 ..
lrwxrwxrwx    1 root     root    29 Apr 19  2023 cms -> dpm/grid.nchc.org.tw/home/cms
drwxrwxr-x    3 root     root   512 Feb  7  2023 dpm
drwxrwxr-x    4 dteam001 dteam  512 Aug  1 10:51 dteam
drwxrwxr-x    2 enmr001  enmr   512 Jan 16  2023 enmr.eu
drwxrwxr-x    2 kagra001 kagra  512 May 20  2024 kagra
drwxrwxr-x  940 ops001   ops    512 Jan 10 09:37 ops
drwxrwxr-x    3 root     root   512 Jan 10 03:49 SRR
drwx--x--x   14 root     root   512 Feb 19  2023 upload
drwxr-xr-x    2    10000 10000  512 May  9  2024 wlcg
```

### Start dCache and SLAC xrootd server:
```
# systemctl start dcacge.target
# systemctl start xrootd@clusterd
# systemctl start cmsd@clusterd
```
