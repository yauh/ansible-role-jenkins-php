Jenkins CI for PHP
=====

This role installs and configures the Jenkins CI server so that it builds PHP projects. Initially it set ups the system specifically for Yii projects but works with all other PHP frameworks just as well. It sets up a sample job so you can check if everything is working ok.

Requirements
------------

This role requires Ansible 1.4 or higher and platform requirements are listed
in the metadata file.

Role Variables
--------------

The variables that can be passed to this role and a brief description about
them are as follows.

```
jenkins:
  # repository that provides jenkins binaries and the corresponding key for debian
  deb:
    repo: 'deb http://pkg.jenkins-ci.org/debian binary/' # Jenkins repository
    key: 'http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key' # Jenkins key
  # variables for php.ini that will be used for cli php
  php: 
    php_version: 5
    max_execution_time: 30
    max_input_time: 60
    memory_limit: 128M
    upload_max_filesize: 8M
    allow_url_fopen: On
    allow_url_include: Off
    session_cookie_httponly: 1
    display_errors: Off
    error_reporting: E_ALL & ~E_DEPRECATED
    # where to download PHP frameworks to
    framework_directory: /var/www/
```    

Examples
========

Set up complete CI environment on all CI hosts

```
- hosts: ci
  sudo: True
  roles:
     - { role: role-jenkins-php, tags: php-ci}
```

Dependencies
------------

None

License
-------

BSD

Author Information
------------------

Stephan Hochhaus <stephan@yauh.de>

[yauh.de](http://yauh.de)


