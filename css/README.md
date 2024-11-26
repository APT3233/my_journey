# CSS CHEATSHEET

## Background
1. <code>Background</code>
    - Thêm màu nền vào element
        ```CSS
        background-color: red;
        ```
1. <code>background-clip</code>
    - Xác định phạm vi được thiết lập màu nền của phần tử (Áp dụng cho background là màu sắc)
        ```CSS
        background-clip: border-box
        ```
    - **border-box**: Mặc định. Đổ màu từ content cho đến hết border.
    - **padding-box**: Đổ màu từ content cho đến hết padding.
    - **content-box**: Chỉ đổ màu phần content
    
2. <code>background-image</cpde>
    - Nền là hình ảnh hoặc màu gradient.
    ```CSS
    background-image: url("path");
    ```
3. <code>background-size:</code>
    - Kích thước của background
    ```CSS
    background-size: (px,%,..);
    ```
    - **contain**: sẽ co dãn hình ảnh để hình ảnh nằm trọn trong khung element, hình ảnh không bị vỡ.
    - **cover**: kéo dãn hình ảnh sao cho vừa với khung, cắt bỏ đi những phần ảnh thừa để hình ảnh không bị vỡ.
4. <code>background-repeat</code>
    - Nền có được lặp lại hay không.
    ```CSS
    background-repeat: no-repeat;
    ```
    - **no-repeat**:  Không lặp lại ảnh
	- **repeat-x**:   Lặp theo trục ngang
	- **repeat-y**:   Lặp theo trục dọc
5. <code>background-position</code>
    - Vị trí hình nền so với element. Có các giá trị: top, left, right, bottom, center.
    ```CSS
    background-position: top left; 
    ```
6. <code>background-attachment</code>
    - Nền sẽ được cuộn hoặc cố định.
    ```CSS
    background-attachment: fixed;
    ```
7. <code>background-origin</code>
    - Giống background-clip, nhưng blackground-clip là dành cho nền là màu sắc, còn background-origin là dùng cho nền  ảnh.
    ```CSS
    background-origin: content-box;
    ```
    - **content-box**: background chỉ chiếm phần content.
    - **padding-box**: background chiếm phần content và padding.
    - **border-box**: background chiếm phần content, padding và border.
8. <code>background</code>
    - Cách viết ngắn
    ```CSS
    background: #ffffff url("hinh-anh.png") no-repeat top right;
    ```
## Text
1. <code>text-align</code>
    - Dùng để can lề ngang của văn bản
    ```CSS
    text-align: center;
    ```
2. <code>text-transform</code>
    - Thuộc tính text-transform được sử dụng để chỉ định chữ hoa và chữ thường trong văn bản.
    ```CSS
    text-transform: uppercase;
    ```
    - **text-transform: uppercase;** // VIẾT CHỮ HOA
    - **text-transform: lowercase;**   // viết chữ thường
    - **text-transform: capitalize;**  // viết hoa chữ cái đầu

## List
1. <code>list-style-type</code>
    ```CSS
    list-style-type: disc;              /* Mặc định: Hình tròn đen */
    list-style-type: circle;            /* Hình tròn rỗng */
    list-style-type: square;            /* Hình vuông */
    list-style-type: disclosure-closed; /* Tam giác trỏ phải */
    list-style-type: none;              /* Không hiển thị */
    list-style-type: upper-roman;       /* Số La Mã: I, II, III */
    list-style-type: lower-alpha;       /* Chữ cái: a, b, c */
    ```


## Display
1. <code>display</code>
    ```CSS
    display: inline;        /* Không đặt width/height, margin/padding trên dưới */
    display: block;         /* Chiếm toàn hàng, cho phép width/height, margin/padding */
    display: inline-block;  /* Không chiếm hàng mới, cho phép width/height, margin/padding */
    display: none;          /* Ẩn element */
    ```

2. <code>visiblity</code>
    ```CSS
    visibility: hidden;     /* Ẩn nhưng vẫn chiếm một khoảng trống */
    visibility: visible;    /* Hiển thị. mặc định. */
    ```
