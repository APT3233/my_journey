# JavaScript CheatSheet

## Template

## String
1. **charAt()**
    ```javascript
    let str = "Hello";
    let result = str.charAt(1);  // 'e'
    ```
    - Cách sử dụng: Trả về ký tự tại một vị trí chỉ định trong chuỗi.
    - Ví dụ: `str.charAt(1)` trả về ký tự ở vị trí thứ 1 trong chuỗi, là 'e'.

2. **charCodeAt()**
    ```javascript
    let str = "Hello";
    let result = str.charCodeAt(1);  // 101
    ```
    - Cách sử dụng: Trả về mã unicode của ký tự tại vị trí chỉ định trong chuỗi.
    - Ví dụ: `str.charCodeAt(1)` trả về mã unicode của ký tự 'e', là 101.

3. **concat()**
    ```javascript
    let str1 = "Hello";
    let str2 = " World";
    let result = str1.concat(str2);  // "Hello World"
    ```
    - Cách sử dụng: Nối hai hoặc nhiều chuỗi thành một chuỗi duy nhất.
    - Ví dụ: `str1.concat(str2)` kết hợp chuỗi `"Hello"` và `" World"` thành `"Hello World"`.

4. **fromCharCode()**
    ```javascript
    let result = String.fromCharCode(72, 101, 108, 108, 111);  // "Hello"
    ```
    - Cách sử dụng: Trả về chuỗi tạo thành từ dãy mã Unicode (UTF-16) đã cho.
    - Ví dụ: `String.fromCharCode(72, 101, 108, 108, 111)` trả về chuỗi `"Hello"`.

5. **indexOf()**
    ```javascript
    let str = "Hello World";
    let result = str.indexOf("World");  // 6
    ```
    - Cách sử dụng: Trả về vị trí xuất hiện đầu tiên của một chuỗi con trong chuỗi hiện tại.
    - Ví dụ: `str.indexOf("World")` trả về vị trí của "World" trong chuỗi `"Hello World"`, là 6.

6. **lastIndexOf()**
    ```javascript
    let str = "Hello World World";
    let result = str.lastIndexOf("World");  // 12
    ```
    - Cách sử dụng: Tương tự như `indexOf()`, nhưng tìm kiếm vị trí xuất hiện cuối cùng của chuỗi con trong chuỗi hiện tại.
    - Ví dụ: `str.lastIndexOf("World")` trả về vị trí xuất hiện cuối cùng của "World" trong chuỗi `"Hello World World"`, là 12.

7. **match()**
    ```javascript
    let str = "The quick brown fox";
    let result = str.match(/quick/);  // ["quick"]
    ```
    - Cách sử dụng: Trả về một mảng chứa các kết quả khớp với biểu thức chính quy (regex) trong chuỗi.
    - Ví dụ: `str.match(/quick/)` tìm kiếm chuỗi `"quick"` trong `"The quick brown fox"` và trả về mảng `["quick"]`.

8. **replace()**
    ```javascript
    let str = "Hello World";
    let result = str.replace("World", "JavaScript");  // "Hello JavaScript"
    ```
    - Cách sử dụng: Tìm và thay thế một chuỗi con trong chuỗi hiện tại bằng một chuỗi mới.
    - Ví dụ: `str.replace("World", "JavaScript")` thay thế `"World"` bằng `"JavaScript"` trong `"Hello World"`.

9. **search()**
    ```javascript
    let str = "The quick brown fox";
    let result = str.search("quick");  // 4
    ```
    - Cách sử dụng: Thực hiện tìm kiếm văn bản theo biểu thức chính quy và trả về vị trí tìm thấy.
    - Ví dụ: `str.search("quick")` trả về vị trí đầu tiên của từ `"quick"` trong `"The quick brown fox"`, là 4.

