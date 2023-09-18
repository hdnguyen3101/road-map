## <a name="vagrant_cheat_sheet"></a> <u>Vagrant Cheat Sheet</u>
### <a name="cheat_sheet_cli"></a>*Vagrant CLI Cheat Sheet*
1. Creating the Vagrantfile
   - Khởi tạo Vagrantfile với box "base" của Vagrant 
   
   `vagrant init`

   - Khởi tạo Vagrantfile với một box cụ thể. Ex: vagrant init ubuntu/trusty64 
   
   `vagrant init <box-name>`

2. Staring a VM
   - Tạo và cấu hình máy ảo theo Vagrantfile 

   `vagrant up <name|id>`

   - Khởi động lại máy ảo sau khi suspend

   `vagrant resume <name|id>`

   - Chọn 1 provisioning để cài đặt các package cho máy ảo

   `vagrant provision <vm-name>`
   
   - Khởi động lại máy ảo Vagrant, load lại cấu hình Vagrantfile mới
   
   `vagrant reload <name|id>`

   - Khởi động lại máy ảo với 1 provision mới

   `vagrant reload --provision `

3. Truy cập vào máy ảo
   - Kết nói với máy ảo bằng SSH

   `vagrant ssh`

   `vagrant ssh <name|id> ` -- có thể ssh vào bằng tên hoặc id của máy ảo tại bất kỳ thư mục nào

4. Stoping a VM
   - Dừng hoàn toàn 1 máy ảo, lệnh này tương đương với hành động shutdown.

   `vagrant halt <name|id>`

   - Tạm dừng máy ảo, ghi nhớ trạng thái hiện tại, tương đương với sleep

   `vagrant suspend <name|id>`

5. Cleaning up a VM
   - Dừng và xóa tất cả tài nguyên của máy ảo

   `vagrant destroy <name|id>` -- (-f hoặc --force sẽ xóa mà không cần xác nhận)

   - Xóa box đã cài đặt

   `vagrant box remove <name>`

6. Boxes
   - Xem danh sách tất cả các box được cài đặt vào Vagrant trên máy tính

   `vagrant box list`

   - Thêm một box local hoặc public vào Vagrant trên máy tính
   
   `vagrant box add <address>`
   
   - Kiểm tra update cho các box
   
   `vagrant box outdated (--global)`

   - Xóa box khỏi Vagrant trên máy tính
   
   `vagrant box remove <name>`
   
   - Xóa các phiên bản cũ của các box đã cài

   `vagrant box prune`

   - Đóng gói môi trường box đang chạy để có thể tái sử dụng
   
   `vagrant package –output <package.box>`

7. Saving Progress
   - Ghi lại 1 bản snapshot của máy ảo tại thời điểm hiện tại

   `vagrant snapshot save <vm-name> <snapshot-name>`

   - Khôi phục lại trạng thái máy ảo tại điểm snapshot
   
   `vagrant snapshot restore  <vm-name> <snapshot-name>`

8. Tips
   - Kiểm tra phiên bản
   
   `vagrant -v`

   - Kiểm tra trạng thái máy ảo
   
   `vagrant status <name|id>`
   
   - Kiểm tra trạng thái tất cả máy ảo
   
   `vagrant global-status`
### <a name="cheat_sheet_file"></a>*Vagrantfile Cheat Sheet*
- Port forwarding
```ruby
# Create a forwarded port mapping which allows access to a specific port
# within the machine from a port on the host machine. In the example below,
# accessing "localhost:8080" will access port 80 on the guest machine.
# NOTE: This will enable public access to the opened port
config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
```
- Mount folders and permissions
```ruby
# Share an additional folder to the guest VM. The first argument is
# the path on the host to the actual folder. The second argument is
# the path on the guest to mount the folder. And the optional third
# argument is a set of non-required options.
config.vm.synced_folder ".", "/vagrant",
  owner: "vagrant",
  group: "vagrant",
  mount_options: ["dmode=775,fmode=664"]
```
- Network
```ruby
# Create a private network, which allows host-only access to the machine
# using a specific IP.
config.vm.network "private_network",
    ip: "192.168.32.10",
    auto_config: true

# Create a public network, which generally matched to bridged network.
# Bridged networks make the machine appear as another physical device on
# your network.
config.vm.network "public_network"
```
- Provider
```ruby
# Provider-specific configuration so you can fine-tune various
# backing providers for Vagrant. These expose provider-specific options.
# Example for VirtualBox:
#
config.vm.provider "virtualbox" do |vb|
   # Display the VirtualBox GUI when booting the machine
   vb.gui = true

   # Customize the amount of memory on the VM:
   vb.memory = "1024"

   # Customize the number of CPUs on the VM:
   vb.cpus = "2"
end
```
- Provisioning: inline

Option 1:
```ruby
# Enable provisioning with a shell script. Additional provisioners such as
# Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
# documentation for more information about their specific syntax and use.
config.vm.provision "shell", inline: <<-SHELL
   apt-get update
   apt-get install -y apache2
SHELL
```
Option 2:
```ruby
$script = <<SCRIPT
apt-get update
apt-get -y upgrade
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: $script
end
```
- Launching 2 machines
```ruby
config.vm.define "zipi" do |zipi|
   zipi.vm.host_name = "zipi"
   zipi.vm.box = "ubuntu/trusty64"
   zipi.vm.network "private_network", ip: "192.168.32.10", virtualbox__intnet: true, auto_config: true
end
config.vm.define "zape" do |zape|
   zape.vm.host_name = "zape"
   zape.vm.box = "ubuntu/trusty64"
   zape.vm.network "private_network", ip: "192.168.32.11", virtualbox__intnet: true, auto_config: true
end
```
### *&rarr;* Để có thể sử dụng Vagrant một cách cơ bản nhất, chúng ta chỉ cần tập trung vào các lệnh cơ bản sau:
```shell
vagrant init
vagrant up
vagrant ssh
vagrant resume
vagrant halt
vagrant destroy
```  