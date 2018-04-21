---
image: https://3.bp.blogspot.com/-CPe3_HPHM3I/WtrPQWE6KMI/AAAAAAAABr8/yC1b6nnNszcWyeaG9RPH9zB2iGWD-0LJQCLcBGAs/s640/serverless.jpg
instantfeedback: true
description: Giới thiệu và hướng dẫn sử dụng framework serverless, serverless hello word
layout: post
title: Hướng dẫn Serverless - Hello word
category: Serverless
tags: Serverless, hello word
keywords: Serverless, hello word, hướng dẫn
---

**Serverless giúp xây dựng các ứng dụng từ các dịch vụ đám mây, chẳng hạn như lưu trữ, tính toán và phân quyền**. Nhiệm vụ của lập trình viên là học cách kết hợp nhiều dịch vụ đám mây khác nhau như AWS Lambda, Google cloud function hay Azure function.

<figure><img src="https://3.bp.blogspot.com/-CPe3_HPHM3I/WtrPQWE6KMI/AAAAAAAABr8/yC1b6nnNszcWyeaG9RPH9zB2iGWD-0LJQCLcBGAs/s640/serverless.jpg" alt="Giới thiệu và hướng dẫn sử dụng framework serverless" title="Giới thiệu và hướng dẫn sử dụng framework serverless"></figure>

## Serverless framework

Việc viết serverless với AWS Lambda thật sự là rất khó mà mất thời gian với người mới, nên để dễ dàng hơn chúng ta nên dùng framework có sẵn là Serverless trên github [https://github.com/serverless/serverless](https://github.com/serverless/serverless).

Trước khi bắt đầu thì những thứ bạn cần có ngoài máy tính ra thì còn phải có một tài khoản AWS. AWS cho dùng thử miễn phí Lambda 1 năm, tha hồ xài. Nhưng để kích hoạt được thì cần có thẻ visa.

## Cài đặt Serverless framework

Nếu bạn xài `npm` thì dùng lệnh:

```
npm install -g serverless
```

Hoặc

```
yarn global add serverless
```

nếu xài yarn.

## Cấu hình đến AWS Lambda

1. Đăng nhập vào tài khoản AWS của bạn và nhập thông tin IAM (ví dụ: Identity & Access Management). 
2. Vào User => Add user, nhập tên user và chọn "Select AWS Access Type", cuối cùng là tích vào Programmatic Access.
3. Nhấn nut Next sau đó chọn "Append existing policy directly" và AdministratorAccess, rồi nhấn "Create user".

***Vì user này được cấp quyền Admin nên tuyệt đối không để lộ key nhé***

Sau khi tạo user xong thì sẽ được cấp một cặp Key ID và Key Secret, lưu nó lại. Sau đó thay vào các câu lệnh dưới đây rồi chạy nó trong terminal:

```
export AWS_ACCESS_KEY_ID=<your-key-here>
export AWS_SECRET_ACCESS_KEY=<your-secret-key-here>

serverless deploy
```

Lúc này cấu hình sẽ được lưu trong `~/.aws/credentials`

## Tạo Hello word service

Chạy lệnh

```
serverless create --template aws-nodejs --path hello-world
```

Và đây là kết quả:

```
Serverless: Generating boilerplate...
Serverless: Generating boilerplate in "/Users/robowonder/serverless-guide/hello-world"
 _______                             __
|   _   .-----.----.--.--.-----.----|  .-----.-----.-----.
|   |___|  -__|   _|  |  |  -__|   _|  |  -__|__ --|__ --|
|____   |_____|__|  \___/|_____|__| |__|_____|_____|_____|
|   |   |             The Serverless Application Framework
|       |                           serverless.com, v1.23.0
 -------'

Serverless: Successfully generated boilerplate for template: "aws-nodejs" (play-env)
```

Trong thư mục hello-word tạo 2 file `handler.js` và `serverless.yml`.

Copy đoạn code sau vào file handler.js:

```
'use strict';

module.exports.hello = (event, context, callback) => {
  const response = {
    statusCode: 200,
    body: JSON.stringify({
      message: 'Go Serverless v1.0! Your function executed successfully!',
      input: event,
    }),
  };

  callback(null, response);
};
```

Và file serverless.yml:

```
service: hello-world

provider:
	name: aws
	runtime: nodejs6.10

functions:
	hello:
    	handler: handler.hello
```


## Triển khai

Chạy lệnh deploy:

```
serverless deploy -v
```

Và ngồi chờ, terminal sẽ log từng bước được thực hiện tương tự như sau nếu không có lỗi:

```
Serverless: Packaging service...
Serverless: Excluding development dependencies...
Serverless: Uploading CloudFormation file to S3...
Serverless: Uploading artifacts...
Serverless: Uploading service .zip file to S3 (409 B)...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
CloudFormation - UPDATE_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-dev
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - HelloLogGroup
CloudFormation - CREATE_COMPLETE - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - HelloLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - HelloLambdaFunction
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - HelloLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloLambdaVersionPSzzisjnTvvYknuXwQOlAvdkQZ67qXYSvgoAi9T8W0
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloLambdaVersionPSzzisjnTvvYknuXwQOlAvdkQZ67qXYSvgoAi9T8W0
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - HelloLambdaVersionPSzzisjnTvvYknuXwQOlAvdkQZ67qXYSvgoAi9T8W0
CloudFormation - UPDATE_COMPLETE_CLEANUP_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-dev
CloudFormation - UPDATE_COMPLETE - AWS::CloudFormation::Stack - hello-world-dev
Serverless: Stack update finished...
Service Information
service: hello-world
stage: dev
region: us-east-1
stack: hello-world-dev
api keys:
  	None
endpoints:
  	None
functions:
  	hello: hello-world-dev-hello

Stack Outputs
HelloLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:706605665335:function:hello-world-dev-hello:1
ServerlessDeploymentBucketName: hello-world-dev-serverlessdeploymentbucket-bk066p5c9zgl
```

Sau khi chạy xong thì cần test thử xem service có được deploy thành công hay không bằng cách bắn message lên server và chờ response:

```
serverless invoke -f hello -l
```

Nêu kết quả trả về như dưới đây thì code đã ok rồi nhé:

```
{
    "statusCode": 200,
    "body": "{\"message\":\"Go Serverless v1.0! Your function executed successfully!\",\"input\":{}}"
}
--------------------------------------------------------------------
START RequestId: 041138f9-bc81-11e7-aa63-0dbab83f773d Version: $LATEST
END RequestId: 041138f9-bc81-11e7-aa63-0dbab83f773d
REPORT RequestId: 041138f9-bc81-11e7-aa63-0dbab83f773d  Duration: 2.49 ms   Billed Duration: 100 ms     Memory Size: 1024 MB    Max Memory Used: 20 MB
```

Vậy là xong service hello word, nó sẽ luôn chạy trên server để lắng nghe liên tục, để tiết kiệm chi phí vì bài này chỉ test chơi thì nên xóa nó đi sau khi test xong bằng lệnh ```serverless remove```.
