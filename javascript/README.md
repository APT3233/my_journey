# JavaScript CheatSheet


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