# CSC217 Operating System Individual Project (Hadoop)

## 62130500226 Wisarut Kitticharoenphonngam

## Virtual Machine
I use 4 Virtual Machines (Ubuntu 16.04) on Azure
- hadoop-master	`13.71.140.165`
- hadoop-worker-1 `13.78.82.132`
- hadoop-worker-2 `52.231.199.119`
- hadoop-worker-3 `52.141.4.84`

## Hadoop
I use hadoop 3.2.1 that can download from 
`http://mirror.cc.columbia.edu/pub/software/apache/hadoop/common/hadoop-3.2.1/hadoop-3.2.1.tar.gz`


## Hadoop Dashboard

http://13.71.140.165:9870

## Step that I done

1) Create 4 Virtual Machine
2) SSH to each Virtual Machine
3) Switch from root to non-root account
```
sudo adduser ggolfzuser
sudo adduser ggolfzuser sudo
sudo su - ggolfzuser
```
4) Install Java JDK from 
`sudo apt-get update && sudo apt-get -y dist-upgrade && sudo apt-get -y install openjdk-8-jdk-headless`
5) Make Directory for working
`mkdir my-hadoop-install && cd my-hadoop-install`
6) Download Hadoop
`wget http://mirror.cc.columbia.edu/pub/software/apache/hadoop/common/hadoop-3.2.1/hadoop-3.2.1.tar.gz`
7) Extract Tar file and remove compressed
`tar xvzf hadoop-3.2.1.tar.gz && rm hadoop-3.2.1.tar.gz`
8) Export environment by configure `etc/hadoop/hadoop-env.sh` to be same as `hadoop-env.sh` for all virtual machine and use `source ${HADOOP_HOME}/etc/hadoop/hadoop-env.sh` to activate environment
9) Run `ssh-keygen` on all machine and store ssh-keygen of master in all virtual machine `~/.ssh/authorized_keys` and save config to master machine `~/.ssh/config` as same as `ssh-config`
10) Configure `core-site.xml` which located in `etc/hadoop/core-site.xml` to be same as `core-site.xml` for all virtual machine
11) Configure `hdfs-site.xml` which located in `etc/hadoop/hdfs-site.xml` to be same as `hdfs-site.xml` for all virtual machine
12) Configure `yarn-site.xml` which located in `etc/hadoop/yarn-site.xml` to be same as `yarn-site.xml` for master machine and same as `yarn-site-worker.xml` for worker machine
13) Configure `mapred-site.xml` which located in `etc/hadoop/mapred-site.xml` to be same as `hdfs-site.xml` for master machine
14) Configure `masters` file which located in `etc/hadoop/masters` to be same as `masters` for master machine
15) Configure `workers` file which located in `etc/hadoop/workers` to be same as `workers` for master machine
16) Create Directory for hdfs by using `sudo mkdir -p /usr/local/hadoop/hdfs/data` and grant permission with `sudo chown -R ggolfzuser:ggolfzuser /usr/local/hadoop/hdfs/data`
17) Format namenode by `bin/hdfs namenode -format`
18) Start service by `sbin/start-all.sh`