10. **slice()**
    ```javascript
    let str = "Hello World";
    let result = str.slice(0, 5);  // "Hello"
    ```
    - Cách sử dụng: Trích xuất một phần của chuỗi từ chỉ số bắt đầu đến chỉ số kết thúc (không bao gồm chỉ số kết thúc).
    - Ví dụ: `str.slice(0, 5)` trả về phần đầu tiên của chuỗi `"Hello World"`, từ vị trí 0 đến 5, là `"Hello"`.

11. **split()**
    ```javascript
    let str = "Hello World";
    let result = str.split(" ");  // ["Hello", "World"]
    ```
    - Cách sử dụng: Chia chuỗi thành một mảng các chuỗi con, phân tách tại một ký tự hoặc biểu thức chính quy.
    - Ví dụ: `str.split(" ")` chia chuỗi `"Hello World"` thành mảng `["Hello", "World"]`.

12. **substr()**
    ```javascript
    let str = "Hello World";
    let result = str.substr(0, 5);  // "Hello"
    ```
    - Cách sử dụng: Trích xuất một chuỗi con từ chuỗi gốc, dựa trên vị trí bắt đầu và số lượng ký tự.
    - Ví dụ: `str.substr(0, 5)` trích xuất 5 ký tự bắt đầu từ vị trí 0 trong `"Hello World"`, trả về `"Hello"`.

13. **substring()**
    ```javascript
    let str = "Hello World";
    let result = str.substring(0, 5);  // "Hello"
    ```
    - Cách sử dụng: Tương tự `slice()`, nhưng không chấp nhận chỉ số âm và không bao gồm chỉ số kết thúc.
    - Ví dụ: `str.substring(0, 5)` trả về `"Hello"` trong `"Hello World"`.

14. **toLowerCase()**
    ```javascript
    let str = "Hello World";
    let result = str.toLowerCase();  // "hello world"
    ```
    - Cách sử dụng: Chuyển toàn bộ chuỗi thành chữ thường.
    - Ví dụ: `str.toLowerCase()` chuyển `"Hello World"` thành `"hello world"`.

15. **toUpperCase()**
    ```javascript
    let str = "Hello World";
    let result = str.toUpperCase();  // "HELLO WORLD"
    ```
    - Cách sử dụng: Chuyển toàn bộ chuỗi thành chữ in hoa.
    - Ví dụ: `str.toUpperCase()` chuyển `"Hello World"` thành `"HELLO WORLD"`.

16. **valueOf()**
    ```javascript
    let str = new String("Hello World");
    let result = str.valueOf();  // "Hello World"
    ```
    - Cách sử dụng: Trả về giá trị nguyên thủy của đối tượng String (chuỗi đơn giản).
    - Ví dụ: `str.valueOf()` trả về chuỗi `"Hello World"` từ đối tượng `String`.
## Array
1. **concat()**
    ```javascript
    let arr1 = [1, 2, 3];
    let arr2 = [4, 5, 6];
    let result = arr1.concat(arr2);  // [1, 2, 3, 4, 5, 6]
    ```
    - Cách sử dụng: Kết hợp nhiều mảng thành một mảng duy nhất.
    - Ví dụ: `arr1.concat(arr2)` kết hợp mảng `[1, 2, 3]` và `[4, 5, 6]` thành `[1, 2, 3, 4, 5, 6]`.

2. **indexOf()**
    ```javascript
    let arr = [10, 20, 30, 40, 50];
    let result = arr.indexOf(30);  // 2
    ```
    - Cách sử dụng: Trả về vị trí đầu tiên mà một phần tử xuất hiện trong mảng.
    - Ví dụ: `arr.indexOf(30)` trả về vị trí đầu tiên của phần tử `30`, là `2`.

3. **join()**
    ```javascript
    let arr = ["apple", "banana", "cherry"];
    let result = arr.join(", ");  // "apple, banana, cherry"
    ```
    - Cách sử dụng: Kết hợp các phần tử của mảng thành một chuỗi duy nhất và trả về chuỗi đó.
    - Ví dụ: `arr.join(", ")` kết hợp các phần tử trong mảng thành chuỗi `"apple, banana, cherry"`.

