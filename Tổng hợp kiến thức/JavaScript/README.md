1. Variables — Biến

1.1. Variable là gì?

Variable là một tên dùng để tham chiếu đến một giá trị mà chương trình đang sử dụng.

let userName = "John";
let age = 30;

Có thể hình dung:

userName ─────→ "John"
age      ─────→ 30

Biến thường dùng để lưu:

dữ liệu người dùng;

trạng thái chương trình;

kết quả tính toán;

object, array;

function;

dữ liệu tạm thời trong quá trình xử lý.

1.2. let, const, var

let

Dùng khi biến có thể được gán lại.

let message = "Hello";
message = "Hi";

const

Dùng khi binding không được gán lại sau khi khởi tạo.

const PI = 3.14159;
// PI = 4; // Error

const không có nghĩa là object bên trong hoàn toàn bất biến.

const user = { name: "John" };

user.name = "Pete"; // OK
// user = {};       // Error

Các hằng số cấu hình cố định thường được đặt theo UPPER_SNAKE_CASE:

const MAX_RETRY = 3;
const API_URL = "/api/users";

var

Là cách khai báo biến cũ. Trong code hiện đại, thông thường ưu tiên let và const.

Đặc điểm quan trọng:

function scope thay vì block scope;

cho phép redeclare;

có cơ chế hoisting;

có thể dẫn đến các hành vi khó đoán trong code lớn.

if (true) {
  var x = 10;
}

console.log(x); // 10

Trong khi:

if (true) {
  let y = 10;
}

// console.log(y); // ReferenceError

Quy tắc thực tế

const → mặc định
let   → khi cần reassignment
var   → chủ yếu gặp trong code cũ

1.3. Scope — Phạm vi biến

Scope quyết định nơi một identifier có thể được truy cập.

Các phạm vi quan trọng:

Global scope

Function scope

Block scope

Module scope

let và const có block scope:

{
  let a = 1;
  const b = 2;
}

// a, b không tồn tại ở đây

1.4. Hoisting

JavaScript xử lý declarations trước khi thực thi code theo cách khiến một số declaration có thể được truy cập trước vị trí xuất hiện trong source.

Function declaration

sayHello();

function sayHello() {
  console.log("Hello");
}

Có thể hoạt động vì function declaration được hoist.

var

console.log(x); // undefined
var x = 10;

Không nên hiểu hoisting đơn giản là "JavaScript kéo nguyên dòng code lên đầu".

let / const

console.log(x); // ReferenceError
let x = 10;

Khoảng thời gian từ đầu scope đến khi declaration được thực thi được gọi là Temporal Dead Zone (TDZ).

1.5. Quy tắc đặt tên

Identifier thường có thể chứa:

chữ cái;

chữ số;

_;

$.

Không được bắt đầu bằng chữ số.

let userName;
let user123;
let _private;
let $element;

// let 123user; // Error

Quy ước phổ biến:

userName
totalPrice
isLoggedIn
getUser()
calculateTotal()

Thường dùng:

camelCase cho biến/hàm;

PascalCase cho class/constructor;

UPPER_SNAKE_CASE cho constant cấu hình thực sự cố định.

2. Data Types — Kiểu dữ liệu

JavaScript là ngôn ngữ dynamic typing.

let value = "hello";
value = 123;
value = true;

Một biến có thể tham chiếu đến các kiểu giá trị khác nhau ở những thời điểm khác nhau.

JavaScript có 8 kiểu dữ liệu chính:

Primitive

string

number

bigint

boolean

undefined

null

symbol

Non-primitive

object

Function về mặt kỹ thuật là một object có khả năng callable.

2.1. Number

number biểu diễn số nguyên và số thực.

let a = 123;
let b = 12.345;

Các giá trị đặc biệt:

Infinity
-Infinity
NaN

Ví dụ:

console.log(10 / 0);      // Infinity
console.log("hello" / 2); // NaN

JavaScript Number dùng floating-point theo chuẩn IEEE 754 nên có các vấn đề về độ chính xác:

0.1 + 0.2 === 0.3; // false

Với số nguyên lớn cần độ chính xác cao, dùng BigInt.

2.2. BigInt

Dùng cho số nguyên vượt quá phạm vi an toàn của Number.

const big = 123456789012345678901234567890n;

Có thể tạo bằng:

BigInt(123);

