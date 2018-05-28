BOX_NAME='CentBox'

Vagrant.configure("2") do |config|
	
	config.vm.box = "centos/7"    	
	
	config.vm.provider "virtualbox" do |vb|  
		vb.gui = false  
		vb.memory = "2048"
		vb.cpus=2
		vb.name = BOX_NAME
	end
	
	config.vm.hostname = BOX_NAME
	
	config.vm.synced_folder './ansible_playbook', '/vagrant/ansible_playbook/'
	
	config.vm.network 'private_network', ip: '192.168.33.10'
	
	config.vm.provision :ansible_local do |ansible|
		ansible.provisioning_path = '/vagrant/ansible_playbook/'
		ansible.playbook = 'site.yml'
		ansible.inventory_path = 'inventory'
		ansible.limit= 'all'
		ansible.verbose= true
		ansible.install= true
	end
end