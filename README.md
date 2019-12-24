Hướng dẫn tự động chèn link vào file ảnh Wordpress, để khi click vào ảnh nó ra ảnh luôn, tiện cho phóng to, hoặc gắn Fluidbox cho tiện.

Hướng suy nghĩ: Tận dụng Shortcode Caption của Wordpress để chèn

=> Tìm phần code: Nó nằm trong wp-includes/media.php

Chú ý dòng 1734 hoặc gần gần đó =)))

Có if ($html5) {
...

Chỉ cần chỉnh sửa chút chỗ này là xong:

'<figure %s%s%sclass="%s">%s%s</figure>',

thì chuyển thành '<figure %s%s%sclass="%s"><a href="%s">%s</a>%s</figure>',
và

      $id,
			$describedby,
			$style,
			esc_attr( $class ),
			wp_get_attachment_url( (int) filter_var($atts['id'], FILTER_SANITIZE_NUMBER_INT)), // thêm dòng này say esc_attr( $class ),
      
______________

Tương tự, sửa ở dòng 1751

'<div %s%sclass="%s">%s%s</div>',

thành '<div %s%sclass="%s"><a href="%s">%s</a>%s</div>',


và thêm cái này như trên: wp_get_attachment_url( (int) filter_var($atts['id'], FILTER_SANITIZE_NUMBER_INT)),

Ổn luôn, tuy là phải sửa core của Wordpress nhưng nó tiện, nhanh =_=, không phải nghiên cứu code nhiều. Sửa ngay và dùng luôn.

Mình sẽ sửa trong blog bán đá quý của mình: https://daquyanan.com. Ghé thăm xem có gì hay ho nhé.
      
