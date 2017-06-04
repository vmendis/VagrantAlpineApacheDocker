# BPTest

The idea behind this repository is to use Vargrant, Oracle VirtualBox and Ansible to
provision a simple server, build a web service based on nginx and serve out a
simple web page.

1. Download and install the appropriate version of VirtualBox from here:
   https://www.virtualbox.org/

1a. Make sure Ansible is installed on your computer. 

2. Download the scripts from this site

3. Network setup

Local computer ip = 192.168.1.146
Guest OS ip = 192.168.33.99
     Specified in Vagrantfile
     defined config.vm.network "private_network", ip: "192.168.33.99"


Confirm
   config.vm.network "forwarded_port", guest: 80, host: 8080



   ssh -l vagrant  -i .vagrant/machines/default/virtualbox/private_key 192.168.33.99



NOTES:

0. debian/jessie64 is used as the guest host
1. Checking of the Debian version is omitted for simplicity
2. For MacOS users:
   I encountered the following bugs and used a workaround. Your mileage may vary.

   docker_image, docker_container and docker modules fails with:
   "Failed to import docker-py - No module named requests.exceptions. Try `pip install docker-py`"}

   See: https://github.com/ansible/ansible-modules-core/issues/4246
        time spent on researching this

   So, I am using the ansible 'command' module as an alternative.
