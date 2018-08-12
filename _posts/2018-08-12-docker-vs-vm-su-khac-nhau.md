---
image: https://msdnshared.blob.core.windows.net/media/2017/10/docker.png
instantfeedback: true
description: Docker vs VM - Sự khác nhau giữa container và ảo hóa
layout: post
title: Docker vs VM - Sự khác nhau giữa container và ảo hóa
category: Công nghệ
tags: Công nghệ
keywords: docker, vitual machine, su khac nhau
---

khi nói đến cơ sở hạ tầng đám mây máy ảo đã là tiêu chuẩn vì có nhiều lợi thế như dễ cài đặt và quản lý tập trung, phần cứng ảo hóa hoàn toàn và tách biệt với nhau. Tuy nhiên, máy ảo có nhược điểm là quá cồng kềnh và tốn nhiều tài nguyên. Nếu có một giải pháp thay thế thì đó chính là Docker.

<figure><img src="https://msdnshared.blob.core.windows.net/media/2017/10/docker.png" alt="Các khái niệm cơ bản Docker" title="Các khái niệm cơ bản Docker"></figure>

<h3>Máy ảo (Virtual Machine) là gì?</h3>

Máy ảo (Virtual machine) là mô phỏng của một hệ thống máy tính, hiểu đơn giản, máy ảo có thể chạy bất kỳ phần mềm nào chạy được trên máy thực. Phần cứng của máy ảo được chia sẽ bởi hệ thống máy chủ chứa nó. Mỗi máy ảo yêu cầu có hệ điều hành của riêng nó. Kể từ khi ra đời, máy ảo được tiếp nhận rộng rãi và có độ phủ lớn vì giá cả phải chăng. Các Data Center sử dụng nó để giảm chi phí và tăng hiệu quả sử dụng máy chủ.

Lợi ích của máy chủ ảo là hệ điều hành chạy trên nó đáp ứng đủ cho phần mềm như một máy thực, các máy ảo tách biệt hoàn toàn với nhau nên bảo mật tốt hơn.

Những máy ảo phổ biến hiện nay là VMware, Virtualbox, Kvm và Hyper-v (Microsoft).

<h3>Container là gì?</h3>

Công nghệ Container được dẫn đầu bởi Docker, là vùng chứa để chạy các ứng dụng. Được sinh ra để giải quyết vấn đề ứng dụng trên đám mây lai (Hyper-Cloud). Container không ảo hóa máy tính, thay vào đó ứng dụng sẽ chạy trực tiếp trên phần cứng của máy thực, nhưng dữ liệu và ứng dụng chỉ được truy cập từ bên trong Container. 

Ưu điểm của Container nhẹ hơn máy ảo vì không cần tài nguyên cho hệ điều hành ảo. Giảm đáng kể việc sử dụng dung lượng của máy chủ vật lý. Chỉ mất vài giây để start một Container so với vài phút của máy ảo.

Hiện nay có 2 công nghệ Container phổ biến là Docker Container và Linux Container. 

Linux Container là một dạng phân cấp của hệ điều hành Linux. Nôm na là có nhiều hệ điều hành Linux được cô lập với nhau và chạy trên hệ điều hành Linux thực.

Container làm làm giảm thiểu chi phí quản lý CNTT, nếu như trước đây một máy chủ vật lý chỉ chạy được dưới 10 máy ảo thì nay có thể chạy hàng chục, thậm chí là hàng trăm Container, nhờ vào dung lượng của Image container rất nhỏ vì không chứa hệ điều hành. 

<h3>Sự khác nhau giữa Container và máy ảo (Virtual Machine)</h3>

- Container chạy trực tiếp trên hệ điều hành thực và phần cứng vật lý của máy chủ. Trong khi máy ảo cần hệ điều hành của chính nó mới có thể hoạt động. Nếu bạn sử nhiều phần mềm chạy được trên cùng hệ điều hành thì Container là giải pháp tốt. Tuy nhiên, các phần mềm chạy trên các hệ điều hành khác nhau thì phải sử dụng máy ảo. Vì máy ảo cần có hệ điều hành riêng và hệ điều hành có thể thuộc bất kỳ loại nào.
- Container phụ thuộc vào độ bảo mật của máy chủ vật lý, nếu một phần mềm trong Container bị hack thì hacker có thể hack luôn cả máy chủ; Máy chủ ảo thì tách biết hoàn toàn bởi hệ điều hành riêng nên trong trường hợp này chỉ mình máy ảo đó bị hack. Phần còn lại của hệ thống vấn được an toàn.
- Các Container có thể được di chuyển giữa các môi trường khác nhau mà không lo vấn đề tương thích như máy ảo.

Tóm lại có thể nói các Container như những người con trong một nhà, môi trường, văn hóa, và mức sống giữa mỗi người là như nhau. Còn các máy ảo thì như từng ngôi nhà riêng biệt, không phụ thuộc nhau, phát triển theo cách riêng, đặc biệt, nhà này cháy nhà kia vẫn còn.

Số đông hiện nay nghĩ rằng Container hiệu quả hơn máy ảo. Nhưng cần phải nói là mục đích của từng công nghệ là khác nhau, với lợi ích, ưu nhược điểm của từng công nghệ. Nên nói Container hiệu quả hơn máy ảo là sai lầm. Tùy vào mục đích của dự án mà lựa chọn công nghệ phù hợp./