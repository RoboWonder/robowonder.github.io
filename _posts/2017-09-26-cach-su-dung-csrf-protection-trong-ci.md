---
image: https://4.bp.blogspot.com/-_dA-Vfq1q1E/WawpL-2WovI/AAAAAAAABk8/HRpIYBwUqy4KaNeFt6XasJxBsU1jSq2EQCLcBGAs/s400/codeigniter-csrf-security-token-ajax.png
instantfeedback: true
description: Cross Site Request Forgery, là lỗ hổng phổ biến nhất trong các trang web và ứng dụng web.
layout: post
title: Cách sử dụng CSRF Protection trong CodeIgniter
category: Lập trình
tags: CodeIgniter, Angular, Jquery
keywords: Angular, CodeIgniter, JavaScript, Jquery, PHP, csrf protection  
---

## CSRF là gì?

Cross Site Request Forgery, là lỗ hổng phổ biến nhất trong các trang web và ứng dụng web. Lỗ hổng này đã được phát hiện từ rất lâu nên tôi không đi vào chi tiết về nó mà chỉ nói về cách sử dụng trong framework CodeIgniter. Nếu bạn muốn biết thêm về nó thì đọc trên [wikipedia](https://en.wikipedia.org/wiki/Cross-site_request_forgery)

<figure><img src="https://4.bp.blogspot.com/-_dA-Vfq1q1E/WawpL-2WovI/AAAAAAAABk8/HRpIYBwUqy4KaNeFt6XasJxBsU1jSq2EQCLcBGAs/s400/codeigniter-csrf-security-token-ajax.png" alt="Cách sử dụng CSRF Protection trong CodeIgniter" title="Cách sử dụng CSRF Protection trong CodeIgniter"></figure>

Để kích hoạt CSRF Protect trong CodeIgniter, bạn vào trong file config tìm *$config['csrf_protection'] = FALSE;* và đổi giá trị lại là **TRUE**. Và thay các giá trị phía bên dưới theo ý bạn. Như vậy, sau mỗi lần request thì CI sẽ làm mới token và lưu vào cookie với tên bạn đã cấu hình *$config['csrf_cookie_name']*. 

Sau khi cấu hình bật csrf protect thì tất cả các form và ajax trong trang web sẽ không hoạt động. CI sẽ không sử lý dữ liệu được POST lên nếu không gửi kèm token này.

## Cách dùng trong view

Với các view có form, trong controller gọi view bạn cần phải lấy name và token trong lớp Security và truyền vào cho view, bằng cách gọi phương thức get_csrf_token_name() cho name và get_csrf_hash() cho token. Ví dụ:

```php
$csrf = array(
        'name' => $this->security->get_csrf_token_name(),
        'hash' => $this->security->get_csrf_hash()
);

$this->load->view('form', array('csrf'=>$csrf));
```

Sau đó trong form bạn thêm thẻ input này vào:

```html
<input type="hidden" name="<?=$csrf['name'];?>" value="<?=$csrf['hash'];?>" />
```

## Cách dùng với ajax jquery
Với ajax jquery, chúng ta sẽ bắt sự kiện beforeSend để thêm token vào trước khi data được gửi lên server. Để làm điều này đơn giản hơn thì sử dụng hàm ajaxSetup của jquery. Tất cả code gọi ajax đều sẽ lấy cấu hình từ ajaxSetup này.

Chúng ta sẽ lấy token được lưu trong cookie nên cần import thêm file jquery cookie vào:

```javascript
$.ajaxSetup({
  beforeSend: function(xhr, settings) {
    if (settings.data.indexOf('csrf_test_name') === -1) {
      settings.data += '&csrf_test_name=' + encodeURIComponent(Cookies.get('csrf_cookie_name'));
    }
  }
});
```


Nhớ thay csrf_test_name và csrf_cookie_name như đã cấu hình trong file config.php của CI nhé.

## Cách dùng với Angular

Với angular thì quá đơn giản, từ angular 1.2 đã mặc định hỗ trợ CSRF Protect, chỉ cần đặt csrf_cookie_name là X-Token là angular sẽ tự biết để lấy gửi lên server.