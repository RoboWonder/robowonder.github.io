---
image: https://4.bp.blogspot.com/-zRXAUpuJt78/WD6-e4drdYI/AAAAAAAABgY/BSGV_4U1VJgdLGqyik-ORAlBaE9DS3p1wCLcB/s320/angular2%2Bva%2Bes6.png
instantfeedback: true
description: khi bắt đầu với Angular2 bạn không biết bắt đầu từ đâu, các thư viện liên quan để chạy Angular...Bài viết này sẽ hướng dẫn từ đầu cho các bạn.
title: Angular và ES6 - Tạo bộ khung ứng dụng
category: Lập trình
tags: Angular, Angular2, 2016
keywords: Angular, Angular2, ES6, Setup, 2016
---

<figure><img src="https://4.bp.blogspot.com/-zRXAUpuJt78/WD6-e4drdYI/AAAAAAAABgY/BSGV_4U1VJgdLGqyik-ORAlBaE9DS3p1wCLcB/s320/angular2%2Bva%2Bes6.png" alt="Angular và ES6: Tạo bộ khung ứng dụng" title="Angular và ES6: Tạo bộ khung ứng dụng"></figure>


Nếu bạn cũng như tôi, đã từng biết đến Angular1. Và khi bắt đầu với Angular2 bạn không biết bắt đầu từ đâu, các thư viện liên quan để chạy Angular...

Bài viết này sẽ hướng dẫn từ đầu cho các bạn. Quá trình này chỉ mất vài phút để cài đặt.

## Cài đặt Yeoman và Generator

Tất cả mọi cài đặt đều thông qua npm nhé. Mở Terminal hoặc Cmd nếu bạn dùng Windows và gõ đoạn lệnh sau:

```
$ npm install -g yo
$ npm install generator-angular2
```

## Tạo ứng dụng Hello Word

Tạo thư mục hello và vào đó chạy  yo  để tạo ra bộ khung cho ứng dụng của bạn. 

```
$ mkdir hello
$ cd hello
$ yo angular2
```

Yo sẽ tự động chạy npm install cho bạn chứ bạn không cần chạy như trên hướng dẫn của angular.io nữa.

<figure><img src="https://2.bp.blogspot.com/--viIQm8iuao/WD7hvSr_ZdI/AAAAAAAABgw/PM37AfROhI4pECTWqwFwhxJ7zG_3c4fsACLcB/s640/yo%2Bgenerator%2Bangular%2B2.jpg" alt="Sau khi chạy Yo" title="Sau khi chạy Yo"></figure>


## Chạy thử

Gõ lệnh sau rồi vào trình duyệt truy cập http://localhost:8000.

```
$ npm start
```

Trang web của bạn hiện ra đơn giản chỉ là chữ hello. Bởi vì chúng ta chưa xây dựng nội dung cho nó.

