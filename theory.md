# *JSX*

### 1. JSX là gì ?
    - JSX  -> Javascript XML
    - Dùng để viết HTMl trong file Javascript
    - JSX cho phép chúng ta viết HTML trong React.
    Note: 
    - JSX không phải HTML
    - Vì JSX gần với JavaScript hơn là HTML, nên React DOM sử dụng camelCasequy ước đặt tên thuộc tính thay vì tên thuộc tính HTML.

### 2. Sử dụng JSX ?
####    a. Những biểu thức trong JSX
    Trong ví dụ dưới đây, chúng tôi khai báo một biến được gọi name và sau đó sử dụng nó bên trong JSX bằng cách gói nó trong dấu ngoặc nhọn:
    
    Ex:
    const name = 'Josh Perez';
    const element = <h1>Hello, {name}</h1>;

    ReactDOM.render(element, document.getElementById('root')
    )

####    b. JSX cũng là một biểu thức
    - bạn có thể sử dụng JSX bên trong các câu lệnh if và vòng lặp for , gán nó cho các biến, chấp nhận nó dưới dạng đối số và trả về nó từ các hàm:

    function getGreeting(user) {
    if (user) {
    return <h1>Hello, {formatName(user)} !</h1>;
    }
    return <h1>Hello, Stranger.</h1>;
    }

####    c. Chỉ định các thuộc tính với JSX
    - Bạn có thể sử dụng dấu ngoặc kép để chỉ định các ký tự chuỗi làm thuộc tính:
    Ex: 
    const element = <a href="https://www.reactjs.org"> link </a>;

    - Bạn cũng có thể sử dụng dấu ngoặc nhọn để nhúng biểu thức JavaScript vào một thuộc tính:
    Ex:
    const element = <img src={user.avatarUrl}></img>;

    Note: 
    - Không đặt dấu ngoặc kép quanh dấu ngoặc nhọn khi nhúng biểu thức JavaScript vào một thuộc tính. Bạn nên sử dụng dấu ngoặc kép (đối với giá trị chuỗi) hoặc dấu ngoặc nhọn (đối với biểu thức), nhưng không nên sử dụng cả hai trong cùng một thuộc tính.
    - Dùng thư viện bable để chuyển đổi

# *component and props*
    - components giống như các hàm JavaScript. Họ chấp nhận các đầu vào bất kỳ (được gọi là “props”) và trả về các phần tử React mô tả những gì sẽ xuất hiện trên màn hình.

##    A. Component
###    1. Rendering a Component
    - các phần tử cũng có thể đại diện cho các thành phần do người dùng xác định
    - ex: const element = <Welcome name="Sara" />
    - Note:
      - Luôn bắt đầu các tên thành phần bằng một chữ cái viết hoa.

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
    Ex: const App = () => <Welcome name="Luong" age=20>Xin chào </Welcome>
    Vậy trong components Welcome giá trị của props sẽ là một object bao gồm các giá trị truyền vào :
    {
    name: "Luong",
    age: 20,
    children: "Xin chào"
    }

# *state and lifecycle*
##   A. State
###    1. Khai niem
    - State chỉ tồn tại trong phạm vi của components chứa nó, mỗi khi state thay đổi thì components đó sẽ được render lại.
    - Khái niệm functional component hay còn được hiểu là stateless component còn class component thì là stateful component.
###    2. Khởi tạo state
    - this.state = { name : 'freetuts.net' }
###    3. Cập nhật một state
    - this.setState((state) => {
      return newValue;
    });
###    4. Phân biệt state và props
    - State: Dữ liệu chỉ nằm trong phạm vi của một component. Nó được sở hữu bởi một components cụ thể mà chỉ là của component đó . Và mỗi khi state thay đổi thì component cũng phải thay đổi theo.
    - Props: Dữ liệu đường truyền từ component cha cho componet con, components con khi nhận được sẽ chỉ được đọc mà không thể thay đổi dữ liệu đó.
  
##    B. lifecycle
    - Khi một components được khởi chạy nó sẽ phải trải qua 4 giai đoạn chính:
        - initialization
        - mounting
        - updating
        - unmounting
###    1. initialization
    - Đây là giai đoạn mà thành phần sẽ bắt đầu hành trình của mình bằng cách khởi tạo state và props.
###    2. mounting
####   a. componentWillMount()
     - Được khởi chạy khi một component chuẩn bị được mount (tức là trước khi thực hiện render), sau khi thực hiện xong componentWillMount() thì component mới có thể được mount.
     - Lưu ý: Chúng ta không nên thực hiện bất cứ thay đổi nào liên quan đến state, props hay call API ở trong hàm này, bởi thời gian chuẩn bị mount -> mount rất ngắn nên các tác vụ đó không thể hoàn thành kịp
  
####    b. componentDidMount()
    - Được gọi khi component đã được mount (render thành công ), quá trình này xảy ra sau khi componentWillMount() thực hiện xong. Trong phương thức này bạn có thể gọi API, thay đổi state, props.
  
##    3. updating
    Trong giai đoạn này, dữ liệu của các phần (props & state) sẽ được cập nhật để đáp ứng với các sự kiện của người dùng như click, gõ, v.v. Điều này dẫn đến việc re-render lại component, ở trong giai đoạn này chúng ta sẽ có 4 phương thức chính:
####    a. shouldComponentUpdate()
    - Phương thức này xác định xem component có nên được render lại hay không ? Theo mặc định, nó trả về true. Nhưng bạn có thể thay đổi giá trị trả về của nó theo từng trường hợp.
####    b. componentWillUpdate()
    - Phương thức này được gọi trước khi tiến hành re-render, bạn có thể thực hiện các hành động như update state, props,...trong phương thức này trước khi tiến hành re-render
####    c. ComponentDidUpdate()
    - Phương thức này được gọi khi component đã re-render xong    
  
##   4. unmouting
    -Đây là bước cuối cùng trong mỗi component, khi tất cả các tác vụ hoàn thành và bạn tiến hành unmount DOM. Quá trình này chỉ có duy nhất 1 phương thức đó là componentWillUnmount() :

# *functional component*
    - Hàm này là một thành phần React hợp lệ vì nó chấp nhận một “props” đơn (viết tắt của thuộc tính) đối số đối tượng với dữ liệu và trả về một phần tử React . Chúng tôi gọi các thành phần như vậy là “function components” bởi vì chúng thực sự là các hàm JavaScript.
  
    function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
    }

    -Vậy 1 React Functional Component là:
        - một function Javascript / ES6 function
        - phải trả về 1 React element
        - nhận props làm tham số nếu cần
# *class component*
    - Chúng phức tạp hơn functional components ở chỗ nó còn có: phương thức khởi tạo, life-cycle, hàm render() và quản lý state (data).
    class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>;
        }
    }

    - Vì vậy, một React class component là:
      + là một class ES6, nó sẽ là một component khi nó "kế thừa" React component.
      + có thể nhận props (trong hàm khởi tạo) nếu cần.
      + có thể maintain data của nó với state
      + phải có 1 method render() trả về 1 React element (JSX), or null