4. **lastIndexOf()**
    ```javascript
    let arr = [10, 20, 30, 20, 40];
    let result = arr.lastIndexOf(20);  // 3
    ```
    - Cách sử dụng: Trả về vị trí xuất hiện cuối cùng của một phần tử trong mảng.
    - Ví dụ: `arr.lastIndexOf(20)` trả về vị trí cuối cùng của phần tử `20`, là `3`.

5. **pop()**
    ```javascript
    let arr = [1, 2, 3, 4];
    let result = arr.pop();  // 4
    ```
    - Cách sử dụng: Loại bỏ phần tử cuối cùng của mảng và trả về phần tử đó.
    - Ví dụ: `arr.pop()` loại bỏ phần tử `4` khỏi mảng và trả về `4`.

6. **push()**
    ```javascript
    let arr = [1, 2, 3];
    let result = arr.push(4);  // 4
    ```
    - Cách sử dụng: Thêm một hoặc nhiều phần tử vào cuối mảng và trả về độ dài mới của mảng.
    - Ví dụ: `arr.push(4)` thêm `4` vào mảng `[1, 2, 3]` và trả về độ dài mảng mới, là `4`.

7. **reverse()**
    ```javascript
    let arr = [1, 2, 3, 4];
    let result = arr.reverse();  // [4, 3, 2, 1]
    ```
    - Cách sử dụng: Đảo ngược thứ tự các phần tử trong mảng.
    - Ví dụ: `arr.reverse()` thay đổi thứ tự mảng thành `[4, 3, 2, 1]`.

8. **shift()**
    ```javascript
    let arr = [10, 20, 30];
    let result = arr.shift();  // 10
    ```
    - Cách sử dụng: Loại bỏ phần tử đầu tiên của mảng và trả về phần tử đó.
    - Ví dụ: `arr.shift()` loại bỏ phần tử `10` khỏi mảng và trả về `10`.

9. **slice()**
    ```javascript
    let arr = [1, 2, 3, 4, 5];
    let result = arr.slice(1, 3);  // [2, 3]
    ```
    - Cách sử dụng: Lấy một phần của mảng và trả về một mảng mới.
    - Ví dụ: `arr.slice(1, 3)` lấy các phần tử từ vị trí 1 đến 2 trong mảng, tạo thành mảng `[2, 3]`.

10. **sort()**
    ```javascript
    let arr = [4, 1, 3, 2];
    let result = arr.sort();  // [1, 2, 3, 4]
    ```
    - Cách sử dụng: Sắp xếp các phần tử trong mảng theo thứ tự tăng dần (mặc định).
    - Ví dụ: `arr.sort()` sắp xếp mảng `[4, 1, 3, 2]` thành `[1, 2, 3, 4]`.

11. **splice()**
    ```javascript
    let arr = [1, 2, 3, 4];
    let result = arr.splice(2, 1, 5);  // [3]
    ```
    - Cách sử dụng: Thêm hoặc loại bỏ phần tử tại vị trí chỉ định trong mảng.
    - Ví dụ: `arr.splice(2, 1, 5)` loại bỏ phần tử ở vị trí 2 và thêm phần tử `5`, kết quả là mảng `[1, 2, 5, 4]`.

12. **toString()**
    ```javascript
    let arr = [1, 2, 3];
    let result = arr.toString();  // "1,2,3"
    ```
    - Cách sử dụng: Chuyển các phần tử trong mảng thành một chuỗi, cách nhau bởi dấu phẩy.
    - Ví dụ: `arr.toString()` chuyển mảng `[1, 2, 3]` thành chuỗi `"1,2,3"`.

13. **unshift()**
    ```javascript
    let arr = [2, 3, 4];
    let result = arr.unshift(1);  // 4
    ```
    - Cách sử dụng: Thêm một hoặc nhiều phần tử vào đầu mảng và trả về độ dài mới của mảng.
    - Ví dụ: `arr.unshift(1)` thêm `1` vào đầu mảng `[2, 3, 4]` và trả về độ dài mảng mới, là `4`.

