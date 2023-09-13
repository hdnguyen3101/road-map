# **ROADMAP STUDY**

>*Lộ trình này sẽ đi từ những kiến thức được tổng hợp từ [Jin](mailto:hdnguyen3101@gmail.com) trong quá trình học tập và làm việc tính đến thời điểm 2023. Nội dung bao gồm các kiến thức về Source version control (SVC), Virtualization (ảo hóa), Containerized, Continuous Integration và Continuous Delivery/Deployment (CI/CD), Configuration management (CM), Cloud Computing and Storage, Log solution (EFK), Database, Testing tool, Monitoring tools…*	

**Bắt đầu thôi!**

Dựa vào những đề mục, tôi sẽ hệ thống thứ tự các kiến thức cần học để đạt hiệu quả tiếp thu tốt nhất cho những người mới bắt đầu theo danh mục sau:

 **Table of content:**
1. [SOURCE VERSION CONTROL](#svc)

- [Git](#git)

- [(Optional) BitBucket](#bitbucket)

2. [VIRTUALIZATION](#virtualization)

- [Virtualbox](#virtualbox)

- [VMware Workstation](#vmware_workstation)

- [HyperV](#hyper_v)

- [Vagrant](#vagrant)

   + [Vagrant là gì?](#vagrant_overview)

   + [Vagrant vs. Docker](vagrant_vs_docker)

   + [Kiến trúc Vagrant](#vagrant_architecture)

   + [Vagrant Commands (CLI)](#cli)

   + [Vagrantfile](#vaagrantfile)

   + [Boxes](#boxes)

   + [Providers](#providers)

   + [Provisioning](#provisioning)

   + [Vagrant Cheat Sheet](#vagrant_cheat_sheet)
            
      - [Vagrant CLI Cheat Sheet](#cheat_sheet_cli)

      - [Vagrantfile Cheat Sheet](#cheat_sheet_file)

- [(Advanced) VMware vSphere](#vmware_vsphere)

3. [CONTAINERIZATION](#containerization)

- [Docker](#docker)

- [Docker Swarm](#docker_swarm)

- [Kubernetes](#kubernetes)

4. [CONTINUOUS INTERGRATION CONTINUOUS DELIVERY/DEPLOYMENT](#ci/cd)

- [Gitlab CI/CD](#gitlab_ci/cd)

- [Jenkins](#jenkins)

- [Argo CD](#argo_cd)

5. [CONFIGURATION MANAGEMENT (CM)](#cm)

- [Ansible](#ansible)

- [Progress Chef](#chef)

- [Puppet](#puppet)

- [Terraform](#terraform)

6. [CLOUD COMPUTING AND STORAGE](#cloud)

- [AWS](#aws)

- [Azure](#azure)

7. [LOG SOLUTION (EFK)](#log)

- [Elasticsearch](#es)

- [Fluentd/Fluentbit](#fluentd)

- [Kibana](#kibana)

8. [DATABASE](#db)

- [SQL](#sql)

- [MongoDB](#mongoDB)

- [Redis](#redis)

9. [TESTING TOOL](#test_tool)

- [Selenium](#selenium)

- [Jenkins](#jenkins_test_tool)

10. [MONITORING](#monitor)

- [Prometheus/Grafana](#prometheus/grafana)

- [Raygun](#raygun)

## <a name="svc"></a>**1.SOURCE VERSION CONTROL**
- ### <a name="git"></a>***Git***
- ### <a name="bitbucket"></a>***(Optional) BitBucket***

## <a name="virtualization"></a>**2.VIRTUALIZATION**
>Virtualization là gì? Virtualization được biết đến là công nghệ giúp tạo ra một phiên bản ảo của tài nguyên, như hệ điều hành (OS), Máy chủ (Server), Thiết bị lưu trữ (Storage), hệ thống mạng (network). Virtualization sử dụng các phần mềm mô phỏng chức năng của phần cứng để tạo ra một hệ thống ảo hóa. Các phần mềm tiêu biểu: Virtualbox, VMware

- ### <a name="virtualbox"></a>***Virtualbox***
Virutalbox là phần mềm ảo hóa Open-source dành cho kiến trúc x86 và AMD64/Intel64. Virtualbox chạy được trên các nền tảng Windows, Linux, MacOS (tại thời điểm viết bài này, Virtualbox chưa hỗ trợ trên các thiết bị sử dụng Chip M1) 26 thg 8, 2023.

- ### <a name="vmware_workstation"></a>***VMware Workstation***
VMware workstation là trình ảo hóa Type 2, tương tự như Virtualbox nhưng không Open-source.
- ### <a name="hyper_v"></a>***HyperV***
- ### <a name="vagrant"></a>***Vagrant***
#### <a name="vagrant_overview"></a> <u>Vagrant là gì?</u>
Vagrant là một tiện ích CLI Open-source của HashiCorp để quản lý lifecycle của các máy ảo. Nó là công cụ để xây dựng môi trường development hiệu quả. Với quy trình làm việc dễ sử dụng và tập trung vào tự động hóa, Vagrant giảm thời gian thiết lập môi trường development , tăng tính tương đồng giữa môi trường development/production và để loại bỏ lý do “Cái này trên máy tôi chạy bình thường mà”.

Vagrant phát triển dựa trên nguyên tắc “đứng trên vai những người khổng lồ”. Các máy ảo được cung cấp trên các trình ảo hóa quen thuộc như: Virtualbox, VMware, HyperV, AWS hoặc bất kỳ nhà cung cấp nào khác. Sau đó, có thể sử dụng các bộ công cụ tự động hóa, quản lý cấu hình như shell script, Chef, Puppet hoặc Ansible dể tự động cài đặt và cấu hình phần mềm trên máy ảo.

**Vagrant được thiết kế cho mọi người như một cách dễ dàng và nhanh nhất để tạo môi trường ảo hóa!**
   
#### <a name="vagrant_vs_docker"></a> <u>Vagrant vs. Docker</u>
Vagrant là một công cụ tập trung vào việc cung cấp quy trình làm việc môi trường phát triển nhất quán trên nhiều hệ điều hành. Docker là một công cụ quản lý vùng chứa có thể chạy phần mềm một cách nhất quán miễn là có hệ thống chứa. 

Các container thường nhẹ hơn máy ảo nên việc khởi động và dừng các container diễn ra cực kỳ nhanh chóng. Docker sử dụng chức năng chứa gốc trên macOS, Linux và Windows. 

Hiện tại, Docker thiếu hỗ trợ cho một số hệ điều hành nhất định (chẳng hạn như BSD). Nếu mục tiêu triển khai của bạn là một trong những hệ điều hành này, Docker sẽ không cung cấp mức sản xuất tương đương như một công cụ như Vagrant. Vagrant cũng sẽ cho phép bạn chạy môi trường phát triển Windows trên Mac hoặc Linux. 

Đối với các môi trường nặng về microservice, Docker có thể hấp dẫn vì bạn có thể dễ dàng khởi động một máy ảo Docker duy nhất và khởi động nhiều vùng chứa ở trên rất nhanh chóng. Đây là trường hợp sử dụng tốt cho Docker. Vagrant cũng có thể làm điều này với nhà cung cấp Docker. Lợi ích chính của Vagrant là quy trình làm việc nhất quán nhưng có nhiều trường hợp quy trình làm việc thuần Docker có ý nghĩa. 

Cả Vagrant và Docker đều có một thư viện khổng lồ gồm các "images" hoặc “boxes" do cộng đồng đóng góp để bạn lựa chọn.
#### <a name="vagrant_architecture"></a> <u>Kiến trúc Vagrant</u>

#### <a name="cli"></a> <u>Vagrant Commands (CLI)</u>
Hầu như mọi tương tác với Vagrant đều được thực hiện thông qua giao diện dòng lệnh. Gõ lệnh *vagrant* từ Commandline sẽ liệt kê tất cả lệnh được dùng. Hãy chắc chắn rằng khi thực hiện lệnh phải ở cùng thư mục với Vagrantfile.
#### <a name="vagrantfile"></a> <u>Vagrantfile</u>
Vagrant sử dụng file cấu hình có cú pháp là ngôn ngữ Ruby cơ bản để mô tả các môi trường được gọi là Vagrantfile. Tên của file cấu hình này phải đặt là Vagrantfile.

Mỗi project, sử dụng 1 Vagrantfile để quản lý version hiệu quả, Vagrantfile hoàn toàn Flexible trên các nền tảng mà Vagrant hỗ trợ.

Cơ chế quan trọng của Vagrant là **Load order và Merging,** khi chúng ta sử dụng các lệnh Vagrant, nó sẽ tìm các Vagrantfiles khác trên hệ thống và hợp nhất các file cài đặt có liên quan để xây dựng cấu hình cuối cùng. Ví dụ: Chúng ta có Vagrantfile trong thư mục chính tên Vagrant với một số cấu hình mặc định và ghi đè các giá trị dành riêng cho dự án trong mỗi thư mục dự án. *(Đoạn này tôi ít sử dụng, do các project đa phần đều làm cá nhân).* Lưu ý rằng nếu không tìm thấy Vagrantfile ở bất kỳ bước nào, Vagrant sẽ tiếp tục với bước tiếp theo.

Vagrant có cơ chế Lookup Path, Vagrant sẽ duyệt cây thư mục để tìm Vagrantfile đầu tiên được tìm thấy, bắt đầu từ thư mục hiện tại khi thực hiện lệnh Vagrant bất kỳ.
#### <a name="boxes"></a> <u>Boxes</u>
Image của Vagrant được gọi là Vagrant box. Các box này đã được đánh phiên bản để có thể nhanh chóng clone một máy ảo. Có nhiều box được public trên [Vagrant Cloud](https://app.vagrantup.com/boxes/search). Tuy nhiên nên cẩn thận trong việc lựa chọn box, vì chỉ có 2 loại box được chính thức là [HashiCorp](https://app.vagrantup.com/hashicorp) và [Bento](https://app.vagrantup.com/bento) boxes.
#### <a name="providers"></a> <u>Providers</u>
Vagrant hỗ trợ nhiều nhà cung cấp máy ảo khác nhau, nhưng các nhà cung cấp này không được cài đặt sẵn. Các nhà cung cấp này có thể được cài đặt thông qua plugin. Các nhà cung cấp được hỗ trợ bởi Vagrant bao gồm: VirtualBox, VMware, Hyper-V, Docker, AWS, Azure, Google Cloud Platform, DigitalOcean, Linode, và nhiều hơn nữa. Nhà cung cấp mặc định là Virtualbox.
Các mức độ ưu tiên lựa chọn nhà cung cấp:
1. Option --provider trong lệnh vagrant up.
Ex: `vagrant up --provider=vmware_fusion`
2. Biến môi trường `VAGRANT_DEFAULT_PROVIDER`
3. Cấu hình trong Vagrantfile
```ruby
Vagrant.configure("2") do |config|
  # ... other config up here

  # Prefer VMware Fusion before VirtualBox
  config.vm.provider "vmware_fusion"
  config.vm.provider "virtualbox"
end
```
4. Vagrant sẽ tự động chọn nhà cung cấp đầu tiên được cài đặt. Nếu không có nhà cung cấp nào được cài đặt, Vagrant sẽ báo lỗi.
#### <a name="provisioning"></a> <u>Provisioning</u>
Provisioners trong Vagrant cho phép người dùng cài đặt các phần mềm trên máy ảo và thực hiện các tác vụ cấu hình. Vagrant hỗ trợ nhiều loại provisioners khác nhau, bao gồm: shell, Chef, Puppet, Ansible, Salt, Docker, File, và một số loại provisioners khác. Provisioners có thể được cấu hình trong Vagrantfile.
Provisioning có thể được chạy trong các trường hợp:
- Trong quá trình khởi tạo máy ảo. Trong lần `vagrant up` đầu tiên, Vagrant sẽ chạy tất cả các provisioners được cấu hình. Nếu máy ảo đã được tạo trước đó, Vagrant sẽ bỏ qua các provisioners trừ khi được chỉ định option `--provision`. Ex: `vagrant up --provision`
- Trong quá trình khởi động lại máy ảo. Provisioning sẽ được chạy khi chúng ta sử dụng lệnh `vagrant reload --provision`
- Trong trường hợp được cấu hình trong Vagrantfile. Ex:
```ruby
Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "echo hello",
    run: "always"
end
```

Có thể cấu hình provisioners trong Vagrantfile:
```ruby
Vagrant.configure("2") do |config|
  # ... other configuration

  config.vm.provision "shell", inline: "echo hello"
end
```
hoặc có thể sử dụng biến để lưu trữ các script theo syntax của ngôn ngữ Ruby:
```ruby
Vagrant.configure("2") do |config|
  # ... other configuration

  config.vm.provision "shell" do |s|
    s.inline = "echo hello"
  end
end
```
### <a name="vagrant_cheat_sheet"></a> <u>Vagrant Cheat Sheet</u>
##### <a name="cheat_sheet_cli"></a>*Vagrant CLI Cheat Sheet*
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
##### <a name="cheat_sheet_file"></a>*Vagrantfile Cheat Sheet*
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
## *&rarr;* Để có thể sử dụng Vagrant một cách cơ bản nhất, chúng ta chỉ cần tập trung vào các lệnh cơ bản sau:
```shell
vagrant init
vagrant up
vagrant ssh
vagrant resume
vagrant halt
vagrant destroy
```  
- ### <a name="vmware-vsphere"></a>***(Advanced) VMware vSphere***



## <a name="containerization"></a>**3.CONTAINERIZATION**
- ### <a name="docker"></a>***Docker***
- ### <a name="docker_swarm"></a>***Docker Swarm***
- ### <a name="kubernetes"></a>***Kubernetes***

## <a name="ci/cd"></a>**4.ONTINUOUS INTERGRATION CONTINUOUS DELIVERY/DEPLOYMENT**
- ### <a name="gitlab_ci/cd"></a>***Gitlab CI/CD***
- ### <a name="jenkins"></a>***Jenkins***
- ### <a name="argo_cd"></a>***Argo CD***

## <a name="cm"></a>**5.CONFIGURATION MANAGEMENT (CM)**
- ### <a name="ansible"></a>***Ansible***
- ### <a name="chef"></a>***Progress Chef***
- ### <a name="puppet"></a>***Puppet***
- ### <a name="terraform"></a>***Terraform***

## <a name="cloud"></a>**6.CLOUD COMPUTING AND STORAGE**
- ### <a name="aws"></a>***AWS***
- ### <a name="azure"></a>***Azure***

## <a name="log"></a>**7.LOG SOLUTION (EFK)**
- ### <a name="es"></a>***Elasticsearch***
- ### <a name="fluentd"></a>***Fluentd/Fluentbit***
- ### <a name="kibana"></a>***Kibana***

## <a name="db"></a>**8.DATABASE**
- ### <a name="sql"></a>***SQL***
- ### <a name="mongodb"></a>***MongoDB***
- ### <a name="redis"></a>***Redis***

## <a name="test_tool"></a>**9.TESTING TOOL**
- ### <a name="selenium"></a>***Selenium***
- ### <a name="jenkins_test_tool"></a>***Jenkins***

## <a name="monitor"></a>**10.MONITORING**
- ### <a name="prometheus/grafana"></a>***Prometheus/Grafana***
- ### <a name="raygun"></a>***Raygun***