### Cloudinit files for AWS Ubuntu to install HA Jenkins controllers in two AZ:
## [link to Youtube guide](https://www.youtube.com/watch?v=zHavme2iaFA)

jenkins01.yaml
#cloud-config
hostname: jenkins01
fqdn: jenkins01
manage_etc_hosts: true
runcmd:
  - add-apt-repository ppa:webupd8team/java -y
  - echo 'deb http://nectar-downloads.cloudbees.com/nectar/debian binary/' >> /etc/apt/sources.list
  - echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
  - echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections
  - wget -q -O - http://nectar-downloads.cloudbees.com/nectar/debian/cloudbees.com.key | sudo apt-key add -
  - apt-get update
  - apt-get install oracle-java8-installer nfs-common -y



jenkins02.yaml
#cloud-config
hostname: jenkins02
fqdn: jenkins02
manage_etc_hosts: true
runcmd:
  - add-apt-repository ppa:webupd8team/java -y
  - echo 'deb http://nectar-downloads.cloudbees.com/nectar/debian binary/' >> /etc/apt/sources.list
  - echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
  - echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections
  - wget -q -O - http://nectar-downloads.cloudbees.com/nectar/debian/cloudbees.com.key | sudo apt-key add -
  - apt-get update
  - apt-get install oracle-java8-installer nfs-common -y