14. **valueOf()**
    ```javascript
    let arr = [1, 2, 3];
    let result = arr.valueOf();  // [1, 2, 3]
    ```
    - Cách sử dụng: Trả về giá trị nguyên thủy của mảng.
    - Ví dụ: `arr.valueOf()` trả về mảng `[1, 2, 3]` (giá trị nguyên thủy của mảng).
## Loop
1. **for**
    ```javascript
    for (let i = 0; i < 5; i++) {
        console.log(i);
    }
    ```
    - Cách sử dụng: Vòng lặp `for` thực hiện một khối mã lặp lại cho đến khi điều kiện là `false`.
    - Ví dụ: `for (let i = 0; i < 5; i++)` sẽ in ra các giá trị từ `0` đến `4`.

2. **while**
    ```javascript
    let i = 0;
    while (i < 5) {
        console.log(i);
        i++;
    }
    ```
    - Cách sử dụng: Vòng lặp `while` tiếp tục thực hiện một khối mã miễn là điều kiện là `true`.
    - Ví dụ: `while (i < 5)` sẽ in ra các giá trị từ `0` đến `4`.

3. **do...while**
    ```javascript
    let i = 0;
    do {
        console.log(i);
        i++;
    } while (i < 5);
    ```
    - Cách sử dụng: Vòng lặp `do...while` thực hiện ít nhất một lần, sau đó tiếp tục lặp lại miễn là điều kiện là `true`.
    - Ví dụ: `do...while (i < 5)` sẽ in ra các giá trị từ `0` đến `4`.

4. **for...in**
    ```javascript
    let person = { name: "John", age: 30, city: "New York" };
    for (let key in person) {
        console.log(key + ": " + person[key]);
    }
    ```
    - Cách sử dụng: Vòng lặp `for...in` được sử dụng để lặp qua các thuộc tính của một đối tượng.
    - Ví dụ: `for (let key in person)` sẽ lặp qua các thuộc tính của đối tượng `person` và in ra tên thuộc tính cùng giá trị của nó.

5. **for...of**
    ```javascript
    let arr = [10, 20, 30, 40];
    for (let value of arr) {
        console.log(value);
    }
    ```
    - Cách sử dụng: Vòng lặp `for...of` được sử dụng để lặp qua các phần tử của một mảng hoặc một đối tượng iterable.
    - Ví dụ: `for (let value of arr)` sẽ lặp qua các phần tử trong mảng `arr` và in ra từng phần tử.

6. **break**
    ```javascript
    for (let i = 0; i < 10; i++) {
        if (i === 5) {
            break;  // Dừng vòng lặp khi i bằng 5
        }
        console.log(i);
    }
    ```
    - Cách sử dụng: `break` dừng vòng lặp ngay lập tức và thoát khỏi vòng lặp.
    - Ví dụ: `break` sẽ dừng vòng lặp khi `i` bằng `5`, không tiếp tục lặp.

7. **continue**
    ```javascript
    for (let i = 0; i < 10; i++) {
        if (i === 5) {
            continue;  // Bỏ qua vòng lặp khi i bằng 5
        }
        console.log(i);
    }
    ```
    - Cách sử dụng: `continue` bỏ qua phần còn lại của vòng lặp hiện tại và chuyển đến vòng lặp tiếp theo.
    - Ví dụ: `continue` sẽ bỏ qua khi `i` bằng `5`, và tiếp tục với các giá trị khác.






## Function
1. **Function Declaration**
    ```javascript
    fucntion myFunction(){
        console.log('Hello World')
    }
    ```
    - Cách sử dụng: Hàm được khai báo với từ khóa function, có thể gọi hàm ở bất kỳ đâu trong mã nguồn (do hoisting).
    - Hoisting: Hàm được đưa lên đầu phạm vi (scope) ngay khi mã nguồn được biên dịch.
