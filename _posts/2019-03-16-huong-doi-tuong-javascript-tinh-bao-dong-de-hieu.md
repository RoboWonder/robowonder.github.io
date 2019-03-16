---
image: null
instantfeedback: true
description: Hướng dẫn hướng đối tượng trong Javascript phần đóng gói siêu dễ hiểu
layout: post
title: Hướng đối tượng Javascript - Tính bao đóng (Siêu dễ hiểu)
category: Lập trình
tags: Javascript, OOP
keywords: hướng đối tượng, lập trình, javascript, dễ hiểu
---

<h3>Tính bao đóng là gì</h3>

Giả sử một lớp có 2 đối tượng, một đối tượng cho có thuộc tính public và một đối tượng là private - chỉ cho phép truy cập nội bộ. Thì khi được khởi tạo từ đối tượng bên ngoài lớp, người dùng chỉ có thể thao tác trên đối tượng public.

<h3>Ví dụ trên ES5</h3>

```javascript
function Member(name){
	var _age = 30; //private
	this.name = name;
	this.getAge = function(){
		console.log(_age);
	}
}
```

Chạy thử:

```javascript
var member = new Member('Robo Wonder');
console.log(member);
```

Kết quả:

```Member {name: "Robo Wonder", getAge: ƒ}```

Thử truy cập thuộc tính private:

```javascript
_age in member;
```
```Error: Uncaught ReferenceError: _age is not defined```

```javascript
console.log(member.getAge());
30 //ket qua
```


<h3>Ví dụ trong ES6</h3>

Về bản chất thì chả khác gì nhau, nhưng cách viết thì lại khác:

```javascript
class Member{
	constructor(name){
		this.name = name;
		this.getYearOld = function(){
			console.log(_yearOld);
		}
	}
}
```

Cách triển khai thì như thế, còn chạy thử thì kết quả như ES5 nhé.