## Links
https://qiita.com/Imasug/items/71d2ff21c7d1d3454bff  
https://help.sonatype.com/learning/repository-manager-3/first-time-installation-and-setup/lesson-1%3A--installing-and-starting-nexus-repository-manager#Lesson1:InstallingandStartingNexusRepositoryManager-DownloadingtheRepositoryManager  
https://www.liquidweb.com/kb/install-java-8-on-centos-7/  
https://www.rootusers.com/how-to-open-a-port-in-centos-7-with-firewalld/  
https://qiita.com/fukasawah/items/48330564736d3368b632  


## Environment
CentOS 7
VMware vSphere 6.7


## Procedure
1. Install CentOS
1. Install Java
1. Download nexus
1. Unpack and locate nexus (ex. /opt)
1. `./nexus3/bin/nexus run`  
1. confirm the below message
```
-------------------------------------------------

Started Sonatype Nexus OSS 3.20.1-01

-------------------------------------------------
```
1. Open 8081 port
```
[root@nexus ~]# firewall-cmd --zone=public --add-port=8081/tcp --permanent
success
[root@nexus ~]# firewall-cmd --reload
success
[root@nexus ~]# iptables-save |grep 8081
-A IN_public_allow -p tcp -m tcp --dport 8081 -m conntrack --ctstate NEW,UNTRACKED -j ACCEPT
[root@nexus ~]#
[root@nexus ~]# firewall-cmd --list-ports
8081/tcp
[root@nexus ~]#
[root@nexus ~]# firewall-cmd --permanent --add-service=http
success
[root@nexus ~]# firewall-cmd --reload
success
```
1. access `http://<nexus-ip>:8081/` from blowser
1. make sure the default password in `/opt/sonatype-work/nexus3/admin.password`  
1. sign in as `admin` and default password
1. follow the setup wizard
1.1. change password
1.1. Anonymous Access -> Enable (for test purpose)

## Make Service
https://help.sonatype.com/repomanager3/installation/run-as-a-service#RunasaService-systemd


## Confirmation (From docker client)
1. Create `Dockerfile`
1. Build image with `docker build -t <tagname>
1. tag the image `docker tag <local image:tag> <remote image:tag>
1. `docker login http://<nexus-ip>:<nexus-docker-port>`
1. docker push <remote image:tag>

## Insecure Registry
https://github.com/Juniper/contrail-docker/wiki/Configure-docker-service-to-use-insecure-registry
#If you dont set this up, you cannot log in to insecure registry as well as client side
