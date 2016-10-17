Vagrant.configure("2") do |config|

  proname="node"  
  (1..3).each do |i|
      config.vm.define "#{proname}-#{i}" do |node|
         node.vm.box="centos/7"
         node.vm.network :private_network, ip: "192.168.51.#{i}", virtualbox__intnet: true
         node.vm.hostname="#{proname}-#{i}"
         node.vm.provision :ansible do |ansible|
            ansible.playbook="initial_setup.yml"
         end
      end
  end
end