Không nên trộn BigInt và Number trong cùng phép toán nếu chưa chuyển kiểu:

1n + 2n; // OK
// 1n + 2; // TypeError

2.3. String

String có thể dùng:

"Hello"
'Hello'
`Hello`

Template literal:

const name = "John";
const age = 30;

const message = `Hello ${name}, you are ${age}.`;

Có thể nhúng expression:

const result = `1 + 2 = ${1 + 2}`;

Các thao tác thường gặp:

"hello".length
"hello".toUpperCase()
"hello".includes("ell")
"hello".slice(1, 4)

2.4. Boolean

Chỉ có:

true
false

Thường xuất hiện trong điều kiện:

const isAdult = age >= 18;

if (isAdult) {
  console.log("Allowed");
}

2.5. undefined

Thường biểu diễn việc chưa có giá trị.

let age;

console.log(age); // undefined

Một function không return cũng trả về undefined.

function test() {}

console.log(test()); // undefined

2.6. null

null thường được dùng để biểu diễn trạng thái "không có giá trị" một cách chủ động.

let selectedUser = null;

Có thể phân biệt về ý nghĩa:

undefined → chưa được gán / không có giá trị theo trạng thái mặc định
null      → lập trình viên chủ động biểu diễn "không có giá trị"

Một điểm đặc biệt:

typeof null; // "object"

Đây là hành vi lịch sử của JavaScript, không có nghĩa null thực sự là object.

2.7. Symbol

Symbol tạo ra các giá trị định danh duy nhất.

const id1 = Symbol("id");
const id2 = Symbol("id");

console.log(id1 === id2); // false

Symbol thường được dùng làm property key đặc biệt.

2.8. Object

Object dùng để nhóm dữ liệu có cấu trúc.

const user = {
  name: "John",
  age: 30,
  isAdmin: true
};

Value của property có thể là bất kỳ kiểu nào:

const user = {
  name: "John",
  age: 30,
  hobbies: ["coding", "music"],
  address: {
    city: "Hanoi"
  },
  sayHello() {
    console.log("Hello");
  }
};

2.9. typeof

typeof undefined;        // "undefined"
typeof 123;              // "number"
typeof 10n;              // "bigint"
typeof true;             // "boolean"
typeof "hello";          // "string"
typeof Symbol("id");     // "symbol"
typeof {};               // "object"
typeof function () {};   // "function"
typeof null;             // "object"

Kiểm tra Array nên dùng:

Array.isArray([]);

3. Type Conversion — Chuyển kiểu

Có hai loại:

Explicit conversion  → lập trình viên chủ động chuyển
Implicit conversion  → JavaScript tự chuyển

3.1. String conversion

String(true);      // "true"
String(123);       // "123"
String(null);      // "null"
String(undefined); // "undefined"

3.2. Number conversion

Number("123"); // 123
Number("12.5"); // 12.5
Number(""); // 0
Number("abc"); // NaN
Number(true); // 1
Number(false); // 0
Number(null); // 0
Number(undefined); // NaN

Có thể dùng unary +:

const value = +"123";

Nhưng Number(...) thường dễ đọc hơn.

3.3. Boolean conversion

Falsy values quan trọng:

false
0
-0
0n
""
null
undefined
NaN

Các giá trị còn lại thường là truthy, bao gồm:

" "
[]
{}

Ví dụ:

Boolean(0);   // false
Boolean(1);   // true
Boolean("");  // false
Boolean(" "); // true
Boolean([]);  // true

4. Operators — Toán tử và biểu thức

Đây là phần nền tảng nên học trước conditionals.

4.1. Arithmetic operators

+  -  *  /  %  **

10 % 3;  // 1
2 ** 3;  // 8

4.2. Assignment operators

= 
+=
-=
*=
/=
%=

let total = 10;
total += 5; // 15

4.3. Comparison operators

>
<
>=
<=
===
!==

Ưu tiên dùng:

===
!==

thay vì:

==
!=

vì === và !== không thực hiện coercion kiểu như ==.

5 === "5"; // false
5 == "5";  // true

4.4. Logical operators

&&
||
!

Ví dụ:

age >= 18 && isLoggedIn

Đặc biệt, && và || không nhất thiết trả về Boolean; chúng trả về một operand.

const name = userName || "Guest";

4.5. Nullish coalescing ??

Dùng khi chỉ muốn fallback cho null hoặc undefined.

