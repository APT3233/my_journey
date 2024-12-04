# ExpressJS CheatSheet
1. [Basic](#basic)
2. [Express()](#express)
3. [Router()](#router)
4. [App](#app)
5. [Request](#req)
    - 5.1 [Attribute](#attribute)
    - 5.2 [Method](#method)
6. [Response](#res)
    - 6.1 [Attribute](#attribute)
    - 6.2 [Method](#method)
7. [Example](#example)

### Basic 
1. `index.js`
    ```
    const express = require("express");
    const app = express();
    const port = 3000;

    app.get("/", (req, res) => {
        res.send("hello world!");
    });

    app.listen(port, () => console.log(`Server app listening on port ${port}!`));
    ```
2. Routes
    ```
    app.get('/', function (req, res) {
    // code here
    })

    app.post('/', function (req, res) {
    // code here
    })

    app.put('/', function (req, res) {
    // code here
    })

    app.delete('/', function (req, res) {
    // code here
    })
    ```
3. Router Routes
    ```
    router.get('/', function (req, res) {
    // code here
    })

    router.post('/', function (req, res) {
    // code here
    })

    router.post('/', function (req, res) {
    // code here
    })

    router.delete('/', function (req, res) {
    // code here
    })
    ```
3. Static Files
    ```
    // basic syntax
    app.use(express.static('public'))

    // use multilpe dir for assets
    app.use(express.static('public'))
    app.use(express.static('files'))

    // use virtual prefix path
    app.use('/static', express.static('public'))

    app.use(express.static(path.join(__dirname, 'public')))

    app.use('/static', express.static(path.join(__dirname, 'public')))
    ```
3. Body Parser
    ```
    var bodyParser = require('body-parser')

    // parse application/x-www-form-urlencoded
    app.use(bodyParser.urlencoded({ extended: false }))

    // parse application/json
    app.use(bodyParser.json())
    ```
4. Template handlebars
    ```
    const handlebar  = require('express-handlebars');

    // set view engine
    app.engine('handlebars', handlebar());
    app.set('view engine', 'handlebars');

    // render
    app.get('/', function (req, res) {
        res.render('home');
    });
    ```
### Express
1. **express.json()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use(express.json());
    
    app.post('/data', (req, res) => {
        console.log(req.body);  // JSON object from the request body
        res.send('Received JSON');
    });
    ```
    - Cách sử dụng: Middleware để phân tích cú pháp JSON trong body của yêu cầu HTTP.
    - Ví dụ: `express.json()` giúp phân tích cú pháp dữ liệu JSON trong yêu cầu POST và gán nó vào `req.body`.

2. **express.raw()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use(express.raw());
    
    app.post('/data', (req, res) => {
        console.log(req.body);  // Raw buffer of the request body
        res.send('Received raw data');
    });
    ```
    - Cách sử dụng: Middleware để phân tích cú pháp dữ liệu thô (raw) trong body của yêu cầu HTTP dưới dạng buffer.
    - Ví dụ: `express.raw()` cho phép bạn làm việc với dữ liệu thô từ yêu cầu HTTP, chẳng hạn như các tệp tin nhị phân.

3. **express.Router()**
    ```javascript
    const express = require('express');
    const app = express();
    const router = express.Router();
    
    router.get('/user', (req, res) => {
        res.send('User Route');
    });
    
    app.use('/api', router);
    ```
    - Cách sử dụng: Tạo và sử dụng một router con để nhóm các route lại với nhau.
    - Ví dụ: `express.Router()` cho phép bạn phân chia các route của ứng dụng thành các phần riêng biệt, dễ quản lý hơn.

4. **express.static()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use(express.static('public'));
    
    // Static files in the 'public' directory will be served
    ```
    - Cách sử dụng: Middleware để phục vụ các tệp tĩnh (như HTML, CSS, hình ảnh, v.v.) từ một thư mục.
    - Ví dụ: `express.static('public')` giúp phục vụ các tệp tĩnh từ thư mục `public`.

5. **express.text()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use(express.text());
    
    app.post('/data', (req, res) => {
        console.log(req.body);  // Raw text data from the request body
        res.send('Received text');
    });
    ```
    - Cách sử dụng: Middleware để phân tích cú pháp dữ liệu văn bản (text) trong body của yêu cầu HTTP.
    - Ví dụ: `express.text()` cho phép xử lý các dữ liệu văn bản thô từ yêu cầu HTTP.

6. **express.urlencoded()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use(express.urlencoded({ extended: true }));
    
    app.post('/data', (req, res) => {
        console.log(req.body);  // URL-encoded data from the request body
        res.send('Received URL-encoded data');
    });
    ```
    - Cách sử dụng: Middleware để phân tích cú pháp dữ liệu URL-encoded (như form data) trong body của yêu cầu HTTP.
    - Ví dụ: `express.urlencoded({ extended: true })` cho phép phân tích cú pháp dữ liệu form URL-encoded thành một đối tượng JavaScript.
### Router
1. **router.all()**
    ```javascript
    const express = require('express');
    const app = express();
    const router = express.Router();
    
    router.all('*', (req, res) => {
        res.send('This route matches all HTTP methods');
    });
    
    app.use('/api', router);
    ```
    - Cách sử dụng: Phương thức `all()` cho phép bạn định nghĩa một route mà sẽ xử lý tất cả các phương thức HTTP cho một endpoint cụ thể.
    - Ví dụ: `router.all('*')` sẽ bắt tất cả các loại phương thức HTTP (GET, POST, PUT, DELETE, v.v.) cho bất kỳ đường dẫn nào.

2. **router.METHOD()**
    ```javascript
    const express = require('express');
    const app = express();
    const router = express.Router();
    
    router.get('/user', (req, res) => {
        res.send('GET request to /user');
    });
    
    router.post('/user', (req, res) => {
        res.send('POST request to /user');
    });
    
    app.use('/api', router);
    ```
    - Cách sử dụng: Phương thức `METHOD()` (như `get()`, `post()`, `put()`, `delete()`) được sử dụng để xác định các route cho một phương thức HTTP cụ thể.
    - Ví dụ: `router.get('/user')` sẽ xử lý các yêu cầu GET cho đường dẫn `/user`, còn `router.post('/user')` sẽ xử lý các yêu cầu POST cho đường dẫn đó.

3. **router.param()**
    ```javascript
    const express = require('express');
    const app = express();
    const router = express.Router();
    
    router.param('id', (req, res, next, id) => {
        console.log('ID parameter:', id);
        next();
    });
    
    router.get('/user/:id', (req, res) => {
        res.send(`User ID: ${req.params.id}`);
    });
    
    app.use('/api', router);
    ```
    - Cách sử dụng: Phương thức `param()` cho phép bạn định nghĩa middleware mà sẽ được thực thi khi một tham số route được truyền vào.
    - Ví dụ: `router.param('id', callback)` sẽ tự động gọi middleware này mỗi khi tham số `id` được sử dụng trong một route.

4. **router.route()**
    ```javascript
    const express = require('express');
    const app = express();
    const router = express.Router();
    
    router.route('/user')
        .get((req, res) => {
            res.send('GET request to /user');
        })
        .post((req, res) => {
            res.send('POST request to /user');
        });
    
    app.use('/api', router);
    ```
    - Cách sử dụng: `route()` cho phép bạn định nghĩa một route cụ thể và kết hợp các phương thức HTTP (GET, POST, PUT, DELETE) cho một endpoint.
    - Ví dụ: `router.route('/user')` giúp nhóm các phương thức như `get()`, `post()` cho cùng một endpoint `/user`.

5. **router.use()**
    ```javascript
    const express = require('express');
    const app = express();
    const router = express.Router();
    
    router.use((req, res, next) => {
        console.log('Middleware for all routes');
        next();
    });
    
    router.get('/user', (req, res) => {
        res.send('GET request to /user');
    });
    
    router.post('/user', (req, res) => {
        res.send('POST request to /user');
    });
    
    app.use('/api', router);
    ```
    - Cách sử dụng: `use()` cho phép bạn thêm middleware vào một route hoặc cho tất cả các route của router.
    - Ví dụ: `router.use(callback)` sẽ thêm một middleware cho tất cả các route trong router, giúp xử lý các yêu cầu trước khi đến các route thực tế.
### App
1. **app.use()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use((req, res, next) => {
        console.log('Middleware for all routes');
        next();
    });
    
    app.get('/', (req, res) => {
        res.send('Hello World');
    });
    
    app.listen(3000, () => {
        console.log('Server running on port 3000');
    });
    ```
    - **Cách sử dụng**: Được sử dụng để định nghĩa middleware cho tất cả các route hoặc một route cụ thể.
    - **Ví dụ**: `app.use()` giúp chèn middleware vào ứng dụng Express để xử lý tất cả các yêu cầu hoặc các route cụ thể.



2. **app.all()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.all('*', (req, res) => {
        res.send('This route matches all HTTP methods');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để xử lý tất cả các phương thức HTTP (GET, POST, PUT, DELETE...) cho một route.
    - **Ví dụ**: `app.all('*')` sẽ xử lý tất cả các phương thức HTTP cho mọi route.



3. **app.delete()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.delete('/user', (req, res) => {
        res.send('User deleted');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để định nghĩa route xử lý phương thức HTTP DELETE.
    - **Ví dụ**: `app.delete('/user')` sẽ xử lý yêu cầu DELETE đối với route `/user`.



4. **app.disable()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.disable('x-powered-by');
    
    app.get('/', (req, res) => {
        res.send('X-Powered-By header is disabled');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để tắt một cấu hình trong ứng dụng.
    - **Ví dụ**: `app.disable('x-powered-by')` tắt header `X-Powered-By` trong HTTP response.



5. **app.disabled()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.disable('x-powered-by');
    
    app.get('/', (req, res) => {
        res.send(`x-powered-by is disabled: ${app.disabled('x-powered-by')}`);
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem một cấu hình có bị tắt hay không.
    - **Ví dụ**: `app.disabled('x-powered-by')` sẽ trả về `true` nếu cấu hình `x-powered-by` đã bị tắt.



6. **app.enable()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.enable('trust proxy');
    
    app.get('/', (req, res) => {
        res.send('Trust proxy is enabled');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để bật một cấu hình trong ứng dụng.
    - **Ví dụ**: `app.enable('trust proxy')` sẽ bật cấu hình `trust proxy`.



7. **app.enabled()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.enable('trust proxy');
    
    app.get('/', (req, res) => {
        res.send(`Trust proxy is enabled: ${app.enabled('trust proxy')}`);
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem một cấu hình có được bật hay không.
    - **Ví dụ**: `app.enabled('trust proxy')` sẽ trả về `true` nếu cấu hình `trust proxy` đã được bật.



8. **app.engine()**
    ```javascript
    const express = require('express');
    const app = express();
    const ejs = require('ejs');
    
    app.engine('html', ejs.renderFile);
    
    app.get('/', (req, res) => {
        res.render('index.html', { title: 'Hello World' });
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để chỉ định engine template cho ứng dụng.
    - **Ví dụ**: `app.engine('html', ejs.renderFile)` để sử dụng EJS như một template engine.



9. **app.get(name)**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.set('view engine', 'ejs');
    
    const viewEngine = app.get('view engine');
    console.log(viewEngine);  // ejs
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Truy xuất giá trị của một cấu hình trong ứng dụng.
    - **Ví dụ**: `app.get('view engine')` sẽ trả về giá trị cấu hình của `view engine`.



10. **app.get(path, callback)**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/home', (req, res) => {
        res.send('Welcome to Home Page');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để xử lý yêu cầu GET với route cụ thể.
    - **Ví dụ**: `app.get('/home', callback)` xử lý các yêu cầu GET tại route `/home`.



11. **app.listen()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.listen(3000, () => {
        console.log('Server is running on port 3000');
    });
    ```
    - **Cách sử dụng**: Được sử dụng để khởi động server và lắng nghe các yêu cầu tại cổng chỉ định.
    - **Ví dụ**: `app.listen(3000)` khởi động server và lắng nghe tại cổng 3000.



12. **app.METHOD()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/home', (req, res) => {
        res.send('Welcome to Home Page');
    });
    
    app.post('/home', (req, res) => {
        res.send('POST Home');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Các phương thức HTTP như `app.get()`, `app.post()`, v.v.
    - **Ví dụ**: `app.get('/home')` xử lý yêu cầu GET tại route `/home`.



13. **app.param()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.param('id', (req, res, next, id) => {
        console.log(`ID is: ${id}`);
        next();
    });
    
    app.get('/user/:id', (req, res) => {
        res.send(`User ID is: ${req.params.id}`);
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để xử lý tham số trong route (ví dụ `:id`).
    - **Ví dụ**: `app.param('id')` xử lý tham số `id` trong URL.



14. **app.path()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/about', (req, res) => {
        res.send(`The current path is ${app.path()}`);
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về đường dẫn root của ứng dụng.
    - **Ví dụ**: `app.path()` trả về đường dẫn root của ứng dụng, ví dụ: `/home`.



15. **app.post()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use(express.json());
    
    app.post('/submit', (req, res) => {
        console.log(req.body);
        res.send('Data received');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để xử lý yêu cầu HTTP POST.
    - **Ví dụ**: `app.post('/submit')` xử lý yêu cầu POST tại route `/submit`.



16. **app.put()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.put('/update', (req, res) => {
        res.send('Data updated');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để xử lý yêu cầu HTTP PUT.
    - **Ví dụ**: `app.put('/update')` xử lý yêu cầu PUT tại route `/update`.



17. **app.render()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.set('view engine', 'ejs');
    
    app.get('/', (req, res) => {
        res.render('index', { title: 'Hello World' });
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để render view với template engine.
    - **Ví dụ**: `app.render()` render ra view với template engine.



18. **app.route()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.route('/user')
        .get((req, res) => {
            res.send('GET User');
        })
        .post((req, res) => {
            res.send('POST User');
        });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để định nghĩa các phương thức HTTP (GET, POST, PUT, DELETE) cho một route cụ thể.
    - **Ví dụ**: `app.route('/user')` xử lý GET và POST cho route `/user`.



19. **app.set()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.set('views', './views');
    
    app.get('/', (req, res) => {
        res.send('View directory is set');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Được sử dụng để thiết lập các cấu hình trong ứng dụng.
    - **Ví dụ**: `app.set('views', './views')` thiết lập thư mục chứa view templates.
### Req
#### Attribute
1. **req.app**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use((req, res, next) => {
        console.log(req.app);  // Trả về ứng dụng Express
        next();
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về đối tượng ứng dụng Express (app) mà yêu cầu này được xử lý.
    - **Ví dụ**: `req.app` có thể được sử dụng để truy cập các cài đặt và middleware của ứng dụng.



2. **req.baseUrl**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use('/api', (req, res) => {
        res.send(`Base URL: ${req.baseUrl}`);  // /api
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về URL cơ bản mà route hiện tại được gắn vào (bao gồm cả tiền tố của middleware).
    - **Ví dụ**: `req.baseUrl` sẽ trả về `/api` nếu route được gắn vào `/api`.



3. **req.body**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use(express.json());
    
    app.post('/data', (req, res) => {
        console.log(req.body);  // Trả về dữ liệu JSON trong body của yêu cầu
        res.send('Received data');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Lưu trữ dữ liệu trong thân của yêu cầu (chỉ có sau khi sử dụng middleware như `express.json()` hoặc `express.urlencoded()`).
    - **Ví dụ**: `req.body` chứa dữ liệu từ yêu cầu POST hoặc PUT.



4. **req.cookies**
    ```javascript
    const express = require('express');
    const cookieParser = require('cookie-parser');
    const app = express();
    
    app.use(cookieParser());
    
    app.get('/', (req, res) => {
        console.log(req.cookies);  // Trả về các cookie từ yêu cầu
        res.send('Cookies received');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về đối tượng chứa tất cả các cookie mà client gửi đến server.
    - **Ví dụ**: `req.cookies` trả về đối tượng như `{ username: 'John' }` nếu có cookie `username=John`.



5. **req.fresh**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        if (req.fresh) {
            res.send('Cache is fresh');
        } else {
            res.send('Cache is stale');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem yêu cầu có phải là mới hay không, thường dùng với HTTP cache.
    - **Ví dụ**: `req.fresh` trả về `true` nếu yêu cầu được coi là mới (tức là không cần phải làm mới từ server).



6. **req.hostname**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.hostname);  // Trả về hostname của yêu cầu
        res.send('Hostname is logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về hostname của yêu cầu.
    - **Ví dụ**: `req.hostname` có thể trả về tên miền của server, ví dụ: `localhost` hoặc `example.com`.



7. **req.ip**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.ip);  // Trả về địa chỉ IP của client
        res.send('IP logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về địa chỉ IP của client thực hiện yêu cầu.
    - **Ví dụ**: `req.ip` trả về địa chỉ IP của client như `127.0.0.1` hoặc địa chỉ IP công cộng nếu truy cập từ xa.



8. **req.ips**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.ips);  // Trả về danh sách các địa chỉ IP từ xa
        res.send('IPs logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về mảng các địa chỉ IP mà yêu cầu đi qua, hữu ích khi ứng dụng được proxy qua nhiều server.
    - **Ví dụ**: `req.ips` có thể trả về một mảng như `['192.168.1.1', '203.0.113.0']`.



9. **req.method**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.method);  // Trả về phương thức HTTP của yêu cầu
        res.send('Method logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về phương thức HTTP của yêu cầu (GET, POST, PUT, DELETE, v.v...).
    - **Ví dụ**: `req.method` trả về `GET` nếu yêu cầu là GET.



10. **req.originalUrl**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/user/:id', (req, res) => {
        console.log(req.originalUrl);  // Trả về URL gốc của yêu cầu
        res.send('Original URL logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về URL gốc mà yêu cầu đã được gửi đến, bao gồm cả query string.
    - **Ví dụ**: `req.originalUrl` sẽ trả về `/user/123?search=test`.



11. **req.params**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/user/:id', (req, res) => {
        console.log(req.params);  // Trả về các tham số route trong URL
        res.send('Params logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về đối tượng chứa các tham số route, ví dụ: `:id` trong URL `/user/:id`.
    - **Ví dụ**: `req.params.id` trả về giá trị của tham số `id` trong URL, ví dụ: `123`.



12. **req.path**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.path);  // Trả về đường dẫn của yêu cầu mà không bao gồm domain
        res.send('Path logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về đường dẫn của yêu cầu, không bao gồm hostname hoặc query string.
    - **Ví dụ**: `req.path` có thể trả về `/user/123`.



13. **req.protocol**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.protocol);  // Trả về giao thức của yêu cầu (http hoặc https)
        res.send('Protocol logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về giao thức HTTP của yêu cầu (http hoặc https).
    - **Ví dụ**: `req.protocol` có thể trả về `https` nếu yêu cầu sử dụng HTTPS.



14. **req.query**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.query);  // Trả về các tham số query trong URL
        res.send('Query parameters logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về đối tượng chứa các tham số query trong URL.
    - **Ví dụ**: `req.query` sẽ trả về đối tượng như `{ search: 'test' }` nếu URL là `/search?search=test`.



15. **req.route**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/user/:id', (req, res) => {
        console.log(req.route);  // Trả về thông tin về route hiện tại
        res.send('Route logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về thông tin về route hiện tại, bao gồm các phương thức HTTP đã được định nghĩa.
    - **Ví dụ**: `req.route` trả về route `/user/:id` khi có yêu cầu đến đó.


16. **req.secure**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.secure);  // Trả về true nếu yêu cầu được gửi qua HTTPS
        res.send('Secure status logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về `true` nếu yêu cầu được gửi qua HTTPS, ngược lại trả về `false`.
    - **Ví dụ**: `req.secure` trả về `true` nếu giao thức là `https`.



17. **req.signedCookies**
    ```javascript
    const express = require('express');
    const cookieParser = require('cookie-parser');
    const app = express();
    
    app.use(cookieParser('secret'));
    
    app.get('/', (req, res) => {
        console.log(req.signedCookies);  // Trả về các signed cookies
        res.send('Signed Cookies logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về các cookie đã được ký từ client.
    - **Ví dụ**: `req.signedCookies` trả về các cookie đã được mã hóa với một khóa bí mật.


18. **req.stale**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        if (req.stale) {
            res.send('Cache is stale');
        } else {
            res.send('Cache is fresh');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem yêu cầu có phải là cũ hay không, sử dụng cho mục đích cache.
    - **Ví dụ**: `req.stale` trả về `true` nếu yêu cầu được coi là cũ.



19. **req.subdomains**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        console.log(req.subdomains);  // Trả về mảng các subdomains của yêu cầu
        res.send('Subdomains logged');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Trả về một mảng các subdomains của yêu cầu, nếu có. Subdomains là các phần nhỏ của tên miền (ví dụ, `sub.example.com` thì `sub` là subdomain).
    - **Ví dụ**: `req.subdomains` sẽ trả về một mảng như `['sub']` nếu URL là `sub.example.com`.



20. **req.xhr**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        if (req.xhr) {
            res.send('This is an AJAX request');
        } else {
            res.send('This is not an AJAX request');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem yêu cầu có phải là một yêu cầu AJAX (XMLHttpRequest) hay không.
    - **Ví dụ**: `req.xhr` trả về `true` nếu yêu cầu được gửi từ JavaScript (ví dụ, thông qua `fetch` hoặc `XMLHttpRequest`), ngược lại sẽ trả về `false`.
#### Method


21. **req.accepts()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        if (req.accepts('json')) {
            res.json({ message: 'Accepted JSON' });
        } else {
            res.send('JSON not accepted');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem client có chấp nhận loại nội dung nhất định không (ví dụ: JSON, HTML, v.v.).
    - **Ví dụ**: `req.accepts('json')` trả về `true` nếu client có thể xử lý dữ liệu JSON.



22. **req.acceptsCharsets()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        if (req.acceptsCharsets('utf-8')) {
            res.send('UTF-8 charset accepted');
        } else {
            res.send('Charset not accepted');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem client có chấp nhận bộ mã ký tự (charset) nhất định không.
    - **Ví dụ**: `req.acceptsCharsets('utf-8')` trả về `true` nếu client có thể xử lý charset `utf-8`.



23. **req.acceptsEncodings()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        if (req.acceptsEncodings('gzip')) {
            res.send('Gzip encoding accepted');
        } else {
            res.send('Encoding not accepted');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem client có chấp nhận kiểu mã hóa nội dung nhất định không (ví dụ: gzip, deflate).
    - **Ví dụ**: `req.acceptsEncodings('gzip')` trả về `true` nếu client có thể xử lý mã hóa nội dung `gzip`.



24. **req.acceptsLanguages()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        if (req.acceptsLanguages('en')) {
            res.send('English accepted');
        } else {
            res.send('Language not accepted');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem client có chấp nhận ngôn ngữ nhất định không (ví dụ: 'en' cho tiếng Anh).
    - **Ví dụ**: `req.acceptsLanguages('en')` trả về `true` nếu client có thể xử lý ngôn ngữ `en` (tiếng Anh).



25. **req.get()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        const userAgent = req.get('User-Agent');
        res.send(`User-Agent: ${userAgent}`);
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Lấy giá trị của một trường header trong yêu cầu HTTP.
    - **Ví dụ**: `req.get('User-Agent')` trả về thông tin User-Agent từ header của yêu cầu.



26. **req.is()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.post('/', (req, res) => {
        if (req.is('json')) {
            res.send('Content type is JSON');
        } else {
            res.send('Content type is not JSON');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem kiểu nội dung của yêu cầu có khớp với kiểu MIME cho trước không.
    - **Ví dụ**: `req.is('json')` trả về `true` nếu kiểu nội dung của yêu cầu là `application/json`.



27. **req.param()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/:id', (req, res) => {
        const id = req.param('id');
        res.send(`The ID is ${id}`);
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Lấy tham số từ URL hoặc query string của yêu cầu.
    - **Ví dụ**: `req.param('id')` trả về giá trị của tham số `id` trong URL (ví dụ: `req.param('id')` sẽ trả về giá trị của `id` từ `/123`).


28. **req.range()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        const range = req.range(0, 100);  // Lấy dải byte yêu cầu
        if (range) {
            res.send(`Range requested: ${JSON.stringify(range)}`);
        } else {
            res.send('No range requested');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Phân tích dải byte yêu cầu trong header `Range`.
    - **Ví dụ**: `req.range(0, 100)` phân tích dải byte từ 0 đến 100 nếu header `Range` có trong yêu cầu.
### Res
#### Attribute
1. **res.app**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        const appName = res.app.get('name');  // Lấy tên ứng dụng từ app.locals
        res.send(`App Name: ${appName}`);
    });
    
    app.set('name', 'My Express App');
    app.listen(3000);
    ```
    - **Cách sử dụng**: Truy cập vào ứng dụng Express từ đối tượng `res`. Thường dùng để lấy các biến hoặc cấu hình của ứng dụng.
    - **Ví dụ**: `res.app.get('name')` lấy giá trị của biến cấu hình `name` từ ứng dụng, nếu đã được đặt.


2. **res.headersSent**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        if (!res.headersSent) {
            res.send('Hello, world!');
        } else {
            console.log('Headers already sent');
        }
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kiểm tra xem tiêu đề (headers) của phản hồi đã được gửi hay chưa. Hữu ích để tránh việc gửi nhiều phản hồi trong một yêu cầu.
    - **Ví dụ**: `res.headersSent` trả về `true` nếu tiêu đề của phản hồi đã được gửi, giúp ngăn chặn việc gửi dữ liệu hoặc tiêu đề nhiều lần.

3. **res.locals**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use((req, res, next) => {
        res.locals.username = 'John Doe';  // Thiết lập giá trị cho res.locals
        next();
    });
    
    app.get('/', (req, res) => {
        res.send(`Hello, ${res.locals.username}`);
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Lưu trữ các biến địa phương để sử dụng trong các middleware hoặc trong các views (nếu sử dụng template engine).
    - **Ví dụ**: `res.locals.username = 'John Doe'` lưu trữ giá trị trong `res.locals`, có thể được sử dụng ở bất kỳ middleware hoặc route nào sau đó.

#### Method
4. **res.append()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.append('X-Custom-Header', 'Some value');
        res.send('Header appended');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Thêm giá trị vào một hoặc nhiều tiêu đề HTTP mà chưa gửi phản hồi. Có thể gọi nhiều lần để thêm nhiều giá trị vào cùng một tiêu đề.
    - **Ví dụ**: `res.append('X-Custom-Header', 'Some value')` sẽ thêm giá trị `'Some value'` vào tiêu đề `X-Custom-Header`.



5. **res.attachment()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/file', (req, res) => {
        res.attachment('file.txt');  // Đặt tiêu đề Content-Disposition
        res.send('Download this file!');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Thiết lập tiêu đề `Content-Disposition` để yêu cầu tải xuống tệp tin, kèm theo tên tệp tin mặc định.
    - **Ví dụ**: `res.attachment('file.txt')` sẽ gửi phản hồi yêu cầu tải xuống tệp với tên `file.txt`.



6. **res.cookie()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/set-cookie', (req, res) => {
        res.cookie('user', 'John Doe', { maxAge: 900000, httpOnly: true });
        res.send('Cookie has been set');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Gửi một cookie đến trình duyệt. Bạn có thể đặt các tùy chọn như `maxAge`, `secure`, `httpOnly`.
    - **Ví dụ**: `res.cookie('user', 'John Doe')` sẽ thiết lập một cookie có tên là `user` và giá trị là `'John Doe'`.



7. **res.clearCookie()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/clear-cookie', (req, res) => {
        res.clearCookie('user');
        res.send('Cookie has been cleared');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Xóa cookie đã được thiết lập trước đó. Thường được sử dụng trong quá trình đăng xuất.
    - **Ví dụ**: `res.clearCookie('user')` sẽ xóa cookie có tên `user`.



8. **res.download()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/download', (req, res) => {
        res.download('./path/to/file.txt', 'file.txt', (err) => {
            if (err) {
                res.status(500).send('Download failed');
            }
        });
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Gửi một tệp về trình duyệt để tải xuống. Bạn có thể chỉ định tên tệp để trình duyệt sử dụng khi tải xuống.
    - **Ví dụ**: `res.download('./path/to/file.txt')` sẽ tải xuống tệp từ đường dẫn đã cho.



9. **res.end()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.end('End the response');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Kết thúc quá trình phản hồi HTTP. Không gửi thêm dữ liệu vào phản hồi.
    - **Ví dụ**: `res.end('End the response')` sẽ kết thúc phản hồi ngay lập tức và gửi một chuỗi đơn giản.



10. **res.format()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/format', (req, res) => {
        res.format({
            'text/plain': () => {
                res.send('Plain text response');
            },
            'application/json': () => {
                res.json({ message: 'JSON response' });
            },
            'default': () => {
                res.status(406).send('Not Acceptable');
            }
        });
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Dựa trên loại dữ liệu mà client chấp nhận (từ `Accept` header), gửi phản hồi tương ứng.
    - **Ví dụ**: `res.format()` giúp lựa chọn loại phản hồi (như `text/plain` hoặc `application/json`) dựa trên yêu cầu từ client.



11. **res.get()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/header', (req, res) => {
        const contentType = res.get('Content-Type');
        res.send(`Content-Type is: ${contentType}`);
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Lấy giá trị của một tiêu đề HTTP trong phản hồi.
    - **Ví dụ**: `res.get('Content-Type')` sẽ trả về giá trị của tiêu đề `Content-Type` trong phản hồi.



12. **res.json()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/json', (req, res) => {
        res.json({ message: 'This is JSON response' });
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Gửi dữ liệu JSON về client. Express tự động thiết lập tiêu đề `Content-Type` thành `application/json`.
    - **Ví dụ**: `res.json({ message: 'This is JSON response' })` gửi một đối tượng JSON cho client.



13. **res.jsonp()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/jsonp', (req, res) => {
        res.jsonp({ message: 'This is a JSONP response' });
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Gửi phản hồi JSONP. Phản hồi này được bao bọc trong một hàm callback để hỗ trợ cross-domain requests.
    - **Ví dụ**: `res.jsonp({ message: 'This is a JSONP response' })` gửi dữ liệu JSONP.



14. **res.links()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.links({
            next: '/page/2',
            prev: '/page/4'
        });
        res.send('Links header added');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Thêm tiêu đề `Link` vào phản hồi, thường dùng trong phân trang (pagination).
    - **Ví dụ**: `res.links({ next: '/page/2', prev: '/page/4' })` thêm các liên kết phân trang vào tiêu đề.



15. **res.location()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.location('https://example.com').send('Redirecting...');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Thiết lập URL mà client sẽ được chuyển hướng đến. Được sử dụng với mã trạng thái 3xx.
    - **Ví dụ**: `res.location('https://example.com')` thiết lập URL cho chuyển hướng.




16. **res.redirect()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/redirect', (req, res) => {
        res.redirect('https://example.com');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Chuyển hướng yêu cầu đến một URL khác. Có thể sử dụng mã trạng thái HTTP 3xx để chỉ định kiểu chuyển hướng.
    - **Ví dụ**: `res.redirect('https://example.com')` sẽ chuyển hướng client đến URL `'https://example.com'`.



17. **res.render()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.set('view engine', 'ejs');
    
    app.get('/', (req, res) => {
        res.render('index', { title: 'My Express App' });
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Render một view template (chẳng hạn như EJS, Pug) và gửi HTML về cho client.
    - **Ví dụ**: `res.render('index', { title: 'My Express App' })` sẽ render view `'index'` với dữ liệu `{ title: 'My Express App' }`.



18. **res.send()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.send('Hello, World!');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Gửi một phản hồi tới client dưới nhiều dạng khác nhau như chuỗi, đối tượng JSON, hay mảng.
    - **Ví dụ**: `res.send('Hello, World!')` gửi một chuỗi văn bản `'Hello, World!'` về client.



19. **res.sendFile()**
    ```javascript
    const express = require('express');
    const path = require('path');
    const app = express();
    
    app.get('/download', (req, res) => {
        res.sendFile(path.join(__dirname, 'file.txt'));
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Gửi một tệp tin từ server đến client.
    - **Ví dụ**: `res.sendFile(path.join(__dirname, 'file.txt'))` gửi tệp `'file.txt'` đến client.



20. **res.sendStatus()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.sendStatus(404);  // Gửi trạng thái 404 Not Found
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Gửi một mã trạng thái HTTP (ví dụ: 200, 404, 500) kèm theo thông báo trạng thái tương ứng.
    - **Ví dụ**: `res.sendStatus(404)` sẽ gửi phản hồi với mã trạng thái 404 và thông báo "Not Found".



21. **res.set()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.set('X-Custom-Header', 'Some value');
        res.send('Custom header set');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Thiết lập các tiêu đề HTTP cho phản hồi.
    - **Ví dụ**: `res.set('X-Custom-Header', 'Some value')` sẽ thêm tiêu đề `X-Custom-Header` với giá trị `'Some value'`.



22. **res.status()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.status(404).send('Page not found');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Đặt mã trạng thái HTTP cho phản hồi.
    - **Ví dụ**: `res.status(404).send('Page not found')` sẽ gửi mã trạng thái 404 kèm theo thông báo `'Page not found'`.



23. **res.type()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/json', (req, res) => {
        res.type('json').send({ message: 'This is a JSON response' });
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Thiết lập loại nội dung của phản hồi (ví dụ: `json`, `html`, `text`).
    - **Ví dụ**: `res.type('json').send({ message: 'This is a JSON response' })` thiết lập loại nội dung là `json` và gửi một đối tượng JSON.



24. **res.vary()**
    ```javascript
    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.vary('Accept-Encoding');
        res.send('Vary header set');
    });
    
    app.listen(3000);
    ```
    - **Cách sử dụng**: Thiết lập tiêu đề `Vary`, cho biết server có thể phản hồi khác nhau tùy thuộc vào giá trị của một hoặc nhiều header trong yêu cầu.
    - **Ví dụ**: `res.vary('Accept-Encoding')` thêm tiêu đề `Vary: Accept-Encoding` vào phản hồi.
### Example
1. `app.get('/user/:id', (req, res))`
    ```javascript
    app.get('/user/:id', (req, res) => {
      res.send('user ' + req.params.id);
    });
    ```
    - **Cách sử dụng**: 
      - `app.get('/user/:id', callback)` định nghĩa một route HTTP GET với tham số động trong URL.
      - Tham số `:id` có thể truy xuất qua `req.params.id`.
    - **Ví dụ**: 
      - Nếu URL là `/user/123`, `req.params.id` sẽ trả về `123`, và phản hồi sẽ là `'user 123'`.

2. `app.get('/users/:id', function(req, res))`
    ```javascript
    app.get('/users/:id', function(req, res) {
      // handler code
    });
    ```
    - **Cách sử dụng**: 
      - `app.get('/users/:id', callback)` định nghĩa một route HTTP GET với tham số động `:id` trong URL.
      - `req.params.id` sẽ chứa giá trị của tham số `id` được truyền trong URL.
    - **Ví dụ**: 
      - Nếu URL là `/users/456`, `req.params.id` sẽ trả về `456`. Trong handler code, bạn có thể sử dụng giá trị này để lấy thông tin người dùng từ cơ sở dữ liệu hoặc thực hiện các thao tác khác.


3. `app.get('/posts/:id([0-9]+)/:slug([a-z]+)', function(req, res))`
    ```javascript
    app.get('/posts/:id([0-9]+)/:slug([a-z]+)', function(req, res) {
      var id = req.params.id;
      var slug = req.params.slug;
      res.send('Post ' + id + ': ' + slug);
    });
    ```
    - **Cách sử dụng**: 
      - `app.get()` định nghĩa route HTTP GET với các tham số động trong URL.
      - Các tham số `:id([0-9]+)` và `:slug([a-z]+)` sử dụng biểu thức chính quy để chỉ định rằng `id` chỉ có thể là một chuỗi số (`[0-9]+`) và `slug` chỉ có thể là một chuỗi chữ thường (`[a-z]+`).
      - `req.params.id` và `req.params.slug` cho phép truy xuất giá trị của các tham số này.
    - **Ví dụ**: 
      - Nếu URL là `/posts/123/hello`, `req.params.id` sẽ là `123` và `req.params.slug` sẽ là `hello`. Phản hồi sẽ là: `'Post 123: hello'`.
    
4. `app.get('/users/:userId/posts/:postId', function(req, res))`
    ```javascript
    app.get('/users/:userId/posts/:postId', function(req, res) {
      // handler code
    });
    ```
    - **Cách sử dụng**: 
      - `app.get('/users/:userId/posts/:postId', callback)` định nghĩa một route HTTP GET với hai tham số động `:userId` và `:postId` trong URL.
      - `req.params.userId` và `req.params.postId` sẽ chứa giá trị của các tham số `userId` và `postId` được truyền trong URL.
    - **Ví dụ**: 
      - Nếu URL là `/users/123/posts/456`, `req.params.userId` sẽ trả về `123` và `req.params.postId` sẽ trả về `456`.
      - Bạn có thể sử dụng các giá trị này để lấy thông tin người dùng và bài viết từ cơ sở dữ liệu hoặc thực hiện các thao tác khác.
5. `app.all('/secret', (req, res, next))`
    ```javascript
    app.all('/secret', (req, res, next) => {
      console.log('Accessing the secret section ...');
      next(); // pass control to the next handler
    });
    ```
    - **Cách sử dụng**: 
      - `app.all('/secret', callback)` định nghĩa một route xử lý tất cả các phương thức HTTP (GET, POST, PUT, DELETE, v.v.) tại URL `/secret`.
      - Hàm callback nhận ba đối số: `req`, `res`, và `next`.
      - `next()` chuyển quyền kiểm soát sang handler tiếp theo trong chuỗi middleware hoặc route.
    - **Ví dụ**: 
      - Khi người dùng truy cập URL `/secret` với bất kỳ phương thức HTTP nào, console sẽ hiển thị "Accessing the secret section ...".
      - Sau đó, `next()` chuyển quyền kiểm soát tới middleware hoặc route tiếp theo.
6. `app.get('/users/:id(\\d+)', (req, res))`
    ```javascript
    app.get('/users/:id(\\d+)', (req, res) => {
      const userId = req.params.id;
      // ...
    });
    ```
    - **Cách sử dụng**:
      - `app.get('/users/:id(\\d+)', callback)` định nghĩa một route xử lý yêu cầu GET tới URL `/users/:id`, trong đó `:id` là tham số được truyền vào URL.
      - `:id(\\d+)` sử dụng biểu thức chính quy để chỉ định rằng giá trị của `:id` chỉ được nhận các ký tự số (digit).
      - Hàm callback nhận hai đối số: `req` (yêu cầu) và `res` (phản hồi).
      - `req.params.id` trả về giá trị của tham số `id` từ URL.
    - **Ví dụ**:
      - URL `/users/123` sẽ khớp với route và trả về `req.params.id` là `123`.
      - Nếu `:id` không phải là một chuỗi số, route này sẽ không khớp và không xử lý yêu cầu.
7. `app.param('id', callback)`
    ```javascript
    app.param('id', (req, res, next, id) => {
      if (isValidUserId(id)) {
        req.params.id = id;
        next();
      } else {
        res.status(400).send('Invalid user ID');
      }
    });
    ```
    - **Cách sử dụng**:
      - `app.param('id', callback)` được sử dụng để định nghĩa middleware cho các tham số route.
      - Middleware này sẽ được gọi mỗi khi có một yêu cầu với tham số `id` trong URL.
      - Hàm callback có bốn tham số: `req` (yêu cầu), `res` (phản hồi), `next` (hàm tiếp theo), và `id` (giá trị của tham số `id` từ URL).
      - Nếu giá trị của `id` hợp lệ (ví dụ qua hàm `isValidUserId`), ta tiếp tục xử lý yêu cầu với `next()`.
      - Nếu giá trị của `id` không hợp lệ, trả về phản hồi lỗi với mã trạng thái `400` và thông báo lỗi.
    - **Ví dụ**:
      - Với URL `/users/123`, middleware sẽ kiểm tra `123` có hợp lệ hay không.
      - Nếu `123` là ID hợp lệ, yêu cầu tiếp tục đến các handler tiếp theo.
      - Nếu ID không hợp lệ, server sẽ trả về mã lỗi `400` và thông báo "Invalid user ID".
8. Template
    ```javascript
    const express = require('express');
    const app = express();

    // Set the view engine to use EJS templates
    app.set('view engine', 'ejs');

    // Define a route that renders a home page
    app.get('/', (req, res) => {
    res.render('home', { title: 'Home Page' });
    });

    // Define a route that renders a contact page
    app.get('/contact', (req, res) => {
    res.render('contact', { title: 'Contact Us' });
    });

    // Define a route that renders a product page
    app.get('/product/:id', (req, res) => {
    const productId = req.params.id;
    // Query the database to get the product with the specified ID
    const product = getProductById(productId);
    res.render('product', { title: product.name, product });
    });

    // Start the server
    app.listen(3000, () => {
    console.log('Server started on port 3000');
    });
    ```

### SOON