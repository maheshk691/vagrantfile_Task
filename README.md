# Task 1
Build a vagrantfile that creates a virtualbox VM (centos 7.x) with the latest version of docker and docker-compose. docker-compose will create a docker image (using a dockerfile) with nginx latest open source version.
 
run the nginx docker container as a systemctl process on the virtualbox, and expose the port 80 from virtual guest to local host OS on port 80.

# Creating the Windows Environment for this Task 

# Create below entries on the hosts file where the browser (host system) is running
myfirstpage.com  127.0.0.1

mysecondpage.com  127.0.0.1

mythirdpage.com 127.0.0.1

# Installing Vagrant on Windows

Download and install the Vagrant_1.9.8_x86_64.msi (use this link: https://releases.hashicorp.com/vagrant/1.9.8/vagrant_1.9.8_x86_64.msi)
 
# Installing VirtualBox on Windows 

Download and install the VirtualBox5.1.26 (use this link http://download.virtualbox.org/virtualbox/5.1.26/VirtualBox-5.1.26-117224-Win.exe )

Download and install VirtualBox5.1.26 Extension Pack (use this link http://download.virtualbox.org/virtualbox/5.1.26/Oracle_VM_VirtualBox_Extension_Pack-5.1.26-117224.vbox-extpack )
 
# Clone the Repo

Clone the Repo and unzip the file. 
change the directory to the location where the VagrantFile is exist. Run the below command

# vagrant up
 
# Once the Script completed.

use the local machine browser and use the below url. which will serve the content.

myfirstpage.com 
mysecondpage.com 
mythirdpage.com 
