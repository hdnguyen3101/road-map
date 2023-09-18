### <a name="provisioning"></a> <u>Provisioning</u>
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