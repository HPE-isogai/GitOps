# Links
https://about.gitlab.com/install/#ubuntu
http://kottas.hatenablog.com/entry/2019/03/29/000000
https://linuxize.com/post/how-to-change-hostname-on-ubuntu-18-04/

# Env
~~Ubuntu 18.04~~  
CentOS 7  
VMware vSphere 6.7 (VMware ESXi, 6.7.0, 13006603)  
DNS (dnsmasq: Exnternal)  

# Procedure
## Install Ubuntu 18.04
Set Static IP address   
## Set Hostname
FQDN hostname  

~~hostnamectl set-hostname~~  
~~sudo vim /etc/cloud/cloud.cfg~~  
~~#preserve_hostname: true~~  
/etc/hostname  

## Set Hostname in dns record


## Linux Common Settings
```
ssh key authentication
yum install vim tree tmux
yum update
```
## GitLab dependency packages
~~sudo apt-get install -y curl openssh-server ca-certificates~~
```
sudo yum install -y curl policycoreutils-python openssh-server cronie
sudo lokkit -s http -s ssh
```
#postfix ?

## Add GitLab repository
```
curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash

```  




## Install gitlabce
#modify  
#use http:// if you use self signed certificate  
sudo EXTERNAL_URL="http://<your-gitlab-server-hostnameFQDN>"  yum -y install gitlab-ce  

## Configure Docker Registry
#1. Run docker registy in gitlab server
#https://docs.gitlab.com/ee/administration/packages/container_registry.html
#1. Set Insecure registry
#2. configure `/etc/gitlab/gitlab.rb`  
#https://docs.gitlab.com/ee/administration/packages/container_registry.html
#* modify `registry_external_url`  
#3. `gitlab-ctl reconfigure`  

## If you fail fail install
- when you want reinstall package  
```
# du -sh /var/cache/yum     <-キャッシュの確認
# rm -rf /var/cache/yum/*　 <-キャッシュ削除
# yum clean all
```

- when you reconfigure without reinstalling packages  
`sudo gitlab-ctl reconfigure` 

# git update 1.8.X -> latest
https://computingforgeeks.com/how-to-install-latest-version-of-git-git-2-x-on-centos-7/  
```
sudo yum remove git*
sudo yum -y install  https://centos7.iuscommunity.org/ius-release.rpm
sudo yum -y install  git2u-all
```

# memo

https://bugzilla.redhat.com/show_bug.cgi?id=1506395
https://kikumoto.hatenablog.com/entry/2016/06/04/124922
https://qiita.com/chroju/items/375582799acd3c5137c7

