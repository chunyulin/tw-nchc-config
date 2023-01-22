# dCache SE
- Packages:
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
- Chimera mounting point: 
```
# mount localhost:/ /pnfs
# ls /pnfs -l
total 12
drwxrwxrwx  3 lincy lincy 512 Jan 14 06:47 cccc
lrwxrwxrwx  1 root  root   29 Jan 16 15:10 cms -> dpm/grid.nchc.org.tw/home/cms
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 data01
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 data02
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 data03
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 data04
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 data05
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 data06
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 disk01
drwxrwxr-x  2  4000  4000 512 Sep 21  2020 disk01.grid.nchc.org.tw:
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 disk02
drwxrwxr-x  2  4000  4000 512 Sep 21  2020 disk02.grid.nchc.org.tw:
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 disk03
drwxrwxr-x  3  4000  4000 512 Sep 21  2020 disk04
drwxrwxr-x  4 root  root  512 Dec 25  2015 dpm
lrwxrwxrwx  1 root  root   31 Jan 16 15:10 dteam -> dpm/grid.nchc.org.tw/home/dteam
lrwxrwxrwx  1 root  root   33 Jan 16 15:10 enmr.eu -> dpm/grid.nchc.org.tw/home/enmr.eu
drwx------  2 root  root  512 Jan 14 02:51 lost+found
lrwxrwxrwx  1 root  root   29 Jan 16 15:10 ops -> dpm/grid.nchc.org.tw/home/ops
drwxrwxr-x  2  4000  4000 512 Sep 21  2020 proxy.grid.nchc.org.tw:
drwxrwxr-x  2  4000  4000 512 Sep 21  2020 se02.grid.nchc.org.tw:
lrwxrwxrwx  1 root  root   29 Jan 16 15:11 SRR -> dpm/grid.nchc.org.tw/home/SRR
drwx--x--x 14 root  root  512 Jan 14 06:48 upload
lrwxrwxrwx  1 root  root   39 Jan 16 15:10 vo.neugrid.eu -> dpm/grid.nchc.org.tw/home/vo.neugrid.eu

```
- Start service 
```
systemctl start xrootd@clusterd
systemctl start cmsd@clusterd
#  See log in /var/log/xrootd/clustered/*
```
- Test
```
# gfal-copy root://se01.grid.nchc.org.tw//store/test/xrootd/T2_TW_NCHC/store/temp/x /tmp/x -f    ## Works.
# gfal-ls   root://cms-xrd-global.cern.ch//store/test/xrootd/T2_TW_NCHC/store/temp/x             ## Not work yet !
```
