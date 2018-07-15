---
image: https://2.bp.blogspot.com/-_D8g7B1iY_o/W0l2I9nepnI/AAAAAAAABtM/qTV5eVMqasgyvJlJ5eD8Zf-2o0_05dpSwCLcBGAs/s1600/apps.58737.13873416619328643.04a0851a-edb6-4d10-b0e0-3481ab1919c1.jpg
instantfeedback: true
description: So sánh Developer Tools của Microsoft Edge với Chrome và FireFox
layout: post
title: F12 Developer Tools Microsoft Edge vs Chrome và FireFox
category: Công nghệ
tags: DevTools, Microsoft Edge, Chrome, FireFox
keywords: F12 Developer Tools, Microsoft Edge, Chrome, FireFox
---

Microsoft Edge là trình duyệt mặc định mới của Windows 10 thay thế cho Internet Explorer từ năm 2015. Qua 3 năm phát triển, liệu Developer Tools của Microsoft Edge có sánh được với cách trình duyệt đã phổ biến hiện nay như Chrome hay FireFox?

Tôi đã sử dụng Microsoft Edge từ những ngày đầu khi còn chưa có tên chính thức, lúc đó nó vẫn mang tên mã của project là Spartan. Kể từ lúc đó đến nay thì DevTools của Microsoft Edge được cải tiến rất nhiều. Điển hình như có thể dock vào cùng tab của trang web hiện tại ở phía dưới hoặc bên phải như Chrome, hoặc tách ra thành cửa sổ riêng biệt. Ngày xưa thì chỉ có tách ra thành cửa sổ riêng biệt mà thôi.

## Kiểm tra DOM

Tab **DOM Explorer** (`Ctrl`+`1`) là tab đầu tiên của Microsoft Edge DevTools, cũng là tab mặc định khi mở ra như Chrome và FireFox. Về cách bố trí và cái nhìn tổng quan thì chẳng khác gì Chrom và Firefox.

Ở cả 3 trình duyệt đều có thể sửa trực tiếp mã HTML trong DevTools, cũng như thêm, sửa, xóa các thuộc tính CSS. Ở Edge có thêm cái hay khi bạn sửa mã code sẽ được log lại ở 1 tab con bên phải tên là "Changes", cái này cực kỳ hữu ích khi sửa nhiều element cùng lúc rồi xem lại ở tab con này để copy vào IDE mà không bị sót, đây là một điểm cộng của Edge Devtools so với Chrome và Firefox.

Ở Firefox thì lại có chức năng mà Chrome và Edge không có, đó là chức năng phân tích Fonts và Animation. Chức năng này cực kỳ hữu ích cho Designer.

Về màu sắc trong code (Colour Picker) của Edge thì rất rõ ràng, hơn hẵn Chrome và Firefox. Tuy nhiên vì dùng toàn màu đậm nên sẽ gây chói cho những bạn đã quen dùng Chrome, nhưng khi đã quen thì sẽ thích màu của Edge hơn hẳn.

<figure><img src="https://2.bp.blogspot.com/-_D8g7B1iY_o/W0l2I9nepnI/AAAAAAAABtM/qTV5eVMqasgyvJlJ5eD8Zf-2o0_05dpSwCLcBGAs/s1600/apps.58737.13873416619328643.04a0851a-edb6-4d10-b0e0-3481ab1919c1.jpg" alt="Developer Tools của Microsoft Edge" title="Developer Tools của Microsoft Edge"></figure>

## Tương tác với Javascript

Tab **Console** (`Ctrl`+`2`) cho phép tương tác với Javascript trong trang web giống như Chrome và Firefox, cả 3 trình duyệt đều cho phép theo dõi lỗi Javascript theo thời gian thực và nhập mã ở tab này.

Edge DevTools cũng có gợi ý khi viết code nhưng có vẻ ít lệnh hơn so với Chrome và Firefox.

Về mặt phân loại Errors, Warnings, Messages thì cả 3 trình duyệt đều như nhau, không có gì đáng nói. Tuy nhiên trình duyệt Firefox thì xịn hơn ở chỗ phân biệt được Errors do mạng, hay CSS và cả lỗi bảo mật chứ không chỉ lỗi Javascript.

## Debug code

