# VagrantAlpineApacheDocker

The idea behind this repository is to use Vargrant, Oracle VirtualBox and Ansible to
provision a simple server, build a web service based on nginx and serve out a
simple web page.

1. Download and install the correct versions of following software :
   1a. VirtualBox 
       https://www.virtualbox.org/
   
   1b. Vagrant 
       https://www.vagrantup.com/downloads.html

2. Download this git repository to your computer and unzip it

3. cd to the directory where the unziped file are

4. Run "vagrant up"

5. Following message indicates the Web server has been built and in service

TASK [start the container] *****************************************************

NOTE: See "screen-capture-of-the-run.txt" for full output of the command


Testing:

1. Open a browser and enter :
http://localhost:8080/


2. Following message must appear on the browser window:

   Hello BP..........

3. Interactive login to the docker

   ssh -l vagrant  -i .vagrant/machines/default/virtualbox/private_key 192.168.33.99


Cleanup :

1. Press Ctrl/C on the terminal window where "vagrant up" was run

2. Tidy up Vagrant enviornment

$ vagrant global-status     // look for the id of the virtual box. Your output will be different to mine

id       name    provider   state   directory                                                                       
--------------------------------------------------------------------------------------------------------------------
d21c245  default virtualbox running /Users/virantha/BPTest-July-2018-Fixing-README/VagrantAlpineApacheDocker-master <br />


$ vagrant destroy d21c245       // destroy the virtualbox  <br />
    default: Are you sure you want to destroy the 'default' VM? [y/N] y  <br />
==> default: Forcing shutdown of VM...  <br />
==> default: Destroying VM and associated drives...  <br />



NETWORK SETUP

Local computer ip = 192.168.1.146

Guest OS ip = 192.168.33.99 <br />
     This is specified in Vagrantfile  <br />     
             defined config.vm.network "private_network", ip: "192.168.33.99" <br />

Port 80 in the docker is mapped to port 8080 on local computer

Confirm <br />
   config.vm.network "forwarded_port", guest: 80, host: 8080





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

