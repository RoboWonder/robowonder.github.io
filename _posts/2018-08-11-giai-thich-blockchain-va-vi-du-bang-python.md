---
image: https://1.bp.blogspot.com/-xghaY6Tuiw8/W25yH8Kj4TI/AAAAAAAABt8/b7uNE1cYhIE0qA7gqqmDpevHciBMNnUUQCLcBGAs/s1600/biometric_blockchain_bitcoin.jpg
instantfeedback: true
description: Blockchain là gì? Giải thích và ví dụ bằng python
layout: post
title: Blockchain là gì? Giải thích và ví dụ bằng python
category: Công nghệ
tags: Công nghệ
keywords: blockchain, python
---

Trong vài năm trở lại đây, blockchain đã trở thành thuật ngữ nổi tiếng mà không một người làm công nghệ nào không biết đến nó. Tuy nhiên, số người thật sự hiểu sâu về nó thì cũng rất hiếm, lang thang trên internet cũng có nhiều bài viết về blockchain nhưng quá mơ hồ, nhiều vấn đề chính không được rõ ràng. Bài viết này nhằm giải thích về blockchain một cách đơn giản nhất dựa trên hiểu biết của cá nhân và có ví dụ viết bằng python.

<h3>Blockchain là gì?</h3>

<figure><img src="https://1.bp.blogspot.com/-xghaY6Tuiw8/W25yH8Kj4TI/AAAAAAAABt8/b7uNE1cYhIE0qA7gqqmDpevHciBMNnUUQCLcBGAs/s1600/biometric_blockchain_bitcoin.jpg" alt="Blockchain là gì?" title="Blockchain là gì?"></figure>

Blockchain là một cuốn sổ cái ghi lại lịch sử của mọi giao dịch được phát sinh trên hệ thống, là giải pháp để duy trì chung một cơ sở dữ liệu đáng tin cậy thông qua phân cấp.

Lấy Bitcoin làm ví dụ, blockchain là một chuỗi (chain) bao gồm các khối (block) kết nối lần lượt như một chuỗi tuyến tính dài vô tận.

Block chia làm 2 loại là block khởi tạo và block thường. Block khởi tạo là block đầu tiên của một project blockchain, block thường đầu tiên sẽ dùng mã hash của block khởi tạo để làm khóa mã hóa nội dung lưu bên trong nó. Một block được tạo ra đều dựa vào mã hash của block trước đó để làm khóa mã hóa nội dung. Vì vậy khi blockchain đã được phát hành thì dữ liệu của nó không thể bị sửa đổi.

Vậy, Một block có những gì:
- Index: là số tuần tự từ 0-n, gọi là vị trí của block.
- Hash: Một chuỗi 256bit ngẫu nhiên, là chuỗi duy nhất của block.
- Previous hash: Là hash của chuỗi trước đó.
- Tempstamp: Là thời gian block được sinh ra.
- Difficulty: Độ khó của việc tạo ra block, độ khó càng cao thì việc tạo ra block mới càng khó.
- Nonce: Một số ngẫu nhiên dùng để tạo ra block tiếp theo.
- Data: Dữ liệu giao dịch cần được mã hóa (Chỉ có ở block thường)

<h3>Tạo block mới</h3>

Hiện tại, mọi người thường dùng khái niệm "mining" để nói về việc tạo block mới. Theo cá nhân tôi thì khái niệm đó không đúng, mọi người đã quá quen với các khái niệm của Bitcoin. Trong Bitcoin, khi các "miner" tạo thành công một block sẽ nhận được một phần thưởng nhất định bằng Bitcoin, nên số Bitcoin trong một thời điểm là tăng chậm và số Bitcoin là có giới hạn nhằm mục đích làm cho Bitcoin có giá, vì vậy việc tạo mới block trong Blockchain là rất khó và cần đến thiết bị "miner" có cấu hình khủng.

Nhưng trên thực tế việc tạo block mới rất dễ dàng và nhanh chóng, như thế thì khi ứng dụng vào thực tế như việc lưu lại các giao dịch của ngân hàng. Thì ngân hàng không cần phải sắm những dàn "miner" khủng giá vài chục đến trăm củ.

