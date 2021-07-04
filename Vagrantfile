# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    config.vm.box = "centos/7"
    #config.ssh.insert_key = false
    config.vm.provider :virtualbox do |v|
        v.memory = 256
        v.cpus = 1
    end

    boxes =[
        {
            :name => "Nginx1",
            :ip => "10.0.0.101",
        },
        {
            :name => "Nginx2",
            :ip => "10.0.0.102",
        },
        {
            :name => "backend1",
            :ip => "10.0.0.103"
        },
        {
            :name => "backend2",
            :ip => "10.0.0.104",
        },
    ]
    boxes.each do |b|
        config.vm.define b[:name] do |box|
            box.vm.host_name = b[:name]
            box.vm.network "private_network", ip: b[:ip]
            if b[:name] == "Nginx1"
                box.vm.network "public_network"
            end
            if b[:name] == "Nginx2"
                box.vm.network "public_network"
            end
        end
    end
end
