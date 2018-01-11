---
image: ""
instantfeedback: true
description: Bài này nói về các khái niệm cơ bản của Docker, những lưu ý và các câu lệnh quan trọng khi sử dụng Docker.
layout: post
title: Tóm lượt tất tần tật về Docker
category: Công nghệ
tags: Docker, tóm lượt, kiến thức cần nhớ
keywords: Docker, tóm lượt, kiến thức cần nhớ, centos, ubuntu
---

Bài này nói về các khái niệm cơ bản của Docker, những lưu ý và các câu lệnh quan trọng khi sử dụng Docker.

## Các khái niệm cơ bản

Docker có 3 khái niệm chính là Image, Container và Repository. Hiểu được 3 khái niệm này thì sẽ hiểu được toàn bộ vòng đời của Docker

#### Image

Tại sao lại gọi là Image (ảnh)? Tương tự như file Image của máy ảo, hay file .ghost của Windows cũng được gọi là Image, bởi vì nó được chụp lại từ một máy thực. Không thể chỉnh sửa hay cấu hình trực tiếp trên file đó, nên có độ tin cậy cao. Hay nói cách khác nó là bản sao của một ổ cứng và dữ liệu bên trong nó là dữ liệu của ổ cứng tại thời điểm nó được chụp.

Giống như việc thay đổi dữ liệu của một ổ cứng chỉ thực hiện được khi cắm vào trong một máy tính, thì dữ liệu bên trong Image cũng chỉ được thay đổi khi đã cắm vào máy ảo.

Trong Docker, cơ chế để tạo, cập nhật Image rất đơn giản. Đương nhiên bạn cũng có thể tải Image của người khác về xài cho lẹ.

#### Container

Hiểu nôm na thì Container như là một máy ảo Linux để chạy Image. Bao gồm quyền root, xử lý tiến trình, quản lý người dùng... Nên ứng dụng có thể chạy bên trong Container. 

Mỗi Container được cách ly hoàn toàn với nhau để đảm bảo sự an toàn.

**Quá trình khởi tạo Container:**
- Kiểm tra Image tại local, nếu không có thì tải Image về từ các Repository
- Tạo Container và khởi động với Image
- Tạo một cơ chế cho phép đọc - ghi bao quanh cơ chế chỉ đọc (readonly) của Image
- Khởi tạo giao diện ảo có thể điều khiển trực tiếp từ giao diện vật lý (hãy tưởng tượng như màn hình máy ảo hay Teamviewer vậy, nhưng không phải hoàn toàn vì đây là Linux :D)
- Cấu hình một địa chỉ IP cho Container.
- Thực thi ứng dụng được chỉ định bên trong Container
- Hủy Container - Kết thúc vòng đời.

#### Repository

Nơi lưu trữ Image. Nếu là Repository public thì ta có thể tải Image trong đó về xài. Hoặc có thể tạo Repository private trong mạng nội bộ để xài nếu thích. 

Sau khi tạo xong Image có thể push lên Repository để lần sau xài máy khác thì chỉ việc tải về xài.

Repository public lớn nhất là [Docker Hub](https://hub.docker.com/), chứa rất nhiều Image, nghe nói là hơn 100.000 lận.

## Cài đặt Docker

Docker hiện nay đã hỗ trợ rất nhiều nền tảng, nên muốn xem cách cài đặt với nền tảng của bạn đang xài thì lên trang chủ Docker tải về và làm theo hướng dẫn. Ở đây tôi chỉ hướng dẫn với hệ điều hành phổ biến cho máy chủ là Centos:

#### Centos 6

Chạy lần lượt các lệnh sau để tải Docker về và cài đặt:

```
$ sudo yum install http://mirrors.yun-idc.com/epel/6/i386/epel-release-6-8.noarch.rpm
$ sudo yum install docker-io
```

Sau khi cài đặt xong, chạy lệnh sau để khởi động Docker và cấu hình tự động chạy cùng hệ điều hành:

```
$ sudo service docker start
$ sudo chkconfig docker on
```

#### Centos 7

Chạy lệnh sau:

```
$ sudo yum install docker
```

Vậy là xong rồi đó =))

## Cách câu lệnh cơ bản khi sử dụng Docker

**Tải về một Image**
```
$ docker pull ten_image
```

Ví dụ: ```docker pull ubuntu: 16.04```

**Hiện tất cả Image có trong máy**
```
$ docker images
```

**Tìm Image**
```
$ docker search ten_image
```

**Xóa Image**
```
$ docker rmi ten_image
```

**Tạo Image**
```
$ docker build -t ten_image duong_dan_file
```

**Nén Image**
```
$ docker save ten_image -o file.tar
```

**Giải nén Image**
```
$ docker load file.tar
```


Hôm nay tạm dừng ở đây đã. Ngày mai sẽ viết tiếp những câu lệnh liên quan đến Container và file.