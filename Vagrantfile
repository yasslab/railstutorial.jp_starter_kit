Vagrant.configure(2) do |config|
  config.vm.box = "hanachin/railstutorial4.0-32"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.synced_folder "./data", "/vagrant_data"
end

