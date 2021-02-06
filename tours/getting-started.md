# Bắt đầu với Dart

## Một chương trình Dart cơ bản

Đoạn mã sau sử dụng nhiều tính năng cơ bản nhất của ngôn ngữ Dart:

```dart
// Định nghĩa một hàm
void printInteger(int aNumber) {
    print('The number is $aNumber.') // In ra console
}

// Đây là nơi ứng dụng bắt đầu chạy
void main() {
    var number = 42;  // Khai báo và khởi tạo một biến.
    printInteger(numer);  // gọi một hàm
}
```

## Các khái niệm quan trọng

- Mọi thứ bạn đặt vào một biến là một *đối tượng* (object), và  mọi đối tượng là thực thể của một *lớp* (class). Các số, các hàm, thậm chí giá trị `null` cũng là các đối tượng. Mọi đối tượng được thừa kế từ lớp `Object`.
- Dù Dart là ngôn ngữ có kiểu tĩnh, không cần viết rõ kiểu của biến khi khai báo bởi vì Dart tự động suy ra kiểu của biến khi ta khởi tạo giá trị. Trong đoạn mã ở phần đầu, kiểu của biến `number` là `int` được suy ra từ giá trị `42` gán cho nó.
- Dart hỗ trợ các *kiểu đồng loại* (generic types), như `List<int>` (một danh sách các số nguyên) hoặc `List<dynamic>` (một danh sách các đối tượng có kiểu bất kỳ).
- Dart hỗ trợ các hàm *cấp cao* (top-level function) như `main()` trong ví dụ trên, cũng như các hàm của một lớp (*phương thức tĩnh*) và của đối tượng (*phương thức thực thể*). Bạn cũng có thể tạo các hàm bên trong hàm (*hàm lồng* hay *hàm cục bộ*).
- Tương tự, Dart hỗ trợ các biến *cấp cao* (top-level variable) hay còn gọi là *biến toàn cục*, cũng như các biến của một lớp (*biến tĩnh* hay *thuộc tính tĩnh*) và biến của một đối tượng (*biến thực thể* hay *thuộc tính thực thể*). Các biến thực thể còn được gọi là *thuộc tính* hoặc *trường*.
- Không như Java, Dart không có các từ khóa `public`, `protected` và `private`. Nếu một định danh bắt đầu bằng dấu gạch dưới (`_`), nó được xem là biến riêng.
- *Các định danh* có thể bắt đầu bằng chữ cái hoặc dấu gạch dưới, theo sau là những ký tự này cộng thêm với chữ số.
- Dart phân biệt *biểu thức* (chạy và trả về giá trị) và *câu lệnh* (chạy không trả về giá trị).
- Các công cụ của Dart có thể báo cáo hai kiểu vấn đề gặp phải: *cảnh báo* (warning) và *lỗi* (error). Cảnh báo chỉ rằng mã của bạn có thể không hoạt động, nhưng nó vẫn cho chương trình chạy. Lỗi có thể xuất hiện trong quá trình biên dịch hoặc trong quá trình thực thi. Lỗi biên dịch khiến chương trình không thể chạy được; lỗi thực thi tạo ra một *ngoại lệ* (exception) khi chạy chương trình.

## Các từ khóa

Hiện tại Dart có các từ khóa sau:

| | | | |
|-|-|-|-|
| abstract | else | import | super |
| as | enum | in | switch |
| assert | export | interface | sync |
| async | extends | is | this |
| await | extension | library | throw |
| break | external | mixin | true |
| case | factory | new | try |
| catch | false | null | typedef |
| class | final | on | var |
| const | finally | operator | void |
| continue | for | part | while |
| covariant | Function | rethrow | with |
| default | get | return | yield |
| deferred | hide | set | | |
| do | if | show | |
| dynamic | implements | static | |


## Chú thích

Dart hỗ trợ chú thích một dòng, chú thích nhiều dòng và chú thích tài liệu.

### Chú thích một dòng

```dart
void main() {
  // TODO: refactor into an AbstractLlamaGreetingFactory?
  print('Welcome to my Llama farm!');
}
```

### Chú thích nhiều dòng

```dart
void main() {
  /*
   * This is a lot of work. Consider raising chickens.

  Llama larry = Llama();
  larry.feed();
  larry.exercise();
  larry.clean();
   */
}
```

### Chú thích tài liệU

```dart
/// A domesticated South American camelid (Lama glama).
///
/// Andean cultures have used llamas as meat and pack
/// animals since pre-Hispanic times.
class Llama {
  String name;

  /// Feeds your llama [Food].
  ///
  /// The typical llama eats one bale of hay per week.
  void feed(Food food) {
    // ...
  }

  /// Exercises your llama with an [activity] for
  /// [timeLimit] minutes.
  void exercise(Activity activity, int timeLimit) {
    // ...
  }
}
```