2. **Function Expression**
    ```javascript
    const myFunction = function() {
        console.log("Hello, World!");
    };
    Or
    const myFunction = function myNamedFunction() {
        console.log("Hello, World!");
    };
    ```
    - Cách sử dụng: Hàm được gán cho một biến, không thể gọi hàm trước khi khai báo.
    - Hoisting: Không có hoisting, phải khai báo hàm trước khi gọi.
3. **Arrow Function**
    ```javascript
    const myFunction = () => {
        console.log("Hello, World!");
    };
    ```
    - Cách sử dụng: Hàm ngắn gọn, sử dụng cú pháp =>. Không có từ khóa function.
    - Lưu ý: Không có this riêng, nó kế thừa this từ phạm vi bên ngoài.

4. **Anonymous Function**
    ```javascript
    setTimeout(function() {
        console.log("Hello after 1 second!");
    }, 1000);
    ```
5. **Function Constructor**
    ```javascript
    const myFunction = new Function('a', 'b', 'return a + b');
    console.log(myFunction(2, 3)); 
    ```
6. **Async Function**
    ```javascript
    async function myAsyncFunction() {
        const result = await someAsyncTask();
        console.log(result);
    }
    ```
    - Cách sử dụng: Dùng từ khóa async để khai báo hàm bất đồng bộ. Dùng await để chờ kết quả từ các tác vụ bất đồng bộ.
7. **Method in Obj**
    ```javascript
    const myObject = {
        myMethod: function() {
            console.log("Hello, World!");
        }
    };
    myObject.myMethod();
    ```
    - Cách sử dụng: Hàm là một phương thức trong đối tượng, có thể sử dụng this để tham chiếu đến đối tượng.

## Window
1. **alert()**
    ```javascript
    alert("Hello, World!");
    ```
    - Cách sử dụng: Hiển thị một hộp thông báo với thông điệp và một nút OK.
    - Ví dụ: `alert("Hello, World!")` sẽ hiển thị một hộp thông báo với thông điệp "Hello, World!".

2. **blur()**
    ```javascript
    window.blur();
    ```
    - Cách sử dụng: Loại bỏ tiêu điểm (focus) khỏi cửa sổ hiện tại.
    - Ví dụ: `window.blur()` sẽ bỏ tiêu điểm khỏi cửa sổ hiện tại, nghĩa là cửa sổ sẽ không còn được chọn.

3. **close()**
    ```javascript
    window.close();
    ```
    - Cách sử dụng: Đóng cửa sổ hiện tại.
    - Ví dụ: `window.close()` sẽ đóng cửa sổ trình duyệt hiện tại.

4. **confirm()**
    ```javascript
    let result = confirm("Do you want to continue?");
    ```
    - Cách sử dụng: Hiển thị một hộp thoại với thông điệp và hai nút "OK" và "Cancel".
    - Ví dụ: `confirm("Do you want to continue?")` sẽ hiển thị hộp thoại và trả về `true` nếu người dùng chọn "OK", hoặc `false` nếu chọn "Cancel".

5. **focus()**
    ```javascript
    window.focus();
    ```
    - Cách sử dụng: Đặt tiêu điểm (focus) vào cửa sổ hiện tại.
    - Ví dụ: `window.focus()` sẽ làm cho cửa sổ hiện tại trở thành cửa sổ đang hoạt động.

6. **open()**
    ```javascript
    let newWindow = window.open("https://www.example.com", "_blank");
    ```
    - Cách sử dụng: Mở một cửa sổ trình duyệt mới với URL chỉ định.
    - Ví dụ: `window.open("https://www.example.com", "_blank")` sẽ mở trang web "example.com" trong một cửa sổ mới.

11. **print()**
    ```javascript
    window.print();
    ```
    - Cách sử dụng: In nội dung của cửa sổ hiện tại.
    - Ví dụ: `window.print()` sẽ mở hộp thoại in để người dùng có thể in nội dung của trang web.

