---
image: https://1.bp.blogspot.com/-6s7YhOfw4UM/WFPKrfNsJtI/AAAAAAAABkI/57UrZoxi5M8fXJ59E-m9NR6CYTSAJTy2wCLcB/s640/anguar%2B2%2Btao%2Bcomponent%2Bdau%2Btien.png
instantfeedback: true
description: Tạo component đầu tiên của bạn
layout: post
title: Angular và TypeScript - Tạo component
category: Lập trình
tags: Angular, Angular2, 2016
keywords: Angular, Angular2, Angular 2 a-z, component, 2016
---

<figure><img src="https://1.bp.blogspot.com/-6s7YhOfw4UM/WFPKrfNsJtI/AAAAAAAABkI/57UrZoxi5M8fXJ59E-m9NR6CYTSAJTy2wCLcB/s640/anguar%2B2%2Btao%2Bcomponent%2Bdau%2Btien.png" alt="Angular và TypeScript: Tạo component" title="Angular và TypeScript: Tạo component"></figure>

Trước khi đọc bài này, bạn cần phải đọc và làm theo hướng dẫn trong bài Cài đặt và chạy ứng dụng demo. Bởi vì chúng ta sẽ sử dụng ứng dụng demo trong bài đó để viết component.

Sau khi tải ứng dụng demo xong, bây giờ các bạn vào thư mục *helloworld\app* và tìm file *app.component.ts*, đây là file chứa component và chúng ta sẽ sửa lại file này. Hãy mở nó lên bằng IDE của các bạn và bắt đầu.

## Template

Trong cấu hình template hiện tại của component đang là Hello {{name}}, bây giờ các bạn sửa lại như sau:

```
	<h2>{{componentName}}!</h2>
	  <div *ngFor="let f of friends">
	  <h4> Tên : {{f.name}} </h4> <h4>Tuổi: {{f.age}}</h4> 
	</div>
```

Template này sẽ dùng một vòng "for" để in ra tất cả phần tử có trong biến friend.

## Styles

Tiếp theo đến cấu hình styles, các bạn cấu hình theo mẫu css sau:

```
div { 
  background-color:#EFEFEF;
  margin-bottom:15px;
  padding:15px;
  border:1px solid #DDD;
  box-shadow:2px 2px 2px 0 rgba(0, 0, 0, 0.3);
  border-radius:3px;
}
h2 { 
  text-align: center;
}
```

Khi chạy styles này sẽ được ném vào header của web, nhưng chỉ có tác dụng với template trong component này thôi nên sẽ không ảnh hưởng đến styles của toàn bộ web.

## Lập trình component

Vậy thôi là xong phần cấu hình, bây giờ đi vào phần code chính. Code như sau:

```typescript
export class AppComponent  { 
	componentName: string = 'My friends';
   	friends =  [
	    { age: 40, name: 'Thằng thứ nhất' },
	    { age: 23, name: 'Thằng thứ 2' },
	    { age: 23, name: 'Thằng thứ 3' },
	    { age: 24, name: 'Thằng thứ 4' },
	    { age: 22, name: 'Thằng thứ 5' },
	    { age: 23, name: 'Thằng thứ 6' },
	    { age: 25, name: 'Thằng thứ 7' },
	    { age: 21, name: 'Thằng thứ 8' },
	    { age: 21, name: 'Thằng thứ 9' }
    ];
}
```

Biến *componentName* sẽ được đưa vào *{{componentName}}* của template, còn biến *friends* sẽ đưa vào for

## Kết quả

Kết quả chương trình sẽ chạy như sau, xem trên punker [https://embed.plnkr.co/ytw2UQkJpJP6NUVrCBI6/](https://embed.plnkr.co/ytw2UQkJpJP6NUVrCBI6/)