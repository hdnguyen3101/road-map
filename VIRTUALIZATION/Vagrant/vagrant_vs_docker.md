## <a name="vagrant_vs_docker"></a> <u>Vagrant vs. Docker</u>
Vagrant là một công cụ tập trung vào việc cung cấp quy trình làm việc môi trường phát triển nhất quán trên nhiều hệ điều hành. Docker là một công cụ quản lý vùng chứa có thể chạy phần mềm một cách nhất quán miễn là có hệ thống chứa. 

Các container thường nhẹ hơn máy ảo nên việc khởi động và dừng các container diễn ra cực kỳ nhanh chóng. Docker sử dụng chức năng chứa gốc trên macOS, Linux và Windows. 

Hiện tại, Docker thiếu hỗ trợ cho một số hệ điều hành nhất định (chẳng hạn như BSD). Nếu mục tiêu triển khai của bạn là một trong những hệ điều hành này, Docker sẽ không cung cấp mức sản xuất tương đương như một công cụ như Vagrant. Vagrant cũng sẽ cho phép bạn chạy môi trường phát triển Windows trên Mac hoặc Linux. 

Đối với các môi trường nặng về microservice, Docker có thể hấp dẫn vì bạn có thể dễ dàng khởi động một máy ảo Docker duy nhất và khởi động nhiều vùng chứa ở trên rất nhanh chóng. Đây là trường hợp sử dụng tốt cho Docker. Vagrant cũng có thể làm điều này với nhà cung cấp Docker. Lợi ích chính của Vagrant là quy trình làm việc nhất quán nhưng có nhiều trường hợp quy trình làm việc thuần Docker có ý nghĩa. 

Cả Vagrant và Docker đều có một thư viện khổng lồ gồm các "images" hoặc “boxes" do cộng đồng đóng góp để bạn lựa chọn.