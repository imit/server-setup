#!/bin/bash
# A simple Script for installing Rails on Ubuntu 13.04(for CLEAR SYSTEM!!!)
# Author: umit kit
# License: MIT

# fixed error for install rdoc!!!(not work)
export LC_CTYPE=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_ALL="en_US.UTF-8"
RUBY19_VERSION="1.9.3"
RUBY20_VERSION="2.0.0"
LOG_FILE="$HOME/rails_install.log"

# Make sure hostname is set
if ["`cat /etc/hostname`" != "$hostname" ]; then
  echo $hostname > /etc/hostname
  hostname -F /etc/hostname
  # TODO: Add ip address and hostname to /etc/hosts
fi


sudo locale
sudo locale-gen en_US en_US.UTF-8
sudo dpkg-reconfigure locales 

echo "#######################################"
echo "######## Ruby + Rail installer ########"
echo "#######################################"
echo -n "Updating package cache..."
sudo apt-get update >>$LOG_FILE
echo "Done"
echo -n "Upgrading package cache..."
sudo apt-get -y upgrade >>$LOG_FILE
echo "Done"

sudo apt-get install python-software-properties >>$LOG_FILE
# Install git
echo -n "Installing git..."
sudo apt-get -y install git >>$LOG_FILE
echo "Done"
# Install CURL
echo -n "Installing Curl..."
sudo apt-get -y install curl >>$LOG_FILE
echo "Done"

# Install Additional Dependencies
echo -n "Install additional dependencies..."
sudo apt-get -y install build-essential openssl libreadline6 libreadline6-dev zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion >>$LOG_FILE
echo "Done"



# Install nodejs
echo -n "Install nodejs..."
# Node.js
sudo apt-add-repository -y ppa:chris-lea/node.js
sudo apt-get -y update
sudo apt-get -y install nodejs >>$LOG_FILE
echo "Done"
echo "#######################################"
echo "######## Rvm ########"
echo "#######################################"
# Install Ruby Version Manager
echo -n "Installing RVM..."
sudo curl -L https://get.rvm.io | bash -s stable --ruby >>$LOG_FILE
echo "Done"

# Loading Ruby Version Manager
echo -n "Loading RVM..."
source ~/.rvm/scripts/rvm >>$LOG_FILE
echo "Done"

# Check requirements RVM
echo -n "RVM check requirements..."
rvm requirements >>$LOG_FILE
echo "Done"
# Set default ruby version($RUBY19_VERSION)
rvm use $RUBY20_VERSION --default >>$LOG_FILE


# Install latests rails(v4+)
echo -n "Installing Rails(v.4+) gem..."
gem install rails >>$LOG_FILE
echo "Done"

# See all ruby version
echo -n "Start list of ruby installed:"
rvm list
echo "End list of ruby version"


gem install bundler >>$LOG_FILE
# See message about completed install

echo "#######################################"
echo "########## Server ##########"
echo "#######################################"
# Nginx
sudo apt-add-repository -y ppa:nginx/stable
sudo apt-get -y update
sudo apt-get -y install nginx

# Imagemagick
sudo apt-get -y install imagemagick

# Memcached
sudo apt-get -y install memcached

# Monit
apt-get -y install monit



sudo apt-get -y install postfix

echo "deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main" > /etc/apt/sources.list.d/pgdg.list
wget --quiet -O - http://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc | apt-key add -

apt-get -y update
aptitude -y install postgresql-common
aptitude -y install postgresql-9.2

echo "#######################################"
echo "########## Completed install ##########"
echo "#######################################"
