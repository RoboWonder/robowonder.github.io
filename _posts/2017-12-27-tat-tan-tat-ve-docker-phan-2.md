---
image: https://msdnshared.blob.core.windows.net/media/2017/10/docker.png
instantfeedback: true
description: Bài này nói về các khái niệm cơ bản của Docker, những lưu ý và các câu lệnh quan trọng khi sử dụng Docker.
layout: post
title: Tóm lượt tất tần tật về Docker (Phần 2)
category: Công nghệ
tags: Docker, tóm lượt, kiến thức cần nhớ
keywords: Docker, tóm lượt, kiến thức cần nhớ, centos, ubuntu
---

Bài này tiếp tục nói về các câu lệnh quan trọng khi sử dụng Docker. Nếu bạn chưa đọc bài trước thì xem lại [tại đây](http://robowonder.com/2017/12/tat-tan-tat-ve-docker.html), bài trước nói về các khái niệm cơ bản và các lệnh liên quan đến Image.

<figure><img src="https://msdnshared.blob.core.windows.net/media/2017/10/docker.png" alt="Các khái niệm cơ bản Docker" title="Các khái niệm cơ bản Docker"></figure>

# Các câu lệnh cơ bản khi sử dụng Docker (Tiếp theo)

## Câu lệnh về container

- Xem container đang chạy

```
docker ps

# Xem tất cả container trên 1 dòng
docker ps | less -S

# Xem container được chạy gần nhất (sau cùng)
docker ps -l

# Liệt kê tất cả container
docker ps -a
```

- Xem các tiến trình bên trong một container

```
docker top cid
```

- Thông tin chi tiết về container

```
docker inspect cid
```

- Xem log

```
docker logs cid

docker logs -f cid
```

- Xem những thay đổi của container

```
docker diff cid
```

- Kiểm tra mật khẩu gốc của container

```
docker logs cid 2>&1 | grep '^User: ' | tail -n1
```

- Khởi động và tương tác với container

```
docker run -i -t ubuntu /bin/bash

# Xuất từ "hello word" xong tắt
docker run image_name echo "hello word"

# Khởi động container có đặt tên kèm theo
docker run --name test ubuntu

# Khởi động container ở chế độ chạy nền
docker run -d -it ubuntu

# Gán thêm port
docker run -p 8080:8080 ubuntu

# Mount vào volume
docker run -v ./test:/var/www

# Chạy với quyền root
docker run --privileged=false

# Sau khi chạy xong thì xóa container
docker run -it --rm ubuntu bash
```

- Attack vào container đang chạy, sau khi ngừng thì hết attack nhé

```
docker attach cid
```

- Chạy chương trình bên trong container

```
docker run ubuntu apt-get update
```


*Ngoài ra còn rất nhiều câu lệnh về Dockerfile, Docker-composer,... Nhưng liệt kê hết thì dài quá viết không nổi. Trong quá trình sử dụng cần lệnh nào thì hỏi google để biết thêm. Nhớ được nhiêu đây là xài ngon rồi :D*