Quy trình tạo ra một block mới như sau, ví dụ A chuyển cho B một khoản tiền:
1. Một khối mới được tạo ra, bao gồm 7 thông tin như mục trên. Sau đó sẽ gửi thông báo cho tất cả những nơi đang lưu trữ chuỗi block.
2. Quá trình xác minh block là hợp lệ:
	- Kiểm tra số Index, quy tắc băm mã Hash có hợp lệ với chuỗi hiện tại.
	- Kiểm tra Previous Hash có khớp với mã Hash của block cuối cùng trong chuỗi.
	- Kiểm tra xem A có tiền và số tiền có đủ để chuyển cho B hay không.
3. Chấp nhận đưa block vào chuỗi nếu hợp lệ. Tất cả những nơi lưu trữ blockchain sẽ thêm block này thành block cuối của chuỗi.

<h3>Ưu - Nhược điểm của Blockchain</h3>

Không có gì là hoàn hảo cả, Blockchain cũng vậy. 

Ưu điểm của Blockchain thì ai cũng biết, chẳng hạn như bảo mật cao, không thể bị sửa đổi, phân cấp, vv, đã được mô tả rất rõ ràng và ca tụng đầy trên mạng, không cần phải chi tiết thêm nữa. 

Nhưng blockchain cũng có những hạn chế như:
- Độ trễ: blockchain phải xác minh và phân phối lần lượt block nên có độ trễ lớn.
- Tốn năng lượng: Tỉ lệ thuận với độ trễ khi blockchain đòi hỏi rất nhiều tính toán để tạo ra một block, và tính toán lại để xác minh block.

Blockchain càng dài, tương ứng với Difficulty thì càng đòi hỏi nhiều tính toán để tạo và xác minh block dẫn đến độ trễ càng lớn và càng tốn năng lượng.

<h3>Ví dụ bằng Python</h3>

Đầu tiên, tạo class Blockchain:

```python
class BlockChain:
    def __init__(self, initialHash):
        # init block chain
        self.chain = []

        # init miner
        self.miner = []
        for i in range(6):
            self.miner.append(Miner)

        # collect mine results
        self.results = []

        # generate GenesisBlock
        self.new_block(initialHash)
```

`chain` trong hàm `init` đại diện cho blockchain hiện tại, `miner` là các "thợ mỏ", `results` sẽ lưu trữ từng giai đoạn, `new_block` là phương thức tạo một block.

Phương thức trả về block cuối của chuỗi:

```python
@property
def last_block(self):
    if len(self.chain):
        return self.chain[-1]
    else:
        return None
```

Phương thức tạo ngẫu nhiên một thông báo giao dịch:

```python
def get_trans(self):
    return json.dumps({
        'sender': ''.join(random.sample(string.ascii_letters + string.digits, 8)),
        'recipient': ''.join(random.sample(string.ascii_letters + string.digits, 8)),
        'amount': random.randrange(1, 10000)
    })
```

Phương thức tạo block mới:

```python
def new_block(self, initialHash=None):
    if initialHash:
        # generate Genesis Block
        block = Block()
        block.index = 0
        block.nonce = random.randrange(0, 99999)
        block.previousHash = '0'
        block.difficulty = 0
        block.transactionData = self.get_trans()
        guess = f'{block.previousHash}{block.nonce}{block.transactionData}'.encode()
        block.hash = hashlib.sha256(guess).hexdigest()
        block.time = time()
        self.chain.append(block)
    else:
        for i in range(len(self.miner)):
            pm = MyThread(target=self.miner[i].mine,
                                  args=(self.miner[i],
                                        len(self.chain),
                                        self.last_block.get_block()['Hash'],
                                        self.get_trans()))
            pm.start()
            pm.join()
            self.results.append(pm.get_result())

        # show all blocks
        print("All blocks generated by miner:")
        for result in self.results:
            print(result[0].get_block())

        # get new block
        firstblock = self.results[0][0]
        mintime = Decimal(self.results[0][1])
        for i in range(1, len(self.results)):
            if Decimal(self.results[i][1]) < mintime:
                firstblock = self.results[i][0]
            else:
                continue
        self.chain.append(firstblock)
        self.results = []
```

