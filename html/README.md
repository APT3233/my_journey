# HTML CHEATSHEET

## Tag

1.  <code>Link</code>
    ```html
    <a href="url">Text</a>
    ```

    - **target**: thuộc tính xác định nơi mà tài liệu được mở.
      - `_self`: Mặc định. Mở tài liệu ở tab hiện tại.
      - `_blank`: Mở tài liệu trong tab mới.
    - **title**: Thông tin bổ sung về một element.

2.  <code>Img</code>
    ```html
    <img src=“duong-dan-hinh-anh.jpg" alt=“Mô tả hình ảnh">
    ```
    - **src** (source): Chèn đường dẫn ảnh
    - **alt** (alternate): Văn bản thay thế cho hình ảnh khi đường dẫn ảnh bị lỗi.
3.  <code>Video</code>
    ```html
    <video width="320" height="240" controls>
      <source src=“link-video.mp4" type="video/mp4">
    </video>
    ```
    - **width/height**: Chiều rộng và chiều cao của video. Nếu không để width/height thì web có thể bị nhấp nháy trong khi tải video.
    - **controls**: Thuộc tính điều khiển, như là bật, tạm dừng, âm lượng
    - **loop**: Lặp lại video
    - **src**: Đường dẫn video
    - **type**: Kiểu video (mp4, ogg, webm)
    - **autoplay**: Tự động phát video
    - **muted**: Tắt tiếng
4.  <code>Audio</code>
    ```html
    <audio controls><source src=“link-audio.mp3" type="audio/mpeg"></audio>
    ```
    - **controls**: Thuộc tính điều khiển, như là bật, tạm dừng, âm lượng
    - **loop**: Lặp lại audio
    - **src**: Đường dẫn audio
    - **type**: Kiểu video (Ví dụ: mpeg - là mp3, ogg, webm, wav)
    - **autoplay**: Tự động phát audio
    - **muted**: Tắt tiếng
5. <code>Table</code>:
    ```html
    <table>
        <thead>
            <tr>
                <th>STT</th>
                <th>Họ tên</th>
                <th>Số điện thoại</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>Le Van A</td>
                <td>0123456789</td>
            </tr>
            <tr>
                <td>2</td>
                <td>Nguyen Thi B</td>
                <td>0987654321</td>
            </tr>
        </tbody>
    </table>
    ```
    - `<table></table>`: Xác định một bảng
    - `<thead></thead>`: Phần đầu của bảng
    - `<tbody></tbody>`: Phần thân của bảng
    - `<tr></tr>` (table row):  Xác định một hàng của bảng
    - `<th></th>` (table header): Xác định tiêu đề của bảng
    - `<td></td>` (table data): Xác định dữ liệu ô của bảng

    **Output:**

    ![Bảng minh họa](asset/table.png)


6. <code>List</code>  
    ```html
    <ul>
        <li>Mục 1</li>
        <li>Mục 2</li>
        <li>Mục 3</li>
    </ul>
    ```
    - **`<ul></ul>`**: Danh sách hiển thị kiểu không được đánh số.
    - **`<li></li>`**: Một mục trong danh sách.
    - **`<ol></ol>`**: Các mục con của nó được sắp xếp theo thứ tự bằng số hoặc chữ cái.
        + **Thuộc tính dành riêng cho thẻ `<ol></ol>`**:
            * **type="1"**: Mặc định. Các mục trong danh sách sẽ được đánh dưới dạng số.
            * **type="A"**: Các mục trong danh sách sẽ được đánh dưới dạng chữ hoa.
            * **type="a"**: Các mục trong danh sách sẽ được đánh dưới dạng chữ thường.
            * **type="I"**: Các mục trong danh sách sẽ được đánh dưới dạng số La Mã viết hoa.
            * **type="i"**: Các mục trong danh sách sẽ được đánh dưới dạng số La Mã viết thường.
7. <code>Iframe</code>
    ```html
    <iframe src="url" title="description" height="200" width="300"></iframe>
    ```
8. <code>Form</code>
    ```html
    <form action="">
        <label for="fullName">Họ tên:</label><br>
        <input type="text" id="fullName" name="full_name"><br>
        <label for="email">Email:</label><br>
        <input type="text" id="email" name="email"><br><br>
        <input type="submit" value="Gửi">
    </form>
    ```
    - **action**: Đường dẫn xử lý khi gửi form.
    - **target**: Nơi hiển thị phản hồi sau khi gửi.
    - **method**: Phương thức gửi (GET hoặc POST):
        + **GET**: Dữ liệu gắn vào URL, không bảo mật, giới hạn 2048 ký tự.
        + **POST**: Dữ liệu không hiển thị URL, không giới hạn kích thước.
9. <code>Select</code>
    ```html
    <select name="tên_thuộc_tính" id="id_thuộc_tính">
        <option value="giá_trị_1">Tùy chọn 1</option>
        <option value="giá_trị_2">Tùy chọn 2</option>
        <option value="giá_trị_3">Tùy chọn 3</option>
    </select>
    ```
    - **name**: Tên của danh sách, dùng để nhận giá trị khi gửi form.
    - **id**: Định danh cho thẻ `<select>`.
    - **value** (trong `<option>`): Giá trị được gửi khi tùy chọn được chọn.
    - **selected**: Đặt mặc định cho một tùy chọn.
    - **disabled**: Vô hiệu hóa tùy chọn

