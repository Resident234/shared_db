# shared_db
mysql + vagrant + remote access

username: vagrant
password: vagrant

sudo apt-get update
sudo apt-get install build-essential zlib1g-dev git-core sqlite3 libsqlite3-dev
sudo aptitude install mysql-server mysql-client


sudo nano /etc/mysql/my.cnf
change:
bind-address            = 0.0.0.0


mysql -u root -p

use mysql
GRANT ALL PRIVILEGES ON *.* to root@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit


sudo /etc/init.d/mysql restart




# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  config.vm.box = "lucid32"

  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"

  #config.vm.boot_mode = :gui

  # Assign this VM to a host-only network IP, allowing you to access it
  # via the IP. Host-only networks can talk to the host machine as well as
  # any other machines on the same network, but cannot be accessed (through this
  # network interface) by any external networks.
  # config.vm.network :hostonly, "192.168.33.10"

  # Assign this VM to a bridged network, allowing you to connect directly to a
  # network using the host's network device. This makes the VM appear as another
  # physical device on your network.
  # config.vm.network :bridged

  # Forward a port from the guest to the host, which allows for outside
  # computers to access the VM, whereas host only networking does not.
  # config.vm.forward_port 80, 8080

  config.vm.forward_port 3306, 13306

  config.vm.network :hostonly, "33.33.33.10"


end


Set dynamic dns in router settings https://prnt.sc/o5jnxp

Set port forwarding in router settings https://prnt.sc/ou9lqp (more details https://www.noip.com/support/knowledgebase/general-port-forwarding-guide/)

Install Dynamic Update Client https://www.noip.com/download

Find out your public ip here https://2ip.ru/



Another machine access by
mysql -h 176.104.148.151 -P 3306 -u root -p