12. **prompt()**
    ```javascript
    let userInput = prompt("What is your name?");
    ```
    - Cách sử dụng: Hiển thị một hộp thoại yêu cầu người dùng nhập dữ liệu.
    - Ví dụ: `prompt("What is your name?")` sẽ hiển thị một hộp thoại yêu cầu người dùng nhập tên, và trả về giá trị người dùng nhập vào.
## Dom element
1. **getElementById()**
    ```javascript
    let element = document.getElementById("myElement");
    ```
    - Cách sử dụng: Lấy phần tử DOM có `id` cụ thể.
    - Ví dụ: `document.getElementById("myElement")` sẽ trả về phần tử có `id="myElement"`.

2. **getElementsByClassName()**
    ```javascript
    let elements = document.getElementsByClassName("myClass");
    ```
    - Cách sử dụng: Lấy tất cả các phần tử có lớp (`class`) cụ thể. Kết quả trả về là một HTMLCollection.
    - Ví dụ: `document.getElementsByClassName("myClass")` sẽ trả về tất cả các phần tử có lớp `myClass`.

3. **getElementsByTagName()**
    ```javascript
    let elements = document.getElementsByTagName("div");
    ```
    - Cách sử dụng: Lấy tất cả các phần tử có tên thẻ (`tag`) cụ thể. Kết quả trả về là một HTMLCollection.
    - Ví dụ: `document.getElementsByTagName("div")` sẽ trả về tất cả các thẻ `<div>` trong tài liệu.

4. **querySelector()**
    ```javascript
    let element = document.querySelector(".myClass");
    ```
    - Cách sử dụng: Lấy phần tử đầu tiên trong tài liệu phù hợp với bộ chọn CSS (selector) được cung cấp.
    - Ví dụ: `document.querySelector(".myClass")` sẽ trả về phần tử đầu tiên có lớp `myClass`.

5. **querySelectorAll()**
    ```javascript
    let elements = document.querySelectorAll("p.myClass");
    ```
    - Cách sử dụng: Lấy tất cả các phần tử phù hợp với bộ chọn CSS được cung cấp. Kết quả trả về là một NodeList.
    - Ví dụ: `document.querySelectorAll("p.myClass")` sẽ trả về tất cả các thẻ `<p>` có lớp `myClass`.

6. **createElement()**
    ```javascript
    let newDiv = document.createElement("div");
    ```
    - Cách sử dụng: Tạo một phần tử mới theo tên thẻ đã chỉ định.
    - Ví dụ: `document.createElement("div")` sẽ tạo ra một phần tử `<div>` mới.

7. **appendChild()**
    ```javascript
    let newDiv = document.createElement("div");
    document.body.appendChild(newDiv);
    ```
    - Cách sử dụng: Thêm một phần tử con vào cuối phần tử hiện tại.
    - Ví dụ: `document.body.appendChild(newDiv)` sẽ thêm phần tử `newDiv` vào cuối thân (body) của tài liệu.

8. **insertBefore()**
    ```javascript
    let newDiv = document.createElement("div");
    let referenceDiv = document.getElementById("existingDiv");
    document.body.insertBefore(newDiv, referenceDiv);
    ```
    - Cách sử dụng: Thêm một phần tử trước phần tử tham chiếu đã chỉ định.
    - Ví dụ: `document.body.insertBefore(newDiv, referenceDiv)` sẽ chèn `newDiv` vào trước phần tử có `id="existingDiv"`.

9. **removeChild()**
    ```javascript
    let parent = document.getElementById("parentElement");
    let child = document.getElementById("childElement");
    parent.removeChild(child);
    ```
    - Cách sử dụng: Xóa một phần tử con khỏi phần tử cha.
    - Ví dụ: `parent.removeChild(child)` sẽ xóa phần tử `child` khỏi phần tử `parent`.

10. **setAttribute()**
    ```javascript
    let element = document.getElementById("myElement");
    element.setAttribute("class", "newClass");
    ```
    - Cách sử dụng: Thiết lập một thuộc tính (attribute) cho phần tử.
    - Ví dụ: `element.setAttribute("class", "newClass")` sẽ thay đổi giá trị của thuộc tính `class` thành `newClass`.

