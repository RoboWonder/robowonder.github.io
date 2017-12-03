---
layout: post
title: Cú pháp template trong Angular 2 - Phần 2
category: Angular
keywords: Angular, Angular2, template syntax
---

![alt text](https://1.bp.blogspot.com/-c4LnEr9Euok/WEWT6zBIBVI/AAAAAAAABik/1pt6dQF7Lv455VVcU_endSRTeiNTgg6gQCPcB/s1600/angular.png "Cú pháp template trong Angular 2")

Nối tiếp [phần 1 về cú pháp template trong Angular 2](http://www.peamon.com/2016/12/cu-phap-template-trong-angular-2-phan-1.html). Nếu các bạn chưa đọc thì nên đọc lại trước khi đọc bài này.

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

### Cú pháp hoa thị (\*) 

Phần này dài dòng mà angular.io đã nói rất rõ, các bạn [xem tại đây](https://angular.io/docs/ts/latest/guide/template-syntax.html#!#star-template)