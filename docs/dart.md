Dart
===

Содержит наиболее важные концепции, функции, методы и т.д. [Dart](https://dart.dev/) шпаргалка. Полный краткий справочник для начинающих.

Начало
-----

### Установка Dart
<!--rehype:wrap-class=row-span-2-->

#### Windows

```bash
C:\> choco install dart-sdk # Windows
```

#### Linux

Подключить необходимые репозитории

```bash
$ sudo apt-get update
$ sudo apt-get install apt-transport-https
$ wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo gpg --dearmor -o /usr/share/keyrings/dart.gpg
$ echo 'deb [signed-by=/usr/share/keyrings/dart.gpg arch=amd64] https://storage.googleapis.com/download.dartlang.org/linux/debian stable main' | sudo tee /etc/apt/sources.list.d/dart_stable.list
```

Установить Dart SDK

```bash
$ sudo apt-get update
$ sudo apt-get install dart
```

#### Mac

```bash
$ brew tap dart-lang/dart
$ brew install dart
```

### hello.dart

```dart
// Главная функция с которой начинается выполнение приложения
void main() {
    print("Hello World!"); // печать в консоль
}
```

В каждом приложении есть `main()` функция

#### Windows

```bash
$ dart compile exe hellow.dart
$ time ./hello.exe
Hello World!
```

### Переменные

```dart
int x = 2; // явная типизация
var p = 5; // автоматически проанализирует тип
dynamic z = 8; // переменная может быть любого типа. Отключает статическую проверку
z = "cool"; // cool

// используй final или const для объявления констант

final email = "temid@gmail.com";
// динамически вычисляемая в рантайме константа
final String email = user.getEmail();

// только то что можно вычислить во время компиляции
const bar = 1000000;
const double atm = 1.01325 * bar; // константа времени компиляции

//создание постоянных значений
var foo = const [];
final bar = const [];
const baz = []; // эквивалентно `const []`
```

### Типы данных
<!--rehype:wrap-class=row-span-2-->

```dart
// integer, от -2^63 до 2^63 - 1
int age = 20;

// числа с плавающей точкой
double height = 1.85;
// оба наследуются от num
// соответственно x может быть обоих типов int и double
num x = 1;
num += 2.5;
print(num); // напечатает: 3.5

// строковый тип.
String name = "Nicola";
var s1 = 'Строка может быть в одинарных кавычках';
var s2 = "либо в двойных.";
var s3 = 'Это \' экранирование';

// логический тип
bool isFavourite = true;
bool isLoaded = false;
```

### Интерполяция строк

```dart
var firstName = 'Nicola';
var lastName = "Tesla";
// возможно вставлять переменные в строки с помощью $
String fullName = "Привет, $firstName $lastName";

// конкатенация
var name = "Albert " + "Einstein";

// интерполяция выражения ${var}
String upperCase = '${firstName.toUpperCase()}';
print(upperCase); // напечатает: NICOLA
```

### Комментарии

```dart
// однострочный комментарий

/// Комментарий документации, используемый библиотекой комментариев,
/// Используя скобки [], вы можете ссылаться на классы, методы, поля, переменные верхнего уровня,
/// функции и параметры.

/*
  многострочный
  комментарий
*/
```

<!--rehype:className=wrap-text -->

### Импорт

```dart
// импорт встроенных библиотек
import 'dart:math';
// импорт из внешних библиотек
import 'package:test/test.dart';
// импорт файлов
import 'path/to/my_other_file.dart';
```

Операторы
-------

### Арифметические операторы
<!--rehype:wrap-class=row-span-2-->

```dart
print(2 + 3);  // сложение
print(2 - 3);  // вычитание
print(2 * 3);  // умножение
print(5 / 2);  // деление - перевод на double
print(5 ~/ 2); // целочисленное деление, напечатает: 2 - результат типа int
print(5 % 2);  // остаток от деления (1)
```

----

```dart
// инкремент
b = ++a;
b = a++;
// декремент
b = --a;
b = a--;
```

### Логические операторы
<!--rehype:wrap-class=col-span-2-->

```dart
// !expr логическое не (меняет false на true и наоборот)
// || логическое или
// && логическое и
bool isOutOfStock = false;
int quantity = 3;
if (!isOutOfStock && (quantity == 2 || quantity == 3)) {
  // ...Order the product...
}
```

### Операторы сравнения и отношения

```dart
print(2 == 2); // (true) - равно
print(2 != 3); // (true) - не равно
print(3 > 2);  // (true) - больше чем
print(2 < 3);  // (true) - меньше чем
print(3 >= 3); // (true) - больше либо равно
print(2 <= 3); // (true) - меньше либо равно
```

Поток выполнения: Условия
------

### if и else if

```dart
if(age < 18){
    print("Teen");
} else if( age > 18 && age <60){
    print("Adult");
} else {
    print("Old");
}
```

### switch case

```dart
enum Pet {dog, cat}
Pet myPet = Pet.dog;
switch(myPet){
    case Pet.dog:
        print('My Pet is Dog.');
        break;
    case Pet.cat:
        print('My Pet is Cat.');
        break;
    default:
        print('I don\'t have a Pet');
}
// напечатает: My Pet is Dog.
```

Поток выполнения: Циклы
-----

### while цикл

```dart
while (!dreamsAchieved) {
  workHard();
}
```

перед новой итерацией `while` цикл проверит условие

### do-while цикл

```dart
do {
  workHard();
} while (!dreamsAchieved);
```

`do-while` Цикл проверяет условие после выполнения операторов внутри цикла.

### for цикл

```dart
for(int i=0; i< 10; i++){
    print(i);
}
var numbers = [1,2,3];

for(var number in numbers){
    print(number);
}
```

Коллекции
------------

### Lists (списки)
<!--rehype:wrap-class=col-span-2-->

```dart
// ordered group of objects
var list = [1, 2, 3];
print(list.length); //Print: 3
print(list[1]); //Print: 2
// 列表声明和初始化的其他方式
List<String> cities = <String>["New York", "Mumbai", "Tokyo"];
// 创建一个编译时常量的列表
const constantCities = const ["New York", "Mumbai", "Tokyo"];
```

### Maps (карты)
<!--rehype:wrap-class=row-span-2-->

```dart
// 映射是关联键和值的对象
var person = Map<String, String>();
// 要初始化地图，请执行以下操作：
person['firstName'] = 'Nicola';
person['lastName'] = 'Tesla';
print(person);
// 打印: {firstName:Nicola, lastName:Tesla}
print(person['lastName']);
// 打印: Tesla

var nobleGases = {
  // ключ: значение
  2: 'helium',
  10: 'neon',
  18: 'argon',
};
```

### Sets (множества)
<!--rehype:wrap-class=col-span-2-->

```dart
// Dart 中的集合是唯一项的无序集合
var halogens = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};
// 创建一个空集
var names = <String>{};
Set<String> names = {}; // 这也有效
//var names = {}; // 创建地图，而不是集合
```

函数
------

### 函数示例

```dart
// dart 中的函数是对象并且有一个类型
int add(int a, int b){
    return a+b;
}
// 函数可以分配给变量
int sum = add(2,3); // 回报：5
// 可以作为参数传递给其他函数
int totalSum = add(2, add(2,3)); // 返回：7
```

### 箭头语法 (=>)

```dart
// 只包含一个表达式的函数，您可以使用简写语法
bool isFav(Product product) => favProductsList.contains(product);
```
<!--rehype:className=wrap-text-->

### Anonymous (lambda) functions

```dart
// 没有名字的小单行函数
int add(a,b) => a+b;
// lambda 函数大多作为参数传递给其他函数
const list = [
  'apples', 'bananas', 'oranges'
];

list.forEach(
  (item) =>
    print('${list.indexOf(item)}: $item')
);
// 打印: 0: apples 1: bananas 2: oranges
```
<!--rehype:className=wrap-text-->

类和对象
----------

### 类 Class

```dart
class Cat {
    String name;
    // 方法
    void voice(){
        print("Meow");
    }
}
```

### 对象 Object

```dart
// 类的实例
// 在 myCat 下面是 Cat 类的对象
void main(){
    Cat myCat = Cat();
    myCat.name = "Kitty";
    myCat.voice(); // 打印: Meow
}
```

### 构造函数

```dart
class Cat {
    String name;
    Cat(this.name);
}
void main(){
    Cat myCat = Cat("Kitty");
    print(myCat.name); // 打印: Kitty
}
```

### 抽象类

```dart
// 抽象类——不能实例化的类
// 这个类被声明为抽象的，因此不能被实例化
abstract class AbstractContainer {
  // 定义构造函数、字段、方法...
  void updateChildren(); // 抽象方法
}
```

### Getters Setters

```dart
// 提供对对象属性的读写访问
class Cat {
    String name;
    // getter
    String get catName {
        return name;
    }
    // setter
    void set catName(String name){
        this.name = name;
    }
}
```

隐式接口
------------

### 一个基本的界面
<!--rehype:wrap-class=col-span-2-->

```dart
// 一个人。隐式接口包含 greet()。
class Person {
  // 在接口中，但仅在此库中可见。
  final String _name;
  // 不在接口中，因为这是一个构造函数。
  Person(this._name);
  // 在接口中
  String greet(String who) => 'Hello, $who. I am $_name.';
}
// Person 接口的实现。
class Impostor implements Person {
  String get _name => '';
  String greet(String who) => 'Hi $who. Do you know who I am?';
}
String greetBob(Person person) => person.greet('Bob');
void main() {
  print(greetBob(Person('Kathy')));
  // 打印: Hello, Bob. I am Kathy.
  print(greetBob(Impostor()));
  // 打印: Hi Bob. Do you know who I am?
}
```

### 扩展类

```dart
class Phone {
    void use(){
        _call();
        _sendMessage();
    }
}
// 使用 extends 创建子类
class SmartPhone extends Phone {
    void use(){
        // 使用 super 来引用超类
        super.use();
        _takePhotos();
        _playGames();
    }
}
```

枚举
-----

### 定义枚举

```dart
enum Color { red, green, blue }
```

使用枚举，像访问任何其他静态变量一样访问枚举值：

```dart
final favoriteColor = Color.blue;
if (favoriteColor == Color.blue) {
  print('Your favorite color is blue!');
}
```

枚举中的每个值都有一个索引获取器，它返回枚举声明中值从零开始的位置。 例如，第一个值的索引为 0，第二个值的索引为 1

```dart
assert(Color.red.index == 0);
assert(Color.green.index == 1);
assert(Color.blue.index == 2);
```

要获取所有枚举值的列表，请使用枚举的值常量

```dart
List<Color> colors = Color.values;
assert(colors[2] == Color.blue);
```

您可以在 switch 语句中使用枚举，如果您没有处理枚举的所有值，您将收到警告：

```dart
var aColor = Color.blue;

switch (aColor) {
  case Color.red:
    print('Red as roses!');
    break;
  case Color.green:
    print('Green as grass!');
    break;
  default: // 没有这个，你会看到一个警告
    print(aColor); // 'Color.blue'
}
```

如果您需要访问枚举值的名称，例如 `Color.blue` 中的“blue”，请使用 `.name` 属性：

```dart
print(Color.blue.name); // 'blue'
```

### 枚举示例
<!--rehype:wrap-class=col-span-2-->

声明了一个具有多个实例、实例变量、一个 `getter` 和一个已实现接口的增强型枚举

```dart
// 简单定义一个枚举类型
enum PlanetType { terrestrial, gas, ice }

// 定义一个行星复杂的枚举类型
enum Planet {
  mercury(planetType: PlanetType.terrestrial, moons: 0, hasRings: false),
  venus(planetType: PlanetType.terrestrial, moons: 0, hasRings: false),

  uranus(planetType: PlanetType.ice, moons: 27, hasRings: true),
  neptune(planetType: PlanetType.ice, moons: 14, hasRings: true);

  // 定义一个构造函数
  const Planet({required this.planetType, required this.moons, required this.hasRings});

  // 声明枚举类型中的变量
  final PlanetType planetType;
  final int moons;
  final bool hasRings;

  // 实现枚举类型中的get 方法
  bool get isGiant =>
    planetType == PlanetType.gas || planetType == PlanetType.ice;
}

// 使用枚举类型
void main()
{
  final yourPlanet = Planet.mercury;

  if (!yourPlanet.isGiant) {
    print('Your planet is not a "giant planet".');
  }
}
```

Mixin
-----

### 定义Mixin
<!--rehype:wrap-class=col-span-2-->
`Dart`中类只能单继承，使用`Mixin`可以实现多个继承，复用多个类中代码的方法。

```dart
// 定义Mixin
mixin Piloted {
  int astronauts = 1;

  void describeCrew() {
    print('Number of astronauts: $astronauts');
  }
}
```

使用`with`关键字并在其后跟上`Mixin类`的名字来使用

```dart
// 使用with将Piloted混入
class PilotedCraft extends Spacecraft with Piloted {
  // ···
}
```

支持混入多个Mixin，如果出现相同的方法后混入的Mixin会覆盖前面的

```dart
class Musician extends Performer with Musical {
  // ···
}

// 混入多个Mixin
class Maestro extends Person with Musical, Aggressive, Demented {
  Maestro(String maestroName) {
    name = maestroName;
    canConduct = true;
  }
}
```

使用关键字`on`来指定哪些类可以使用该Mixin，比如有Mixin类`MusicalPerformer`，但是`MusicalPerformer`只能被`Musician`类使用，则可以这样定义`MusicalPerformer`：

```dart
class Musician {
  // ...
}
// 现在MusicalPerformer 只能在 Musican及其子类中使用
mixin MusicalPerformer on Musician {
  // ...
}
class SingerDancer extends Musician with MusicalPerformer {
  // ...
}
```

异常
-----

### Throw

```dart
// 抛出 throws 或引发 raises 和异常 exception
throw IntegerDivisionByZeroException();
// 你也可以抛出任意对象
throw "Product out of stock!";
```

### Catch

```dart
try {
    int c = 3/0;
    print(c);
} on IntegerDivisionByZeroException {
    // 一个特定的异常
    print('Can not divide integer by 0.')
} on Exception catch (e) {
    // 任何其他异常情况
    print('Unknown exception: $e');
} catch (e) {
    // 没有指定类型，处理所有
    print('Something really unknown: $e');
}
```

### Finally

```dart
// 确保某些代码无论是否抛出异常都能运行
try {
  cookFood();
} catch (e) {
  print('Error: $e'); // 先处理异常
} finally {
  cleanKitchen();     // 然后清理
}
```

Futures
------------

### Async Await

```dart
// 异步函数：它们在设置可能耗时的操作后返回
// async 和 await 关键字支持异步编程
Future<String> login() {
  String userName="Temidjoy";
  return
    Future.delayed(
      Duration(seconds: 4), () => userName
    );
}
// 异步
main() async {
  print('Authenticating please wait...');
  print(await userName());
}
```

各种各样的
------------

### Null 和 Null 感知
<!--rehype:wrap-class=col-span-2-->

```dart
int x; // 任何对象的初始值为 null
// ?? 空感知运算符
x ??=6;   // ??= 赋值运算符，仅当变量当前为 null 时才为其赋值
print(x); // 打印: 6
x ??=3;
print(x); // 打印: 6 - 结果仍然是 6
print(null ?? 10); // 打印: 10。如果不为空，则显示左侧的值，否则返回右侧的值
```

### 三元运算符

```dart
// 条件 ? 条件如果为真 : 条件如果为假
bool isAvailable;
isAvailable ? orderproduct() : addToFavourite();
```
<!--rehype:className=wrap-text-->

### 条件属性访问
<!--rehype:wrap-class=col-span-2-->

```dart
userObject?.userName
// 上面的代码片段等效于以下代码：
(userObject != null) ? userObject.userName : null
// 您可以将 ? 的多种用途链接起来。一起在一个表达式中
userObject?.userName?.toString()
// 如果 userObject 或 userObject.userName 为 null，则前面的代码返回 null 并且从不调用 toString()
```

### 级联符号 (..)
<!--rehype:wrap-class=row-span-2-->

```dart
// 允许您对同一对象进行一系列操作
// 而不是这样做
var user = User();
user.name = "Nicola";
user.email = "nicola@g.c";
user.age = 24;
// 你可以这样做
var user = User()
  ..name = "Nicola"
  ..email = "nicola@g.c"
  ..age = 24;
```

### 扩展运算符 (...)

```dart
// 将多个值插入到集合中
var list = [1, 2, 3];
var list2 = [0, ...list];
print(list2.length); // 打印: 4
```

另见
----

- [Dart 官方文档](https://dart.dev/) _(dart.dev)_