const count = value ?? 0;

Khác với ||:

0 || 10;  // 10
0 ?? 10;  // 0

"" || "default"; // "default"
"" ?? "default"; // ""

4.6. Optional chaining ?.

Truy cập property an toàn khi object có thể là null/undefined.

user?.address?.city

Gọi function:

user?.sayHello?.();

4.7. Ternary operator

const message = age >= 18 ? "Adult" : "Minor";

Phù hợp với điều kiện ngắn. Với logic phức tạp nên dùng if.

5. Conditionals — Điều kiện

5.1. if

if (condition) {
  // code
}

JavaScript sẽ chuyển condition sang Boolean.

if (0) {
  // không chạy
}

if ("hello") {
  // chạy
}

5.2. if / else

if (age >= 18) {
  console.log("Adult");
} else {
  console.log("Minor");
}

5.3. else if

if (score >= 90) {
  grade = "A";
} else if (score >= 80) {
  grade = "B";
} else {
  grade = "C";
}

5.4. switch

Phù hợp khi so sánh một expression với nhiều giá trị cụ thể.

switch (role) {
  case "admin":
    console.log("Full access");
    break;

  case "user":
    console.log("Normal access");
    break;

  default:
    console.log("Unknown role");
}

Nếu không có break, JavaScript có thể fall-through sang case tiếp theo.

Fall-through đôi khi có chủ ý:

switch (role) {
  case "admin":
  case "manager":
    console.log("Staff access");
    break;
}

6. Loops — Vòng lặp

Vòng lặp dùng để thực hiện một đoạn code nhiều lần.

6.1. while

let i = 0;

while (i < 3) {
  console.log(i);
  i++;
}

Điều kiện được kiểm tra trước mỗi iteration.

6.2. do...while

let i = 0;

do {
  console.log(i);
  i++;
} while (i < 3);

Thân vòng lặp chạy ít nhất một lần.

6.3. for

for (let i = 0; i < 3; i++) {
  console.log(i);
}

Cấu trúc:

for (begin; condition; step)

6.4. break

Dừng vòng lặp ngay lập tức.

for (let i = 0; i < 10; i++) {
  if (i === 5) break;
}

6.5. continue

Bỏ qua iteration hiện tại.

for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) continue;

  console.log(i);
}

6.6. for...of

Duyệt value của iterable, đặc biệt phù hợp với Array.

const fruits = ["Apple", "Orange", "Plum"];

for (const fruit of fruits) {
  console.log(fruit);
}

6.7. for...in

Duyệt property key của object.

const user = {
  name: "John",
  age: 30
};

for (const key in user) {
  console.log(key, user[key]);
}

Không nên dùng for...in để duyệt Array trong code thông thường; dùng for...of, forEach, hoặc các array methods phù hợp hơn.

7. Functions — Hàm

Function là một trong những building blocks quan trọng nhất của JavaScript.

7.1. Function Declaration

function showMessage() {
  console.log("Hello");
}

showMessage();

7.2. Parameters và arguments

function sum(a, b) {
  return a + b;
}

sum(1, 2);

Ở đây:

a, b → parameters
1, 2 → arguments

7.3. Return

function sum(a, b) {
  return a + b;
}

const result = sum(1, 2);

return:

trả kết quả;

kết thúc function tại vị trí đó.

Nếu function không return giá trị:

function test() {}

test(); // undefined

7.4. Default parameters

function greet(name = "Guest") {
  return `Hello ${name}`;
}

7.5. Rest parameters

Cho phép gom nhiều arguments thành Array.

function sum(...numbers) {
  return numbers.reduce((total, n) => total + n, 0);
}

7.6. Function Expression

Function cũng là một value.

const sayHello = function () {
  console.log("Hello");
};

Có thể truyền function vào function khác.

7.7. Arrow function

const sum = (a, b) => a + b;

Nhiều dòng:

const sum = (a, b) => {
  const result = a + b;
  return result;
};

Nếu dùng {} thì muốn return value phải viết return rõ ràng.

Arrow function và this

Arrow function không tạo this riêng; nó lấy this từ lexical scope bên ngoài.

const group = {
  title: "Our Group",
  students: ["John", "Pete"],

  showList() {
    this.students.forEach(student => {
      console.log(this.title, student);
    });
  }
};

Arrow function cũng không có arguments riêng.

7.8. Callback

