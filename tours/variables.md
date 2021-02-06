# Biến

## Khai báo và khởi tạo biến

_Các biến chứa các tham chiếu tới một đối tượng, chứ không chứa nội dung của đối tượng._

Ta có các cách sau để khai báo biến:

### Khai báo biến có kiểu động

Sử dụng từ khóa `var`:

```dart
var name;

name = 'Bob';
print(name);  // Bob
print(name.runtimeType);  // String

name = 123;
print(name);  // 123
print(name.runtimeType);  // int
```

Sử dụng `dynamic` (hoặc `Object`):

```dart
dynamic name;

name = 'Bob';
print(name);  // Bob
print(name.runtimeType);  // String

name = 123;
print(name);  // 123
print(name.runtimeType);  // int
```

Trong các trường hợp này, kiểu của biến tự động được suy ra từ kiểu của đối tượng mà nó tham chiếu tới.

### Khai báo biến có kiểu tĩnh

```dart
String name = 'Bob';
print(name.runtimeType);

name = 123; // Error: a value of type 'int' can't be assigned to a variable of type 'String'
```

## Giá trị mặc định

Các biến chưa được khởi tạo có giá trị ban đầu là `null`.

```dart
int lineCount;
assert(lineCount == null);
```

## Hằng số

Để tạo hằng số ta có thể dùng hai từ khóa `final` hoặc `const`. Chúng có đôi chút khác biệt.

### `final`

`final` được dùng để tạo ra một hằng số, bắt buộc phải được khởi tạo cùng lúc với khai báo.

final có thể dùng một mình, hoặc dùng kèm với khai báo kiểu biến:

```dart
final name = 'Bob';
print(name); // Bob
print(name.runtimeType);  // String

name = 'John'; // Error: the final value 'name' can only be set once
```

```dart
final String name = 'Bob';
print(name);  // Bob
print(name.runtimeType);  // String

name = 'John'; // Error: the final value 'name' can only be set once
```

### `const`

`const` được dùng để tạo ra một hằng số, mà giá trị của nó được tính toán ở giai đoạn biên dịch.

Ta không thể dùng một giá trị được tạo ra khi chương trình thực thi làm giá trị của hằng được tạo ra bởi `const`:

```dart
// hàm này chạy và trả về giá trị khi thực thi
int foo() {
    return 2;
}

const bar = foo(); // Error: const variables must be initialized with a constant value.
```

Với `final` thì hoàn toàn hợp lệ:

```dart
int foo() {
    return 2;
}

final bar = foo();
print(bar); // 2
```

