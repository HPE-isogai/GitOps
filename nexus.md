## Links
https://qiita.com/Imasug/items/71d2ff21c7d1d3454bff
https://help.sonatype.com/learning/repository-manager-3/first-time-installation-and-setup/lesson-1%3A--installing-and-starting-nexus-repository-manager#Lesson1:InstallingandStartingNexusRepositoryManager-DownloadingtheRepositoryManager
https://www.liquidweb.com/kb/install-java-8-on-centos-7/

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
````
-------------------------------------------------

Started Sonatype Nexus OSS 3.20.1-01

-------------------------------------------------
```
1. access `http://localhost:8081/` from blowser
