# *JSX*

### 1. JSX là gì ??
- JSX  -> Javascript XML
- Dùng để viết HTMl trong file Javascript
- JSX cho phép chúng ta viết HTML trong React.
-Note: 
- JSX không phải HTML
- Vì JSX gần với JavaScript hơn là HTML, nên React DOM sử dụng camelCasequy ước đặt tên thuộc tính thay vì tên thuộc tính HTML.

### 2. Sử dụng JSX ?
####    a. Những biểu thức trong JSX
- Trong ví dụ dưới đây, chúng tôi khai báo một biến được gọi name và sau đó sử dụng nó bên trong JSX bằng cách gói nó trong dấu ngoặc nhọn:

```javascript
    const name = 'Luong';
    const element = <h1>Hello, {name}</h1>;

    ReactDOM.render(element, document.getElementById('root')
    )
```

####    b. JSX cũng là một biểu thức
- bạn có thể sử dụng JSX bên trong các câu lệnh if và vòng lặp for , gán nó cho các biến, chấp nhận nó dưới dạng đối số và trả về nó từ các hàm:

 ```javascript
    function getGreeting(user) {
    if (user) {
    return <h1>Hello, {formatName(user)} !</h1>;
    }
    return <h1>Hello, Stranger.</h1>;
    }
```

####    c. Chỉ định các thuộc tính với JSX
- Bạn có thể sử dụng dấu ngoặc kép để chỉ định các ký tự chuỗi làm thuộc tính:
- Ex: 
```javascript
const element = <a href="https://www.reactjs.org"> link </a>;
```
- Bạn cũng có thể sử dụng dấu ngoặc nhọn để nhúng biểu thức JavaScript vào một thuộc tính:
- Ex:
```javascript   
    const element = <img src={user.avatarUrl}></img>;
```
- Note: 
  - Không đặt dấu ngoặc kép quanh dấu ngoặc nhọn khi nhúng biểu thức JavaScript vào một thuộc tính. Bạn nên sử dụng dấu ngoặc kép (đối với giá trị chuỗi) hoặc dấu ngoặc nhọn (đối với biểu thức), nhưng không nên sử dụng cả hai trong cùng một thuộc tính.
  - Dùng thư viện bable để chuyển đổi

# *component and props*
- components giống như các hàm JavaScript. Họ chấp nhận các đầu vào bất kỳ (được gọi là “props”) và trả về các phần tử React mô tả những gì sẽ xuất hiện trên màn hình.

##    A. Component
###    1. Rendering a Component
- các phần tử cũng có thể đại diện cho các thành phần do người dùng xác định
- Ex:
```javascript 
ex: const element = <Welcome name="Sara" /> 
```
- Note: Luôn bắt đầu các tên thành phần bằng một chữ cái viết hoa.

###    2. Composing Components
- Nút, biểu mẫu, hộp thoại, màn hình: trong ứng dụng React, tất cả những thứ đó thường được biểu thị dưới dạng component.

###    3. Phân nhỏ Component  
- tách các component thành các thành phần nhỏ hơn.

##    B. props
###    1. Khai niem
- Props là một object được truyền vào trong một components, mỗi components sẽ nhận vào props và trả về react element. Props cho phép chúng ta giao tiếp giữa các components với nhau bằng cách truyền tham số qua lại giữa các components.
  
###    2. Truyền props trong các components
- Có thể truyền dữ liệu từ một component với nhau bằng cách truyền như một attributes trong HTML.
- Giả sử mình muốn truyền cho components có tên Welcome các giá trị như:
```javascript    
    Ex: const App = () => <Welcome name="Luong" age=20>Xin chào </Welcome>
```
- Vậy trong components Welcome giá trị của props sẽ là một object bao gồm các giá trị truyền vào :
```javascript
{
name: "Luong",
age: 20,
children: "Xin chào"
}
```

