unless Vagrant.has_plugin?("vagrant-docker-compose")
  system("vagrant plugin install vagrant-docker-compose")
  puts "Dependencies installed, please try the command again."
  exit
end

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.network "public_network"
  config.vm.synced_folder ".", "/vagrant"
  config.vm.network(:forwarded_port, guest: 80, host: 80)
#---------------------------------------#
# Docker-related stuff
#
config.vm.provision "shell", inline: <<-EOC
# install Docker
curl -sSL https://get.docker.com/ | sudo sh

# add 'vagrant' user to "docker" group
sudo usermod -aG docker vagrant

# enabled when booting
sudo systemctl enable docker
sudo systemctl start  docker

EOC

 # Install docker-compose
  config.vm.provision "shell", inline: <<-EOC
  sudo yum install epel-release -y
  sudo yum install -y python-pip
  sudo pip install docker-compose
  sudo yum upgrade python* -y
  docker network create site1_default
  docker network create site2_default
  docker network create site3_default
    
  EOC
  # docker-compose to create reverseproxy and 3 Nginx web container
   
   config.vm.provision :docker
   config.vm.provision :docker_compose, yml: ["/vagrant/Nginx/reverse-proxy/docker-compose-base.yml"], project_name: "myproject", run: "always"
   config.vm.provision :docker
   config.vm.provision :docker_compose, yml: ["/vagrant/Nginx/site1/docker-compose.yml"], project_name: "app_site1", run: "always"
   config.vm.provision :docker
   config.vm.provision :docker_compose, yml: ["/vagrant/Nginx/site2/docker-compose.yml"], project_name: "app_site2", run: "always"
   config.vm.provision :docker
   config.vm.provision :docker_compose, yml: ["/vagrant/Nginx/site3/docker-compose.yml"], project_name: "app_site3", run: "always"
#File Ends   
   end
