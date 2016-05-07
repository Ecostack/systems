# Ubuntu 16.04 setup

## fix wifi issue after suspend/hibernate
sudo nano /etc/systemd/system/wifi-resume.service

```
#/etc/systemd/system/wifi-resume.service
#sudo systemctl enable wifi-resume.service
[Unit]
Description=Restart networkmanager at resume
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
```

sudo systemctl enable wifi-resume.service


## Create default directories
mkdir ~/development
mkdir ~/git

## arc theme install
http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme

## Chrome install
sudo dpkg -i --force-depends google-chrome-stable_current_amd64.deb 
sudo apt install -f

## KeePassX 2.0
sudo add-apt-repository ppa:eugenesan/ppa
sudo apt update
sudo apt install keepassx

## Git
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git

## ZSH
sudo apt install zsh
sudo chsh -s /usr/bin/zsh $USER
### http://michael-prokop.at/computer/tools_zsh_liebhaber.html#faehigkeiten
sudo curl -L http://install.ohmyz.sh | sh
### Enable ZSH as default command in terminal under profile
### http://askubuntu.com/a/342342

## Ubuntu make
sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
sudo apt update
sudo apt install ubuntu-make
umake ide webstorm
umake android

## Node version manager (NVM)
### CHECK NEWEST VERSION OF NVM
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh | bash
### Restart terminal
nvm install 5
nvm install 4
nvm install 0.10

nvm use 5

## mongo db
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
sudo apt install -y mongodb-org
### Setup autostart
### https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-16-04

sudo nano /etc/systemd/system/mongodb.service

```
[Unit]
Description=High-performance, schema-free document-oriented database
After=network.target

[Service]
User=mongodb
ExecStart=/usr/bin/mongod --quiet --config /etc/mongod.conf

[Install]
WantedBy=multi-user.target
```

sudo systemctl enable mongodb.service


## elasticsearch
cd /tmp && wget https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-1.7.5.deb
cd /tmp && sudo dpkg -i elasticsearch-1.7.5.deb
sudo systemctl start elasticsearch.service
sudo systemctl enable elasticsearch.service

## robomongo
https://robomongo.org/download
### extract to ~/development/robomongo
