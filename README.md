# Speech-To-Text
Speech to text by Selenium 4.11.0 and ChromeDriver 121.0.6167.85 with Ttsfree.com 

Tiếng việt : 
- Tool phục vụ quá trình chuyển đổi văn bản thành giọng nói thông qua việc user gửi các tham số được lưu trữ trong API và gửi đi , trong đó API có 3 tham số :
  + tham số 1 : văn bản
  + tham số 2 : tên file lưu
  + tham số 3 : giọng nam hoặc nữ

- Trong đó văn bản sẽ được đoạn mã phân tích về độ dài
  + nếu độ dài <= 4000 kí tự , chương trình sẽ liệt vào hướng 1 ( chạy đa Driver Google ) 
  + nếu độ dài => 4001 kí tự , chương trình sẽ liệt vào hướng 2 ( chạy lần lượt Tab )
  -> phải chia hai hướng như này bởi vì website Ttsfree.com ô chứa text chỉ có tối đa 2000 kí tự , ở hướng 2 là đa driver google theo tính toán chỉ nên mở 2 driver google cùng một lúc , bởi lẽ nếu mở một lúc >= 3 googld driver sẽ xảy ra tình trạng giật , đơ ở một số thiết bị cấu hình yếu . Còn hướng 2 phải áp dụng cho những văn bản >= 4001 kí tự , nếu áp dụng cho trường hợp <= 4000 kí tự sẽ không tối ưu được tốc độ

- Phần tên file lưu chương trình sẽ đọc toàn bộ dữ liệu ở file download ổ C và scan có trùng tên file ở params trước khi tải hay không ? đồng thời check tên file lưu User gửi đi có kí tự đặc biệt không ? nếu không bị trùng tên file và tên file không có kí tự đặc biệt sẽ hợp lệ thì sau khi file được tải xuống ở file download ổ C sẽ đổi thành tên đã gửi đi ở params trong API

- Phần giọng nói , đoạn mã dựa vào đó để chọn Male / Female Voice trên website

- Phần xử lý captcha , chương trình sẽ cắt vùng ảnh đoạn mã captcha -> lưu về 1 file -> gửi về telegram user theo chatId telegram -> User có 1 khoảng thời gian nhất định để nhập cho tới khi đúng -> chương trình sẽ lấy đoạn tin nhắn user gửi lại và lắp lại vào phần điền captcha -> nếu khớp thì thao tác tiếp -> không khớp sẽ reload ảnh captcha mới và gửi lại về telegram tiếp 