## Block
- Một số thẻ dạng block:

    `<address>, <article>, <aside>, <blockquote>, <canvas>, <dd>, <div>, <dl>, <dt>, <fieldset>, <figcaption>, <figure>, <footer>, <form>, <h>, <header>, <hr>, <li>, <main>, <nav>, <noscript>, <ol>, <p>, <pre>, <section>, <table>, <tfoot>, <ul>.`
- Một số thẻ dạng inline:

    `<a>, <abbr>, <acronym>, <b>, <bdo>, <big>, <br>, <button>, <cite>, <code>, <em>, <i>, <img>, <input>, <kbd>, <label>, <map>, <object>, <output>, <q>, <samp>, <script>, <select>, <small>, <span>, <strong>, <sub>, <sup>, <textarea>, <time>, <tt>, <var>.`

## Bootstrap
1. **Các lớp col trong Bootstrap 3**
    - Bootstrap 3 cung cấp hệ thống lưới (grid system) cho phép bạn tạo các layout linh hoạt và đáp ứng trên nhiều thiết bị khác nhau. Mỗi dòng (row) có thể chứa tối đa 12 cột (`col`), và bạn có thể tùy chỉnh kích thước cột cho các màn hình khác nhau bằng cách sử dụng các lớp `col-{size}-{number}`.

    - **col-xs-{number}**: Dành cho màn hình extra small (di động). Sử dụng khi màn hình có chiều rộng nhỏ hơn 768px.
    - **col-sm-{number}**: Dành cho màn hình small (máy tính bảng). Sử dụng khi màn hình có chiều rộng từ 768px đến 991px.
    - **col-md-{number}**: Dành cho màn hình medium (máy tính để bàn). Sử dụng khi màn hình có chiều rộng từ 992px đến 1199px.
    - **col-lg-{number}**: Dành cho màn hình large (máy tính để bàn lớn). Sử dụng khi màn hình có chiều rộng từ 1200px trở lên.

    Các lớp này sẽ giúp bạn xác định số lượng cột mà phần tử sẽ chiếm trong mỗi loại màn hình.

    ```html
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-6 col-md-4 col-lg-3">
                <div class="panel panel-default">
                    <div class="panel-body">
                        Content for col-xs-12 col-sm-6 col-md-4 col-lg-3
                    </div>
                </div>
            </div>
            <div class="col-xs-12 col-sm-6 col-md-4 col-lg-3">
                <div class="panel panel-default">
                    <div class="panel-body">
                        Content for col-xs-12 col-sm-6 col-md-4 col-lg-3
                    </div>
                </div>
            </div>
            <div class="col-xs-12 col-sm-12 col-md-4 col-lg-6">
                <div class="panel panel-default">
                    <div class="panel-body">
                        Content for col-xs-12 col-sm-12 col-md-4 col-lg-6
                    </div>
                </div>
            </div>
        </div>
    </div>
    ```


    - **col-xs-12**: Cột này chiếm 12 phần (toàn bộ chiều rộng) của dòng trên các thiết bị nhỏ (màn hình dưới 768px).
    - **col-sm-6**: Cột này chiếm 6 phần (1/2 chiều rộng) của dòng trên các thiết bị vừa (màn hình từ 768px đến 991px).
    - **col-md-4**: Cột này chiếm 4 phần (1/3 chiều rộng) của dòng trên các thiết bị lớn (màn hình từ 992px đến 1199px).
    - **col-lg-3**: Cột này chiếm 3 phần (1/4 chiều rộng) của dòng trên các thiết bị rất lớn (màn hình trên 1200px).
    
    **Lưu ý**: Tổng số cột trong mỗi dòng phải cộng lại thành 12. Nếu bạn dùng 2 cột mỗi cái chiếm 6 phần, tổng cộng sẽ là 12, nhưng nếu bạn sử dụng 4 cột mỗi cột chiếm 3 phần, tổng cộng cũng là 12.

    
    - **Offset**: Bạn có thể tạo khoảng cách (offset) cho các cột bằng cách sử dụng các lớp như `col-md-offset-3`, làm cho cột bị lệch sang phải một số lượng cột nhất định.
    
    ```html
    <div class="container">
        <div class="row">
            <div class="col-md-4 col-md-offset-4">
                <div class="panel panel-default">
                    <div class="panel-body">
                        This column is centered with an offset
                    </div>
                </div>
            </div>
        </div>
    </div>
    ```
    
    - **Nesting**: Bạn có thể lồng các cột bên trong các cột khác để tạo các cấu trúc lưới phức tạp hơn.
    
    ```html
    <div class="container">
        <div class="row">
            <div class="col-md-6">
                <div class="row">
                    <div class="col-md-6">Nested column 1</div>
                    <div class="col-md-6">Nested column 2</div>
                </div>
            </div>
            <div class="col-md-6">Column 2</div>
        </div>
    </div>
    ```

- **Tóm tắt**:
    - Sử dụng hệ thống lưới của Bootstrap 3, bạn có thể dễ dàng tạo các layout có tính đáp ứng (responsive) với các cột có kích thước khác nhau tùy thuộc vào loại màn hình.
    - Đảm bảo tổng số cột trong một dòng không vượt quá 12.
    - Sử dụng `col-xs`, `col-sm`, `col-md`, và `col-lg` để tạo các layout tối ưu cho từng kích thước màn hình.
    - Các lớp bổ sung như `offset` giúp điều chỉnh vị trí của các cột, trong khi tính năng nesting cho phép bạn lồng các cột bên trong cột khác.


