---
image: https://www.softzone.es/app/uploads/2016/08/Windows-10-Ubuntu.png
instantfeedback: true
description: Với Windows Subsystem for Linux, các Dev web và back-end sử dụng Windows có thêm môi trường dev tuyệt vời
layout: post
title: Windows Subsystem for Linux - Món quà tuyệt vời cho Dev
category: Công nghệ
tags: Windows, Subsystem, Linux
keywords: Windows, Subsystem, for Linux
---

Không kể các developer dùng MAC thì trước đây các web developer thường dùng song song 2 hệ điều hành trên máy tính, là Windows và Ubuntu. Các back-end hay full-stack developer thì xài hẳn Ubuntu luôn (mặc dù tụi nó cũng thèm Windows lắm :)))

<figure><img src="https://2.bp.blogspot.com/-Gcn5mb3mcYM/Wr5GRC28fqI/AAAAAAAABrQ/INQjTmBzhfcL4PcfZtUd_XlSMMf5dSdfQCEwYBhgL/s1600/Windows-10-Ubuntu.png" alt="Windows Subsystem for Linux - Món quà tuyệt vời cho Dev" title="Windows Subsystem for Linux - Món quà tuyệt vời cho Dev"></figure>

Đầu năm 2016, bộ phận phát triển Windows Kernel của Microsoft đã tung ra bản alpha đầu tiên của Windows Subsystem for Linux (WSL) làm dậy sóng cả cộng đồng develop. WSL giúp người dùng có thể sử dụng một phiên bản của Linux trên Windows mà không phải dùng ảo hóa.

WSL không phải là ảo hóa! Đúng vậy, bạn không đọc nhầm đâu. Nhiều người vẫn nhầm lẫn Microsoft tạo một máy ảo chạy Ubuntu trên Windows nhưng không phải vậy. Bạn không cần phải chạy Hyper-V khi sử dụng WSL.

Microsoft đã hợp tác với Canonical (Công ty phát triển và phân phối Ubuntu) để tạo ra một bộ nhân Linux (tên là lxcore) để map Api của Windows với Linux Kernel. Điều này giúp cho các ứng dụng native của Linux (Linux ELF64) có thể chạy trên Windows mà không cần biên dịch lại.

WSL có thể chạy bất kỳ ứng dụng native nào của Ubuntu, Fedora và OpenSUSE (các Linux Distro). Từ các ứng dụng chạy nền như MySqL, Postgresql, Memcached, Redis... đến các ứng dụng GUI như GNOME-VIM. Quá chi là tuyệt vời :))

**Đặc biệt: Có thể chạy nhiều Linux Distro cùng lúc**

Như hình dưới, bạn có thể cài đặt và chạy Ubuntu, openSUSE, và SUSE Linux Enterprise Server cùng với nhau, hoàn toàn độc lập nhưng có thể truy cập vào hệ thống tập tin của Windows, mạng stack ... 

<figure><img src="https://4.bp.blogspot.com/-jQGEJ0RSUC8/WmlZgkssGPI/AAAAAAAABqM/0xgXkeeBpOglYjg_FY0M0dbLtV-UAqUEwCLcBGAs/s640/multiple-distors-600x338.png" alt="Windows Subsystem for Linux - Chạy nhiều distro cùng lúc" title="Windows Subsystem for Linux - Chạy nhiều distro cùng lúc"></figure>

## Cài đặt Windows Subsystem for Linux

Vào Control Panel -> Programs and Feature -> Turn Windows feature on or off. Đánh dấu tích vào Windows Subsystem for Linux

<figure><img src="https://1.bp.blogspot.com/-aH14LBzOfno/WmlaXeR_S4I/AAAAAAAABqU/G6PviFWQ6gck38vYNC0MKJF-wq-ZWBU3ACLcBGAs/s640/enable_windows_subsystem_for_linux.jpg" alt="Bật Windows Subsystem for Linux" title="Bật Windows Subsystem for Linux"></figure>

hoặc mở Power Shell ở chế độ Run as Administrator rồi gõ vào lệnh sau:

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

Sau đó khởi động lại máy.

Sau khi khởi động máy xong, vào Windows Store tìm Ubuntu hoặc OpenSUSE tải về. Thích nhanh thì bấm vào link này https://www.microsoft.com/store/p/ubuntu/9nblggh4msv6

Sau khi cài Bash xong thì mở lên, ngay lần đầu nó sẽ yêu cầu tạo username và password, cứ làm theo yêu cầu của nó là xong.

**Cài nhiều Linux Distro**

Hiện nay trên Windows Store đã hỗ trợ đến 5 hệ điều hành Linux Distro cho các bạn lựa chọn, bao gồm: Ubuntu, openSUSE, SUSE Enterprise, Debian Linux và Kali Linux.

<figure><img src="https://1.bp.blogspot.com/-ep-03JmU80M/Wr5DIoy6ZTI/AAAAAAAABrE/xWL8XcKW4m43dByjuB6T93EVuA2OGIHpgCLcBGAs/s640/multiple-linux-distro.JPG" alt="Cài nhiều Linux Distro trên Windows Store" title="Cài nhiều Linux Distro trên Windows Store"></figure>

Thích cái nào thì cứ Install cái đó thôi.


## App của Windows Subsystem for Linux chạy trên phần cứng vật lý

Như đã nói từ đầu, đây không phải là máy ảo Linux trên Windows. Vì vậy app của Linux cũng chạy dựa trên phần cứng vật lý của máy tính. 

Xem hình sau đây các bạn sẽ thấy. Hiện tại máy tôi đang chạy webserver bao gồm Nginx, PHP-fpm, MySQL Server, Redis và tất cả đều xuất hiện trên Task Manager của Windows. Và có thể dùng Task Manager để kill nó bất cứ lúc nào. 

<figure><img src="https://2.bp.blogspot.com/-0YMYXVwk8J0/Wr5E9cOLLqI/AAAAAAAABrM/-vp63q35O8IGvCDpdXXDtZpF7z-VmpAEgCLcBGAs/s640/app-chay-tren-phan-cung-that.jpg" alt="App của Windows Subsystem for Linux chạy trên phần cứng vật lý" title="App của Windows Subsystem for Linux chạy trên phần cứng vật lý"></figure>

Quá đã phải không nào. Các app này chạy lại tốn rất ít tài nguyên nhé, chỉ xấp xỉ 1MB thôi :0