Callback là function được truyền vào function khác.

function processUser(name, callback) {
  callback(name);
}

function greeting(name) {
  console.log(`Hello ${name}`);
}

processUser("John", greeting);

Callback là nền tảng để hiểu:

forEach;

event handlers;

asynchronous code;

Promise;

các higher-order functions.

8. Scope, Closure và Execution Context

Đây là phần rất quan trọng nhưng thường bị học thiếu.

8.1. Local và outer variables

let userName = "John";

function showMessage() {
  let message = "Hello " + userName;
  console.log(message);
}

Function có thể truy cập biến ở outer scope nếu không tìm thấy identifier trong local scope.

8.2. Closure

Một function có thể "ghi nhớ" lexical environment nơi nó được tạo.

function createCounter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();

console.log(counter()); // 1
console.log(counter()); // 2

Function bên trong vẫn truy cập được count dù createCounter() đã kết thúc.

Closure thường được dùng cho:

private state;

factory function;

callback;

event handler;

module pattern.

9. Objects — Đối tượng

Object biểu diễn dữ liệu dạng key-value.

const user = {
  name: "John",
  age: 30
};

9.1. Đọc property

Dot notation:

user.name

Bracket notation:

user["name"]

Bracket notation hữu ích khi key nằm trong biến:

const key = "name";

console.log(user[key]);

9.2. Thêm / sửa / xóa

user.email = "john@example.com";
user.age = 31;

delete user.email;

9.3. Computed property

const key = "name";

const user = {
  [key]: "John"
};

9.4. Property shorthand

const name = "John";
const age = 30;

const user = {
  name,
  age
};

Tương đương:

const user = {
  name: name,
  age: age
};

9.5. Method

Function bên trong object thường được gọi là method.

const user = {
  name: "John",

  sayHello() {
    console.log(`Hello ${this.name}`);
  }
};

9.6. this

this trong JavaScript phụ thuộc vào cách function được gọi, ngoại trừ arrow function.

const user = {
  name: "John",

  sayHello() {
    console.log(this.name);
  }
};

user.sayHello();

Khi gọi:

user.sayHello()

this là user.

10. Object references và copying

Đây là phần rất dễ nhầm.

10.1. Primitive copy

let a = 10;
let b = a;

b = 20;

console.log(a); // 10

Giá trị primitive được copy theo value.

10.2. Object reference

const user = { name: "John" };
const admin = user;

admin.name = "Pete";

console.log(user.name); // Pete

user và admin cùng tham chiếu đến một object.

Mô hình hóa:

user  ──┐
        ├──→ { name: "Pete" }
admin ──┘

10.3. So sánh object

{} === {}; // false

Vì đây là hai object khác nhau.

const a = {};
const b = a;

a === b; // true

Vì cùng reference.

10.4. const và object

const user = {
  name: "John"
};

user.name = "Pete"; // OK

const khóa việc reassign binding, không tự động freeze object.

10.5. Shallow copy

Spread

const clone = { ...user };

Object.assign

const clone = Object.assign({}, user);

Cả hai chủ yếu là shallow copy.

Nếu có nested object:

const user = {
  name: "John",
  address: {
    city: "Hanoi"
  }
};

const clone = { ...user };

clone.address.city = "Da Nang";

user.address và clone.address vẫn có thể cùng reference.

10.6. Deep clone

Có thể dùng:

const clone = structuredClone(user);

structuredClone hỗ trợ nhiều cấu trúc dữ liệu và circular references.

Tuy nhiên, không phải mọi JavaScript value đều clone được. Ví dụ function không được structured-clone theo cách thông thường.

Không nên mặc định dùng:

JSON.parse(JSON.stringify(object))

như một deep-clone tổng quát vì nó làm mất hoặc biến đổi một số kiểu dữ liệu.

11. Destructuring và Spread

11.1. Object destructuring

const user = {
  name: "John",
  age: 30
};

const { name, age } = user;

Đổi tên:

const { name: userName } = user;

Default:

const { role = "user" } = user;

11.2. Array destructuring

const colors = ["red", "green", "blue"];

const [first, second] = colors;

Bỏ qua phần tử:

const [, , third] = colors;

11.3. Spread syntax

Array:

const a = [1, 2];
const b = [3, 4];

const result = [...a, ...b];

Object:

const user = { name: "John" };

const updatedUser = {
  ...user,
  age: 30
};

