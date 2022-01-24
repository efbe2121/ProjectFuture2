# If you want to test an ansible use this format
# vm.provision "ansible" do |asb|
#      asb.playbook = "playbooktester.yaml"
#    end


# -*- mode: ruby -*-
# vi: set ft=ruby :

######################################################
#
require 'yaml'
#
######################################################

cfgs = YAML.load_file(File.join(File.dirname(__FILE__), 'config.yml'))

Vagrant.configure("2") do |config|

  # Vagrant plugin which automatically installs the host's 
  # VirtualBox Guest Additions on the guest system

  # VirtualBox Guest Additions are a collection of 
  # device drivers and system applications designed 
  # to achieve closer integration between the host 
  # and guest operating systems. They help to enhance 
  # the overall interactive performance and usability of guest systems

  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end

  # This setting will send keep-alive packets every 5 seconds by default to keep connections alive
  config.ssh.keep_alive = true

  ################################
  #                              #
  # Looping over master creation #
  #                              #
  ################################

  (1..cfgs.fetch('master').fetch('count')).each do |i|

    config.vm.define "master%d" % i do |master|

      hostname =  "master%d" % i

      master.vm.box = cfgs.fetch('vagrantBox')
      master.vm.hostname = hostname

      master.vm.network "private_network", :name => "vboxnet0", :adapter => 2, :ip => cfgs.fetch('ip').fetch('master%d' % i)

      master.vm.provider :virtualbox do |vb|
        vb.name = hostname
        vb.cpus = cfgs.fetch('master').fetch('cpus')
        vb.memory = cfgs.fetch('master').fetch('memory')
        vb.customize ["modifyvm", :id, "--cpuexecutioncap", cfgs.fetch('master').fetch('cpuexecutioncap')]
      end

      master.vm.provision "ansible" do |asb|
        asb.playbook = "provisioning/master/playbook.yaml"
        asb.host_vars = {
          hostname => { "node_ip" => cfgs.fetch('ip').fetch(hostname),
                        "current_host" => hostname}
        }
        asb.vault_password_file = "secrets/vault_pwd"
      end
      
    end
  end

  ################################
  #                              #
  # Looping over worker creation #
  #                              #
  ################################

  (1..cfgs.fetch('worker').fetch('count')).each do |i|

    config.vm.define "worker%d" % i do |worker|

      hostname =  "worker%d" % i

      worker.vm.box = cfgs.fetch('vagrantBox')
      worker.vm.hostname = hostname
      
      worker.vm.network "private_network", :name => "vboxnet0", :adapter => 2, :ip => cfgs.fetch('ip').fetch('worker%d' % i)

      worker.vm.provider :virtualbox do |vb|
        vb.name = hostname
        vb.cpus = cfgs.fetch('worker').fetch('cpus')
        vb.memory = cfgs.fetch('worker').fetch('memory')
        vb.customize ["modifyvm", :id, "--cpuexecutioncap", cfgs.fetch('worker').fetch('cpuexecutioncap')]
      end
      
      worker.vm.provision "ansible" do |asb|
        asb.playbook = "provisioning/worker/playbook.yaml"
        asb.host_vars = {
          hostname => { "node_ip" => cfgs.fetch('ip').fetch(hostname),
                        "current_host" => hostname}
        }
        asb.vault_password_file = "secrets/vault_pwd"
      end
      
    end

  end

  ################################
  #                              #
  # Creation of MonitoringServer #
  #                              #
  ################################

  config.vm.define "monitoringServer" do |mn|

    mn.vm.box = cfgs.fetch('vagrantBox')
    mn.vm.hostname = cfgs.fetch('monitoring').fetch('hostname')
    
    mn.vm.network "private_network", :name => "vboxnet0", :adapter => 2, :ip => cfgs.fetch('ip').fetch('monitor')

    mn.vm.provider :virtualbox do |vb|
      vb.name = "monitor"
      vb.cpus = cfgs.fetch('monitoring').fetch('cpus')
      vb.memory = cfgs.fetch('monitoring').fetch('memory')
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", cfgs.fetch('monitoring').fetch('cpuexecutioncap')]
    end

    mn.vm.provision "ansible" do |asb|
      asb.playbook = "provisioning/monitoring/playbook.yaml"
    end

  end

  ################################
  #                              #
  # Creation of DatabaseServer   #
  #                              #
  ################################

  config.vm.define "databaseServer" do |db|

    db.vm.box = cfgs.fetch('vagrantBox')
    db.vm.hostname = cfgs.fetch('database').fetch('hostname')

    db.vm.network "private_network", :name => "vboxnet0", :adapter => 2, :ip => cfgs.fetch('ip').fetch('dbase')

    db.vm.provider :virtualbox do |vb|
      vb.name = "database"
      vb.cpus = cfgs.fetch('database').fetch('cpus')
      vb.memory = cfgs.fetch('database').fetch('memory')
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", cfgs.fetch('database').fetch('cpuexecutioncap')]
    end

  end

end
