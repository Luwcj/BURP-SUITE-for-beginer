# BURP-SUITE-for-beginer
- Khi mới mở lên, giao diện ban đầu sẽ như hình dưới đây:
![](https://whitehat.vn/attachments/upload_2021-5-6_12-48-10-png.8652/)

- Ở giao diện Dashboard, sẽ có các thông tin về các Task đang được chạy, Event log, phía bên phải là các lỗ hổng đã tìm thấy (chỉ áp dụng cho bản Burp Suite Pro, bản Community chỉ show các demo mà thôi). Lưu ý là các thông tin ở Event Log khá quan trọng, một số trường hợp gặp lỗi, liên quan đến certificate, lỗi kết nối sẽ được hiển thị ở đây, giúp bạn nhanh chóng troubleshoot hơn.
- Tiếp đến là giao diện tab Target
![](https://whitehat.vn/attachments/screen_shot_2021-05-06_at_11-47-11-png.8653/)

Ở Target, sẽ có thông tin về các sites được truy cập, các request được thực hiện trên các site này, bạn có thể nhấn nút > ở trong mỗi site, để xem dưới dạng cây, sẽ có cái nhìn trực quan hơn về target. Cũng ở trong Target, có subtab Scope, dùng để chỉ định những Site nào thuộc scope, phục vụ việc filter các request nhanh chóng hơn.
- Tiếp đến là giao diện tab Proxy, phần quan trọng nhất của Burp Suite. Tab HTTP history sẽ lưu lịch sử các request được thực hiện trong quá trình tương tác với ứng dụng. Bạn sẽ sử dụng các thông tin này để xem chi tiết request, response của ứng dụng.

Từ tab Proxy, bạn có thể chọn một request và gửi request này đến các tool khác trong Burp, như Repeater, Intruder, Comparer, ...

Ở bản mới này, Burp Suite có embed Chromium vào bên trong, cho phép bạn không cần phải tự cấu hình một trình duyệt mới để đẩy request sang Burp nữa, rất tiện lợi.

Cách mở: Ở dưới tab Proxy, bạn chọn subtab Intercept, nhấn Open Browser
![](https://whitehat.vn/attachments/upload_2021-5-6_14-13-54-png.8665/)

Bạn nhớ chọn Intercept is off, để ứng dụng chưa Intercept request của bạn (phần này sẽ được đề cập ở một bài sau, sẽ có lúc chúng ta dùng tới tính năng này).

Khi trình duyệt Chromium được khởi chạy, bạn vào một trang web bất kì, whitehat.vn chẳng hạn, và xem các request được ghi nhận ở trong tab HTTP Proxy.

Tab tiếp theo là Intruder, được sử dụng để brute force username/password, directory, hoặc dùng để test IDOR,..., phần này rất quan trọng, và khá dài, do đó mình sẽ mô tả ở một bài viết khác.
![](https://whitehat.vn/attachments/upload_2021-5-6_14-17-3-png.8668/)

- Kế bên tab Intruder, là Repeater, thành phần không thể thiếu trong mỗi lần pentest của chúng ta. Các request ở trong tab Target, Proxy khi chọn "Sent request to Repeater" sẽ được hiển thị ở đây. Tại giao diện này, cho phép chúng ta có thể chỉnh sửa bất kì thành phần nào của request, từ method, headers, parameters,... Sau khi chỉnh sửa request xong, bạn nhấn Send để gửi request đến server.
![](https://whitehat.vn/attachments/upload_2021-5-6_13-13-32-png.8656/)

Vì sao mình gọi đây là thành phần không thể thiếu trong mỗi lần pentest, là bởi vì việc tấn công một target, đòi hỏi chúng ta phải gửi những payload khác nhau, ở những vị trí khác nhau của ứng dụng. Bản chất của những công cụ tự động cũng tương tự.

Việc tự thay đổi request như thế này, cho phép chúng ta thử toàn bộ các payload mà chúng ta có, hoặc gửi payload để tìm thêm thông tin về ứng dụng, tìm các input được reflect trong response (khi tìm lỗ hổng XSS), hoặc xem kết quả trả về khi chúng ta nhập payload là SQL injection payload,..., và để làm những tác vụ đó, Repeater là giải pháp tốt nhất để thực hiện.

Khi đi vào các ví dụ cụ thể, các bạn sẽ thấy, chúng ta sử dụng nó rất nhiều.
- Tiếp đến là tab Sequencer, được dùng để phân tích các token trong ứng dụng, được sử dụng nhiều để xem mức độ phức tạp của thuật toán tạo token, xem có dễ bị dò đoán hay không.
![](https://whitehat.vn/attachments/upload_2021-5-6_13-13-51-png.8657/)

- Tiếp đến là tab Decoder, dùng để encode, decode những thông tin mà người dùng nhập vào, ví dụ decode Base64, encode MD5, ..., cũng được sử dụng rất nhiều.
![](https://whitehat.vn/attachments/upload_2021-5-6_13-14-15-png.8658/)

- Tab Comparer, dùng để so sánh các request, response khác nhau, do bạn gửi vào (thông qua Proxy tab hoặc Target tab, bằng việc nhấn chuột phải vào request, và chọn "Sent to Comparer"). Chức năng này rất hữu dụng trong việc tìm điểm khác nhau giữa 2 request, trong trường hợp request quá lớn để xem bằng mắt thường.
- ![](https://whitehat.vn/attachments/upload_2021-5-6_13-13-9-png.8655/)

- Tab Logger được dùng để log lại tất cả các request được thực hiện trên Burp, các bạn sẽ thắc mắc là vì sao đã có Proxy History rồi, lại cần có Logger? Vì một số extension, scanner (bản Pro) sẽ gửi các request mà không được lưu lại ở trên Proxy History, nên cần có một nơi để log lại, để bạn xem được toàn bộ request, trong trường hợp bạn muốn biết ứng dụng có đang chạy scan gì hay không.
![](https://whitehat.vn/attachments/upload_2021-5-6_13-15-56-png.8660/)

- Tab Extender: Ở tab này, cho phép bạn thêm mới các extension có sẵn của Burp, hoặc thêm những extension do chính bạn phát triển.
    - Các extensions này sẽ giúp chúng ta rất nhiều trong việc pentest, ví dụ: làm cho request trông gọn gàng hơn, tự động gửi những request tương tự, thay đổi một tham số nào đó,..
    ![](https://whitehat.vn/attachments/upload_2021-5-6_13-16-55-png.8662/)
    - Hai tab Project Options và User Options được dùng để cấu hình về xác thực (khi pentest các ứng dụng yêu cầu xác thực mới vào được), hoặc chỉnh Upstream proxy, để đẩy request từ Burp đến các proxy khác (dùng khi tương tác với nhiều thành viên khác nhau, để tập trung các request của nhiều tester về một nơi duy nhất, ..)