Spread rất hữu ích để tạo shallow copy và merge.

12. Arrays — Mảng

Array là cấu trúc dữ liệu có thứ tự.

const fruits = ["Apple", "Orange", "Plum"];

Index bắt đầu từ 0.

fruits[0]; // Apple
fruits[2]; // Plum

12.1. length

fruits.length;

Phần tử cuối:

fruits[fruits.length - 1];

hoặc:

fruits.at(-1);

12.2. Thêm/xóa phần tử

push

Thêm cuối:

fruits.push("Pear");

pop

Xóa cuối và trả về phần tử:

const last = fruits.pop();

unshift

Thêm đầu:

fruits.unshift("Apple");

shift

Xóa đầu và trả về phần tử:

const first = fruits.shift();

12.3. splice

Thay đổi array gốc.

arr.splice(start, deleteCount, ...items);

Ví dụ:

const arr = ["I", "study", "JavaScript"];

arr.splice(2, 0, "complex", "language");

Kết quả:

["I", "study", "complex", "language", "JavaScript"]

12.4. slice

Tạo array mới từ một phần array.

const part = arr.slice(start, end);

end không được lấy vào.

[1, 2, 3, 4].slice(1, 3);
// [2, 3]

Không mutate array gốc.

12.5. concat

const result = [1, 2].concat([3, 4]);

Không mutate array gốc.

13. Array methods — Xử lý mảng bằng tư duy Functional

Đây là nhóm method cần học kỹ.

13.1. forEach

Dùng khi muốn thực hiện side effect cho từng phần tử.

users.forEach((user, index) => {
  console.log(index, user.name);
});

forEach không tạo array kết quả mới.

13.2. map

Biến đổi mỗi phần tử thành một giá trị mới.

const numbers = [1, 2, 3];

const doubled = numbers.map(n => n * 2);

// [2, 4, 6]

Tư duy:

Array A
  ↓ map
Array B có cùng số lượng phần tử

13.3. filter

Giữ lại các phần tử thỏa điều kiện.

const numbers = [1, 2, 3, 4];

const even = numbers.filter(n => n % 2 === 0);

// [2, 4]

13.4. find

Trả về phần tử đầu tiên thỏa điều kiện.

const user = users.find(user => user.id === 2);

Nếu không tìm thấy:

undefined

13.5. findIndex

const index = users.findIndex(user => user.id === 2);

Không tìm thấy:

-1

13.6. findLast / findLastIndex

Tìm từ cuối về đầu.

arr.findLast(x => x > 10);
arr.findLastIndex(x => x > 10);

13.7. includes

Kiểm tra tồn tại:

[1, 2, 3].includes(2); // true

13.8. indexOf / lastIndexOf

arr.indexOf(value);
arr.lastIndexOf(value);

Nếu không tìm thấy:

-1

13.9. some

Có ít nhất một phần tử thỏa điều kiện?

const hasAdult = users.some(user => user.age >= 18);

Trả về Boolean.

13.10. every

Tất cả phần tử có thỏa điều kiện?

const allAdults = users.every(user => user.age >= 18);

13.11. reduce

Gom nhiều phần tử thành một kết quả.

const numbers = [1, 2, 3, 4];

const total = numbers.reduce(
  (sum, current) => sum + current,
  0
);

// 10

Có thể dùng cho:

tổng;

đếm;

group;

tạo object;

xây dựng cấu trúc dữ liệu.

13.12. sort

sort() mutate array gốc.

const numbers = [10, 2, 5];

numbers.sort((a, b) => a - b);

Nếu không truyền comparator, sort mặc định theo thứ tự chuỗi.

[10, 2, 5].sort();
// không phải cách đáng tin để sort số tăng dần

13.13. reverse

Đảo array và mutate array gốc.

arr.reverse();

Nếu muốn tránh mutate, tạo bản sao trước:

const reversed = [...arr].reverse();

13.14. flat và flatMap

[1, [2, 3], [4]].flat();
// [1, 2, 3, 4]

flatMap kết hợp map + flatten một mức:

const result = users.flatMap(user => user.tags);

13.15. Array.isArray

Array.isArray([]);
 // true

Array.isArray({});
 // false

typeof [] trả về "object" nên không dùng typeof để phân biệt Array.

14. String methods quan trọng

String cũng có nhiều method tương tự Array.

const text = "JavaScript";

