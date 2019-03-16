---
image: null
instantfeedback: true
description: Hướng dẫn hướng đối tượng trong Javascript phần đa hình siêu dễ hiểu
layout: post
title: Hướng đối tượng Javascript - Tính đa hình (Siêu dễ hiểu)
category: Lập trình
tags: Javascrip, OOP
keywords: hướng đối tượng, lập trình, javascript, dễ hiểu
---

<h3>Tính đa hình là gì</h3>

Một phương thức hoạt động trên nhiều đối tượng khác nhau sẽ cho ra kết quả khác nhau.

<h3>Ví dụ không sử dụng đa hình</h3>

```javascript
function Dog(){
}

function Cat(){
}

let punch = (animal) => {
	if(animal instanceof Dog){
		console.log('ẳng ẳng');
	}
	else if(animal instanceof Cat){
		console.log('éo..éo..o..o');
	}
}

punch(new Dog());
'ẳng ẳng' // kết quả

punch(new Cat())
'éo..éo..o..o' // kết quả
```

Khi các con vật khác nhau bị "ăn đập" thì kêu khác nhau, và để xử lý xuất ra tiếng kêu tương ứng với con vật nào đó thì phải xử lý trong hàm "ăn đập" (punch). Cách này rất phức tạp nếu chương trình định nghĩa nhiều loài vật.

<h3>Ví dụ về đa hình</h3>

```javascript
function Dog(){

}
Dog.prototype.yell = function(){
	console.log('ẳng ẳng');
}


function Cat(){

}
Cat.prototype.yell = function(){
	console.log('éo..éo..o..o');
}


let punch = (animal) => {
	animal.yell();
}
```

Khi cài đặt đối tượng thì ta thêm phước thức `yell` (kêu) vào từng đối tượng, và hàm punch chỉ việc gọi phương thức `yell` này. Như vậy có thêm hàng trăm con vật nữa thì cách sử dụng (hàm punch) cũng không cần thay đổi.