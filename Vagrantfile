# https://www.vagrantup.com/docs/provisioning/ansible.html
# https://www.vagrantup.com/docs/provisioning/ansible_local.html
# https://www.vagrantup.com/docs/provisioning/ansible_intro.html
# https://www.vagrantup.com/docs/provisioning/ansible_common.html

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.4"

  # run ansible within the vm, local playbook
  config.vm.provision "ansible_local" do |ansible|
  
    ansible.install_mode = "pip"
    ansible.install_mode = "pip_args_only"
    ansible.pip_args = "-r /vagrant/requirements.txt"

    ansible.playbook       = "playbooks/development.yml"
    ansible.limit	   = "all"
    ansible.inventory_path = "hosts/local"
    ansible.verbose        = true
    ansible.raw_arguments  = Shellwords.shellsplit(ENV['ANSIBLE_ARGS']) if ENV['ANSIBLE_ARGS']

  end
end
