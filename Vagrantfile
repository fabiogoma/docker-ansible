docker_boxes = %w(docker1 docker2 docker3 docker4)

Vagrant.configure('2') do |config|
  config.vm.box = 'centos/7'

  config.vm.network :private_network, type: 'dhcp', name: 'vboxnet0', adapter: 2
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.vm.provider 'virtualbox' do |vb|
    vb.memory = '1024'
  end

  docker_boxes.each do |box|
    config.vm.define box.to_s do |node|
      node.vm.hostname = box.to_s
      node.vm.provision 'ansible' do |ansible|
        ansible.limit = 'all'
        ansible.playbook = 'provisioning/playbook.yml'
      end
    end
  end
end