11. **getAttribute()**
    ```javascript
    let element = document.getElementById("myElement");
    let classValue = element.getAttribute("class");
    ```
    - Cách sử dụng: Lấy giá trị của một thuộc tính (attribute) của phần tử.
    - Ví dụ: `element.getAttribute("class")` sẽ trả về giá trị của thuộc tính `class` của phần tử.

12. **removeAttribute()**
    ```javascript
    let element = document.getElementById("myElement");
    element.removeAttribute("class");
    ```
    - Cách sử dụng: Xóa một thuộc tính (attribute) khỏi phần tử.
    - Ví dụ: `element.removeAttribute("class")` sẽ xóa thuộc tính `class` khỏi phần tử.

13. **classList.add()**
    ```javascript
    let element = document.getElementById("myElement");
    element.classList.add("newClass");
    ```
    - Cách sử dụng: Thêm một lớp (class) vào phần tử.
    - Ví dụ: `element.classList.add("newClass")` sẽ thêm lớp `newClass` vào phần tử.

14. **classList.remove()**
    ```javascript
    let element = document.getElementById("myElement");
    element.classList.remove("oldClass");
    ```
    - Cách sử dụng: Xóa một lớp (class) khỏi phần tử.
    - Ví dụ: `element.classList.remove("oldClass")` sẽ xóa lớp `oldClass` khỏi phần tử.

15. **classList.toggle()**
    ```javascript
    let element = document.getElementById("myElement");
    element.classList.toggle("active");
    ```
    - Cách sử dụng: Thêm một lớp (class) nếu nó chưa có, hoặc xóa lớp đó nếu nó đã tồn tại.
    - Ví dụ: `element.classList.toggle("active")` sẽ chuyển đổi lớp `active` của phần tử.

16. **style.property**
    ```javascript
    let element = document.getElementById("myElement");
    element.style.backgroundColor = "blue";
    ```
    - Cách sử dụng: Thay đổi các thuộc tính CSS của phần tử.
    - Ví dụ: `element.style.backgroundColor = "blue"` sẽ thay đổi màu nền của phần tử thành màu xanh.
## Dom event
1. **addEventListener()**
    ```javascript
    let button = document.getElementById("myButton");
    button.addEventListener("click", () => {
        alert("Button clicked!");
    });
    ```
    - Cách sử dụng: Đăng ký một sự kiện cho một phần tử. Phương thức này cho phép bạn đăng ký nhiều sự kiện cho cùng một phần tử.
    - **Ví dụ**: Khi người dùng nhấn nút có ID `myButton`, một thông báo `Button clicked!` sẽ xuất hiện.

2. **removeEventListener()**
    ```javascript
    let button = document.getElementById("myButton");
    const clickHandler = () => {
        alert("Button clicked!");
    };
    button.addEventListener("click", clickHandler);
    // Hủy bỏ sự kiện sau 5 giây
    setTimeout(() => {
        button.removeEventListener("click", clickHandler);
    }, 5000);
    ```
    - Cách sử dụng: Hủy bỏ một sự kiện đã được đăng ký bằng `addEventListener()`.
    - **Ví dụ**: Sau khi người dùng nhấn nút `myButton` trong 5 giây, sự kiện `click` sẽ bị hủy bỏ và không còn hoạt động.

3. **click**
    ```javascript
    let button = document.getElementById("myButton");
    button.onclick = () => {
        alert("Button clicked!");
    };
    ```
    - Cách sử dụng: Sử dụng thuộc tính `onclick` để đăng ký sự kiện khi người dùng nhấp chuột vào phần tử.
    - **Ví dụ**: Khi người dùng nhấn vào nút có ID `myButton`, một thông báo sẽ xuất hiện.

