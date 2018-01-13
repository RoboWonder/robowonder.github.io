---
image: https://4.bp.blogspot.com/-OIsfM_7uAhw/WD3w12mgjOI/AAAAAAAABf8/s9PH6lkSuT8vPEM2r0HWQ0pnPFtQ57t0QCLcB/s320/angular2_thu_vien_phu_thuoc.png
instantfeedback: true
layout: post
description: Giới thiệu về Angular 2 và các thư viện liên quan
title: Angular 2 và các thư viện liên quan
category: Lập trình
tags: Angular, Angular2, 2016
keywords: Angular, Angular2, 2016
---

<figure><img src="https://4.bp.blogspot.com/-OIsfM_7uAhw/WD3w12mgjOI/AAAAAAAABf8/s9PH6lkSuT8vPEM2r0HWQ0pnPFtQ57t0QCLcB/s320/angular2_thu_vien_phu_thuoc.png" alt="Giới thiệu về Angular 2 và các thư viện liên quan" title="Giới thiệu về Angular 2 và các thư viện liên quan"></figure>

Angular 2 ra đời và chính thức lấy tên là Angular chứ không còn là AngularJs nữa. Và như tôi nhận thấy thì rất rất nhiều người đã phải bối rối ngay từ khi Angular vẫn đang beta.

Thử nhìn vào source của ví dụ "Hello Word" từ chính trang [angular.io](http://angular.io). Bạn có thể xem trên Plunker [tại đây](http://plnkr.co/edit/w2FVfKlWP72pzXIsfsCU?p=previews).

Mở source file index.html ra và... Ôi mẹ ơi, một mớ lằng nhằng chẳng hiểu để làm cái gì nữa. Có đến 5 file được import chứ không phải chỉ 1 file như Angular1 nữa.

1. system.js
2. typescript.js
3. angular2-polyfills.js
4. Rx.js
5. angular2.dev.js

## Giờ đi tìm hiểu từng file xem nó là cái gì.

**System.js**

Đây là một thư viện được viết bởi [Guy Bedford](https://github.com/guybedford) và các cộng sự. Được viết dựa trên es6-module-loader để thay vì chỉ load các module của es6 thì còn có thể load được cả CommonJs, AMD, global script. Được gọi là  “Universal dynamic module loader”.

Như vậy, Angular không có hệ thống module riêng như Angular1 mà sử dụng lại của System.js. Vậy nên đầu tiên phải import nó vào trước nếu không Angular sẽ không chạy được đâu nhá.

**Typescript.js**

Chắc hẳn các bạn đa số đều biết về TypeScript, trước đây tôi có một loạt bài viết về thằng này nhưng quên backup lại khi trả server.

TypeScript là ngôn ngữ mới do Microsoft phát triển. Được gọi là siêu javascript và khả năng là sẽ dần thay thế javascript trong tương lai. Về cơ bản là TypeScript có cấu trúc như các ngôn ngữ lập trình hướng đối tượng. Sau đó trình biên dịch sẽ dịch ra JavaScript để trình duyệt hiểu được.

File typescript.js này chính là transpiler cho system.js sử dụng để dịch TypeScript thành JavaScript .

```javascript
System.config({
	transpiler: 'typescript',   // hắn đây
	typescriptOptions: { emitDecoratorMetadata: true }, 
	packages: {'src': {defaultExtension: 'ts'}} 
});
```

**angular2-polyfills**

File thực chất là hợp nhất giữa zone.js và reflect-metadata.

**Rx.js**

Là thư viện Observables. Thuật ngữ này sẽ gặp nhiều khi đi sâu vào Angular. Nó được bổ sung giống Promises ở Angular1. Cho dù bạn có hay không sử dụng Observables thì vẫn phải import thư viện này vào.

**angular2.dev.js**

Cái này nhìn thấy chữ dev là rõ rồi hen. Không cần nói thêm nữa.

## Tổng kết

Hi vọng bài viết này sẽ giúp các bạn đỡ băn khoăn về các thư viện mà Angular sử dụng. Vào angular.io để tìm hiểu thêm trong lúc tôi viết bài mới.

Nhớ đăng ký theo dõi blog để nhận những bài viết mới nhất. Cảm ơn các bạn đã đọc bài.