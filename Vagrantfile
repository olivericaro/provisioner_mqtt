Vagrant.configure("2") do |config|
  # Configuração da box do Ubuntu 20.04
  config.vm.box = "ubuntu/focal64"  # Box para o Ubuntu 20.04

  # Configuração de rede, compartilhamento de pastas e etc.
  config.vm.network "private_network", type: "dhcp"
  
  # Provisionamento para instalar o Ansible
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install ansible -y
    sudo apt list --installed ansible
  SHELL

  # Provisionamento para executar o playbook do Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "mqtt_setup.yml"
    ansible.verbose = "v"  # Para mais detalhes durante a execução do playbook
  end
end