4. **submit**
    ```javascript
    let form = document.getElementById("myForm");
    form.onsubmit = (event) => {
        event.preventDefault();  // Ngừng việc gửi form
        alert("Form submitted!");
    };
    ```
    - Cách sử dụng: Đăng ký sự kiện `submit` để thực hiện hành động khi một biểu mẫu được gửi.
    - **Ví dụ**: Khi người dùng gửi biểu mẫu `myForm`, một thông báo "Form submitted!" sẽ hiển thị, nhưng việc gửi biểu mẫu sẽ bị ngừng lại.

5. **keydown**
    ```javascript
    document.addEventListener("keydown", (event) => {
        console.log("Key pressed: " + event.key);
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi một phím được nhấn xuống.
    - **Ví dụ**: Khi người dùng nhấn phím bất kỳ, tên phím sẽ được in ra console.

6. **keyup**
    ```javascript
    document.addEventListener("keyup", (event) => {
        console.log("Key released: " + event.key);
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi một phím được thả ra.
    - **Ví dụ**: Khi người dùng thả phím bất kỳ, tên phím sẽ được in ra console.

7. **mouseover**
    ```javascript
    let box = document.getElementById("myBox");
    box.addEventListener("mouseover", () => {
        box.style.backgroundColor = "yellow";
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi chuột di chuyển vào một phần tử.
    - **Ví dụ**: Khi người dùng di chuột vào phần tử `myBox`, màu nền của nó sẽ thay đổi thành màu vàng.

8. **mouseout**
    ```javascript
    let box = document.getElementById("myBox");
    box.addEventListener("mouseout", () => {
        box.style.backgroundColor = "white";
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi chuột di chuyển ra khỏi một phần tử.
    - **Ví dụ**: Khi người dùng di chuột ra khỏi phần tử `myBox`, màu nền của nó sẽ trở lại màu trắng.

9. **focus**
    ```javascript
    let input = document.getElementById("myInput");
    input.addEventListener("focus", () => {
        input.style.border = "2px solid blue";
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi phần tử nhận được tiêu điểm (focus).
    - **Ví dụ**: Khi trường nhập liệu `myInput` được chọn (focus), viền của nó sẽ chuyển thành màu xanh dương.

10. **blur**
    ```javascript
    let input = document.getElementById("myInput");
    input.addEventListener("blur", () => {
        input.style.border = "1px solid gray";
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi phần tử mất tiêu điểm (blur).
    - **Ví dụ**: Khi trường nhập liệu `myInput` bị mất tiêu điểm (khi người dùng rời khỏi), viền của nó sẽ trở lại màu xám.

11. **change**
    ```javascript
    let input = document.getElementById("myInput");
    input.addEventListener("change", () => {
        alert("Input changed!");
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi giá trị của phần tử (thường là input) thay đổi.
    - **Ví dụ**: Khi người dùng thay đổi giá trị của trường nhập liệu `myInput`, một thông báo sẽ hiển thị "Input changed!".

12. **input**
    ```javascript
    let input = document.getElementById("myInput");
    input.addEventListener("input", () => {
        console.log("Current value: " + input.value);
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi giá trị của phần tử input thay đổi, ngay khi người dùng gõ.
    - **Ví dụ**: Mỗi khi người dùng gõ vào trường nhập liệu `myInput`, giá trị hiện tại của nó sẽ được log ra console.

13. **resize**
    ```javascript
    window.addEventListener("resize", () => {
        console.log("Window resized!");
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi cửa sổ trình duyệt thay đổi kích thước.
    - **Ví dụ**: Mỗi khi người dùng thay đổi kích thước cửa sổ trình duyệt, thông báo "Window resized!" sẽ được log ra console.

14. **scroll**
    ```javascript
    window.addEventListener("scroll", () => {
        console.log("Page scrolled!");
    });
    ```
    - Cách sử dụng: Đăng ký sự kiện khi người dùng cuộn trang.
    - **Ví dụ**: Mỗi khi người dùng cuộn trang, thông báo "Page scrolled!" sẽ được log ra console.
