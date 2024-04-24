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
  -> phải chia hai hướng như này bởi vì website Ttsfree.com ô chứa text chỉ có tối đa 2000 kí tự , ở hướng 1 là đa driver google theo tính toán chỉ nên mở 2 driver google cùng một lúc , bởi lẽ nếu mở một lúc >= 3 google driver sẽ xảy ra tình trạng giật , đơ ở một số thiết bị cấu hình yếu . Còn hướng 2 phải áp dụng cho những văn bản >= 4001 kí tự , nếu áp dụng cho trường hợp <= 4000 kí tự sẽ không tối ưu được tốc độ

- Phần tên file lưu chương trình sẽ đọc toàn bộ dữ liệu ở file download ổ C và scan có trùng tên file ở params trước khi tải hay không ? đồng thời check tên file lưu User gửi đi có kí tự đặc biệt không ? nếu không bị trùng tên file và tên file không có kí tự đặc biệt sẽ hợp lệ thì sau khi file được tải xuống ở file download ổ C sẽ đổi thành tên đã gửi đi ở params trong API
- Vì website chỉ có thể chứa 2000 kí tự nên những trường hợp >= 2001 kí tự sẽ có >= 2 file được tải về , sau khi hoàn tất quá trình , các fileName sẽ được đánh dấu từ 1 .... n và gộp thành một file name duy nhất là tên file user đã đặt ở params khi gửi API đi

- Phần giọng nói , đoạn mã dựa vào đó để chọn Male / Female Voice trên website

- Phần xử lý captcha , chương trình sẽ cắt vùng ảnh đoạn mã captcha -> lưu về 1 file -> gửi về telegram user theo chatId telegram -> User có 1 khoảng thời gian nhất định để nhập cho tới khi đúng -> chương trình sẽ lấy đoạn tin nhắn user gửi lại và lắp lại vào phần điền captcha -> nếu khớp thì thao tác tiếp -> không khớp sẽ reload ảnh captcha mới và gửi lại về telegram tiếp

--------------------------------------------------------------------------------

English : 
- The tool serves the process of converting text to speech through the user sending parameters stored in the API and sending, in which the API has 3 parameters:
  + parameter 1 : text
  + parameter 2: save file name
  + parameter 3: male or female voice
 
- In which the text will be analyzed by the code for length
  + If length <= 4000 characters, the program will be listed in direction 1 (running multiple Google Drivers)
  + if length => 4001 characters, the program will be listed in direction 2 (run Tab sequentially)
  -> must be divided into two directions like this because the Ttsfree.com website box containing text only has a maximum of 2000 characters. In direction 1, there are multiple google drivers. According to calculations, you should only open 2 google drivers at the same time, because if you open one When >= 3 google driver will cause lag and freeze on some weakly configured devices. Direction 2 must be applied to documents >= 4001 characters. If applied to <= 4000 characters, speed will not be optimized

- In the saved file name part, the program will read all the data in the downloaded file on drive C and scan to see if it matches the file name in the params before downloading? At the same time, check if the file name sent by the User has special characters? If there is no duplicate file name and the file name does not have special characters, it will be valid, then after the file is downloaded in the C drive download file, it will be changed to the name sent in the params in the API.
- Because the website can only contain 2000 characters, in cases where >= 2001 characters will have >= 2 files downloaded, after completing the process, the fileName will be marked from 1 .... n and combined into a single file name is the file name the user placed in the params when sending the API

- Voice part, code based on which to select Male / Female Voice on the website
- In the captcha processing part, the program will cut the image area of ​​the captcha code -> save it to a file -> send it to the user's telegram according to the telegram chatId -> The user has a certain amount of time to enter until it is correct -> the program will Take the message sent by the user and re-insert it into the captcha field -> if it matches, proceed next -> if it doesn't match, the new captcha image will be reloaded and sent back to telegram



