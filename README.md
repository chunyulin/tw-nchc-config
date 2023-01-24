# dCache SE config

### Packages:
```
# yum list installed | grep dcache
dcache.noarch                         8.2.11-1                 @/dcache-8.2.11-1.noarch
dcache-plugin-xrootd-monitor.noarch   7.0.0-0                  @/dcache-plugin-xrootd-monitor-7.0.0-0.noarch

# yum list installed | grep xrootd
dcache-plugin-xrootd-monitor.noarch   7.0.0-0                  @/dcache-plugin-xrootd-monitor-7.0.0-0.noarch
xrootd.x86_64                         1:5.4.2-1.osg35up.el7    @osg-upcoming-development
xrootd-client-libs.x86_64             1:5.4.2-1.osg35up.el7    @osg-upcoming-development
xrootd-cmstfc.x86_64                  1.5.2-6.osg35up.el7      @osg-upcoming-development
xrootd-lcmaps.x86_64                  1.7.8-3.osgup.el7        @osg-upcoming-development
xrootd-libs.x86_64                    1:5.4.2-1.osg35up.el7    @osg-upcoming-development
xrootd-selinux.noarch                 1:5.4.2-1.osg35up.el7    @osg-upcoming-development
xrootd-server.x86_64                  1:5.4.2-1.osg35up.el7    @osg-upcoming-development
xrootd-server-libs.x86_64             1:5.4.2-1.osg35up.el7    @osg-upcoming-development
xrootd4j-cms-plugin.noarch            4.0.4-1                  @/xrootd4j-cms-plugin-4.0.4-1.noarch
```

### dCache/Chimera mounting point: 
```
# mount localhost:/ /pnfs
# ls /pnfs -l
total 5
lrwxrwxrwx  1 root root  29 Jan 16 15:10 cms -> dpm/grid.nchc.org.tw/home/cms
drwxrwxr-x  4 root root 512 Dec 25  2015 dpm
lrwxrwxrwx  1 root root  31 Jan 16 15:10 dteam -> dpm/grid.nchc.org.tw/home/dteam
lrwxrwxrwx  1 root root  33 Jan 16 15:10 enmr.eu -> dpm/grid.nchc.org.tw/home/enmr.eu
drwx------  2 root root 512 Jan 14 02:51 lost+found
lrwxrwxrwx  1 root root  29 Jan 16 15:10 ops -> dpm/grid.nchc.org.tw/home/ops
drwxr-xr-x  3 root root 512 Jan 23 04:20 pnfs
lrwxrwxrwx  1 root root  29 Jan 16 15:11 SRR -> dpm/grid.nchc.org.tw/home/SRR
drwx--x--x 14 root root 512 Jan 14 06:48 upload
lrwxrwxrwx  1 root root  39 Jan 16 15:10 vo.neugrid.eu -> dpm/grid.nchc.org.tw/home/vo.neugrid.eu
```

### Start dCache and SLAC xrootd server:
```
# systemctl start dcacge.target
# systemctl start xrootd@clusterd
# systemctl start cmsd@clusterd
```

### Current issue:
Any direct access thru dCache's xrootd door (call it `A`) at standard 1094 port including CMS-TFC has no problem, such as: 
```
$ gfal-copy -f root://se01.grid.nchc.org.tw//store/test/xrootd/T2_TW_NCHC/store/user/chunyu/x /dev/null
```
My issue is the correct "federation host", which is the standalone (SLAC) xrootd server running `cmsd` (subscribe to regional redirector) and another `xrootd` (call it `B`).

I guess `B` is similar to `A` but only for returning namespace results to `cmsd`, instead of for actual data transferring.

Now, my `B` is keeping to restart itself w/o success, maybe due to the LCMAPS setting.
```
$ gfal-ls root://se01.grid.nchc.org.tw:11001//store  ## NOT works!
```
