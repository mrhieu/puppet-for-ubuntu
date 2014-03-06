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
$ sudo apt-get install puppet-common #standalone mode, no need master puppet to run
```
After installation finish we will find directory /etc/puppet/. Copy manifests and modules of vagrant from https://github.com/mrhieu/puppet-for-ubuntu into that directory.

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
Drink coffee en enjoy your working environment :)

Ref: https://help.ubuntu.com/12.04/serverguide/puppet.html