Độ dài

text.length;

Tìm kiếm

text.includes("Script");
text.startsWith("Java");
text.endsWith("Script");

Cắt

text.slice(0, 4);

Chuyển chữ

text.toUpperCase();
text.toLowerCase();

Loại bỏ khoảng trắng đầu/cuối

"  hello  ".trim();

Tách thành Array

"a,b,c".split(",");

Ghép Array thành String

["a", "b", "c"].join(",");

15. Map, Set và các cấu trúc dữ liệu thường dùng

15.1. Map

Lưu key-value.

const map = new Map();

map.set("name", "John");
map.set("age", 30);

map.get("name");
map.has("age");
map.delete("age");

Ưu điểm quan trọng: key của Map có thể là nhiều kiểu dữ liệu khác nhau, không chỉ string/symbol.

15.2. Set

Lưu các value duy nhất.

const set = new Set([1, 2, 2, 3]);

console.log(set); // 1, 2, 3

Kiểm tra:

set.has(2);

Loại duplicate trong Array:

const unique = [...new Set(numbers)];

16. Error Handling — Xử lý lỗi

Lỗi có thể xuất hiện do:

input không hợp lệ;

network;

server;

logic;

runtime;

dữ liệu không đúng cấu trúc.

16.1. throw

throw new Error("Something went wrong");

16.2. try...catch

try {
  riskyOperation();
} catch (error) {
  console.error(error);
}

16.3. finally

finally chạy sau try/catch bất kể có lỗi hay không.

try {
  // work
} catch (error) {
  // handle error
} finally {
  // cleanup
}

16.4. Error object

const error = new Error("Invalid input");

console.log(error.name);
console.log(error.message);
console.log(error.stack);

Một số Error type:

TypeError
ReferenceError
SyntaxError
RangeError

Có thể tạo error cụ thể:

throw new TypeError("Expected a number");

17. Asynchronous JavaScript

JavaScript thường chạy code theo mô hình event loop và có thể xử lý các tác vụ bất đồng bộ mà không chặn toàn bộ ứng dụng.

Ví dụ:

network request;

timer;

user event;

file I/O trong môi trường hỗ trợ;

database trong môi trường server.

Ba khái niệm cần hiểu theo thứ tự:

Callback
   ↓
Promise
   ↓
async/await

18. Promise

Promise đại diện cho kết quả của một tác vụ bất đồng bộ trong tương lai.

Có 3 trạng thái:

pending
   ↓
fulfilled

hoặc

pending
   ↓
rejected

Promise đã settled thì không chuyển sang trạng thái khác.

18.1. Tạo Promise

const promise = new Promise((resolve, reject) => {
  // async work

  if (success) {
    resolve(value);
  } else {
    reject(error);
  }
});

executor chạy ngay khi Promise được tạo.

18.2. .then()

promise.then(value => {
  console.log(value);
});

18.3. .catch()

promise.catch(error => {
  console.error(error);
});

18.4. .finally()

promise.finally(() => {
  console.log("Finished");
});

19. Promise chaining

Promise có thể nối thành chuỗi.

getUser()
  .then(user => getOrders(user.id))
  .then(orders => processOrders(orders))
  .catch(error => {
    console.error(error);
  });

Giá trị return từ callback của .then() trở thành input cho .then() tiếp theo.

20. Promise API

Promise.all

Chờ tất cả Promise fulfilled.

const results = await Promise.all([
  fetchUsers(),
  fetchProducts()
]);

Nếu một Promise reject, Promise.all reject.

Phù hợp khi các tác vụ độc lập và cần tất cả kết quả.

Promise.allSettled

Chờ tất cả hoàn thành, bất kể fulfilled/rejected.

const results = await Promise.allSettled([
  task1(),
  task2()
]);

Phù hợp khi muốn biết kết quả của từng task.

Promise.race

Settles theo Promise đầu tiên settle.

await Promise.race([
  request(),
  timeout()
]);

Promise.any

Chờ Promise đầu tiên fulfilled.

Nếu tất cả reject thì Promise.any reject.

21. async/await

async/await là syntax giúp làm việc với Promise theo cách dễ đọc hơn.

21.1. async

async function getData() {
  return 1;
}

Function async luôn trả về Promise.

getData().then(console.log);

21.2. await

async function loadData() {
  const result = await getData();
  console.log(result);
}

