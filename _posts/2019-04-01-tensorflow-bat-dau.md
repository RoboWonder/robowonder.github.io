---
image: null
instantfeedback: true
description: Hướng dẫn học TensorFlow cơ bản qua ví dụ
layout: post
title: TensorFlow - Kiến thức cơ bản
category: TensorFlow
tags: TensorFlow, Machine Learning
keywords: Kiến thức cơ bản, TensorFlow, python, machine learning
---

Bài viết này giới thiệu việc sử dụng API chính của TensorFlow thông qua ví dụ đơn giản. Mục đích của bài viết này là hướng dẫn những sinh viên mới làm quen với TensorFlow hoặc Machine Learning từ bước đầu tiên. Để dễ hiểu bài này thì bạn cần có những kiến thức sau:

	- Lập trình Python (TensorFlow cũng xài được Go, C#, C++)
	- Một số kiến ​​thức liên quan đến mảng và đại số tuyến tính
	- Tốt nhất là nên biết thêm cơ bản về Machine Learning (chưa có thì Google hay Bing gì tạm đê)

<h3>Tensor</h3>

Các tính toán cơ bản của TensorFlow dựa trên các "tensor" (vietsub là tenxơ), do đó cần nói qua một chút về khái niệm tenxơ này. Định nghĩa chi tiết thì rất phức tạp, khó nắm. Nên nói đại khái thì tenxơ được tựa như các vectơ vô hướng mà ta đã được học hồi còn trẻ. Chúng ta có thể hiểu đơn giản nó là một mảng nhiều chiều:

```python
3                                       # Vô hướng，shape=[]
[1., 2., 3.]                            # Mảng 1 chiều，shape=[3]
[[1., 2., 3.], [4., 5., 6.]]            # Mảng 2 chiều，shape=[2, 3]
[[[1., 2., 3.]], [[7., 8., 9.]]]        # Mảng 3 chiều，shape=[2, 1, 3]
```

Lớp Tensor của TensorFlow sẽ control các tenxơ này, lớp này có hai thuộc tính:

	- dtype là kiểu dữ liệu dùng trong Tensor: float32, int32, string...
	- Shape là Số lượng phần tử trong một mảng của mỗi thứ nguyên trong một mảng nhiều chiều được lưu trữ, chẳng hạn như hình dạng trong ví dụ trên

Xem khai báo tenxơ qua ví dụ sau:

```python
# Import thư viện tensorflow
import tensorflow as tf

# Tạo vecto vô hướng
t0 = tf.constant(3, dtype=tf.int32)

# Tạo mảng 1 chiều (Tensor bậc 1)
t1 = tf.constant([3., 4.1, 5.2], dtype=tf.float32)

# Tạo mảng 2 chiều (2x2) (Tensor bậc 2)
t2 = tf.constant([['Apple', 'Orange'], ['Potato', 'Tomato']], dtype=tf.string)

# Tạo mảng 3 chiều (2x3x1)  (Tensor bậc 3)
t3 = tf.constant([[[5], [6], [7]], [[4], [3], [2]]])

# In ra 3 cái đầu tiên
print(t0)
print(t1)
print(t2)
```

Kết quả như sau, chú ý shape nha:

```python
>>> print(t0)
Tensor("Const:0", shape=(), dtype=int32)
>>> print(t1)
Tensor("Const_1:0", shape=(3,), dtype=float32)
>>> print(t2)
Tensor("Const_2:0", shape=(2, 2), dtype=string)
>>> print(t3)
Tensor("Const_3:0", shape=(2, 3, 1), dtype=int32)
```

Cách in trên chỉ show ra được thuộc tính của tenxơ, muốn in giá trị của tenxơ thì cần phải chạy tenxơ đó. Cách chạy như sau:

```python
>>> sess = tf.Session()
>>> print(sess.run(t0))
3
>>> print(sess.run(t1))
[ 3.          4.0999999   5.19999981]
>>> print(sess.run(t2))
[[b'Apple' b'Orange']
 [b'Potato' b'Tomato']]
>>> print(sess.run(t3))
[[[5]
  [6]
  [7]]

 [[4]
  [3]
  [2]]]
>>> 
```

<h3>Biểu đồ dữ liệu (Dataflow Graph)</h3>

Luồng dữ liệu là một mô hình lập trình điện toán song song thường được sử dụng. Biểu đồ luồng dữ liệu là biểu đồ có hướng bao gồm các nút (nodes) và cạnh (edges):

	- Nodes: Đại diện cho các đơn vị tính toán và cũng có thể là điểm bắt đầu của đầu vào hoặc điểm cuối của đầu ra.
	- Edges: Thể hiện mối quan hệ đầu vào / đầu ra giữa các node.

Trong TensorFlow, mỗi node được đại diện bởi tenxơ, nghĩa là đầu vào/ra của mỗi node chính là tenxơ. Xem luồng tenxơ chạy trong hình dưới đây:

<figure><img src="https://3.bp.blogspot.com/-4EB2k3bh7fc/XKIWcDzSbHI/AAAAAAAABug/RhkfI7MM8xI_ez4XFmoq27V3_dxHRe1iQCLcBGAs/s400/20171212161708280.gif" alt="Bắt đầu TensorFlow - Luồng dữ liệu" title="Bắt đầu TensorFlow - Luồng dữ liệu"></figure>

Nhìn sơ đồ trên ta có thể thấy một số lợi thế của luồng dữ liệu trong TensorFlow như sau: 

	- Các node song song với nhau được kết nối với nhau, do đó hệ thống dễ dàng xác định các hoạt động được tính toán đồng thời.
	- Mỗi node được phân bổ trên các tài nguyên khác nhau (CPU, GPU, TPU, ...), thậm chí là trên các máy tính khác nhau và dữ liệu của mỗi node có thể gửi đến node tiếp theo.
	- Trình biên dịch XLA (Accelerated Linear Algebra) có thể tối ưu hóa theo biểu đồ luồng dữ liệu để tăng tốc độ hoạt động.
	- Thông tin biểu đồ dữ liệu sau khi biên dịch không phụ thuộc vào code, ví dụ biểu đồ tạo bởi python thì C++ hay C# vẫn lấy xài được.


<h3>Session</h3>

Session là một lớp trong code của TensorFlow được viết bằng C++, nhiệm vụ kết nối các máy đang chạy với C++ runtime. Để đảm bảo dữ liệu giữa các node không bị chậm trễ.

Ví dụ khi cần tính toán trên Python thì ta sử dụng thư viện NumPy, với những tính toán phức tạp cỡ như ma trận thì NumPy lại gửi data sang nhờ C/C++ tính dùm để bảo đảm tính chính xác. Như vậy việc gửi dữ liệu qua về sẽ làm mất thời gian hơn. Mặc dù thời gian bị mất không đáng kể, nhưng nếu node được phân bổ trên các máy hoặc các phần cứng khác nhau để cùng tính, thì dữ liệu gửi về không đồng bộ sẽ ảnh hưởng đến chương trình vì phải mất thời gian chờ.

Do dó dù ứng dụng TensorFlow bằng Python hay C++ thì việc tính toán cũng dựa trên C++.

<h3>Xây dựng biểu đồ tính toán</h3>

Trên đây là khái niệm về Tensor và Graph. Phần sau đây mô tả cách xây dựng một đồ thị với Tensor. 
Tensor có thể đại diện cho các điểm cuối đầu vào và đầu ra, và cũng có thể đại diện cho đơn vị tính toán. Đoạn mã sau đây tạo ra một Tensor thực hiện các hoạt động + trên hai Tensor:

```python
import tensorflow as tf

node1 = tf.constant(3.2)
node2 = tf.constant(4.8)

adder = node1 + node2

print(adder)

sess = tf.Session()
print(sess.run(adder))
```

Kết quả, 2 dòng tương ứng với 2 lệnh print ở trên:

```python
Tensor("add:0", shape=(), dtype=float32)
8.0
```

Trên chỉ là môt ví dụ nhỏ, các bạn nên đổi code để thực hiện các phép cộng trừ hay nhân chia gì đó với tenxơ phức tạp hơn, đa hướng hơn để nắm vững hơn nguyên lý của nó rồi bài sau chúng ta sẽ cùng thực hiện ứng dụng TensorFlow vào bài toán thực tế.