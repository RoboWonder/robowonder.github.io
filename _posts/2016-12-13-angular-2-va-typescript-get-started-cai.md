---
image: https://2.bp.blogspot.com/-c4LnEr9Euok/WEWT6zBIBVI/AAAAAAAABiY/do5l9pATlbUxBzVU_q9IesrpNDRfODFogCLcB/s1600/angular.png
instantfeedback: true
layout: post
description: Để chạy được Angular 2 trước tiên cần phải có Nodejs, tại sao lại như vậy? Angular 2 dùng ngôn ngữ TypeScript nên cần có Nodejs để biên dịch và một số thư viện được Angular 2 mượn của Nodejs.
layout: post
title: Angular 2 và TypeScript - Get started - Cài đặt và chạy ứng dụng demo
category: Lập trình
tags: Angular, Angular2, 2016
keywords: Angular, Angular2, Get start, TypeScript , 2016
---

<figure><img src="https://4.bp.blogspot.com/-vpu83W2dQNM/WE2E7ZuwFQI/AAAAAAAABi8/qm-KFc3WmQYLNJh0FZBvVw2yjS-4WMkhgCLcB/s640/angular2typescript.jpg" alt="Cài đặt và chạy ứng dụng demo Angular 2" title="Cài đặt và chạy ứng dụng demo Angular 2"></figure>

Tôi đang bắt đầu một serial viết tutorial cho Angular 2 với TypeScript theo yêu cầu của đệ tử. Trước đây tôi chỉ có ý định viết về ES6 chứ không viết về TypeScript vì ngôn ngữ này đã có tài liệu rất rõ trên angular.io rồi.

## Cài đặt Nodejs

Để chạy được Angular 2 trước tiên cần phải có Nodejs, tại sao lại như vậy? Angular 2 dùng ngôn ngữ TypeScript nên cần có Nodejs để biên dịch và một số thư viện được Angular 2 mượn của Nodejs.

Để cài đặt các bạn vào nodejs.org tải phiên bản phù hợp với hệ điều hành của máy tính bạn rồi cài đặt theo hướng dẫn,

## Cài đặt NPM

Mở command line lên và gõ

```
npm install npm@latest -g
```

## Cài đặt Git

Vào https://git-scm.com/download để tải git theo hệ điều hành và cài đặt như hướng dẫn của nó.

## Tạo và chạy Angular demo

- Mở command line, di chuyển con trỏ làm việc vào trong thư mục nơi bạn muốn tạo ứng dụng helloworld vừa tạo bằng lệnh cd. Ví dụ:

```
cd E:/project/
```

- Tiếp theo chạy lần lượt từng lệnh sau, đợi lệnh này chạy xong thì chạy lệnh tiếp theo:

```
git clone https://github.com/angular/quickstart.git helloworld
cd helloworld
npm install
npm start
```

Sau khi chạy xong lệnh cuối cùng là *npm start*,  trình duyệt sẽ tự động mở lên và chạy web. Nếu trình duyệt không tự mở bạn có thể mở bằng tay và chạy địa chỉ http://localhost:3000/

Chừng nào muốn ngừng máy chủ Nodejs thì ấn Ctrl+C. 

## Tổng kết

Vậy là bạn đã có những thứ cần thiết để chạy ứng dụng Angular 2 và bộ khung của ứng dụng. Muốn làm ứng dụng khác to hơn thì chỉ cần code theo bộ khung này là được. Chúng ta sẽ đi sâu vào viết ứng dụng Angular 2 trong những bài tiếp theo. Cảm ơn các bạn đã đọc bài.