await làm function async tạm dừng tại điểm đó cho đến khi Promise settle; nó không "đóng băng" toàn bộ JavaScript runtime.

Trong môi trường hỗ trợ top-level await, await cũng có thể dùng ở module scope.

21.3. Chạy song song

Không nên viết:

const a = await taskA();
const b = await taskB();

nếu taskA và taskB hoàn toàn độc lập và có thể chạy đồng thời.

Thay vào đó:

const [a, b] = await Promise.all([
  taskA(),
  taskB()
]);

21.4. Error handling với async/await

async function loadData() {
  try {
    const response = await fetch(url);
    return await response.json();
  } catch (error) {
    console.error(error);
  }
}

Hoặc xử lý bên ngoài:

loadData().catch(error => {
  console.error(error);
});

Một điểm quan trọng với fetch:

fetch() thường chỉ reject khi request gặp lỗi ở tầng network. HTTP status như 404 hoặc 500 không tự động khiến Promise reject. Nên kiểm tra response.ok khi cần.

const response = await fetch(url);

if (!response.ok) {
  throw new Error(`HTTP error: ${response.status}`);
}

22. Modules

Module giúp chia chương trình thành nhiều file độc lập.

Mục tiêu:

tổ chức code;

tái sử dụng;

tránh global namespace;

quản lý dependency;

tạo ranh giới rõ giữa các phần của ứng dụng.

22.1. export

export const API_URL = "/api";

export function getUser() {
  // ...
}

22.2. import

import { API_URL, getUser } from "./api.js";

Có thể alias:

import { getUser as fetchUser } from "./api.js";

22.3. Default export

export default function getUser() {
  // ...
}

Import:

import getUser from "./api.js";

Một module chỉ có một default export.

22.4. Re-export

export { getUser } from "./api.js";

Hoặc:

export * from "./api.js";

23. DOM và Browser JavaScript

Phần này là cầu nối giữa JavaScript và web browser.

23.1. DOM

DOM biểu diễn HTML dưới dạng cây object.

Ví dụ:

<button id="btn">Click</button>

JavaScript:

const button = document.querySelector("#btn");

23.2. Thay đổi nội dung

button.textContent = "Clicked";

23.3. Class

button.classList.add("active");
button.classList.remove("active");
button.classList.toggle("active");

23.4. Events

button.addEventListener("click", () => {
  console.log("Clicked");
});

Các event thường gặp:

click
input
change
submit
keydown
keyup
mouseover
load

23.5. Event object

button.addEventListener("click", event => {
  console.log(event.target);
});

23.6. preventDefault

Dùng để ngăn hành vi mặc định của event.

form.addEventListener("submit", event => {
  event.preventDefault();
});

23.7. Event bubbling

Event thường bubble từ element con lên element cha.

Điều này dẫn đến kỹ thuật event delegation:

list.addEventListener("click", event => {
  if (event.target.matches(".item")) {
    // handle item
  }
});

24. Fetch và HTTP cơ bản

fetch() dùng để thực hiện network request.

const response = await fetch("/api/users");

Đọc JSON:

const data = await response.json();

POST:

const response = await fetch("/api/users", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    name: "John"
  })
});

Luồng thường gặp:

fetch()
   ↓
Response
   ↓
kiểm tra response.ok
   ↓
response.json()
   ↓
data

25. Classes và Prototype — Nền tảng Object Model

JavaScript là ngôn ngữ prototype-based.

class cung cấp syntax thuận tiện hơn để làm việc với prototype.

25.1. Class

class User {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    console.log(`Hello ${this.name}`);
  }
}

Tạo instance:

const user = new User("John");

user.sayHello();

25.2. extends

class Admin extends User {
  deleteUser() {
    console.log("Delete user");
  }
}

25.3. Prototype

Khi truy cập property/method không có trực tiếp trên object, JavaScript có thể tìm tiếp trên prototype chain.

Mô hình:

object
   ↓
prototype
   ↓
prototype của prototype
   ↓
null

Hiểu prototype giúp giải thích:

inheritance;

method của Array;

method của String;

Object.prototype;

instanceof.

26. Những khái niệm cần đặc biệt phân biệt

== vs ===

==  → có coercion
=== → strict equality

Ưu tiên ===.

null vs undefined

undefined → chưa có giá trị / chưa được gán
null      → chủ động biểu diễn không có giá trị