Tab **Debug** (`Ctrl`+`3`) giúp theo dõi code Javascript chạy theo kiểu *step by step*, có thể theo dõi giá trị thay đổi của biến (Watches), đặt breakpoint, hay là xem call stack...

Giới thiệu sơ qua chức năng của tab này vậy thôi chứ không có gì so sánh giữa 3 trình duyệt với nhau. Ở cả 3 trình duyệt thì tab này mạnh ngang ngửa nhau thôi chứ không có gì đặt biệt.

## Theo dõi request với server

Tab **Network** (`Ctrl`+`4`) của Chrome cho cái nhìn ít trực quan hơn. Tab này của Edge và Firefox đều có giao diện người dùng thân thiện cho phép bạn xem tiêu đề HTTP, cơ chế HTTP, parameters, cookie và thời gian theo từng mục. Bên Chrome thì phải vào chi tiết từng request mới xem được.

## Phân tích tốc độ xử lý trang

Tab **Performance** (`Ctrl`+`5`) sẽ giúp bạn hiểu lý do vì sao một trang web xử lý chậm. Với công cụ Performance, Microsoft đã có cải tiến lớn bằng cách kết hợp các công cụ Responsive UI và Profiler trước đó để tạo ra một cái nhìn toàn diện về tất cả các mã code, và trực quan hóa hiệu suất.

Công cụ này cung cấp cho bạn các báo cáo về CPU đã được sử dụng cho các loại khác nhau như: loading, rendering, image decode... Rất chi tiết và tổng thể về trang web. Bạn cũng có thể phân loại các event bằng cách đặt label, ví dụ như xem animation, callback xử lý mất bao nhiêu thời gian... Nói chung giải thích bằng từ ngữ thì hơi khó vì có quá nhiều từ chuyên ngành không thể dịch. Nhưng xài rồi sẽ biết ngay.

Công cụ này của Edge hơn hẳn Chrome và Firefox về độ chi tiết, giao diện được thiết kế khá tốt giúp có nhiều cách nhìn tổng quan hơn và cũng dễ sử dụng, 

## Memory

Tab **Memory** (`Ctrl`+`6`) phân tích các thành phần "ăn RAM" có thể ảnh hưởng đến hiệu suất và sự ổn định của trang web. 

Với giao diện dạng biểu đồ như tab performance thì bạn có thể dễ dàng hiểu được việc "ăn RAM" ở giai đoạn nào và cũng có thể chụp ảnh trang web tại các thời điểm cụ thể giúp phân tích việc sử dụng bộ nhớ, cũng có thể so sánh hai ảnh chụp tại các thời điểm khác nhau của vòng đời trang web để so sánh mức độ "ăn RAM".

Tab này của Firefox là cùi bắp nhất, trong khi của Chrome thì nhiều tính năng nhất. Ví dụ như cho phép ghi lại phân bổ đối tượng JavaScript theo thời gian có thể giúp tìm ra các function "ăn RAM".

## Test Reponsive

Tab **Emulation** (`Ctrl`+`7`) thì không cần nói nhiều nữa, ai làm web front-end cũng biết. Về tab này thì Chrome lại thắng thế khi cung cấp chế độ adjust size khá thuận tiện, trong khi Edge thì cung cấp chế độ giả lập Bot, GPS. Ngoài ra Edge còn giả lập các trình duyệt khác như Chrome, Firefox, IE.

## Các tính năng mở rộng

DevTools của Microsoft Edge có thể debug remote trực tiếp với trình duyệt trên điện thoại di động thông qua cáp USB hoặc WiFi. Cũng như webview control trong ứng dụng viết bằng C-Sharp.

Nếu bạn viết app UWP bằng HTML hoặc PWAs cho windows thì cũng có thể dùng DevTools của Microsoft Edge để inspect.

## Chốt

Nhìn chung DevTools của Microsoft Edge có sự tiến bộ vượt bậc và đáng ngạc nhiên so với người tiền nhiệm. Các tính năng khá giống với các trình duyệt hiện đại khác, thậm chí có cái còn vượt trội hơn. Giao diện trực quan, thân thiện với người dùng, công cụ Performance cực mạnh.

Như vậy, bạn có thể cân nhắc việc chuyển sang hoặc sử dụng song song với DevTools của các trình duyệt khác. Hoặc ít nhất là xài thử nghiệm. Thank for read!