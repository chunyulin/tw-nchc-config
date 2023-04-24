## Requirements to host WLCG/CMS workload on a "less-restrict" HPC

### Sepc
- CPU: No specific requirement.
- RAM: 2GB per core is accept.
- Job size: 8-core per job; no MPI yet.
- Job duration: 2-day at least.

### Networking
- Egress networking should be allowed on head/worker nodes.
- For the head node, we need some ingress ports open to any:
```
<service>
  <short>ARC-CE</short>
  <description>ARC-CE</description>
  <port protocol="tcp" port="443"/>
  <port protocol="tcp" port="2170"/> <!-- LDAP: site BDII -->
  <port protocol="tcp" port="2135"/> <!-- LDAP: GIIS -->
  <port protocol="tcp" port="60000"/>  <!-- A-REX -->
  <port protocol="tcp" port="2811"/> <!-- GridFTP -->
  <port protocol="tcp" port="9000-9300"/>
  <port protocol="udp" port="9000-9300"/>
</service>
```

### Add several local users to which grid users will map for accounting
```
useradd ops cms cmspil
```

### Some system packages include singularity and cgroup
```
setenforce 0    # Turn off SELinux 
yum -y install epel-release
yum -y install libcgroup-tools redhat-lsb-core ntpdate zsh tcsh wget time git
yum -y install apptainer-suid    ## or singularity for older OS
systemctl enable cgconfig;        systemctl restart cgconfig
```

### Install EGI IGTF (The International Grid Trust Federation)
```
curl https://repository.egi.eu/sw/production/cas/1/current/repo-files/EGI-trustanchors.repo -o /etc/yum.repos.d/EGI-trustanchors.repo
yum -y install ca-policy-egi-core
systemctl enable fetch-crl-cron;  systemctl restart fetch-crl-cron
fetch-crl -v
```

### Install CVMFS and autofs
```
yum install -y https://ecsft.cern.ch/dist/cvmfs/cvmfs-release/cvmfs-release-latest.noarch.rpm
yum install -y cvmfs fuse autofs
mkdir -p /cvmfs
systemctl enable autofs; systemctl restart autofs
cvmfs_config chksetup
cvmfs_config probe
```

### Some grid client software 
```
yum -y install http://linuxsoft.cern.ch/wlcg/centos7/x86_64/wlcg-repo-1.0.0-1.el7.noarch.rpm
yum -y install nordugrid-arc6-wn nordugrid-arc6-client nordugrid-arc6-plugins-globus \
               nordugrid-arc6-plugins-gfal nordugrid-arc6-plugins-xrootd \
               wlcg-voms-ops wlcg-voms-cms voms-clients-cpp
```

### Push collectd monitoring to promethesus (Optional)
```
yum -y install collectd collectd-write_prometheus   # collectd-smart collectd-hugepages
systemctl enable collectd;     systemctl start collectd
```
