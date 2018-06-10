---
instantfeedback: true
description: Cài đặt Nginx, PHP-Fpm 7.1, MariaDB cho Windows Subsystem for Linux
layout: post
title: Cài đặt Nginx, PHP-Fpm 7.1, MariaDB cho WSL
category: Công nghệ
tags: Windows, Subsystem, Linux, PHP-Fpm 7.1
keywords: Windows, Subsystem, for Linux, WSL, Nginx, PHP-Fpm, MariaDB
---


Hiện nay trên mạng có rất nhiều bài viết hướng dẫn cài đặt webserver dùng cả Apache và cả Nginx. Tuy nhiên, các bài viết chủ yếu hướng dẫn cài php 5, mà hiện nay các framework php đa số yêu cầu php 7. Và php 7 hiệu suất tốt hơn php 5 rất nhiều.

Server web chủ yếu chạy nginx nên bài này chỉ hướng dẫn cài nginx. Để trên máy dev và máy server cùng môi trường thì khi deploy sẽ dễ dàng cũng như ít phát sinh lỗi hơn.

## Cài đặt và cấu hình Nginx

Trước khi bắt đầu cài đặt phần mềm trên Ubuntu cần cập nhật apt lấy danh sách gói phần mềm phiên bản mới nhất:

```
sudo apt-get update
```

Sau khi chạy xong tiến hành cài đặt nginx bằng lệnh sau:

```
sudo apt-get install -y nginx
```
Nginx sẽ được cài đặt vào thư mục `/etc/nginx`, mọi cấu hình cũng nằm trong thư mục này. Sau khi cài xong, cấu hình vitual host.

***Đầu tiên cần xác định thư mục chứa source web trên máy tính.***
Ví dụ như của tôi là: `D:\web` thì tương ứng trên Ubuntu là `/mnt/d/web`, đối với ổ đĩa `C:\` thì `/mnt/c`...

**\* Cấu hình virtual host:**

Mở file cấu hình:

```
sudo vi /etc/nginx/sites-available/default
```
Sau đó cấu hình file mẫu sau:
```
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /mnt/d/web;

        index index.php index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                try_files $uri $uri/ =404;
        }
}
```
Giải thích sơ qua thì:

- `root` là địa chỉ của thư mục chứa source code. 
- `index` là file index mặc định của source code, nếu thiếu index.php thì gõ thêm vào.
- `server_name` là tên domain, dấu "\_" nghĩa là localhost.

Vậy là cấu hình xong, chạy lệnh sau để khởi động Nginx:

```
sudo service nginx start
```

Bây giờ mở trình duyệt ra và vào localhost xem, nếu hiện đúng thư mục chứa source code là đã thành công.


## Cài đặt và cấu hình PHP-Fpm 7.1

PHP 7.1 hiện nay chưa hỗ trợ trên kho reponstory của Ubuntu, nên phải cài từ kho ngoài. Chạy lần lượt từng lệnh sau để thêm kho vào Ubuntu và cập nhật lại package list cho Ubuntu.

```
sudo apt-get install -y python-software-properties
sudo add-apt-repository -y ppa:ondrej/php
sudo apt-get update -y
```

Tiếp theo cài php-fpm:

```
apt-get -y install php7.0-fpm
```

**\* Cấu hình PHP-Fpm:**

Mở file cấu hình php:

```
sudo vi /etc/php/7.1/fpm/pool.d/www.conf
```

Tìm dòng:

```
listen = unix:/run/php/php7.0-fpm.sock
```

thay bằng:

```
listen = 127.0.0.1:9000
```

Lưu lại rồi vào file cấu hình Nginx hồi nãy sửa lại như sau:

```
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /mnt/d/web;

        index index.php index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                try_files $uri $uri/ =404;
        }
        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass 127.0.0.1:9000;
        }
}
```

Thêm block location cuối cùng (Lúc cấu hình nginx chỉ có 1 block location) dùng để kết nối nginx với php-fpm.

Khởi động lại nginx và start php là xong:

```
sudo service nginx restart
sudo service php7.1-fpm start
```

## Cài đặt và cấu hình MariaDB

Chạy lần lượt từng lệnh sau để cài đặt và cấu hình:

```
sudo apt-get -y install mariadb-server 
sudo vi /etc/mysql/mariadb.conf.d/50-server.cnf
```

Tìm 2 dòng:
```
character-set-server  = utf8mb4
collation-server      = utf8mb4_general_ci
```

thay bằng:

```
character-set-server = utf8 
#collation-server = utf8mb4_general_ci 
```

Ô cơ, khởi động MariaDB lên thôi, thằng MariaBD này tuy tên nó như vậy nhưng service nó vẫn là mysql nha:

```
sudo service mysql start
```

Tiếp theo chạy `mysql_secure_installation` và làm theo hướng dẫn. Done, thanks for read!!