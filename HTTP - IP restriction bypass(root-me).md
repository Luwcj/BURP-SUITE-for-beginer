Ta có 2 gợi ý :
- We’re now managing connections to the intranet using private IP addresses, so it’s no longer necessary to login with a username / password when you are already connected to the internal company network.
- Your IP 2405:4802:913c:3810:1c16:1fb0:f141:903a do not belong to the LAN.

Để làm được bài này bạn cần hiểu mạng LAN là gì?
Mạng LAN (Local Area Network) là một mạng máy tính tạo thành bởi một số lượng nhỏ các thiết bị tính toán (như máy tính, máy chủ, máy in, điện thoại, máy điều khiển, v.v.) nằm trong phạm vi giới hạn của một khu vực nhỏ, chẳng hạn như một tòa nhà, một văn phòng hoặc một gia đình. Mục đích chính của mạng LAN là để chia sẻ tài nguyên và thông tin giữa các thiết bị trong mạng, giúp tăng tính linh hoạt và hiệu quả trong việc làm việc, truy cập dữ liệu và sử dụng các ứng dụng.

Mạng LAN được thiết kế để hoạt động trên một phạm vi giới hạn và thường sử dụng các công nghệ kết nối có dây hoặc không dây như Ethernet, Wi-Fi hoặc Bluetooth để kết nối các thiết bị trong mạng với nhau. Các mạng LAN có thể được cấu hình và quản lý bởi các quản trị viên mạng, và có thể kết nối với mạng WAN (Wide Area Network) lớn hơn để truy cập vào các tài nguyên và dịch vụ khác nhau trên Internet.

Các địa chỉ IP mạng LAN thông thường được sử dụng trên các mạng gia đình hoặc văn phòng nhỏ là:

192.168.0.1
192.168.1.1
192.168.0.100
192.168.1.100
192.168.0.10
192.168.1.10

Trong giao thức HTTP, Header IP (hay còn gọi là X-Forwarded-For header) là một trường dữ liệu được sử dụng để xác định địa chỉ IP của người dùng cuối cùng trong trường hợp máy chủ proxy hoặc Load Balancer đứng trước máy chủ web.

Ta thêm Header  X-Forwarded-For và lấy 1 địa chỉ IP mạng LAN phổ biến ở trên để gán vào, sau đó xem Respond để tìm flag
![](https://media.discordapp.net/attachments/1098605833371267172/1099270004215656448/image.png?width=506&height=427)