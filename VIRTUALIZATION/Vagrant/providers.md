## <a name="providers"></a> <u>Providers</u>
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