# Puppet scripts for quickly setup a fresh Ubuntu server

## Including

* Git

* RVM

* Ruby 1.9.3 (binary RVM install)

* Rails 3.2.11

* Bundler

* SQLite3 and Postgres

* System dependencies for nokogiri, sqlite3, mysql, mysql2, and pg

* Databases and users needed to run the Active Record test suite

* Node.js for the asset pipeline

* Memcached

* Redis
 
* Imagemagik
 
* (Elasticsearch - optional)

## How to

Firstly:
```
$ sudo apt-get update
$ sudo apt-get install git vim
```

Install puppet client:
```
#Ref: http://docs.puppetlabs.com/guides/install_puppet/install_debian_ubuntu.html
$ wget https://apt.puppetlabs.com/puppetlabs-release-precise.deb
$ sudo dpkg -i puppetlabs-release-precise.deb
$ sudo apt-get update
$ sudo apt-get install puppet-common #standalone mode, no need master puppet to run
$ puppet module install maestrodev-rvm # puppet module to install RVM
```
After installation finish we will find directory /etc/puppet/. Copy manifests and modules of vagrant from https://github.com/mrhieu/puppet-for-ubuntu into that directory.
Change $home to your root directory.

```
$ cd \
$ git clone https://github.com/mrhieu/puppet-for-ubuntu.git
$ sudo cp puppet-for-ubuntu/manifests /etc/puppet/ -r
$ sudo cp puppet-for-ubuntu/modules /etc/puppet/ -r
```

Run puppet:
```
$ cd /etc/puppet
$ sudo puppet apply manifests/default.pp
```
Drink coffee and enjoy your new working environment :)

## Note
For some reason, I can not use specifics version of ruby (1.9.3) and rails (3.2.16) after running puppet. You can try to mannually install them:

```
$ curl -L get.rvm.io | bash -s -- --auto-dotfiles
$ echo "source $HOME/.rvm/scripts/rvm" >> ~/.bash_profile
$ source ~/.rvm/scripts/rvm
$ rvm install 1.9.3
$ rvm use 1.9.3 --default
$ gem install rails -v 3.2.16
```

Ref: https://help.ubuntu.com/12.04/serverguide/puppet.html
