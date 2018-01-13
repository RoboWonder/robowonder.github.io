---
image: https://facebook.github.io/flux/img/flux-simple-f8-diagram-with-client-action-1300w.png
instantfeedback: true
description: Flux là kiến trúc ứng dụng Facebook dùng để xây dựng các ứng dụng phía client. Kiến trúc này bổ sung khả năng thiết lập dữ liệu theo một hướng cho view của component trong Reactjs.
layout: post
title: Tìm hiểu về Flux
category: Lập trình
tags: JavaScript, Flux
keywords: Flux, JavaScript     
---

## Flux là gì?

Flux là kiến trúc ứng dụng Facebook dùng để xây dựng các ứng dụng phía client. Kiến trúc này bổ sung khả năng thiết lập dữ liệu theo một hướng cho view của component trong Reactjs.

<figure><img src="https://facebook.github.io/flux/img/flux-simple-f8-diagram-with-client-action-1300w.png" alt="Giới thiệu Flux" title="Giới thiệu Flux"></figure>

Flux là một cấu trúc mở rộng của pattern chứ không phải là framework chính thức.

Hiện tại không có nhiều tài liệu về Flux vì Facebook chỉ sử dụng nội bộ. Vậy nên cũng không có mã nguồn trên Github làm cho việc tìm hiểu về Flux cực kỳ cực kỳ khó khăn. Trên Github, Facebook chỉ công bố một thư viện tên là Dispatcher tại [địa chỉ này](https://github.com/facebook/flux/blob/master/src/Dispatcher.js).

Về cơ bản, Flux sẽ tận dụng thư viện Dispatcher này, kết hợp với các module EventEmitter của NodeJS của để thiết lập một hệ thống sự kiện giúp quản lý trạng thái ứng dụng.

Flux có 4 thành phần, để dễ hiểu hơn ta xem qua khái niệm của 4 thành phần này:

- **Actions**: Thằng này đảm nhiệm việc truyền dữ liệu đến Dispatcher. Có thể nói Actions là một helper, bất cứ khi nào có dữ liệu cần thay đổi, nó sẽ tạo ra một action và gửi nó đến cho Dispatcher. Nên nó có tên là Actions 😎. Cứ tạm hiểu Actions chính là con bé xinh xinh ngồi ở chực ở bưu điện. Ai gửi cũng nhận, nhận xong đóng dấu rồi đưa cho thằng vận chuyển.
- **Dispatcher**: Nhận action từ Actions và truyền đến các callbacks đã đăng ký trước. Các callbacks đăng ký với logic riêng, Dispatcher sẽ phân loại action nào phù hợp với logic nào và truyền đến cho callbacks có logic đó. Thằng này giống transporter của bưu điện, vận chuyển hàng theo địa chỉ trên hàng thôi.
- **Store**: Lưu giữ trạng thái và logic ứng dụng. Điểm đặc biệt của store này là nếu muốn thay đổi dữ liệu bên trong nó phải thông qua Actions rồi đi qua Dispatcher.
- **View**: View chỉ là lấy dữ liệu từ store và show hàng ra mà thôi. Nếu dữ liệu từ người dùng có thay đổi, ví dụ như submit một form hay gì đó, view không hiển thị lên ngay mà phải gửi về Actions rồi chạy 1 vòng qua những thằng bên trên để lưu vào store, rồi view lại móc ra để render.

Như vậy quy trình sẽ là:

```
Actions -> Dispatcher -> Store -> View
```

## Tại sao phải xài Flux?

Tui thề là đầy người đọc bài này hỏi cái câu đó. Tự dưng đang xài MVC ngon lành cành đào không thích lại đi mày mò ba cái thứ chạy vòng vòng này làm gì cho mất công.

Xin thưa với các bạn rằng MVC cũng có nhược điểm của nó, nhược điểm không thể khắc phục được luôn, chẳng qua các bạn chưa gặp thôi.

Có lẽ trong số chúng ta chưa ai được dạy về cấu trúc một ứng dụng Front-End, thay vào đó lại đi học về jQuery, Angular, Backbone... Vấn đề lưu lượng dữ liệu cho Front-End thì lại càng nằm ngoài tầm hiểu biết, nên gặp cái mớ quá chi là phức tạp này thì cũng thấy nó không cần thiết.

Flux ra đời từ cái thời 2014 thì phải, hay là trước đó nữa. Đúng ra với những thứ đã có từ lâu này thì tui không có hứng thú viết về nó. Nhưng về Flux thì vẫn phải viết và khuyên các bạn nên tìm hiểu kỹ về nó, bởi vì bài sau tôi sẽ mượn Flux của Facebook vốn dành cho Reactjs để áp dụng vào Angular 2