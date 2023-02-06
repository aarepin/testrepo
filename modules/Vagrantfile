require 'getoptlong'

opts = GetoptLong.new(
    [ '--machine', GetoptLong::OPTIONAL_ARGUMENT ]
)

machine='ubuntu/bionic64'

opts.each do |opt, arg|
    case opt
        when '--machine'
            machine=arg
    end
end

Vagrant.configure("2") do |config|
    config.vm.define "master" do |master|
        master.vm.box = "#{machine}"
        master.vm.hostname = "master.local"
        master.vm.network :private_network, ip: "192.168.56.102"
        master.vm.provision "file", source: "hosts", destination: "/tmp/hosts"
        master.vm.provision "file", source: "id_rsa", destination: "/home/vagrant/.ssh/id_rsa"
        master.vm.provision "shell", inline: "chmod 0600 /home/vagrant/.ssh/id_rsa"
        master.vm.provision "shell", inline: "echo ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDGZrPhQucTAk04dzOiQ3Ux42wO7M9IJp8juSTDy7kVFkXTRYXk5qytUpAkdyj1WozHKE1nt1lwA90nLIM8Z/DJ282So4hJBu9X8mtGre4zkvwVmumYgKNjguarNIo5qw4siFoU3ySR7lv+Lb20rAAr06kpMTkFzJ4KoAJI5zPbmaHSXwqlvpuWpkdzrPz81XhjLGfe70pmOHvGsfDVdsPyKZVqL4+oihjdce831WNXZOVTLRJw3+rrKl0/EAf1WdG2rIG/GegdMi+Dp8F+HtqyhHcDN6uOF7jmvejg5942yXlH3JO646UCVEn4N7xCUw1qmPQT7+j/mo0W/xg4QGL >> /home/vagrant/.ssh/authorized_keys"
        master.vm.provision "shell", inline: "mv /tmp/hosts /etc/hosts"
        master.vm.provision "shell", inline: "sudo apt update -y"
        master.vm.provision "shell", inline: "sudo apt install python -y"
        master.vm.boot_timeout = 360
        master.vm.provider "virtualbox" do |vb|
            vb.memory = "6144"
            vb.cpus = 2
        end
    end
    config.vm.define "node1" do |node1|
        node1.vm.box = "#{machine}"
        node1.vm.hostname = "node1.local"
        node1.vm.network :private_network, ip: "192.168.56.103"
        node1.vm.provision "file", source: "hosts", destination: "/tmp/hosts"
        node1.vm.provision "shell", inline: "mv /tmp/hosts /etc/hosts"
        node1.vm.provision "file", source: "id_rsa", destination: "/home/vagrant/.ssh/id_rsa"
        node1.vm.provision "shell", inline: "chmod 0600 /home/vagrant/.ssh/id_rsa"
        node1.vm.provision "shell", inline: "echo ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDGZrPhQucTAk04dzOiQ3Ux42wO7M9IJp8juSTDy7kVFkXTRYXk5qytUpAkdyj1WozHKE1nt1lwA90nLIM8Z/DJ282So4hJBu9X8mtGre4zkvwVmumYgKNjguarNIo5qw4siFoU3ySR7lv+Lb20rAAr06kpMTkFzJ4KoAJI5zPbmaHSXwqlvpuWpkdzrPz81XhjLGfe70pmOHvGsfDVdsPyKZVqL4+oihjdce831WNXZOVTLRJw3+rrKl0/EAf1WdG2rIG/GegdMi+Dp8F+HtqyhHcDN6uOF7jmvejg5942yXlH3JO646UCVEn4N7xCUw1qmPQT7+j/mo0W/xg4QGL >> /home/vagrant/.ssh/authorized_keys"
        node1.vm.provision "shell", inline: "sudo apt update -y"
        node1.vm.provision "shell", inline: "sudo apt install python -y"
        node1.vm.boot_timeout = 360
        node1.vm.provider "virtualbox" do |vb|
            vb.memory = "1024"
        end

    end

    config.vm.define "node2" do |node2|
        node2.vm.box = "#{machine}"
        node2.vm.hostname = "node2.local"
        node2.vm.network :private_network, ip: "192.168.56.104"
        node2.vm.provision "file", source: "hosts", destination: "/tmp/hosts"
        node2.vm.provision "file", source: "id_rsa", destination: "/home/vagrant/.ssh/id_rsa"
        node2.vm.provision "shell", inline: "chmod 0600 /home/vagrant/.ssh/id_rsa"
        node2.vm.provision "shell", inline: "echo ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDGZrPhQucTAk04dzOiQ3Ux42wO7M9IJp8juSTDy7kVFkXTRYXk5qytUpAkdyj1WozHKE1nt1lwA90nLIM8Z/DJ282So4hJBu9X8mtGre4zkvwVmumYgKNjguarNIo5qw4siFoU3ySR7lv+Lb20rAAr06kpMTkFzJ4KoAJI5zPbmaHSXwqlvpuWpkdzrPz81XhjLGfe70pmOHvGsfDVdsPyKZVqL4+oihjdce831WNXZOVTLRJw3+rrKl0/EAf1WdG2rIG/GegdMi+Dp8F+HtqyhHcDN6uOF7jmvejg5942yXlH3JO646UCVEn4N7xCUw1qmPQT7+j/mo0W/xg4QGL >> /home/vagrant/.ssh/authorized_keys"
        node2.vm.provision "shell", inline: "mv /tmp/hosts /etc/hosts"
        node2.vm.provision "shell", inline: "sudo apt update -y"
        node2.vm.provision "shell", inline: "sudo apt install python -y"
        node2.vm.boot_timeout = 360
        node2.vm.provider "virtualbox" do |vb|
            vb.memory = "1024"
        end

    end
    config.vm.define "ansible" do |ansible|
        ansible.vm.box = "#{machine}"
        ansible.vm.hostname = "ansible.local"
        ansible.vm.network :private_network, ip: "192.168.56.101"
        ansible.vm.provision "file", source: "id_rsa", destination: "/home/vagrant/.ssh/id_rsa"
        ansible.vm.provision "shell", inline: "chmod 0600 /home/vagrant/.ssh/id_rsa"
        ansible.vm.provision "shell", inline: "echo ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDGZrPhQucTAk04dzOiQ3Ux42wO7M9IJp8juSTDy7kVFkXTRYXk5qytUpAkdyj1WozHKE1nt1lwA90nLIM8Z/DJ282So4hJBu9X8mtGre4zkvwVmumYgKNjguarNIo5qw4siFoU3ySR7lv+Lb20rAAr06kpMTkFzJ4KoAJI5zPbmaHSXwqlvpuWpkdzrPz81XhjLGfe70pmOHvGsfDVdsPyKZVqL4+oihjdce831WNXZOVTLRJw3+rrKl0/EAf1WdG2rIG/GegdMi+Dp8F+HtqyhHcDN6uOF7jmvejg5942yXlH3JO646UCVEn4N7xCUw1qmPQT7+j/mo0W/xg4QGL >> /home/vagrant/.ssh/authorized_keys"
        ansible.vm.provision "file", source: "hosts", destination: "/tmp/hosts"
        ansible.vm.provision "shell", inline: "sudo mv /tmp/hosts /etc/hosts"
        ansible.vm.provision "shell", inline: "sudo apt update -y"
        ansible.vm.provision "shell", inline: "sudo apt-get install ansible -y"
        ansible.vm.boot_timeout = 360
    end

end
