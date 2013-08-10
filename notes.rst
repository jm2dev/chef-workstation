=============
Chef :: notes
=============

------------------------
Hosted chef with opscode
------------------------

Workstation setup
=================

Get the starter kit and run::

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
