Vagrant.configure("2") do |config|

    config.vm.define "spellstruck-php" do |box|
        box.vm.provider :virtualbox do |v|
            v.name = "Spellstruck (PHP)"
            v.customize ["modifyvm", :id, "--memory", 2048]
        end

        box.vm.box = "ubuntu/trusty64"

        box.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64/version/1/provider/virtualbox.box"

        box.vm.network :private_network, ip: "192.168.33.98"

        box.hostsupdater.aliases = [ "spellstruck.dev.nl", "www.spellstruck.dev.nl" ]

        box.ssh.forward_agent = true

        box.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible/playbook.yml"
            ansible.inventory_path = "ansible/inventories/dev"
            ansible.limit = 'all'
        end

        box.vm.synced_folder "./", "/vagrant", type: "nfs"
    end
end
