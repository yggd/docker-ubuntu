box_os = "bento/ubuntu-22.04"
network_br = "enp87s0"

vmspec = {
  name: "docker-ce",
  cpu: 4,
  memory: 4096,
  private_ip: "192.168.56.14",
  public_ip: "192.168.11.94",
  disk_size: "50GB",
  synced_folder: "/var/synced"
}

Vagrant.configure("2") do |config|
  config.vm.define vmspec[:name] do |v|
    v.vm.box = box_os
    v.vm.box_check_update = true
    v.vm.boot_timeout = 1000
    v.vm.hostname = vmspec[:name]
    v.vm.disk :disk, size: vmspec[:disk_size], primary: true
    v.vm.network :private_network,ip: vmspec[:private_ip]
    v.vm.network :public_network,ip:  vmspec[:public_ip], bridge: network_br
    v.vm.synced_folder "./", vmspec[:synced_folder]
    v.vm.provider "virtualbox" do |vbox|
      vbox.gui = false
      vbox.cpus = vmspec[:cpu]
      vbox.memory = vmspec[:memory]
      vbox.customize ["modifyvm", :id, "--cableconnected1", "on"]
    end
    v.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/hosts"
      #ansible.verbose = "-v"
    end
  end
end