# *state and lifecycle*
##   A. State
###    1. Khai niem
- State chỉ tồn tại trong phạm vi của components chứa nó, mỗi khi state thay đổi thì components đó sẽ được render lại.
- Khái niệm functional component hay còn được hiểu là stateless component còn class component thì là stateful component.
###    2. Khởi tạo state
```javascript
- this.state = { name : 'freetuts.net' }
```
###    3. Cập nhật một state
```javascript
this.setState((state) => {
    return newValue;
});
```
###    4. Phân biệt state và props
- State: Dữ liệu chỉ nằm trong phạm vi của một component. Nó được sở hữu bởi một components cụ thể mà chỉ là của component đó . Và mỗi khi state thay đổi thì component cũng phải thay đổi theo.
- Props: Dữ liệu đường truyền từ component cha cho componet con, components con khi nhận được sẽ chỉ được đọc mà không thể thay đổi dữ liệu đó.
  
##    B. lifecycle
- Khi một components được khởi chạy nó sẽ phải trải qua 4 giai đoạn chính:
  + initialization
  + mounting
  + updating
  + unmounting
###    1. initialization
- Đây là giai đoạn mà thành phần sẽ bắt đầu hành trình của mình bằng cách khởi tạo state và props.
###    2. mounting
####   a. componentWillMount()
- Được khởi chạy khi một component chuẩn bị được mount (tức là trước khi thực hiện render), sau khi thực hiện xong componentWillMount() thì component mới có thể được mount.
- Lưu ý: Chúng ta không nên thực hiện bất cứ thay đổi nào liên quan đến state, props hay call API ở trong hàm này, bởi thời gian chuẩn bị mount -> mount rất ngắn nên các tác vụ đó không thể hoàn thành kịp
  
####    b. componentDidMount()
- Được gọi khi component đã được mount (render thành công ), quá trình này xảy ra sau khi componentWillMount() thực hiện xong. Trong phương thức này bạn có thể gọi API, thay đổi state, props.
  
##    3. updating
- Trong giai đoạn này, dữ liệu của các phần (props & state) sẽ được cập nhật để đáp ứng với các sự kiện của người dùng như click, gõ, v.v. Điều này dẫn đến việc re-render lại component, ở trong giai đoạn này chúng ta sẽ có 4 phương thức chính:
####    a. shouldComponentUpdate()
- Phương thức này xác định xem component có nên được render lại hay không ? Theo mặc định, nó trả về true. Nhưng bạn có thể thay đổi giá trị trả về của nó theo từng trường hợp.
####    b. componentWillUpdate()
- Phương thức này được gọi trước khi tiến hành re-render, bạn có thể thực hiện các hành động như update state, props,...trong phương thức này trước khi tiến hành re-render
####    c. ComponentDidUpdate()
- Phương thức này được gọi khi component đã re-render xong   . 
  
##   4. unmouting
- Đây là bước cuối cùng trong mỗi component, khi tất cả các tác vụ hoàn thành và bạn tiến hành unmount DOM. Quá trình này chỉ có duy nhất 1 phương thức đó là componentWillUnmount() :

# *functional component*
- Hàm này là một thành phần React hợp lệ vì nó chấp nhận một “props” đơn (viết tắt của thuộc tính) đối số đối tượng với dữ liệu và trả về một phần tử React . Chúng tôi gọi các thành phần như vậy là “function components” bởi vì chúng thực sự là các hàm JavaScript.
```javascript  
    function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
    }
```
- Vậy 1 React Functional Component là:
    + một function Javascript / ES6 function.
    + phải trả về 1 React element.
    + nhận props làm tham số nếu cần.
# *class component*
- Chúng phức tạp hơn functional components ở chỗ nó còn có: phương thức khởi tạo, life-cycle, hàm render() và quản lý state (data).
```javascript
    class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>;
        }
    }
```
- Vì vậy, một React class component là:
  + là một class ES6, nó sẽ là một component khi nó "kế thừa" React component.
  + có thể nhận props (trong hàm khởi tạo) nếu cần.
  + có thể maintain data của nó với state.
  + phải có 1 method render() trả về 1 React element (JSX), or null.

# *Hooks*

- Hook là một hàm đặc biệt cho phép bạn sử dụng các tính năng của React (mà không cần phải tạo class)

