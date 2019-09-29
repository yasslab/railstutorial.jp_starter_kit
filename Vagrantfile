$script = <<-SCRIPT
sudo sed -i -re 's/([a-z]{2}\.)?archive.ubuntu.com|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "YassLab/railstutorial"
  config.vm.box_version = "0.0.4"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.synced_folder "./data", "/vagrant_data"
  config.ssh.insert_key = false
  config.vm.provision "shell", inline: $script
end
