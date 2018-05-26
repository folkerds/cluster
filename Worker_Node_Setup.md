<b>Worder Node Setup</b>

1. Install Ubuntu 16.04 from a bootable USB flash drive
    1. sudo apt update && sudo apt upgrade

2. Install & Configure SSH
    1. sudo apt-get install openssh-server -y
    2. To change port: sudo vim /etc/ssh/sshd_config -> port = 47
    3. sudo service ssh restart

3. Install Java & set Java_Home
    1. sudo apt-get install default-jdk
    2. sudo vim /etc/environment -> JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64/"
    3. source /etc/environment

4. Install ntp
    1. sudo apt-get install ntp
    2. sudo update-rc.d ntp defaults

5. Install Ambari
    1. Download Ambari Repo:
        - wget -O /etc/apt/sources.list.d/ambari.list http://public-repo-1.hortonworks.com/ambari/debian7/2.x/updates/2.6.1.5/ambari.list
        - apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B9733A7A07513CAD
        - apt-get update
    2. Install:
        - sudo apt-get install ambari-agent
        - sudo vim /etc/ambari-agent/conf/ambari-agent.ini -> hostname=<your.ambari.server.hostname>
    3. Start Ambari:
        - sudo ambari agent start