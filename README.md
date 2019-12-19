#install vagrant and virtual box
#go to git bash
# use command :
- vagrant init
# to upload the vagrant use:
- vagrant up
# to go to the vm(virtualmachine)
- vagrant ssh

##before vagrant up however you need to  change the vagrantfile

##for config.vm.box change base to

 - config.vm.box = "ubuntu/xenial64"

##then to ubuntu

#to set the private ip to to the necessary you have to enter this code:

- config.vm.network "private_network", ip: "192.168.10.100"

##also this for development.local
- config.hostsupdater.aliases = ["development.local"]
#then to automatise create  a provision.sh files

# with the necessary commands
# to make provision work add the config to vagrantfile:
``config.vm.provision "shell", path: "provision.sh"``
# to do the necessary updates write these to provision:
`sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -``
# for the app you have to also install nodjs and pm2 :
``sudo apt-get install -y nodejs
sudo npm install pm2 -g``
#to go to the app and run it type these commands:
``cd /app
sudo npm install
sudo npm start``