**\*** Phương thức này có thể tạo block đầu tiên của chuỗi nếu không truyền tham số `initialHash`. Nếu tạo một khối bình thường, thì một số thông tin cơ bản sẽ được phân phối cho các "miner" để khai thác. Tôi đã thiết lập 6 miner và để công bằng, có tôi tạo ra 6 thread để các miner thực hiện khai thác cùng một lúc. Ở đây, tất cả các miner hoàn thành công việc và gửi kết quả và giờ làm việc tương ứng, tạo ra các khối thời gian ngắn nhất để được thêm vào blockchain làm khối chính xác. Về bản chất, miner nào tạo khối trước sẽ được ưu tiên.


Lớp Block:

```python
class Block:
    def __init__(self):
        self.index = None
        self.time = None
        self.difficulty = None
        self.nonce = None
        self.hash = None
        self.previousHash = None
        self.transactionData = None

    def get_block(self):
        return {
            'Index': self.index,
            'Time': self.time,
            'Difficulty': self.difficulty,
            'Hash': self.hash,
            'Nonce': self.nonce,
            'PreviousHash': self.previousHash,
            'TransactionData': self.transactionData
        }
```

Lớp Miner, trong lớp này chỉ cần phương thức mine và tạo mã hash là ok:

```python
class Miner:

    def mine(self, index, previousHash, transactionData):
        beginTime = time()

        block = Block()
        block.index = index
        block.previousHash = previousHash
        block.transactionData = transactionData
        block.difficulty, block.hash, block.nonce = self.generate_hash(previousHash, transactionData)
        block.time = time()
        endTime = time()

        return block, endTime - beginTime

    @staticmethod
    def generate_hash(previousHash, transactionData):
        difficulty = 0
        nonce = random.randrange(0, 99999)
        guess = f'{previousHash}{nonce}{transactionData}'.encode()
        myhash = hashlib.sha256(guess).hexdigest()
        while myhash[-1] != '0':
            difficulty += 1
            nonce += difficulty
            guess = f'{previousHash}{nonce}{transactionData}'.encode()
            myhash = hashlib.sha256(guess).hexdigest()
        return difficulty, myhash, nonce

```

Phương thức tạo mã hash thì mỗi project mỗi khác, tùy ông coder. Ở đây tôi viết kiểu đơn giản cho đỡ nặng máy thôi.

Oke, chạy thử và xem kết quả, sau đây là khối đầu tiên được tạo bởi 6 miner, có 6 khối được tạo, hãy để ý số Index:

```json
{
	"Index":1,
	"Time":1516268156.5971138,
	"Difficulty":5,
	"Hash":"c3ba406bad0d87f816f629830a15e2997638bfa230484c224e5470eaa24d8790",
	"Nonce":62372,
	"PreviousHash":"7532402844a1c130833a27600298d09a007d6124603cf44be9c05fcd5428c34a",
	"TransactionData":"{\"sender\": \"9o8UMDLe\", \"recipient\": \"qTOQu7kv\", \"amount\": 2746}"
}
```
```json
{
	"Index":1,
	"Time":1516268156.5981123,
	"Difficulty":5,
	"Hash":"8ff243885e9017296aa2ef1a611ef5b3927ddce818cb7255a04ff3228c982c60",
	"Nonce":67644,
	"PreviousHash":"7532402844a1c130833a27600298d09a007d6124603cf44be9c05fcd5428c34a",
	"TransactionData":"{\"sender\": \"kIqy1c8C\", \"recipient\": \"WSdK0EXh\", \"amount\": 9329}"
}

```
```json
{
	"Index":1,
	"Time":1516268156.5981123,
	"Difficulty":3,
	"Hash":"ff9716bf9379e2ab7a8640419e7c7b7c7329a5e6e1bbf83a1249f49d070ca8b0",
	"Nonce":37336,
	"PreviousHash":"7532402844a1c130833a27600298d09a007d6124603cf44be9c05fcd5428c34a",
	"TransactionData":"{\"sender\": \"vBwU0luH\", \"recipient\": \"d7o6cRCj\", \"amount\": 5628}"
}
```
```json
{
	"Index":1,
	"Time":1516268156.5981123,
	"Difficulty":3,
	"Hash":"3410c70c31f9bacbfcbd74d63f25f69f27d36075e2d44bddaa60bd72fa042e60",
	"Nonce":34617,
	"PreviousHash":"7532402844a1c130833a27600298d09a007d6124603cf44be9c05fcd5428c34a",
	"TransactionData":"{\"sender\": \"yzcNpBnh\", \"recipient\": \"vbIr7SKo\", \"amount\": 6387}"
}
```
```json
{
	"Index":1,
	"Time":1516268156.5981123,
	"Difficulty":27,
	"Hash":"91e3dc3ef1a151557a1edd837528410b916362bcfb77dbb14dc54c8929f5a0d0",
	"Nonce":49121,
	"PreviousHash":"7532402844a1c130833a27600298d09a007d6124603cf44be9c05fcd5428c34a",
	"TransactionData":"{\"sender\": \"p1MguhVz\", \"recipient\": \"gVSom4D3\", \"amount\": 7356}"
}
```

