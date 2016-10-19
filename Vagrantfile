Vagrant.configure("2") do |config|

  proname="node"  
  N=4
  (1..N).each do |i|
      config.vm.define "#{proname}-#{i}" do |node|
         node.vm.box="centos/7"
         node.vm.network :private_network, ip: "192.168.51.#{i}", virtualbox__intnet: true
         node.vm.hostname="#{proname}-#{i}"
         if i == N
            node.vm.provision :ansible do |ansible|
               ansible.playbook="install_postgresql.yml"
               ansible.limit="all"
            end
            node.vm.provision :ansible, run: "always" do |ansible|
               ansible.playbook="initialized_pgdb.yml"
	       ansible.limit="all"
            end
         end
      end
  end
end
