Vagrant.configure("2") do |config|
    config.vm.define "landing-vm" do |vmLP|
        vmLP.vm.hostname = "landing-vm"
        vmLP.vm.box = "ubuntu/focal64"
        vmLP.vm.network "forwarded_port", guest:80, host:8080, host_ip: "127.0.0.1"
        vmLP.vm.network "private_network", ip: "192.168.56.2"

        vmLP.vm.provider "virtualbox" do |vb|
            vb.name = "landingvm"
            vb.gui = false
            vb.cpus = "2"
            vb.memory = "2048"
        end

    vmLP.vm.provision "shell", inline: <<-SHELL
    sudo su
    git clone https://github.com/mguntursdc/web-server-landing.git
    cd web-server-landing/ && bash landing-server-setup.sh
    SHELL
    end

    config.vm.define "wordpress-vm" do |vmWP|
        vmWP.vm.hostname = "wordpress-vm"
        vmWP.vm.box = "ubuntu/focal64"
        vmWP.vm.network "forwarded_port", guest:80, host:8081, host_ip: "127.0.0.1"
        vmWP.vm.network "private_network", ip: "192.168.56.5"

        vmWP.vm.provider "virtualbox" do |vb|
            vb.name = "wordpressvm"
            vb.gui = false
            vb.cpus = "2"
            vb.memory = "2048"
        end
    end

    config.vm.define "webapp-vm" do |vmWA|
            vmWA.vm.hostname = "webapp-vm"
            vmWA.vm.box = "ubuntu/focal64"
            vmWA.vm.network "forwarded_port", guest:80, host:8090, host_ip: "127.0.0.1"
            vmWA.vm.network "private_network", ip: "192.168.56.3"

            vmWA.vm.provider "virtualbox" do |vb|
                vb.name = "webappvm"
                vb.gui = false
                vb.cpus = "2"
                vb.memory = "2048"
            end
        end
end