## useState 
- Trong lần hiển thị ban đầu, trạng thái (State) được trả về giống với giá trị được truyền như đối số đầu tiên (InitialState).
- Hàm setState được sử dụng để cập nhật trạng thái. Nó chấp nhận một giá trị State mới và xếp hàng đợi một kết xuất lại của component.
- useState trả về một cặp giá trị dưới dạng mảng: state hiện tại và một hàm để update nó.
- seState() áp dụng replacing thay vì merging như bên class component.
- Initial state callback chỉ thực thi 1 lần đầu.
```javascript
    - const [state, setState] = useState(initialCount);
```
- state: định nghĩa tên của state nó có thể là đơn giá trị hoặc object,.. (là   tham số của useState)
- setState: định nghĩa tên function dùng cho việc update state (là tham số của useState)
- initialStateValue: là giá trị ban đầu của state.
```javascript
    - EX: const [count, setCount] = useState(0); #
```
1. Đọc State
- Trong hàm (sử dụng với hooks), chúng ta dùng trực tiếp biến count:
- EX: <p> {count} lần</p>
2. Updating State   
- Trong hàm (sử dụng với hooks), chúng ta đã có biến setState
- setCount(count + 1)
3. Set state có thể dùng với callback
- Set state có thể dùng với callback
    + Ex: 
        setCount(count + 1)  
        setCount(count + 1)  
        setCount(count + 1) 
    count = 2 
- Vì một vài lý do về batch update performance, state không được thay đổi ngay tức khắc sau khi hàm setState() được gọi. Vâng, điều đó có nghĩa là chúng ta không thể call setState() ở dòng đầu tiên và hi vọng nó thay đổi ở dòng tiếp theo.
- React sẽ gộp tất cả những hàm setState() sau đó gọi 1 lần duy nhất, để tránh việc render lại không cần thiết, làm tăng performance của app.
    
-> React sẽ gộp tất cả những hàm setState() sau đó gọi 1 lần duy nhất, để tránh việc render lại không cần thiết, làm tăng performance của app.

- Ngoài cách truyền vào 1 Object, chúng ta có thể truyền 1 function vào hàm setState(), function này nhận vào 2 tham số là prevState và prevProps tại thời điểm các thay đổi được cập nhật. Điều này đảm bảo rằng giá trị được update cuối cùng luôn dựa trên previous state.    
- Ex:
  - setCount(prevState => prevState + 1) 
  - setCount(prevState => prevState + 1) 
  - setCount(prevState => prevState + 1)
- > count = 4 

## useEffect 
- Effect Hook cho phép thực hiện side effect bên trong các function component:
- "side effect": khi có tác động xảy ra khiến dữ liệu bị thay đổi
- Có 2 loại side effect phổ biến trong React component: loại không cần cleanup, và loại cần. Cùng phân biệt 2 loại này kỹ hơn.
- Component cần thực hiện một việc gì đó sau khi render. React sẽ ghi nhớ hàm bạn truyền vào và sau đó gọi lại hàm này sau khi DOM đã update
- Đặt useEffect bên trong component cho phép chúng ta truy xuất đến state count (hoặc bất kỳ prop nào) bên trong effect
- useEffect chạy sau tất cả những lần render. Theo mặc định, nó chạy sau lần render đầu tiên và mỗi lần update.

- Sử dụng khi: 
  + update DOM
  + Call API
  + Listen DOM events (scroll, resize)
    + cleanup(remove listener)
- useEffect(callback, [deps])
    callback: là bắt buộc
    deps: không bắt buộc
- Có 3 trường hơp:
    + TH1 : useEffect(callback,)
    + TH2 : useEffect(callback,[])
    + TH3 : useEffect(callback, [deps])

- Đối với TH1 gọi callback mỗi khi component re-render và gọi callback sau khi component thêm element vào DOM
- Đối với TH2 chỉ gọi lại callback 1 lần sau khi component thêm element vào DOM
- Đối với TH3 callback sẽ được gọi lai mỗi khi deps thay đổi

