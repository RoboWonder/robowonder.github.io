---
image: https://3.bp.blogspot.com/-dZE73m_xDmA/WFLYByetysI/AAAAAAAABjU/mHeO_K22Va02O3IFXP-OtmgOEfW3DderQCLcB/s640/angular_1_component_approximation.png
instantfeedback: true
description: Trong Angular có rất nhiều thứ quan trọng, nhưng tôi chọn viết về component trước bởi vì nó là thư quan trọng nhất. Tập hợp controller, directive, router
layout: post
title: Angular 2 từ A-Z về component
category: Lập trình
tags: Angular, Angular2, 2016
keywords: Angular, Angular2, Angular 2 a-z, component, 2016
---

<figure><img src="https://3.bp.blogspot.com/-dZE73m_xDmA/WFLYByetysI/AAAAAAAABjU/mHeO_K22Va02O3IFXP-OtmgOEfW3DderQCLcB/s640/angular_1_component_approximation.png" alt="Angular 2 từ A-Z về component" title="Angular 2 từ A-Z về component"></figure>

Sau bài Cài đặt và tải ứng dụng demo là bài khởi đầu cho serial về tutorial Angular 2. Bài này viết này là bài được ưu tiên viết kế tiếp. Trong Angular có rất nhiều thứ quan trọng, nhưng tôi chọn viết về component trước bởi vì nó là thư quan trọng nhất. Tập hợp controller, directive, router... đều nằm trong component.

## "Everything is a component"

Tất cả mọi thứ là conponent. Vâng, chính xác là như vậy. Component chính là thứ chúng ta cần xây dựng và xác định các yếu tố cần thiết cũng như logic của trang. Nếu bạn đã từng học Angular 1, biết rõ về directive thì nhìn hình trên bạn sẽ hiểu được component.

## Đi sâu về khái niệm

> Một component cơ bản là chỉ là một phần tử HTML tùy chỉnh phù hợp với tên của một component được code ở một nơi khác. Một component thường có input và output. Các input và output này được xác định bằng các thuộc tính trên phần tử HTML.

Đọc một lần thôi, có đọc đi đọc lại mấy dòng đó vài lần cũng chỉ thêm rối chứ chẳng hiểu hơn được đâu. Tôi đã cố viết theo cách dễ hiểu nhất rồi á. Giờ xem ví dụ sẽ hiểu rõ ngay thôi:

```
	<my-confirmation [message]="'Launch missiles?'" (ok)="launchMissiles()"></my-confirmation>
```

Giả sử chúng ta có một phần tử HTML như trên, nó đã được tùy chỉnh để phù hợp với một component được định nghĩa như sau:

```typescript
@Component({
  selector: 'my-confirmation',
  inputs: ['message'],
  outputs: ['ok']
})
@View({
  template: `
    <div>
      {{message}}
      <button (click)="ok()">OK</button>
    </div>
  `
})
class MyConfirmation {
  okEvents = new EventEmitter();
  ok() {
    this.okEvents.next();
  }
}
```

Ok, giải thích thêm tí về ví dụ. Phần tử HTML có tên là *my-confirmation*. Và tên của component là *MyConfirmation*. Nó ở dòng số 14, *class MyConfirmation* chính là tên component. Như vậy là bạn đã hiểu câu "**một phần tử HTML tùy chỉnh phù hợp với tên của một component được code ở một nơi khác**" rồi chứ. Trong MyComfirmation, chữ "C" sau chữ "My" được viết hoa, khi đó Angular sẽ hiểu bên phía HTML trước chữ C sẽ có dấu "-".

Trong phần tử HTML trên có hai thuộc tính là [message] và (ok) tương ứng với inputs và outputs trong component. Như vậy trên HTML dấu [] có nghĩa là inputs và dấu () có nghĩa là outputs. Vấn đề này đã được nói rõ trong bài [Cú pháp template trong Angular 2 - Phần 1](http://www.robowonder.com/2016/12/cu-phap-template-trong-angular-2-phan-1.html), đọc lại nếu bạn không nhớ.

## Component trong component

Rất nhiều bạn khi bắt đầu với Angular hay có suy nghĩ là làm thế nào để code một website bao gồm một giao diện layout chung ở ngoài, rồi trong đó có các thứ như header, footer, menu giữ nguyên còn các phần khác thì thay đổi ở từng trang như code băng PHP. Hầu hết các bạn đều lo lắng Angular sẽ không đáp ứng được điều đó vì ngay cả hướng dẫn lẫn ứng dụng mẫu của Angular đều không nói đến.

Đừng lo lắng, Angular và các framework javascript khác thừa sức làm điều đó. Như hình sau:

<figure><img src="https://3.bp.blogspot.com/-2BXMmT6Mp_0/WFLkwB-cEsI/AAAAAAAABjs/akQ5I44GnJs4eHLC1RuTRziZ1kvnf_GwgCLcB/s400/component%2Bin%2Bcomponent.jpg" alt="Component trong component" title="Component trong component"></figure>

Cứ từ từ theo dõi blog của tôi sẽ làm được hết, ahihi.

## Cấu hình (Configuration)

Hầu hết các bạn đều biết khai báo cấu hình cho một component thường có cấu hình selector, trong ví dụ trên của tôi có thêm inputs, outputs, trong các ứng dụng trên angular.io có thêm template.

Đó là các dữ liệu tùy chọn để cung cấp cho component, tuy nhiên ngoài những cấu hình đó ra thì còn những cấu hình khác mà các bạn ít biết như là providers, services, styles. 

Bây giờ tôi sẽ giải thích rõ từng cấu hình:
- Selector: Cái này là khu vực làm việc của component trên DOM. Tên của phần tử HTML của các bạn là gì thì cứ copy y chang vào đây. Tương tự như ví dụ trên là my-confirmation
- Providers: providers có thể trả về bất cứ thứ gì khi chạy một hàm. Ví dụ như bạn có thể dùng provider để xử lý ngôn ngữ hoặc parse dữ liệu json chẳng hạn, rồi sau đó trả về kết quả.
- Services: Chịu trách nhiệm thực hiện một nhiệm vụ cụ thể, ví dụ như bạn có thể định nghĩa lại ajax trong này cũng được.
Template: thay vì khai báo trực tiếp View trong component. bạn có thể chỉ thẳng đến một file HTML nào đó trong này.
- Styles: dùng để khai báo css nếu có.

Vậy là cơ bản đã xong về Component trong Angular 2. Các bạn nên nhớ kỹ để sau này làm việc với Angular 2 đỡ bối rối hơn. Cảm ơn các bạn đã đọc bài.