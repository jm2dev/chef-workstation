=============
Chef :: notes
=============

------------------------
Hosted chef with opscode
------------------------

.. sidebar:: Contents

    .. contents::

.. sectnum::

Workstation setup
=================

Get the starter kit and run
::

   unzip chef-starter.zip
   cd chef-repo
   git init
   git add .
   git commit -m 'Initial commit.'
   knife client list

Cookbooks
=========

::

   knife cookbook site install yum
   knife cookbook site install yumrepo
   knife cookbook site install selinux
   knife cookbook site install java
   knife cookbook site install couchdb
   knife cookbook site install haproxy
   knife cookbook site install nginx

Roles
=====

::

   knife role create ci
   knife role show ci -d -Fjson > roles/ci.json
   knife role from file roles/ci.json

Bootstrap
=========

::

   knife bootstrap jm2dev.cloud.tilaa.eu --ssh-user YYY --ssh-password XXX --ssh-port 2222 --run-list "role[ci]"

Data bags
=========

::

   knife data bag create users
   knife data bag from file data_bags/users.json

Issues
======

java not found
--------------

It seems the java recipe does not set ``/etc/alternatives`` properly in
fedora when we have installed the openjdk package.

::

   /etc/alternatives/java -> /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/bin/java
   /etc/alternatives/javac -> /usr/lib/jvm/java-1.7.0-openjdk-1.7.0.25-2.3.12.3.fc19.x86_64/bin/javac
   /etc/alternatives/javac.1.gz -> /usr/share/man/man1/javac-java-1.7.0-openjdk-1.7.0.25-2.3.12.3.fc19.x86_64.1.gz

firewall
--------

`fedora firewall`_.

.. _fedora firewall: https://fedoraproject.org/wiki/FirewallD#Using_firewall-cmd
