[![Build Status](https://travis-ci.org/chrismeyersfsu/role-install_mongod.svg)](https://travis-ci.org/chrismeyersfsu/role-install_mongod)

# role-install_mongod
Ansible role to install mongod
=======
install_mongod
==============

Installed MongoDB, in either standalone or resilient configurations.

Requirements
------------

To configure Mongo with a [replication set](http://docs.mongodb.org/manual/replication/) you should have groups in your inventory called `primary` and `secondary`. Primary should contain just **one** host, secondary can contain as many hosts as you like, but at least two (as MongoDB replica sets are a minimum of three hosts). Then you need to set install_mongod_replset to a name for the replica set.

Role Variables
--------------

    install_mongod_admin_username: ''
    install_mongod_admin_password: ''
    install_mongod_user_username: ''
    install_mongod_user_password: ''
    install_mongod_user_database: ''
    install_mongod_bind_ip: "0.0.0.0"
    install_mongod_replset: ''
    install_mongod_keyfile: ''          # for secure replication
    install_mongod_dbpath: ''

Dependencies
------------

    chrismeyersfsu.required_vars
    chrismeyersfsu.iptables

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: install_mongod
            , install_mongod_admin_username: admin
            , install_mongod_admin_password: Chang3Me!
            , install_mongod_user_username: awx
            , install_mongod_user_password: Chang3Me2!
            , install_mongod_user_database: awx
            , install_mongod_bind_ip: '0.0.0.0'
            , install_mongod_replset: tower
            , install_mongod_keyfile: '/etc/pki/mongo/keyfile'
            , tags: mongo }

License
-------

BSD

Author Information
------------------

Chris Meyers - original
[Mark Phillips](mailto:mark@ansible.com) - HA

