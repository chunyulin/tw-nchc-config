# dCache SE
### Packages:
```
# yum list installed | grep dcache
dcache.noarch                         8.2.11-1                 @/dcache-8.2.11-1.noarch

# yum list installed | grep xrootd
xrootd.x86_64                         1:5.5.1-1.el7            @epel
xrootd-client-libs.x86_64             1:5.5.1-1.el7            @epel
xrootd-cmstfc.x86_64                  1.5.2-6.osgup.el7        @/xrootd-cmstfc-1.5.2-6.osgup.el7.x86_64
xrootd-libs.x86_64                    1:5.5.1-1.el7            @epel
xrootd-selinux.noarch                 1:5.5.1-1.el7            @epel
xrootd-server.x86_64                  1:5.5.1-1.el7            @epel
xrootd-server-libs.x86_64             1:5.5.1-1.el7            @epel
xrootd-voms.x86_64                    1:5.5.1-1.el7            @epel
xrootd4j-cms-plugin.noarch            4.0.4-1                  @/xrootd4j-cms-plugin-4.0.4-1.noarch
```
### Chimera mounting point: 
```
# mount localhost:/ /pnfs
# ls /pnfs
cms  dpm  dteam  enmr.eu  lost+found  ops  SRR  upload  vo.neugrid.eu
```
### Start service 
```
systemctl start xrootd@clusterd
systemctl start cmsd@clusterd
#  See log in /var/log/xrootd/clustered/*
```
### Test
```
# gfal-copy root://se01.grid.nchc.org.tw//store/test/xrootd/T2_TW_NCHC/store/temp/x /tmp/x -f    ## Works.
# gfal-ls   root://cms-xrd-global.cern.ch//store/test/xrootd/T2_TW_NCHC/store/temp/x             ## Not work yet !
```
See [this issue](https://github.com/chunyulin/tw-nchc-config/issues/1).
