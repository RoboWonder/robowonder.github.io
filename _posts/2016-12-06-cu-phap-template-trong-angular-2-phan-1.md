---
image: https://2.bp.blogspot.com/-c4LnEr9Euok/WEWT6zBIBVI/AAAAAAAABiY/do5l9pATlbUxBzVU_q9IesrpNDRfODFogCLcB/s1600/angular.png
instantfeedback: true
description: Bài này sẽ nói về một số cú pháp quy định trong Angular 2 để đưa dữ liệu vào template.
layout: post
title: Cú pháp template trong Angular 2 - Phần 1
category: Lập trình
tags: Angular, Angular2, 2016
keywords: Angular, Angular2, template syntax, 2016
---

<figure><img src="https://2.bp.blogspot.com/-c4LnEr9Euok/WEWT6zBIBVI/AAAAAAAABiY/do5l9pATlbUxBzVU_q9IesrpNDRfODFogCLcB/s1600/angular.png" alt="Cú pháp template trong Angular 2" title="Cú pháp template trong Angular 2"></figure>

Bài này sẽ nói về một số cú pháp quy định trong Angular 2 để đưa dữ liệu vào template. Vấn đề này đã được nói rõ trong hướng dẫn chính thức của Angular trong trang Template Syntax vi vậy ở đây tôi không nói lại tất cả, chỉ nói những cái chưa rõ hay khó hiểu thôi.

## Input - Output

Thuộc tính Input - Output là các API của Directive. Khi định nghĩa một directive thì luồng dữ liệu sẽ đi vào directive thông qua Input và đi ra qua Output. Tôi không nhớ Angular 1 có cái này không vì lâu rồi không còn đụng đến nữa. 

Với có thể cập nhật dữ liệu cho directive vào Input bằng cách bind  data, còn Output có thể dùng để bind event, ta sẽ lần lượt tìm hiểu sau đây.

**Bind data**

Nhìn vào ví dụ sau, giả sử ta có một component dùng để render một Toto:

```html
<mytag [model]="myTodo"></mytag>
```

Khi giá trị myToto thay đổi, ngay lập tức Angular sẽ tự động cập nhật giá trị mới bằng cách gọi setter của model.

**Bind event**

Không chỉ bind data, Angular còn bind cả event mà DOM có hỗ trợ như onClick, onChange, onComplete... Thậm chí là event tự định nghĩa luôn. Giờ sửa ví dụ trên thành:

```html
<mytag [model]="todo" (complete)="onCompletingTodo(todo)"></mytag>
```

Nếu sự kiện complete xãy ra. Angular sẽ gọi ngay đến hàm onCompletingTodo(todo). 

Bây giờ xem qua code của component cho dễ hiểu hơn:

```typescript
@Component({selector: 'mytag'}) 
class mytag {
  @Input() model;

  @Output() complete = new EventEmitter();

  onCompletedButton() { 
    this.complete.next();
  } 
}
```

Component đã được khai báo Input là model, còn Output là sự kiên complete.

Chỉ có Input mới được cập nhật dữ liệu bằng cách bind data,

Angular 2 sử dụng RxJs để giải quyết các event. EventEmitter là để hoàn thành observable và observer interfaces - nếu bạn vẫn chưa hiểu thì đọc lại bài [các thư viện liên quan](http://robowonder.com/2016/11/angular-2-va-cac-thu-vien-lien-quan.html) và định nghĩa trên github [tại đây](https://github.com/jhusain/observable-spec)

## Two-Way Bindings

Bind hai chiều rất cần thiết trong một số tình huống, nhất là để xử lý Input. Bind data được dùng để truyền dữ liệu từ thằng cha xuống thằng con, ngược lại bind event thì truyền từ thằng con lên thằng cha. Vì vậy kết hợp cả hai thành bind hai chiều (two-way bindings).

Dưới đây là ví dụ về Two-Way bindings:

```html
<input [(ngModel)]="todo.text"></input>
```

```typescript
@Directive({ 
  selector: '[ngModel]', 
  host: { 
    "[value]": 'ngModel', 
    "(input)": "ngModelChange.next($event.target.value)" 
  } 
}) 
class NgModelDirective {
  @Input() ngModel:any;
  @Output() ngModelChange = new EventEmitter()
}
```

Đây là ví dụ cực kỳ đơn giản để thực hiện bind dữ liệu hai chiều. Input sẽ cập nhật dữ liệu khi textfiel thay đổi, và thẻ textfiel thay đổi khi Input thay đổi.

Về cơ chế thì cũng giống Angular 1. Angular 2 chỉ thay đổi cú pháp chứ không có gì khác hơn.

Bài này tạm dừng ở đây, phần 2 tôi sẽ viết tiếp về những thứ còn lại. 