So sánh giá trị `Time` thì cái đầu tiên là nhanh nhất, và sẽ được chấp nhận vào chuỗi. 

Và đây là kết quả của chuỗi 6 block:

```json
[
	{
		"Index":0,
		"Time":1516268156.5971138,
		"Difficulty":0,
		"Hash":"7532402844a1c130833a27600298d09a007d6124603cf44be9c05fcd5428c34a",
		"Nonce":87688,
		"PreviousHash":"0",
		"TransactionData":"{\"sender\": \"OuVCmHbs\", \"recipient\": \"kFxbwSLc\", \"amount\": 503}"
	},
	{
		"Index":1,
		"Time":1516268156.5971138,
		"Difficulty":2,
		"Hash":"01f505a276e3f55a868d9ee18f70bcff75429e1de70f5ab59471a3551cc67a30",
		"Nonce":91554,
		"PreviousHash":"7532402844a1c130833a27600298d09a007d6124603cf44be9c05fcd5428c34a",
		"TransactionData":"{\"sender\": \"OY8z0Rrx\", \"recipient\": \"iSGFJsEm\", \"amount\": 8723}"
	},
	{
		"Index":2,
		"Time":1516268156.5991132,
		"Difficulty":4,
		"Hash":"098544436793881e8041c0c903c96c0055e16396113d73c63bc55e7ba78ec130",
		"Nonce":12875,
		"PreviousHash":"01f505a276e3f55a868d9ee18f70bcff75429e1de70f5ab59471a3551cc67a30",
		"TransactionData":"{\"sender\": \"HJZSX1hk\", \"recipient\": \"j82k51yY\", \"amount\": 3521}"
	},
	{
		"Index":3,
		"Time":1516268156.6001143,
		"Difficulty":27,
		"Hash":"7c10243223caf39bc5a6067de8d93f6ea46bad62c4a0fbcc0aa4e086585d8200",
		"Nonce":18663,
		"PreviousHash":"098544436793881e8041c0c903c96c0055e16396113d73c63bc55e7ba78ec130",
		"TransactionData":"{\"sender\": \"cJrGxN5R\", \"recipient\": \"wkZI8QCv\", \"amount\": 1224}"
	},
	{
		"Index":4,
		"Time":1516268156.601114,
		"Difficulty":3,
		"Hash":"60a099d3fe53e031800669fcc1d9b5ab6df1f80a40354135310a799892f1c3d0",
		"Nonce":51446,
		"PreviousHash":"7c10243223caf39bc5a6067de8d93f6ea46bad62c4a0fbcc0aa4e086585d8200",
		"TransactionData":"{\"sender\": \"nCNJoy52\", \"recipient\": \"kYBT9f65\", \"amount\": 3603}"
	},
	{
		"Index":5,
		"Time":1516268156.605163,
		"Difficulty":2,
		"Hash":"765f69163cf95584721015e3ce819c1980ce33752f8a4dea553d3bedd39f8920",
		"Nonce":31804,
		"PreviousHash":"60a099d3fe53e031800669fcc1d9b5ab6df1f80a40354135310a799892f1c3d0",
		"TransactionData":"{\"sender\": \"FqOkiTEu\", \"recipient\": \"y9EDcSYA\", \"amount\": 4185}"
	}
]
```

