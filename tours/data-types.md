# Các kiểu dữ liệU

Dart có sẵn những kiểu dữ liệu sau đây:

- kiểu số
- kiểu chuỗi
- kiểu lôgic
- kiểu danh sách (hay mảng)
- kiểu tập hợp
- kiểu ánh xạ (`map`)
- kiểu symbol

## Kiểu số

- `int`: số nguyên 64bit
- `double`: số thực 64bit

Cả `int` lẫn `double` là kiểu con của `num`. Kiểu `num` hỗ trợ các toán tử cơ bản như `+`, `-`, `*`, `/`..., các hàm như `abs()`, `ceil()`, `floor()` và một số phương thức khác.

Ví dụ về số nguyên:

```dart
var x = 1;
var hex = 0xDEADEEF;
```

Ví dụ về số thực:

```dart
var y = 1.1;
var exponents = 1.42e5;
```

Số nguyên có thể chuyển thành số thực:

```dart
double z = 1; // z = 1.0
```

Chuỗi có thể chuyển thành số và ngược lại:

```dart
// String -> int
var one = int.parse('1');
assert(one == 1);

// String -> double
var onePointOne = double.parse('1.1');
assert(onePointOne == 1.1);

// int -> String
String onAsString = 1.toString();
assert(oneAsString == '1');

// double -> String
String piAsString = 3.14159.toStringAsFixed(2);
assert(piAsString == '3.14');
```

Có thể sử dụng các toán tử bitwise với số nguyên:

```dart
assert((3 << 1) == 6); // 0011 << 1 == 0110
assert((3 >> 1) == 1); // 0011 >> 1 == 0001
assert((3 | 4) == 7); // 0011 | 0100 == 0111
```

## Kiểu chuỗi

Tạo chuỗi:

```dart
var s1 = 'Single quotes work well for string literals.';
var s2 = "Double quotes work just as well.";
var s3 = 'It\'s easy to escape the string delimiter.';
var s4 = "It's even easier to use the other delimiter.";
```

Có thể nhúng biểu thức hoặc biến vào chuỗi bằng cú pháp `${expression}` và `$variable`.

```dart
var s = 'string interpolation';

assert('Dart has $s, which is very handy.' ==
    'Dart has string interpolation, ' +
        'which is very handy.');
assert('That deserves all caps. ' +
        '${s.toUpperCase()} is very handy!' ==
    'That deserves all caps. ' +
        'STRING INTERPOLATION is very handy!');
```

Các chuỗi được nối với nhau bằng toán tử `+`:

```dart
var s1 = 'String '
    'concatenation'
    " works even over line breaks.";
assert(s1 ==
    'String concatenation works even over '
        'line breaks.');

var s2 = 'The + operator ' + 'works, as well.';
assert(s2 == 'The + operator works, as well.');
```

Tạo chuỗi trên nhiều dòng bằng ba dấu nháy (tương tự Python):

```dart
var s1 = '''
You can create
multi-line strings like this one.
''';

var s2 = """This is also a
multi-line string.""";
```

Tạo chuỗi thô bằng tiền tố `r` (tương tự Python):

```dart
var s = r'In a raw string, not even \n gets special treatment.';
```

## Kiểu lôgic

Tên kiểu lôgic là `bool` với hai giá trị là `true` và `false`.

Dart không như JavaScript, không hỗ trợ `if (nonbooleanValue)` hoặc `assert(nonbooleanValue)`. Bạn cần kiểm tra rõ ràng:

```dart
// Kiểm tra chuỗi trống
var fullName = '';
assert(fullName.isEmpty);

// Kiểm tra số không
var hitPoints = 0;
assert(hitPoints <= 0);

// Kiểm tra null
var unicorn;
assert(unicorn == null);

// Kiểm tra NaN
var iMeantToDoThis = 0 / 0;
assert(iMeantToDoThis.isNaN);
```

## Kiểu danh sách

Trong Dart kiểu mảng được gọi là danh sách, nó là một nhóm các đối tượng được sắp xếp.

Tạo danh sách:

```dart
var list = [1, 2, 3]
```

Bạn có thể thêm dấu phảy treo sau phần tử cuối cùng:

```dart
var list = [
  'Car',
  'Boat',
  'Plane',
];
```

Truy cập phần tử của danh sách qua chỉ số của nó:

```dart
var list = [1, 2, 3];
assert(list.length == 3);
assert(list[1] == 2);

list[1] = 1;
assert(list[1] == 1);
```

