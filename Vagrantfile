Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 512
    vb.cpus = 1
  end

  config.vm.define "xymon1" do |xymon1|
    xymon1.vm.network "forwarded_port", guest: 8888, host: 8888
    xymon1.vm.network "public_network", ip: "192.168.1.145"

    xymon1.vm.provision "shell",
      inline: "groupadd xymon && \
              useradd -g xymon -m xymon && \
              yum update -y && \
              yum install gcc make fping pcre-devel openssl-devel openldap-devel rrdtool-devel libtirpc-devel -y"
  end

  config.vm.define "xymon2" do |xymon2|
    xymon2.vm.network "public_network", ip: "192.168.1.146"
  end

  config.vm.define "xymon3" do |xymon3|
    xymon3.vm.network "public_network", ip: "192.168.1.147"
  end

end