Ví dụ về Blockchain đến đây là kết thúc. Blockchain là một xu hướng đang phát triển mạnh mẽ hiện tại cùng với AI, hy vọng sự nghiệp của các lập trình viên sẽ thăng hoa hơn với những xu hướng này. Cảm ơn các bạn đã đọc bài, cá nhân tôi cũng có hiểu biết giới hạn nên mong các bạn bỏ qua những thiếu sót. Sau đây là toàn bộ code ví dụ:

```python
import hashlib
import random
import string
import json
import threading
from decimal import Decimal
from time import time


class MyThread(threading.Thread):

    def __init__(self, target, args=()):
        super(MyThread, self).__init__()
        self.func = target
        self.args = args

    def run(self):
        self.result = self.func(*self.args)

    def get_result(self):
        try:
            return self.result
        except Exception:
            return None


class BlockChain:
    def __init__(self, initialHash):
        # init block chain
        self.chain = []

        # init miner
        self.miner = []
        for i in range(6):
            self.miner.append(Miner)

        # collect mine results
        self.results = []

        # generate GenesisBlock
        self.new_block(initialHash)

    @property
    def last_block(self):
        if len(self.chain):
            return self.chain[-1]
        else:
            return None

    def get_trans(self):
        return json.dumps({
            'sender': ''.join(random.sample(string.ascii_letters + string.digits, 8)),
            'recipient': ''.join(random.sample(string.ascii_letters + string.digits, 8)),
            'amount': random.randrange(1, 10000)
        })

    def new_block(self, initialHash=None):
        if initialHash:
            # generate Genesis Block
            block = Block()
            block.index = 0
            block.nonce = random.randrange(0, 99999)
            block.previousHash = '0'
            block.difficulty = 0
            block.transactionData = self.get_trans()
            guess = f'{block.previousHash}{block.nonce}{block.transactionData}'.encode()
            block.hash = hashlib.sha256(guess).hexdigest()
            block.time = time()
            self.chain.append(block)
        else:
            for i in range(len(self.miner)):
                pm = MyThread(target=self.miner[i].mine,
                                      args=(self.miner[i],
                                            len(self.chain),
                                            self.last_block.get_block()['Hash'],
                                            self.get_trans()))
                pm.start()
                pm.join()
                self.results.append(pm.get_result())

            # show all blocks
            print("All blocks generated by miner:")
            for result in self.results:
                print(result[0].get_block())

            # get new block
            firstblock = self.results[0][0]
            mintime = Decimal(self.results[0][1])
            for i in range(1, len(self.results)):
                if Decimal(self.results[i][1]) < mintime:
                    firstblock = self.results[i][0]
                else:
                    continue
            self.chain.append(firstblock)
            self.results = []

    def show_chain(self):
        print('This is mine first block chain!')
        for block in self.chain:
            print(block.get_block())


class Block:
    def __init__(self):
        self.index = None
        self.time = None
        self.difficulty = None
        self.nonce = None
        self.hash = None
        self.previousHash = None
        self.transactionData = None

    def get_block(self):
        return {
            'Index': self.index,
            'Time': self.time,
            'Difficulty': self.difficulty,
            'Hash': self.hash,
            'Nonce': self.nonce,
            'PreviousHash': self.previousHash,
            'TransactionData': self.transactionData
        }


class Miner:

    def mine(self, index, previousHash, transactionData):
        beginTime = time()

        block = Block()
        block.index = index
        block.previousHash = previousHash
        block.transactionData = transactionData
        block.difficulty, block.hash, block.nonce = self.generate_hash(previousHash, transactionData)
        block.time = time()
        endTime = time()

        return block, endTime - beginTime

    @staticmethod
    def generate_hash(previousHash, transactionData):
        difficulty = 0
        nonce = random.randrange(0, 99999)
        guess = f'{previousHash}{nonce}{transactionData}'.encode()
        myhash = hashlib.sha256(guess).hexdigest()
        while myhash[-1] != '0':
            difficulty += 1
            nonce += difficulty
            guess = f'{previousHash}{nonce}{transactionData}'.encode()
            myhash = hashlib.sha256(guess).hexdigest()
        return difficulty, myhash, nonce


if __name__ == '__main__':
    chain = BlockChain(1)
    length = 5
    for i in range(length):
        chain.new_block()
    chain.show_chain()
```