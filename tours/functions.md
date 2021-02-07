# Hàm

## Giới thiệu về hàm

Hàm thực ra cũng là một đối tượng, nhưng có kiểu `Function`. Hàm do đó cũng có thể thể gán cho biến hoặc truyền như đối số vào hàm khác hoặc được trả về từ một hàm khác.

Ví dụ sau định nghĩa một hàm:

```dart
bool isNoble(int atomicNumber) {
    return _nobleGases[atomicNumber] != null;
}
```

Hàm vẫn làm việc nếu ta bỏ đi các khai báo kiểu của nó va tham số của nó:

```dart
bool isNoble(int atomicNumber) {
    return _nobleGases[atomicNumber] != null;
}
```

Nếu hàm chỉ chứa một biểu thức và trả về giá trị biểu thức này, có thể sử dụng dạng viết tắt sử dụng `=>`:

```dart
bool isNoble(int atomicNumber) => _nobleGases[atomicNumber] != null;
```

## Các tham số

### Tham số có tên

Định nghĩa:

```dart
void enableFlags({bool bold, bool hidden}) {...}
```

Gọi:

```dart
enableFlags(bold: true, hidden: false);
```

Các tham số có tên mặc định là không bắt buộc trừ khi bạn đặt `@required` trước nó.

### Tham số vị trí không bắt buộc

Định nghĩa trong `[]`:

```dart
String say(String from, String msg, [String device]) {
    var result = '$from say $msg';
    if (device != null) {
        result = '$result with a $device';
    }
    return result;
}
```

Gọi:

```dart
assert(say('Bob', 'Howdy') == 'Bob says Howdy');
assert(say('Bob', Howdy', 'smoke signal') == 'Bob says Howdy with a smoke signal');
```

### Tham số mặc định

Định nghĩa:

```dart
// tham số vị trí mặc định
String say(String from, String msg, [String device = 'carrier pigeon']) {...}

// tham số có tên mặc định
void enableFlags({bool bold = false, bool hidden = false}) {...}
```

## Hàm main()

Mọi ứng dụng phải có hàm `main()` ở cấp cao nhất, được gọi đầu tiên khi chương trình chạy. Hàm `main()` phải trả về `void` và có tham số tùy chọn có kiểu `List<String>`.

## Hàm là các đối tượng

Bạn có thể truyền hàm như đối số tới hàm khác. Ví dụ:

```dart
void printElement(int element) {
    print(element);
}

var list = [1, 2, 3];

// truyền printElement vào hàm khác
list.forEach(printElement);
```

Bạn cũng có thể gán hàm cho một biến:

```dart
var loudify = (msg) => '!!! ${msg.toUpperCase()} !!!';
assert(loudify('hello') == '!!! HELLO !!!')
```

## Hàm không tên

Hầu hết các hàm có tên, như `main()`, hoặc `printElement()`. Bạn cũng có thể tạo một hàm không tên, còn được gọi là *lambda* hoặc *closure*.

Hàm không tên trông tương tự như hàm có tên:

```dart
([[Type] param1[, ...]]) {
    codeBlock;
};
```

Ví dụ:

```dart
var list = ['apples', 'bananas', 'oranges'];

list.forEach((item) {
    print('${list.indexOf(item)}: $item');
});
```

Nếu thân hàm chỉ có một lệnh, bạn có thể viết tắt bằng kí hiệu mũi tên `=>`:

```dart
list.forEach(
    (item) => print('${list.indexOf(item)}: $item');
)
```

## Phạm vi của biến

```dart
bool topLevel = true;

void main() {
    var insideMain = true;

    void myFunction() {
        var insideFunction = true;

        void nestedFunction() {
            var insideNestedFunction = true;

            assert(topLevel);
            assert(insideMain);
            assert(insideFunction);
            assert(insideNestedFunction);
        }
    }
}
```

## Closure

Một *closure* là một hàm có thể truy cập các biến trong phạm vi của nó, ngay cả khi nó được sử dụng bên ngoài phạm vi này.

```dart
Function makeAdder (int addBy) {
    return (int i) => addBy + 1;
}

void main() {
    var add2 = makeAdder(2);

    var add4 = makeAdder(4);

    assert(add2(3) == 5)
    assert(add4(3) == 7);
}
```

## Giá trị trả về

Tất cả các hàm đều trả về một giá trị. Nếu không chỉ rõ giá trị trả về, thì giá trị trả về mặc định của hàm là `null`.

```dart
foo() {}

assert(foo() == null);
```