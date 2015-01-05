Vagrant.configure("2") do |config|
    config.env.enable

    boxname = ENV['BOX_NAME']
    machinename = ENV['VIRTUAL_MACHINE_NAME']
    hostname = ENV['HOST_NAME']

    config.vm.define boxname do |box|
        box.vm.provider :virtualbox do |v|
            v.name = machinename
            v.customize ["modifyvm", :id, "--memory", 2048]
        end

        box.vm.box = "ubuntu/trusty64"

        box.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64/version/1/provider/virtualbox.box"

        box.vm.network :private_network, ip: "192.168.33.98"

        box.hostsupdater.aliases = [ hostname, "www." + hostname ]

        box.ssh.forward_agent = true

        box.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible/playbook.yml"
            ansible.limit = 'all'
        end

        box.vm.synced_folder "./", "/vagrant", type: "nfs"
    end
end
