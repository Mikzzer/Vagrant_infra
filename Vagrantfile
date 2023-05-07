Vagrant.configure("2") do |config|
  servers=[
      {
        :hostname => "control",
        :box => "boxomatic/centos-stream-9",
        :ip => "172.16.1.50",
        :ssh_port => '2200',
        :memory => 3072
},
{
        :hostname => "node1",
        :box => "boxomatic/centos-stream-9",
        :ip => "172.16.1.51",
        :ssh_port => '2201',
        :memory => 1024
},
{
        :hostname => "node2",
        :box => "boxomatic/centos-stream-9",
        :ip => "172.16.1.52",
        :ssh_port => '2202',
        :memory => 1024
}
    ]

  servers.each do |machine|
      config.vm.define machine[:hostname] do |node|
          node.vm.box = machine[:box]
          node.vm.hostname = machine[:hostname]
          node.vm.network :private_network, ip: machine[:ip]
          node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
          node.vm.provider :virtualbox do |vb|
              vb.customize ["modifyvm", :id, "--memory", machine[:memory]]
              vb.customize ["modifyvm", :id, "--cpus", 1]
          end
          node.vm.provision "shell", inline: "echo 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCtYJ8U1C/1MwOUicfkduC2ewIkQR2/HqpEHF4xhHEr/JgjCuNkcuKNJOPqHo7ZYGu3I5uDYG4c8R0k2zdmvNRLcCAcNBLZbgJmFb4621OUhsm+gZGXkmFWNd7Odn2j3jVe9l5dYAcn2iRrCP+UoFW4ALqko8cQpZa7JmpYgKnGSYS/aI+py1W6bPJA3jZ3Nr6AYD7kYIzhmq+1uJ+ro1H6wzZsbdZneCJy+HFpAgIUbg7zdfVsd6xvwzBXWWtkeUn1hDVmEg/EqQPXgaNmRr7vcyPnTBeZ8UPIVCN0fxE5HC947dBncAuPSkWSTSh45RGiQxbD6+G4oAFkQrYLMXPH4ig9kAeDLYOdCEoRyHHIBsEiMaWYf0YIia5DMrHplnGxK8YEJoworNJqNBNxm28lEk4eIRSr2KgSA1Y56AREz6B0p/XbGg6+WbQMDAj8MLCdO6CT6X8Cx4FjjPhgANFjhF1L7ystSx2y8R2bdpFsgVQwET0ce/L2E6Jov4Ts9t8= Mikolaj@DESKTOP-3NCCB3Q' >> /home/vagrant/.ssh/authorized_keys"
          node.vm.provision "shell", inline: "echo 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDXJiGje4Fg8mtAFDVuWwPJ+l1Cy/K/tJ6QpeG93C3q+nQu8ZOI4pB+Ypvnb15FBYrqTb7L7DxsXgVukOOsx2E/WQD0Ac5hZLerZMH1fWDa7sGYWIL1DdumAG3u/ly8xJsskTrp/3N47Bj/phHPhmzAd8vVMvpJlAvNouozS86uPUQBTX2dKBJfo93QmtV2K450ihTlb8XG1IXTE2/UsuSyUIlyykHxqjlJwF2M6K7Ur42VMoaV/Up6t1uDSTYSDSQePQf8qSfKkYZ0A4c/Atd18LFGAV3tZ5nSrkbdm719c0P6Kww7GXJoov16odQrf08VtfTqg5FHNqZBxkIacznicTEB9HkJwCS3XXjx6qJbcS/NQI5k93l5c/ETETyM4ljJAAnHgAv4ba6AU3QDGdle3JRF6tTq0D7IqgSVxg/ty3QuO+Lpcwv8NIdxpsiH5jLxXEIB3k4UzuIWIZdaIEOW9wDIdt5cLMcDsgE5yF//guNeeGNamcHzdMOVimD6SiE= mikolaj@DESKTOP-3NCCB3Q' >> /home/vagrant/.ssh/authorized_keys"
      end
  end
end