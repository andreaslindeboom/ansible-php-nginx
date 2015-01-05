#ansible-php-nginx
A basic Vagrant/Ansible setup that can be used for quickly and easily creating and provisioning Vagrant boxes with a 
basic PHP/Nginx setup.

##Usage
- make sure that vagrant-hostsupdater and vagrant-env are installed (vagrant plugin install \[plugin_name\])
- clone the repo
- create a .env file based on .env.dist and add the Vagrant box identifier, Virtualbox machine name and hostname 
- vagrant up

##Dependencies
- Vagrant-hostsupdater
- Vagrant-env