3. <code>position</code>
    ```CSS
    position: static;   /* Mặc định, không ảnh hưởng bởi top, right, bottom, left */
    position: relative; /* Tương đối vị trí ban đầu, dùng được top, right, bottom, left */
    position: absolute; /* Tuyệt đối so với thành phần bao ngoài hoặc viewport */
    position: fixed;    /* Cố định trong viewport, không thay đổi khi cuộn trang */
    position: sticky;   /* Kết hợp relative và fixed, cố định khi cuộn đến vị trí */
    ```
4. <code>overflow</code>
    ```CSS
    overflow: visible; /* Mặc định, nội dung tràn ra ngoài box */
    overflow: hidden;  /* Nội dung tràn bị ẩn */
    overflow: scroll;  /* Luôn hiển thị thanh cuộn ngang và dọc */
    overflow: auto;    /* Thanh cuộn tự động hiển thị nếu cần */
    ```
5. <code>opacity<code>
- Độ mờ
    ```CSS
    opacity: 0.6; /* Element sẽ mờ đi 40% */
    ```
## Pseudo-class
1. **Pseudo-class selectors**
- Dùng để xác định trạng thái đặc biệt của 1 element
- **Cú pháp**:
    ```CSS
    selector:pseudo-class{
        property: value;
    }
    ```
- **Option**:
    - `:link`: Áp dụng cho liên kết chưa truy cập (chỉ thẻ `<a>`).
    - `:visited`: Áp dụng cho liên kết đã truy cập (chỉ thẻ `<a>`).
    - `:hover`: Khi di chuột qua phần tử.
    - `:active`: Khi phần tử được click (áp dụng cho tất cả thẻ).
    - `:first-child`: Áp dụng cho phần tử đầu tiên.
    - `:last-child`: Áp dụng cho phần tử cuối cùng.
    - `:nth-child(n)`: Chọn phần tử thứ `n` (even, odd, số, biểu thức `an + b`).
2. **Pseudo-elements Selectors**
- Dùng để tạo phần tử giả mà không cần tạo phần tử thật.
- **Cú pháp**:
    ```CSS
    selector::pseudo-element {
        property: value;
    }
    ```
- **Option**: 
    - `:link`: Chọn liên kết chưa truy cập (chỉ áp dụng cho thẻ `<a>`).
    - `:visited`: Chọn liên kết đã được truy cập (chỉ áp dụng cho thẻ `<a>`).
    - `:hover`: Chọn khi chuột di chuyển qua phần tử.
    - `:active`: Chọn khi phần tử được click.
    - `:first-child`: Chọn phần tử con đầu tiên.
    - `:last-child`: Chọn phần tử con cuối cùng.
    - `:nth-child(n)`: Chọn phần tử con thứ `n` (chẵn, lẻ, hoặc biểu thức `an + b`).

## Math
1. **Unit**
- Các đơn vị đo lường trong CSS:
    ```CSS
    %:    Giá trị tương đối so với phần tử cha.
    rem:  Giá trị tương đối với font-size của thẻ gốc (`<html>`).
    em:   Giá trị tương đối với font-size của phần tử cha.
    vw:   1% chiều rộng của viewport (cửa sổ trình duyệt).
    vh:   1% chiều cao của viewport.
    ex:   Chiều cao của chữ "x" (in thường) theo font hiện tại.
    ch:   Chiều rộng của chữ "0" theo font hiện tại.
    ```
2. **Calc**
    ```CSS
    width: calc(100% - 100px);
    ```
3. **max/min**
    ```CSS
    width: max(50%, 300px);
    height: min(50%, 500px);
    ```

## Variables
- Create variables
    ```CSS
    :root {
        --ten-bien: giá trị;
    }
    ```
- Use
    ```CSS
    var(--ten-bien);
    ```
- Exeample:
    ```CSS
    root {
        --gray: #333333;
        --white: #ffffff;
    }
    body {
        color: var(--gray);
        background-color: var(--white);
    }
    ```