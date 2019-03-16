---
image: null
instantfeedback: true
description: Hướng dẫn hướng đối tượng trong Javascript phần kế thừa siêu dễ hiểu
layout: post
title: Hướng đối tượng Javascript - Tính kế thừa (Siêu dễ hiểu)
category: Lập trình
tags: Javascript, OOP
keywords: hướng đối tượng, lập trình, javascript, dễ hiểu
---

<h3>Tính kế thừa là gì</h3>

Hành vi của các lớp con được chia sẻ dữ liệu và phương thức của lớp cha (non-private) được gọi là kế thừa.

<h3>Ví dụ trong ES5</h3>

**Trường hợp 1** là kế thừa thông qua constructor. Có thể hiểu là lớp con copy trực tiếp mã của constructor của lớp cha, sau đó "paste" vào constructor của chính nó theo các quy tắc nhất định. Ví dụ:

- Có 2 lớp như sau:
```javascript
function B(name){
	this.name = name;
}

function A(name, age){
	this.age = age;
}
```

Giả sử giờ lớp A thừa kế từ lớp B, đa số các bạn đều nghĩ code sẽ như sau:

```javascript
function B(name){
	this.name = name;
}

function A(name, age){
	B(name);
	this.age = age;
}
```

Chạy thử:
```javascript
new A('Robo Wonder', 30);
```
kết quả:
```A {age: 30}```
=> kế thừa không thành công =))

Theo cách trên chỉ khởi tạo class A. Để A có thể thừa kế B thì phải sửa lại như sau:

```javascript
function B(name){
	this.name = name;
}

function A(name, age){
	B.call(this, name);
	this.age = age;
}

new A('Robo Wonder', 30);
```
Kết quả:

```A {name: "Robo Wonder", age: 30}```


Như vậy, với trường hợp kế thừa constructor trong ES5 là cần phải dùng `B.call(context, value)` thì mới được.


**Trường hợp 2** kế thừa prototype. 

Trong bài nói về [tính đa hình](http://robowonder.com/2019/03/huong-doi-tuong-javascript-tinh-da-hinh-de-hieu.html "Hướng đối tượng Javascript - Tính đa hình (Siêu dễ hiểu)"){:target="_blank"} thì các bạn đã thấy ví dụ có sử dụng `prototype` rồi. Vậy làm sao để A có thể thừa kế prototype của B, thử cách như trường hợp 1 xem:

```javascript
function B(name){
	this.name = name;
}
B.prototype.print = function(){
	console.log(this.name);
}

function A(name, age){
	B.call(this, name);
	this.age = age;
}

var a = new A('Robo Wonder', 30);
a.print();
```

```Uncaught TypeError: a.print is not a function```

Như vậy là không thể vừa thừa kế contructor và prototype cùng lúc được. Chỉ vì trong ES5 chưa có định nghĩa class nên viết OOP mới chua vậy đây.

Để giải quyết vấn đề này thì cần phải gán prototype của B cho A nữa, cách làm như sau:

```javascript
function B(name){
	this.name = name;
}
B.prototype.print = function(){
	console.log(this.name);
}

function A(name, age){
	B.call(this, name);
	this.age = age;
}
A.prototype.__ proto__ = B.prototype; //kế thừa prototype

var a = new A('Robo Wonder', 30);
a.print();
'Robo Wonder' //kết quả
```

***ES5 thực hiện kế thừa đòi hỏi hai bước, bước đầu tiên: "copy and paste" constructor, bước thứ hai: gán prototype.***

<h3>Ví dụ trong ES6</h3>

ES6 về bản chất thì cũng như ES5 nhưng cách viết có thay đổi giống với các ngôn ngữ hướng đối tượng hơn:

```javascript
class B{
	constructor(name){
		this.name = name;
	}

	print(){
		console.log(this.name);
	}
}


class A extends B{
	constructor(name, age){
		super(name);
		this.age = age;
	}
}
```
***ES6 cũng đòi hỏi 2 bước: `extends` dùng để thừa kế prototype và hàm `super` dùng để "copy and paste" constructor***