Để tạo một danh sách không thể thay đổi, thêm từ khóa `const` vào trước:

```dart
var constantList = const [1, 2, 3];
// constantList[1] = 1; // Không thể thay đổi phần tử
```

Bạn có thể sử dụng toán tử `(...)` để chèn nhiều phần tử của một danh sách vào danh sách khác:

```dart
var list = [1, 2, 3];
var list2 = [0, ...list];
assert(list2.length == 4);
```

`..list` sẽ gây ra lỗi khi `list` là `null`. Để tránh lỗi này, sử dụng `...?`:

```dart
var list = [1, 2, 3];
var list2 = [0, ...?list];
assert(list2.length == 4);
```

Tạo danh sách bằng `collection if`:

```dart
var nav = [
    'Home',
    'Furniture',
    'Plants',
    if (promoActive) 'Outlet'
];
```

Tạo danh sách bằng `collection for`:

```dart
var listOfInts = [1, 2, 3];
var listOfStrings = [
    '#0',
    for (var i in listOfInts) '#$i'
];
assert(listOfStrings[1] == '#1')
```

## Kiểu tập hợp

Kiểu tập hợp biểu diễn một nhóm các đối tượng duy nhất, không được sắp xếp. Nó giống kiểu tập hợp trong Python.

Tạo tập hợp:

```dart
var halogens = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};
```

Tạo tập hợp trống:

```dart
var names = <String>{};
// hoặc
var names = Set<String>{};
```

Thêm phần tử vào tập hợp bằng phương thức `add()` hoặc `addAll()`:

```dart
var elements = <String>{};
elements.add('fluorine');
elements.addAll(halogens);
```

Thuộc tính `length` trả về kích thước của tập hợp:

```dart
var elements = <String>{};
elements.add('fluorine');
elements.addAll(halogens);
assert(elements.length == 5);
```

Để tạo tập hợp không thể thay đổi, thêm `const` vào trước:

```dart
final constantSet = const {
  'fluorine',
  'chlorine',
  'bromine',
  'iodine',
  'astatine',
};
// constantSet.add('helium'); // Dòng này gây ra lỗi
```

Tập hợp cũng hỗ trợ `(...)` và `(...?)` như danh sách.

## Kiểu ánh xạ

Kiểu ánh xạ hay Map là một nhóm gồm nhiều khóa và giá trị tương ứng. Cả khóa và giá trị của nó có thể là đối tượng bất kỳ. Mỗi khóa chỉ xuất hiện một lần, nhưng nhiều khóa có thể có cùng giá trị. Kiểu ánh xạ trong Dart tương tự kiểu từ điển trong Python.

Tạo một ánh xạ:

```dart
var gifts = {
    // Khóa: Giá trị
    'first': 'partridge',
    'second': 'turtledoves',
    'fifth': 'golden rings'
};

var nobleGases = {
    2: 'helium',
    10: 'neon',
    18: 'argon',
}
```

Có thể tạo một ánh xạ trống bằng `{}` hoặc hàm `Map()`:

```dart
var gifts = {};
gifts['first'] = 'partridge';
gifts['second'] = 'turtledoves';
gifts['fifth'] = 'golden rings';

var nobleGases = Map();
nobleGases[2] = 'helium';
nobleGases[10] = 'neon';
nobleGases[18] = 'argon';
```

Truy cập một giá trị bằng khóa của nó, nếu khóa không tồn tại, kết quả là `null`:

```dart
var gifts = Map();
gifts['first'] = 'partridge';
gifts['second'] = 'turtledoves';
gifts['fifth'] = 'golden rings';

gifts['fourth'] = 'calling birds'; // Thêm một phần tử

assert(gifts['third'] == null);
```

Thuộc tính `.length` trả về số khóa của ánh xạ:

```dart
var gifts = {'first': 'partridge'};
gifts['fourth'] = 'calling birds';
assert(gifts.length == 2);
```

Để tạo ánh xạ không thể thay đổi, thêm `const` vào trước:

```dart
final constantMap = const {
  2: 'helium',
  10: 'neon',
  18: 'argon',
};

// constantMap[2] = 'Helium'; // Dòng này gây ra lỗi
```

Các ánh xạ cũng hộ trợ toán tử `(...)` và `(...?)`.

## Kiểu symbol

Là đối tượng biểu diễn một toán tử hoặc định danh được khai báo trong chương trình Dart. Nó hiếm khi được sử dụng.

Để lấy symbol của một định danh, them `#` trước định danh đó:

```dart
#radix
#bar
```