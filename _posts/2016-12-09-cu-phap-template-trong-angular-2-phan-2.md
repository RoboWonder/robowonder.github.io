---
image: https://2.bp.blogspot.com/-c4LnEr9Euok/WEWT6zBIBVI/AAAAAAAABiY/do5l9pATlbUxBzVU_q9IesrpNDRfODFogCLcB/s1600/angular.png
instantfeedback: true
layout: post
description: Bài này sẽ nói về một số cú pháp quy định trong Angular 2 để đưa dữ liệu vào template.
layout: post
title: Cú pháp template trong Angular 2 - Phần 2
category: Lập trình
tags: Angular, Angular2, 2016
keywords: Angular, Angular2, template syntax, 2016
---

<figure><img src="https://4.bp.blogspot.com/-zRXAUpuJt78/WD6-e4drdYI/AAAAAAAABgY/BSGV_4U1VJgdLGqyik-ORAlBaE9DS3p1wCLcB/s320/angular2%2Bva%2Bes6.png" alt="alt text" title="Angular và ES6: Tạo bộ khung ứng dụng"></figure>

Nối tiếp [phần 1 về cú pháp template trong Angular 2](http://www.robowonder.com/2016/12/cu-phap-template-trong-angular-2-phan-1.html). Nếu các bạn chưa đọc thì nên đọc lại trước khi đọc bài này.

## Nội suy (Interpolation)

Đơn giản là biến được đặt trong 2 cặp dấu ngoặc nhọn {{var}}. Khi render Angular sẽ thay bằng giá trị của nó. Như trong Angular 1.

```html
<div>Hello {{name}}</div>
```

## Dùng các dấu ngoặc

Sử dụng dấu ngoặc giúp mã HTML của bạn ngắn gọn hơn, tuy nhiên cần phải biết mỗi loại ngoặc có chức năng gì đã. Xem ví dụ sau có dùng ngoặc:

```html
<some-component 
  [prop]="someExp" 
  (event)="someEvent()" 
  [(twoWayProp)]="someExp">
</some-component>
```

Tương đương với:

```html
<some-component 
  bind-prop="someExp" 
  on-event="someEvent()" 
  bindon-twowayprop="someExp">
</some-component>
```

## References

Chẳng biết trong trường hợp này dịch ra là gì, giải thích thì hơi dài dòng. Xem ví dụ sau sẽ hiểu:

```html
<video-player #player></video-player> 
<button (click)="player.pause()">Pause</button>
```

```html
<input #i> 
{{i.value}}
```

Ở hai ví dụ trên, tag đầu tiên có thuộc tính đứng sau dấu #. Angular sẽ hiểu đó như là id và tự động select nó. Lúc cần mình chỉ lấy ra và dùng thôi.

**Cú pháp hoa thị (\*)**

Phần này dài dòng mà angular.io đã nói rất rõ, các bạn [xem tại đây](https://angular.io/docs/ts/latest/guide/template-syntax.html#!#star-template)