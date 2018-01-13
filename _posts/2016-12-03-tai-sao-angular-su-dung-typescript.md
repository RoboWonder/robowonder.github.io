---
image: https://1.bp.blogspot.com/-R9CjK-QcVYQ/WEG3XQ00-2I/AAAAAAAABiA/j2ux7ozqw0Aj7eHERa_8V8CxWczhKjqXQCLcB/s320/tai%2Bsao%2Bangular%2Bchon%2Btypescript.png
instantfeedback: true
description: Giới thiệu về Angular 2 và các thư viện liên quan
layout: post
title: Tại sao Angular sử dụng TypeScript
category: Lập trình
tags: Angular, Angular2, 2016
keywords: Angular, Angular2, TypeScript, 2016
---

<figure><img src="https://1.bp.blogspot.com/-R9CjK-QcVYQ/WEG3XQ00-2I/AAAAAAAABiA/j2ux7ozqw0Aj7eHERa_8V8CxWczhKjqXQCLcB/s320/tai%2Bsao%2Bangular%2Bchon%2Btypescript.png" alt="Tại sao Angular sử dụng TypeScript" title="Tại sao Angular sử dụng TypeScript"></figure>

Như đã biết Angular1 và hầu hết các framework JavaScript đều được viết bằng JavaScript, điều này là đương nhiên rồi. Vậy tại sao Angular2 lại phải viết bằng TypeScript? Thật là rắc rối khi học Angular lại phải học thêm một ngôn ngữ lập trình mới toanh. Cứ như là bạn đang code bằng CodeIgniter lại chuyển qua Diango trong khi chưa biết gì tới Python vậy.

## Có thể viết Angular2 mà không phải viết bằng TypeScript?

Chắc chắn là được. Bạn có thể viết bằng Dart, ES5, ES6. Như tôi đã có bài hướng dẫn tạo bộ khung ứng dụng Angular trên ES6. Tuy nhiên rất không đơn giản vì tài liệu chính thống của Angular trên angular.io đều hướng dẫn trên TypeScript.

Giờ đi tìm hiểu nguyên nhân Angular2 viết trên TypeScript mà tại sao lại không phải là Dart. Trong khi Dart do chính Google phát triển còn TypeScript lại là của đối thủ Microsoft.

## TypeScript có các công cụ tuyệt vời

Vấn đề quan trọng khi quyết định chọn một ngôn ngữ cho dự án của mình. Người ta thường phải tính đến các công cụ hỗ trợ. Nếu một ngôn ngữ không có công cụ hỗ trợ tốt, sau khi quy mô của dự án lớn lên sẽ rất tốn kém để phát triển tiếp cũng như đập bỏ dự án để thay đổi ngôn ngữ.

TypeScript có các công cụ tuyệt vời với các tính năng như gợi ý code, tự động điền, refactor... Đơn giản như việc đổi tên một biến trong dự án lớn. Bình thường bạn sẽ mất cả ngày, thậm chí vài ngày để tìm tất tần tật trong mới code hỗn độn thì với IntelliSense. Biến của bạn được đổi tên trong vòng một giây,

Dart và một số ngôn ngữ khác cũng như TypeScript, sau khi biên dịch kết quả cũng là JavaScript. Nhưng nó không có các công cụ tốt như TypeScript mà đơn thuần chỉ là trình biên dịch.

## TypeScript là Siêu JavaScript

Có thể nói TypeScript là Siêu JavaScript, là phiên bản tối thượng của JavaScript. TypeScript làm cho việc lập trình JavaScript đơn giản hơn rất nhiều, theo cấu trúc OOP, kiểu biến của hàm...

Nếu bạn chưa từng học JavaScript thì có thể bỏ qua và học luôn TypeScript. Nếu bạn đã có dự án viết bằng JavaScript và muốn chuyển qua TypeScript nhưng sợ không đủ thời gian thì bạn cứ yên tâm. Việc cần làm chỉ là đổi đuôi .js sang .ts và chuyển code dần dần. Trong một file code vừa viết bằng TypeScript vừa viết bằng JavaScript cũng chạy ok.

## TypeScript có khái niệm trừu tượng

Bạn đã bao giờ gặp các từ như interface, abstract, implement, extens... Nếu gặp thì bạn đã biết nó là gì rồi đúng không. Vậy làm sao để sử dụng nó trong JavaScript?. Chịu, có lẽ là không làm được.

TypeScript sẽ giải quyết vấn đề đó cho bạn. TypeScript cho phép định nghĩa các abstraction, protocol, hay role.

## TypeScript dễ đọc và dễ hiểu code cũ hơn

Một trong những cơn ác mộng của JavaScript là đọc lại code cũ do thằng khác viết. Khi viết một hàm trong JavaScript, giá trị trả về, các đối số truyền vào đều không ràng buộc rõ ràng về kiểu và số lượng. Vì vậy người đọc không thể nhớ hết được.

TypeScript thì không như vậy, có thể ràng buộc kiểu dữ liệu trả về, kiểu dữ liệu và số lượng các đối số. Nhìn vào đoạn code dưới đây bạn sẽ thấy rõ điều đó

```javascript
ajax(url: string, settings?: JQueryAjaxSettings): JQueryXHR; 

interface JQueryAjaxSettings { 
  async?: boolean; 
  cache?: boolean; 
  contentType?: any; 
  headers?: { [key: string]: any; }; 
  //... 
} 

interface JQueryXHR { 
  responseJSON?: any; //... 
}
```

Như trên:

- Đối số đầu tiên là kiểu String
- Đối số thứ hai là giá trị trả về của một hàm tự định nghĩa
- Kết quả trả về cũng là một hàm tự định nghĩa
- Như vậy chúng ta có thể thấy sức mạnh của TypeScript đến cỡ nào. Điều quan trọng nữa là TypeScript không bắt buộc chúng ta phải làm như vậy, nhưng chúng ta nên làm để code rõ ràng hơn.

## Tổng kết
Qua bài này bạn đã hiểu được vì sao Angular lại chọn TypeScript trong khi có nhiều ngôn ngữ khác như: ES5, ES6, Dart, PureScript, Elm, vv .. 

Mỗi tùy chọn này có ưu và khuyết điểm, nhưng tôi nghĩ TypeScript là một sự lựa chọn tuyệt vời cho hầu hết các dự án. TypeScript có đến 95% các điểm mà một ngôn ngữ bậc cao có. Và mang lại cảm giác như đang viết ES6. Dùng chung các thư viện chuẩn, các định nghĩa, các thư viện của bên thứ ba, các phần mềm phát triển (Như Chrome dev tools)... 