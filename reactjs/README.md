# React CheatSheet

1. [Syntax](#syntax)
2. [Negative](#negative)

### Negative
1. **useNavigate()**
    ```javascript
    import React from 'react';
    import { useNavigate } from 'react-router-dom';

    function HomeButton() {
      const navigate = useNavigate();

      return (
        <button onClick={() => navigate('/')}>Go Home</button>
      );
    }
    ```
    - **Cách sử dụng**: `useNavigate` là một hook được cung cấp bởi `React Router` để điều hướng người dùng đến các route khác trong ứng dụng.
    - **Ví dụ**: Trong ví dụ trên, khi nhấn vào nút "Go Home", người dùng sẽ được điều hướng đến route `/` (trang chủ).

2. **`<Navigate to='/'/>`**
    ```javascript
    import React from 'react';
    import { Navigate } from 'react-router-dom';

    function ProtectedRoute({ isLoggedIn }) {
      if (!isLoggedIn) {
        return <Navigate to="/login" />;
      }

      return <div>Welcome to the protected page!</div>;
    }
    ```
    - **Cách sử dụng**: `<Navigate />` là một component được cung cấp bởi React Router để điều hướng người dùng dựa trên điều kiện nhất định.
    - **Ví dụ**: Trong ví dụ trên, nếu `isLoggedIn` là `false`, người dùng sẽ được chuyển hướng đến trang `/login`. Nếu không, họ sẽ thấy nội dung của trang bảo vệ.

### Hook
1. **useState()**
    ```javascript
    import React, { useState } from 'react';

    function Counter() {
      const [count, setCount] = useState(0);

      return (
        <div>
          <p>You clicked {count} times</p>
          <button onClick={() => setCount(count + 1)}>Click me</button>
        </div>
      );
    }
    ```
    - **Cách sử dụng**: `useState` giúp bạn khai báo và quản lý state trong các component chức năng.
    - **Ví dụ**: Trong ví dụ trên, `count` là state, và `setCount` là hàm cập nhật giá trị của state.
2. **useEffect()**
    ```javascript
    import React, { useState, useEffect } from 'react';

    function FetchData() {
      const [data, setData] = useState(null);

      useEffect(() => {
        fetch('https://api.example.com/data')
          .then(response => response.json())
          .then(data => setData(data));
      }, []);  // Chạy một lần khi component mount

      return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
    }
    ```
    - **Cách sử dụng**: `useEffect` dùng để xử lý các hiệu ứng phụ như gọi API, thay đổi DOM, đăng ký sự kiện, v.v.
    - **Ví dụ**: Trong ví dụ trên, `useEffect` được sử dụng để lấy dữ liệu từ API khi component được mount.
3. **useContext()**
    ```javascript
    import React, { useContext } from 'react';

    const ThemeContext = React.createContext('light');

    function ThemedComponent() {
      const theme = useContext(ThemeContext);

      return <div>Current theme is {theme}</div>;
    }

    function App() {
      return (
        <ThemeContext.Provider value="dark">
          <ThemedComponent />
        </ThemeContext.Provider>
      );
    }
    ```
    - **Cách sử dụng**: `useContext` cho phép bạn truy cập giá trị của một context mà không cần phải sử dụng `Context.Consumer`.
    - **Ví dụ**: Ở ví dụ trên, `useContext` cho phép `ThemedComponent` truy cập giá trị `theme` từ `ThemeContext`.
4. **useReducer()**
    ```javascript
    import React, { useReducer } from 'react';

    const initialState = { count: 0 };

    function reducer(state, action) {
      switch (action.type) {
        case 'increment':
          return { count: state.count + 1 };
        case 'decrement':
          return { count: state.count - 1 };
        default:
          return state;
      }
    }

    function Counter() {
      const [state, dispatch] = useReducer(reducer, initialState);

      return (
        <div>
          <p>Count: {state.count}</p>
          <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
          <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>
        </div>
      );
    }
    ```
    - **Cách sử dụng**: `useReducer` là hook dùng để quản lý state phức tạp hơn với các hành động cụ thể.
    - **Ví dụ**: Ở ví dụ trên, `useReducer` được sử dụng để quản lý state `count`, và các hành động `increment` và `decrement` cập nhật giá trị của `count`.
5. **useRef()**
    ```javascript
    import React, { useRef } from 'react';

    function FocusInput() {
      const inputRef = useRef();

      const focusInput = () => {
        inputRef.current.focus();
      };

      return (
        <div>
          <input ref={inputRef} type="text" />
          <button onClick={focusInput}>Focus the input</button>
        </div>
      );
    }
    ```
    - **Cách sử dụng**: `useRef` được sử dụng để tạo và lưu trữ một tham chiếu tới một DOM element hoặc một giá trị nào đó mà không làm trigger lại render của component.
    - **Ví dụ**: Trong ví dụ trên, `useRef` được sử dụng để tạo tham chiếu tới một input và gọi `focus()` để focus vào input khi nhấn nút.
6. **useMemo()**
    ```javascript
    import React, { useMemo, useState } from 'react';

    function ExpensiveCalculation() {
      const [number, setNumber] = useState(0);

      const expensiveCalculation = useMemo(() => {
        console.log('Calculating...');
        return number * 2;
      }, [number]);

      return (
        <div>
          <p>Result: {expensiveCalculation}</p>
          <button onClick={() => setNumber(number + 1)}>Increment</button>
        </div>
      );
    }
    ```
    - **Cách sử dụng**: `useMemo` giúp tối ưu hóa hiệu suất bằng cách ghi nhớ giá trị của một phép tính phức tạp giữa các lần render.
    - **Ví dụ**: Ở ví dụ trên, `useMemo` sẽ chỉ tính toán lại giá trị khi `number` thay đổi, giúp tránh tính toán lại không cần thiết.
7. **useCallback()**
    ```javascript
    import React, { useCallback, useState } from 'react';

    function Parent() {
      const [count, setCount] = useState(0);

      const increment = useCallback(() => {
        setCount((prevCount) => prevCount + 1);
      }, []); // Chỉ tạo mới hàm khi cần thiết

      return (
        <div>
          <Child increment={increment} />
          <p>Count: {count}</p>
        </div>
      );
    }

    function Child({ increment }) {
      return <button onClick={increment}>Increment</button>;
    }
    ```
    - **Cách sử dụng**: `useCallback` được sử dụng để ghi nhớ hàm, tránh việc tạo lại hàm trong mỗi lần render.
    - **Ví dụ**: Trong ví dụ trên, `useCallback` giúp tránh việc tạo lại hàm `increment` trong mỗi lần render của component `Parent`.
8. **useImperativeHandle()**
    ```javascript
    import React, { useImperativeHandle, forwardRef, useRef } from 'react';

    const CustomInput = forwardRef((props, ref) => {
      const inputRef = useRef();

      useImperativeHandle(ref, () => ({
        focus: () => {
          inputRef.current.focus();
        }
      }));

      return <input ref={inputRef} />;
    });

    function Parent() {
      const inputRef = useRef();

      return (
        <div>
          <CustomInput ref={inputRef} />
          <button onClick={() => inputRef.current.focus()}>Focus the custom input</button>
        </div>
      );
    }
    ```
    - **Cách sử dụng**: `useImperativeHandle` cho phép bạn tùy chỉnh các giá trị mà bạn muốn expose ra ngoài component khi sử dụng `forwardRef`.
    - **Ví dụ**: Component `CustomInput` chỉ expose một phương thức `focus` ra ngoài.
9. **useLayoutEffect()**
    ```javascript
    import React, { useLayoutEffect, useRef } from 'react';

    function MeasureSize() {
      const divRef = useRef();

      useLayoutEffect(() => {
        console.log('Width:', divRef.current.offsetWidth);
      }, []);

      return <div ref={divRef}>Hello</div>;
    }
    ```
    - **Cách sử dụng**: `useLayoutEffect` giống như `useEffect`, nhưng được gọi ngay sau khi DOM đã được cập nhật và trước khi trình duyệt vẽ lại màn hình.
    - **Ví dụ**: Chúng ta đo kích thước của phần tử div ngay sau khi DOM cập nhật.
10. **useDebugValue()**
    ```javascript
    import React, { useState, useDebugValue } from 'react';

    function useCustomHook(value) {
      useDebugValue(value > 10 ? 'High' : 'Low');
      return value;
    }

    function Component() {
      const value = useCustomHook(5);

      return <div>{value}</div>;
    }
    ```
    - **Cách sử dụng**: `useDebugValue` được sử dụng để hiển thị giá trị trong React DevTools cho custom hook.
    - **Ví dụ**: `useDebugValue` giúp bạn ghi chú trạng thái bên trong hook và hiển thị nó trong DevTools.