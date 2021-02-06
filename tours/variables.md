# Biến

## Biến

Đây là ví dụ tạo biến và khởi tạo giá trị cho nó:

```dart
var name = 'Bob';
```

Các biến chứa các tham chiếu. Biến `name` ở trên lưu một tham chiếu tới đối tượng `String` có giá trị `"Bob"`.

Kiểu của biến được tự động suy ra từ giá trị nó tham chiêu tới: `'Bob'`. Ta có thể khai báo kiểu biến rõ ràng như sau:

```dart
String name = 'Bob';
```

Dart có từ khóa `dynamic` ám chỉ một biến có kiểu động, tức có thể tham chiếu tới một đối tượng có kiểu bất kỳ:

```dart
dynamic name = 'Bob';
```

## Giá trị mặc định

Các biến chưa được khởi tạo có giá trị ban đầu là `null`.

```dart
int lineCount;
assert(lineCount == null);
```

## `final` và `const`

`final` được dùng để khai báo một biến chỉ có thể gán một lần. Có thể dùng kèm với khai báo kiểu hoặc không. Khi không có khai báo kiểu, kiểu của biến `final` được suy ra từ kiểu của giá trị gán cho biến.

```dart
final name = 'Bob'; // không có khai báo kiểu
final String nickname = 'Bobby'; // có khai báo kiểu

name = 'Alice';  // Error: a final variable can only be set once.
```

