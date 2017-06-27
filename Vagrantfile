Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    config.vm.define "R1" do |node|
      node.vm.box = "iosxe/clus-gs.20170524"
      node.vm.network "private_network",
        ip: "172.20.20.10",
        auto_config: false
      node.vm.network "private_network",
        virtualbox__intnet: "link1",
        auto_config: false

      # attach a configuration disk
      node.vm.provider "virtualbox" do |v|
        v.customize ["storageattach", :id,
          "--storagectl", "IDE_Controller",
          "--port", 1,
          "--device", 0,
          "--type", "dvddrive",
          "--medium", "R1.iso"
        ]

        #v.customize ["modifyvm", :id,
        #  "--uart1", "0x3F8", 4,
        #  "--uartmode1", 'tcpserver', 65000
        #]
      end
    end

    config.vm.define "R2" do |node|
      node.vm.box = "iosxe/clus-gs.20170524"
      node.vm.network "private_network",
        ip: "172.20.20.20",
        auto_config: false
      node.vm.network "private_network",
        virtualbox__intnet: "link1",
        auto_config: false

      # attach a configuration disk
      node.vm.provider "virtualbox" do |v|
        v.customize ["storageattach", :id,
          "--storagectl", "IDE_Controller",
          "--port", 1,
          "--device", 0,
          "--type", "dvddrive",
          "--medium", "R2.iso"
        ]
        #v.customize ["modifyvm", :id,
        #  "--uart1", "0x3F8", 4,
        #  "--uartmode1", 'tcpserver', 65001
        #]
      end
    end
end