map vs forEach

forEach → thực hiện side effect
map     → tạo array mới

filter vs find

filter → trả về nhiều phần tử dưới dạng Array
find   → trả về phần tử đầu tiên

slice vs splice

slice  → không mutate, tạo array mới
splice → mutate array gốc

for...of vs for...in

for...of → value
for...in → key

Shallow copy vs Deep copy

shallow copy
→ nested object vẫn có thể dùng chung reference

deep copy
→ nested structure được clone độc lập

Promise.all vs tuần tự await

tuần tự:
A → xong → B

song song:
A ─────→
B ─────→
       ↓
   Promise.all

27. Mutating và Non-mutating methods

Một tư duy rất quan trọng khi làm việc với Array/Object là biết operation có làm thay đổi dữ liệu gốc hay không.

Thường mutate Array

push
pop
shift
unshift
splice
sort
reverse

Thường không mutate

slice
concat
map
filter
find
includes
reduce
toSorted
toReversed

Khi code theo hướng immutable, có thể tạo bản sao trước:

const sorted = [...numbers].sort((a, b) => a - b);

Hoặc dùng các method non-mutating hiện đại như:

numbers.toSorted((a, b) => a - b);
numbers.toReversed();

28. Coding conventions nên ghi nhớ

Biến

const userName = "John";
let total = 0;

Boolean

Nên đặt tên thể hiện trạng thái:

isActive
isLoggedIn
hasPermission
canEdit

Function

Tên thường thể hiện hành động:

getUser()
createUser()
calculateTotal()
checkPermission()
validateEmail()

Tránh function quá lớn

Thay vì:

processEverything();

nên chia thành:

validateInput();
fetchData();
transformData();
saveData();

29. Lộ trình học JavaScript hợp lý

Level 1 — Syntax

variables;

primitive types;

operators;

type conversion;

conditionals;

loops.

Level 2 — Function

parameters;

return;

function declaration;

function expression;

arrow function;

callback;

scope;

closure.

Level 3 — Data structures

object;

array;

destructuring;

spread/rest;

Map;

Set.

Level 4 — Array/Object methods

map;

filter;

reduce;

find;

some;

every;

sort;

slice;

splice;

Object methods.

Level 5 — Error & async

try/catch;

throw;

Promise;

then/catch/finally;

Promise.all;

Promise.allSettled;

async/await;

fetch.

Level 6 — Browser

DOM;

events;

event bubbling;

event delegation;

forms;

storage;

Fetch API.

Level 7 — Architecture

ES Modules;

classes/prototypes;

separation of concerns;

reusable functions;

state management;

testing;

tooling.

30. Cheat sheet cuối tài liệu

// Variable
const name = "John";
let age = 30;

// Types
typeof "hello"; // string
typeof 123;     // number
typeof true;    // boolean
typeof null;    // object
typeof undefined; // undefined

// Conversion
String(123);
Number("123");
Boolean(1);

// Condition
if (age >= 18) {
  // ...
} else {
  // ...
}

// Loop
for (let i = 0; i < 10; i++) {
  // ...
}

for (const item of items) {
  // value
}

for (const key in object) {
  // key
}

// Function
function sum(a, b) {
  return a + b;
}

const multiply = (a, b) => a * b;

// Object
const user = {
  name: "John",
  age: 30
};

user.name;
user["name"];

// Destructuring
const { name, age } = user;

// Array
const numbers = [1, 2, 3, 4];

numbers.map(x => x * 2);
numbers.filter(x => x % 2 === 0);
numbers.find(x => x > 2);
numbers.some(x => x > 2);
numbers.every(x => x > 0);
numbers.reduce((sum, x) => sum + x, 0);

// Error
try {
  riskyOperation();
} catch (error) {
  console.error(error);
}

// Promise
fetch("/api/users")
  .then(response => {
    if (!response.ok) {
      throw new Error(`HTTP ${response.status}`);
    }

    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error(error));

// async/await
async function loadUsers() {
  try {
    const response = await fetch("/api/users");

    if (!response.ok) {
      throw new Error(`HTTP ${response.status}`);
    }

    return await response.json();
  } catch (error) {
    console.error(error);
  }
}

// Parallel async tasks
const [users, products] = await Promise.all([
  getUsers(),
  getProducts()
]);

// Module
export function getUser() {
  // ...
}

import { getUser } from "./user.js";
