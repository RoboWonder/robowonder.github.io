---
image: null
instantfeedback: true
description: Ví dụ ứng dụng TensorFlow, Hướng dẫn học TensorFlow
layout: post
title: Ví dụ ứng dung TensorFlow
category: TensorFlow
tags: TensorFlow, Machine Learning
keywords: Kiến thức cơ bản, TensorFlow, python, machine learning, ví dụ ứng dụng
---

Sau bài mở đầu về [API cơ bản của TensorFlow](/2019/04/tensorflow-bat-dau.html "API cơ bản của TensorFlow"). Bài sẽ là ví dụ về ứng dụng TensorFlow cũng như mô hình đào tạo cơ bản cho TensorFlow.

<h3>Dữ liệu thử nghiệm</h3>

Giả sử cho bảng dữ liệu dưới đây:

| Input		| Output	|
|-----------|-----------|
| 1			| 4.8 		|
| 2			| 8.5 		|
| 3			| 10.4 		|
| 6			| 21 		|
| 8			| 25.3 		|

Rất khó để tìm ra quy luật chung giữa input và output phải không? khó thế mới cần đến máy :D
Biểu diễn trên biểu đồ cho dễ nhìn:

<figure><img style="max-width: 500px" src="https://1.bp.blogspot.com/-7xTXcm6xEyc/XKYBx-1AbyI/AAAAAAAABy0/89jZx4AbEdwbiOvNBnfS0m-BN0JIp7OagCLcBGAs/s1600/Annotation%2B2019-04-04%2B200802.png" alt="ví dụ TensorFlow - Mô hình dữ liệu" title="ví dụ TensorFlow - Mô hình dữ liệu"></figure>

Chúng ta cần khái quát một mô hình chung dựa trên dữ liệu hiện có và chúng ta có thể dự đoán các giá trị đầu ra được tạo ra bởi các giá trị đầu vào khác. 
Như hình dưới đây, mô hình mà chúng ta chọn có thể là mô hình đường cong màu đỏ rất khó hiểu, thậm chí là không thể hiểu được hoặc chọn mô hình tuyến tính được biểu thị bằng đường màu xanh. Vẽ tay nên không chính xác lắm đâu nha :D

<figure><img style="max-width: 500px" src="https://2.bp.blogspot.com/-__0obVqOmXc/XKYDawGIpbI/AAAAAAAABzA/qvtgbyyQnzEkjnExuzyOHWY8Vfs3-oGXACLcBGAs/s1600/Annotation%2B2019-04-04%2B201505.png" alt="ví dụ TensorFlow - Mô hình dữ liệu trực quan" title="ví dụ TensorFlow - Mô hình dữ liệu trực quan"></figure>

