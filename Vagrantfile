Vagrant.configure("2") do |config|
  # Run Ansible from the Vagrant VM
  config.vm.box = "ubuntu/trusty64"
  {
    'nginx-01' => '192.168.100.10'
  }.each do |short_name, ip|
    config.vm.define short_name do |host|
      host.vm.network 'private_network', ip: ip
      host.vm.hostname = "#{short_name}.local"

      host.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "playbook.yml"
      end
    end
  end
end
