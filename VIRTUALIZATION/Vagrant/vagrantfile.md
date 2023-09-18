### <a name="vagrantfile"></a> <u>Vagrantfile</u>
Vagrant sử dụng file cấu hình có cú pháp là ngôn ngữ Ruby cơ bản để mô tả các môi trường được gọi là Vagrantfile. Tên của file cấu hình này phải đặt là Vagrantfile.

Mỗi project, sử dụng 1 Vagrantfile để quản lý version hiệu quả, Vagrantfile hoàn toàn Flexible trên các nền tảng mà Vagrant hỗ trợ.

Cơ chế quan trọng của Vagrant là **Load order và Merging,** khi chúng ta sử dụng các lệnh Vagrant, nó sẽ tìm các Vagrantfiles khác trên hệ thống và hợp nhất các file cài đặt có liên quan để xây dựng cấu hình cuối cùng. Ví dụ: Chúng ta có Vagrantfile trong thư mục chính tên Vagrant với một số cấu hình mặc định và ghi đè các giá trị dành riêng cho dự án trong mỗi thư mục dự án. *(Đoạn này tôi ít sử dụng, do các project đa phần đều làm cá nhân).* Lưu ý rằng nếu không tìm thấy Vagrantfile ở bất kỳ bước nào, Vagrant sẽ tiếp tục với bước tiếp theo.

Vagrant có cơ chế Lookup Path, Vagrant sẽ duyệt cây thư mục để tìm Vagrantfile đầu tiên được tìm thấy, bắt đầu từ thư mục hiện tại khi thực hiện lệnh Vagrant bất kỳ.