1. Effect không cần Cleanup
- Đôi lúc, chúng ta muốn chạy một vài đoạn code sau khi React đã cập nhập DOM. Network request, tự ý thay đổi DOM, và logging là những ví dụ điển hình của effect không cần cleanup. Chúng ta gọi như vậy vì có thể chạy chúng và quên ngay lập tức
- Ex: 
```javascript
        import React, { useState, useEffect } from 'react';

        function Example() {
        const [count, setCount] = useState(0);

        useEffect(() => {
            document.title = `You clicked ${count} times`;
        });

         return (
            <div>
                <p>You clicked {count} times</p>
                <button onClick={() => setCount(count + 1)}>
                    Click me
                </button>
            </div>
        );
        } 
```
2. Effect cần Cleanup
- Khi unmounted nó ra thì sự kiện vẫn sẽ được mount ở DOM và không thể sử dụng lại
gây ra hiện tượng rò rỉ bộ nhớ
- cách khắc phục
    + dùng cleanup function
    + dùng return 1 cái hàm remove trong useEffect (closure)
    + trong hàm ý remove  
```javascript
    useEffect(() => {
	window.addEventListener('scroll', handleScroll)
    //Clean UP function
    return () => {
	window.removeEventListener('scroll', handleScroll)
	    }
    })
```

## useLayoutEffect
- Có đặc điểm giống với useEffect khác nhau thứ tự thực hiện công việc
- Quy trình thực hiện 
+ useEffect: 
  - B1. Cập nhật lại State
  - B2. Cập nhật lại Dom (mutated)
  - B3. Render lại UI
  - B4. Gọi cleanup nếu deps thay đổi
  - B5. Gọi useEffect callback
+ useLayoutEffect:
    - B1. Cập nhật lại State
    - B2. Cập nhật lại Dom (mutated)
    - B3. Gọi cleanup nếu deps thay đổi (sync)
    - B4. Gọi useLayoutEffect callback (sync)
    - B5. Render lại UI 
  
## useRef
- lưu các giá trị qua một tham chiếu bên ngoài function component
- useRef trả về một đối tượng ref có thể thay đổi nơi mà thuộc tính .current được khởi tạo và thêm vào giá trị của (initialValue) và giá trị này sẽ không thay đổi mỗi khi reset lại giao diện
    -Ex: 
    ```javascript
    function TextInputWithFocusButton() {
    const inputEl = useRef(null);
     const onButtonClick = () => {
    // `current` trỏ vào element text input đã được mount
    inputEl.current.focus();
    };
    return (
        <>
            <input ref={inputEl} type="text" />
            <button onClick={onButtonClick}>Đưa con trỏ vào ô input</button>
        </>
        );
    }

## React.memo

- React memo sinh ra với mục địch tránh việc rerender nhiều lần ảnh hưởng đến performance
- Cách hoạt động :
- có memo nó sẽ check prop chuyền vào có thay đổi không nếu thay đổi chúng sẽ rerender còn không thay đổi sẽ không cần làm gì, tương đối giống với việc sự dụng shouldComponentUpdate trong class component hay PureComponent
```javascript
- Ex : 
    const MyComponent = React.memo(function MyComponent(props) {
        /* only rerenders if props change */
    });
```    

## useImperativeHandle

## useCallback


## useMemo
- Bản chất useMemo là caching lại giá trị return của function, mỗi lần component rerender nó sẽ kiểm tra giá trị tham số truyền vào function nếu giá trị đó không thay đổi, thì return value đã caching trong memory. Ngược lại nếu giá trị tham số truyền vào thay đổi, nó sẽ thực hiện tính toán lại vào trả về value, sao đó caching lại value cho những lần rerender tiếp theo.
- Nguyên lý hoạt động của deps giống với useEffect useCallback
  + nếu deps là mảng rỗng thì chạy 1 lần
  + nếu giá trị trong deps thay đổi thì mới chạy lại callback nếu không thay đổi thì trả về giá trị trước đó
```javascript
funcion CaculateTotal () {
    ...
    const total = useMemo( () => {
        const result = products.reduce((result, prod) => {
            return result + prod.price
        })

        return result
    }, [products])

    ...
    return (
        ...
    )
}
```