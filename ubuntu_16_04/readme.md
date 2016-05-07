# Ubuntu 16.04 setup

## !activate canoncial partners under software!

## fix wifi issue after suspend/hibernate

`sudo nano /etc/systemd/system/wifi-resume.service`

Copy the contents of wifi-resume.service

`sudo systemctl enable wifi-resume.service`


## Create default directories

```
mkdir ~/development
mkdir ~/git
```

## install indicators

***system monitor***

`sudo apt install indicator-multiload`

***weather***

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install my-weather-indicato
```

## arc theme install
http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme

## Chrome install
Download from https://www.google.de/chrome/browser/desktop/

```
sudo dpkg -i --force-depends google-chrome-stable_current_amd64.deb 
sudo apt install -f
```
## KeePassX 2.0

```
sudo add-apt-repository ppa:eugenesan/ppa
sudo apt update
sudo apt install keepassx
```

## Git

```
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

## ZSH

```
sudo apt install zsh
sudo chsh -s /usr/bin/zsh $USER
sudo curl -L http://install.ohmyz.sh | sh
```

Enable ZSH as default command in terminal under profile

http://askubuntu.com/a/342342

## Ubuntu make
```
sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
sudo apt update
sudo apt install ubuntu-make
umake ide webstorm
umake android
```

## Node version manager (NVM)
Grab latest install command from https://github.com/creationix/nvm and execute

***Restart terminal***

```
nvm install 5
nvm install 4
nvm install 0.10

nvm use 5
```


## mongo db in version 3.0
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
sudo apt install -y mongodb-org
```
### Setup autostart
https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-16-04

`sudo nano /etc/systemd/system/mongodb.service`

Copy the contents of mongodb.service

`sudo systemctl enable mongodb.service`


## elasticsearch in v 1.7.X
```
cd /tmp && wget https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-1.7.5.deb
cd /tmp && sudo dpkg -i elasticsearch-1.7.5.deb
sudo systemctl start elasticsearch.service
sudo systemctl enable elasticsearch.service
```
## robomongo

Grab latest from https://robomongo.org/download

extract to ~/development