Trong xác suất và lý thuyết thống kê, xác suất hai mô hình phù hợp với mô hình gốc là Giống nhau. Theo nguyên tắc [Occam's razor](https://en.wikipedia.org/wiki/Occam%27s_razor) thì chọn cái đơn giản nhất, chọn cái màu xanh. 
Nếu x là đầu vào, còn y là đầu ra ta có phương trình sau:

```
y = w * x + b
```

Đương nhiên đường màu xanh chưa phải là phương án cuối cùng, vì nếu thay tham số vào phương trình để tìm ra w và b thì sẽ có rất nhiều nghiệm, mỗi nghiệm tương ứng với đường thẳng tuyến tính khác nhau:

<figure><img style="max-width: 500px" src="https://1.bp.blogspot.com/-SE4npqjd83w/XKYGuvVQMgI/AAAAAAAABzM/FHljtRN6T_kFBXb-SZKy7KUi9zH366PngCLcBGAs/s1600/Annotation%2B2019-04-04%2B202911.png" alt="ví dụ TensorFlow - Mô hình dữ liệu trực quan" title="ví dụ TensorFlow - Mô hình dữ liệu trực quan"></figure>

Đến đây thì lung mung rồi, tưởng tìm ra phương trình là ngon, ai dè đẻ ra cả mớ đường. Bây giờ cần phải tìm ra mô hình hợp lý nhất và chính xác nhất, bằng cách thiết kế mô hình tổn thất như dưới đây, đường màu vàng là biểu thị sự khác biệt giữa giá trị tính toán của mô hình tuyến tính và giá trị đầu ra thực tế: 

<figure><img style="max-width: 500px" src="https://3.bp.blogspot.com/-Cl68Ch476YE/XKYH2yaaExI/AAAAAAAABzU/yhAnS0F7K7gir8P_CIV7u2GsUNjrxTAnwCLcBGAs/s1600/Annotation%2B2019-04-04%2B203402.png" alt="ví dụ TensorFlow - Mô hình tổn thất" title="ví dụ TensorFlow - Mô hình tổn thất"></figure>

Tổn thất được tính toán bằng phương trình sau:

```
loss=∑n=N(yn−y′n)2
```

Trong đó y' là sản lượng thực tế. Rõ ràng loss càng nhỏ thì mô hình càng chính xác.

<h3>Triển khai mô hình với TensorFlow</h3>

Sau một hồi rối não thì cũng tìm được mô hình tuyến tính và mô hình tổn thất, đoạn này ai chưa hiểu thì cà phê cà pháo giải thích thêm, chủ yếu là môn xác xuất thống kê thôi. Bây giờ áp dụng mô hình vào TensorFlow.

Trong mô hình tuyến tính  `y = w * x + b`, đầu vào `x` có thể được đại diện bởi một Tensor, chúng ta cần phải thay đổi liên tục `w` và `b` để tìm ra `loss` tương ứng nhỏ nhất

```python
import tensorflow as tf

# tạo biến w và b và khởi tạo giá trị ban đầu
w = tf.Variable([.1], dtype=tf.float32)
b = tf.Variable([-.1], dtype=tf.float32)

# tạo biến x để nhập đầu vào
x = tf.placeholder(tf.float32)

# dựng phương trình
linear_model = w*x + b

# tạo biến y để nhập đầu ra
y = tf.placeholder(tf.float32)

# dựng phương trình tổn thất
loss = tf.reduce_sum(tf.square(linear_model - y))

# chuẩn bị xúc
sess = tf.Session()
init = tf.global_variables_initializer()
sess.run(init)
```

Bây giờ nhập dữ liệu đầu vào và đầu ra để tính xem `loss` bằng bao nhiêu:

```python
print(sess.run(loss, {x: [1, 2, 3, 6, 8], y: [4.8, 8.5, 10.4, 21.0, 25.3]}))
```

Kết quả:

```python
>>>print(sess.run(loss, {x: [1, 2, 3, 6, 8], y: [4.8, 8.5, 10.4, 21.0, 25.3]}))
1223.05
```

vcl, thổn thất lớn quá. Đổi lại `w` và `b` để tìm số tối ưu hơn:

```python
fixW = tf.assign(W, [2.])
fixb = tf.assign(b, [1.])

sess.run([fixW, fixb])

print(sess.run(loss, {x: [1, 2, 3, 6, 8], y: [4.8, 8.5, 10.4, 21.0, 25.3]})
```

Kết quả:

```python
>>>print(sess.run(loss, {x: [1, 2, 3, 6, 8], y: [4.8, 8.5, 10.4, 21.0, 25.3]}))
159.94
```

Đỡ hơn rồi á, giờ cứ thử thay số cho tới khi nào tìm được loss nhỏ nhất là ok. Khi nào tìm được `w` và `b` ta chạy phương trình `y = w * x + b` như này để cho đầu ra tương ứng với đầu vào, nhớ thay số đầu vào nha:

```python
print(sess.run(linear_model, {x: [1, 2, 3, 6, 8]}))
```

Bài này đến đây thôi, bài sau sẽ học về cách để đào tạo cho TensorFlow nó thông minh hơn để tự tìm ra số tối ưu, vậy mới gọi là Machine Learning =))