## 01. Variables - Biến
**📝 Giới thiệu & Lý thuyết:** 
Biến là một định danh để lưu trữ giá trị trong bộ nhớ. JS hiện đại sử dụng `const` (hằng số, block-scope) và `let` (có thể gán lại, block-scope). `var` là cách cũ (function-scope, bị hoisting).

**🎯 Trường hợp sử dụng:**
*   Dùng `const` mặc định cho 95% trường hợp để code an toàn, khó bị lỗi ghi đè.
*   Dùng `let` khi chắc chắn biến đó sẽ thay đổi (ví dụ: biến đếm trong vòng lặp, trạng thái thay đổi).
<img width="942" height="122" alt="image" src="https://github.com/user-attachments/assets/56ce8162-2044-49dc-9238-eae7311fd317" />


## 02. Data Types - Kiểu dữ liệu

**📝 Giới thiệu & Lý thuyết cơ bản:**
JavaScript là ngôn ngữ **Dynamic Typing** (Kiểu dữ liệu động). Nghĩa là bạn không cần khai báo kiểu dữ liệu cho biến trước khi chạy chương trình, và một biến có thể thay đổi từ kiểu số sang chuỗi ở bất kỳ đâu trong quá trình thực thi. 

Trong JavaScript có tổng cộng **8 kiểu dữ liệu** cơ bản, được chia làm 2 nhóm chính dựa trên cách chúng lưu trữ trong bộ nhớ:

### 1. Nhóm Primitive (Nguyên thủy - Truyền theo giá trị)
Dữ liệu nguyên thủy là các giá trị đơn giản, không thể bị biến đổi (Immutable). 
*   **`Number`**: Lưu cả số nguyên và số thực (dựa trên chuẩn 64-bit IEEE 754). Chứa các giá trị đặc biệt như `Infinity`, `-Infinity` và `NaN` (Not a Number - một lỗi tính toán). *Lưu ý:* Vì tính toán dấu phẩy động, `0.1 + 0.2 === 0.3` sẽ trả về `false`.
*   **`String`**: Biểu diễn chuỗi văn bản. Được bọc trong nháy đơn `''`, nháy kép `""`, hoặc Template Literal (backticks) ` `` ` để nhúng biến.
*   **`Boolean`**: Logic đúng/sai, chỉ có 2 giá trị `true` hoặc `false`.
*   **`undefined`**: Trạng thái "vô định". Khi một biến được khai báo nhưng chưa gán giá trị, JavaScript tự động cấp cho nó giá trị `undefined`.
*   **`null`**: Trạng thái "rỗng". Đây là giá trị do **lập trình viên chủ động gán** để biểu thị rằng biến này hiện tại không trỏ tới bất kỳ object hay dữ liệu nào.
*   **`BigInt`**: Dùng để lưu các số nguyên cực kỳ lớn vượt qua giới hạn an toàn của Number (`Number.MAX_SAFE_INTEGER`). Hậu tố thêm chữ `n` ở cuối (vd: `100n`).
*   **`Symbol`**: Một định danh duy nhất (unique) và ẩn. Thường dùng làm key đặc biệt cho Object để tránh xung đột tên.

### 2. Nhóm Reference (Tham chiếu - Truyền theo địa chỉ vùng nhớ)
*   **`Object`**: Cấu trúc dữ liệu phức hợp. Mọi thứ không phải kiểu nguyên thủy (như Array, Function, Date, Set, Map...) về bản chất đều là Object.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Phân biệt `null` và `undefined`:** Đừng bao giờ chủ động gán `undefined` cho một biến. Nếu muốn reset dữ liệu của một biến, hãy gán nó bằng `null`. Hãy để `undefined` làm đúng nhiệm vụ là giá trị mặc định của hệ thống.
*   **Kiểm tra kiểu dữ liệu:** Sử dụng toán tử `typeof`. Tuy nhiên, cẩn thận với một lỗi lịch sử (bug) không bao giờ được sửa của JavaScript: `typeof null` lại trả về `"object"`. Để kiểm tra Array, không dùng `typeof`, hãy dùng `Array.isArray()`.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. NUMBER & BIGINT ---
let price = 99.99;
let invalidMath = "Hello" / 2; // NaN (Not a Number)
console.log(Number.isNaN(invalidMath)); // true

const hugeNumber = 9007199254740991n; // BigInt (Có chữ n ở cuối)

// --- 2. STRING ---
const framework = "React";
// Dùng Backticks (`) để nhúng biến và xuống dòng dễ dàng (Template literal)
const description = `Tôi đang học ${framework} 
vào năm 2024.`; 

// --- 3. NULL vs UNDEFINED ---
let userConfig; // Hệ thống tự gán là undefined
let activeUser = null; // Lập trình viên chủ động khai báo biến này rỗng

console.log(userConfig === undefined); // true
console.log(userConfig === null);      // false
console.log(activeUser === null);      // true

// --- 4. BẢNG KIỂM TRA typeof (Bắt buộc nhớ) ---
console.log(typeof 42);             // "number"
console.log(typeof "JS");           // "string"
console.log(typeof true);           // "boolean"
console.log(typeof undefined);      // "undefined"
console.log(typeof Symbol("id"));   // "symbol"
console.log(typeof 10n);            // "bigint"

// CÁC TRƯỜNG HỢP ĐẶC BIỆT CẦN LƯU Ý
console.log(typeof null);           // "object" ⚠️ (Bug lịch sử của JS)
console.log(typeof {});             // "object"
console.log(typeof []);             // "object" ⚠️ (Dùng Array.isArray([]) thay thế)
console.log(typeof function(){});   // "function" (Bản chất hàm vẫn là Object, nhưng typeof tách riêng để dễ nhận diện)
```

## 03. Type Conversion - Chuyển kiểu

**📝 Giới thiệu & Lý thuyết cơ bản:**
Vì JavaScript là ngôn ngữ kiểu động, các giá trị có thể được chuyển đổi qua lại giữa các kiểu dữ liệu khác nhau (ví dụ: từ Chuỗi sang Số, từ Số sang Boolean). Quá trình này chia làm 2 loại chính:

1.  **Explicit Conversion (Chuyển kiểu Tường minh / Chủ động):** Là khi lập trình viên chủ động sử dụng các hàm tích hợp sẵn như `String()`, `Number()`, `Boolean()` để ép kiểu dữ liệu. Điều này giúp code rõ ràng và dễ kiểm soát.
2.  **Implicit Conversion / Coercion (Chuyển kiểu Ngầm định / Tự động):** Là khi JavaScript tự động ép kiểu dữ liệu ngầm ở hậu trường để thực hiện một phép toán. (Ví dụ: khi bạn cộng một chuỗi với một số, JS sẽ tự ép số đó thành chuỗi).

**🔍 Khái niệm Truthy và Falsy (Rất quan trọng):**
Khi chuyển đổi một giá trị bất kỳ sang kiểu `Boolean` (logic Đúng/Sai), JavaScript quy định danh sách **Falsy values** (những giá trị bị coi là `false`). Danh sách này bao gồm đúng 8 giá trị:
*   `false`
*   `0` và `-0`
*   `0n` (BigInt zero)
*   `""` (Chuỗi rỗng)
*   `null`
*   `undefined`
*   `NaN`
*(Mọi giá trị khác không nằm trong danh sách này đều được coi là **Truthy** - tức là `true`, bao gồm cả chuỗi `"0"`, chuỗi khoảng trắng `" "`, mảng rỗng `[]` và object rỗng `{}`).*

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Luôn sử dụng Explicit Conversion:** Đặc biệt là khi xử lý dữ liệu nhập từ người dùng (như thẻ `<input>`), vì giá trị lấy ra luôn là String. Hãy dùng `Number()` hoặc dấu cộng tiền tố `+` để ép về số trước khi tính toán.
*   **Cảnh giác với phép cộng (`+`):** Trong JS, dấu `+` vừa là phép cộng số học, vừa là phép nối chuỗi. Nếu một trong hai toán hạng là chuỗi, JS sẽ ưu tiên biến toán hạng còn lại thành chuỗi và nối chúng lại. Các phép toán khác (`-`, `*`, `/`) sẽ ưu tiên ép kiểu về dạng Số.
*   **Tránh dùng `==`:** Toán tử so sánh lỏng lẻo (`==`) sẽ kích hoạt Implicit Coercion (tự ép kiểu để so sánh). Luôn dùng `===` để so sánh cả giá trị lẫn kiểu dữ liệu, giúp triệt tiêu hoàn toàn các bug khó đoán.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. EXPLICIT CONVERSION (Chủ động - Khuyên dùng) ---
// Chuyển sang Chuỗi (String)
const num = 123;
console.log(String(num));        // "123"
console.log(num.toString());     // "123"

// Chuyển sang Số (Number)
const strPrice = "49.99";
console.log(Number(strPrice));   // 49.99
console.log(+strPrice);          // 49.99 (Sử dụng dấu + đứng trước là một mẹo viết ngắn gọn)
console.log(parseInt("100px"));  // 100 (parseInt bóc tách phần số nguyên từ chuỗi)
console.log(Number("abc"));      // NaN (Không thể chuyển một chuỗi chữ thành số)

// Chuyển sang Boolean
console.log(Boolean(1));         // true
console.log(!! "Hello");         // true (Dùng 2 dấu chấm than !! là mẹo ép kiểu Boolean nhanh)

// --- 2. TRUTHY & FALSY (Hay dùng trong if/else) ---
const emptyArray = [];
console.log(Boolean(emptyArray));// true (Mảng rỗng là Truthy)

const userAge = 0;
// Bug phổ biến: Nếu age là 0 (Falsy), nó sẽ bị coi là chưa nhập
if (!userAge) {
  console.log("Bạn chưa nhập tuổi hợp lệ!"); 
}

// --- 3. IMPLICIT COERCION (Tự động - Cần cảnh giác) ---
console.log("5" + 2);            // "52" (Toán tử + ưu tiên nối chuỗi)
console.log("5" - 2);            // 3    (Toán tử - tự ép "5" thành số 5)
console.log("10" * "2");         // 20   (Toán tử * tự ép cả 2 thành số)

// Sự nguy hiểm của so sánh lỏng lẻo (==)
console.log(0 == false);         // true  (Vì 0 là Falsy)
console.log("" == 0);            // true  (Chuỗi rỗng bị ép về số 0)
console.log([] == 0);            // true  (Mảng rỗng bị ép về chuỗi rỗng, rồi ép về 0)
// -> ĐÓ LÀ LÝ DO LUÔN PHẢI DÙNG ===
console.log("" === 0);           // false (Khác kiểu dữ liệu)
```
## 04. Operators - Toán tử

**📝 Giới thiệu & Lý thuyết cơ bản:**
Toán tử trong JavaScript là các ký hiệu dùng để thực hiện các phép tính logic hoặc toán học trên các giá trị (toán hạng). Chúng ta có các nhóm toán tử chính sau:

1.  **Toán tử số học (Arithmetic):** `+`, `-`, `*`, `/`, `%` (chia lấy dư), `**` (lũy thừa).
2.  **Toán tử gán (Assignment):** `=`, `+=`, `-=`, `*=`, `/=`.
3.  **Toán tử so sánh (Comparison):** `>`, `<`, `>=`, `<=`, `==`, `===`, `!=`, `!==`.
4.  **Toán tử logic (Logical):** `&&` (AND), `||` (OR), `!` (NOT).
5.  **Toán tử hiện đại (Modern/ES6+):** 
    *   **Optional Chaining (`?.`):** Truy cập an toàn vào thuộc tính lồng sâu của một object.
    *   **Nullish Coalescing (`??`):** Cung cấp giá trị dự phòng (fallback) chặt chẽ hơn so với `||`.

**🔍 Cơ chế Short-circuiting (Đoản mạch):**
Các toán tử logic (`&&` và `||`) trong JS không nhất thiết phải trả về `true` hoặc `false`. Chúng trả về **giá trị của một trong các toán hạng**.
*   `A || B`: Trả về A nếu A là Truthy, ngược lại trả về B.
*   `A && B`: Trả về A nếu A là Falsy, ngược lại trả về B.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **LUÔN DÙNG `===` VÀ `!==`:** Tuyệt đối tránh dùng `==` và `!=` vì chúng gây ra lỗi tự ép kiểu (Implicit Coercion) rất khó debug.
*   **Phân biệt `||` và `??` khi làm giá trị mặc định:** 
    *   Dùng `||` khi bạn muốn loại bỏ *tất cả* các giá trị Falsy (bao gồm cả `0` và `""`).
    *   Dùng `??` khi bạn *chỉ* muốn loại bỏ `null` và `undefined` (nghĩa là `0` và `""` vẫn được coi là giá trị hợp lệ).
*   **Dùng `?.` để tránh lỗi Crash App:** Thay vì viết các câu lệnh `if` lồng nhau để kiểm tra xem một object có tồn tại thuộc tính hay không, hãy dùng `?.` để code chạy an toàn, nếu không có thuộc tính nó sẽ trả về `undefined` thay vì báo lỗi đỏ.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. TOÁN TỬ SO SÁNH ---
console.log(5 == "5");  // true  (Tự ép kiểu - KHÔNG NÊN DÙNG)
console.log(5 === "5"); // false (Khác kiểu dữ liệu - LUÔN DÙNG)

// --- 2. SHORT-CIRCUITING VỚI || VÀ && ---
const userName = "Alice";
const defaultName = "Guest";

// Dùng || để gán giá trị mặc định
const displayName = userName || defaultName; 
console.log(displayName); // "Alice" (Vì "Alice" là Truthy)

// Dùng && để thực thi logic có điều kiện (Rất phổ biến trong React)
const isLoggedIn = true;
isLoggedIn && console.log("Chào mừng bạn quay lại!"); // Nếu isLoggedIn là true thì mới chạy console.log

// --- 3. SỰ KHÁC BIỆT GIỮA || VÀ ?? (Nullish Coalescing) ---
const score = 0; // Giả sử người dùng thi được 0 điểm

// Dùng || (Sai logic)
const finalScore1 = score || 10; 
console.log(finalScore1); // 10 (Vì 0 là Falsy nên nó lấy 10 -> Điểm của user bị ghi đè sai)

// Dùng ?? (Đúng logic)
const finalScore2 = score ?? 10; 
console.log(finalScore2); // 0 (?? chỉ bỏ qua null và undefined, 0 vẫn là giá trị hợp lệ)

// --- 4. OPTIONAL CHAINING (?.) ---
const user = {
  id: 1,
  profile: {
    name: "Bob"
    // Giả sử API trả về thiếu trường address
  }
};

// Truy cập kiểu cũ (Dễ crash app "Cannot read properties of undefined")
// const city = user.profile.address.city; 

// Truy cập bằng Optional Chaining (An toàn)
const safeCity = user?.profile?.address?.city;
console.log(safeCity); // undefined (App vẫn sống khỏe)

// Kết hợp ?. và ??
const displayCity = user?.profile?.address?.city ?? "Chưa cập nhật";
console.log(displayCity); // "Chưa cập nhật"
```
## 05. Conditionals - Điều kiện

**📝 Giới thiệu & Lý thuyết cơ bản:**
Conditionals là các cấu trúc điều khiển luồng thực thi của chương trình. Khi một điều kiện được đưa vào, JavaScript sẽ tự động ép kiểu điều kiện đó về dạng Boolean (dựa trên quy tắc Truthy/Falsy) để quyết định xem khối lệnh bên trong có được chạy hay không.
Các cấu trúc phổ biến bao gồm:
1.  **`if...else if...else`**: Cấu trúc rẽ nhánh tiêu chuẩn cho các logic phức tạp.
2.  **`switch...case`**: Phù hợp khi cần so sánh một giá trị (expression) cụ thể với nhiều trường hợp khác nhau. Lưu ý phải có `break` để thoát khỏi vòng kiểm tra, nếu không sẽ xảy ra hiện tượng *fall-through* (chạy tuột xuống các case bên dưới).
3.  **Ternary Operator (Toán tử ba ngôi `? :`)**: Cú pháp rút gọn của `if...else`, rất hữu ích khi cần gán giá trị cho biến dựa trên một điều kiện.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Dùng Toán tử ba ngôi cho việc gán giá trị:** Chỉ nên dùng khi điều kiện đơn giản và ngắn. Tuyệt đối không lồng 2-3 toán tử ba ngôi vào nhau vì sẽ làm code cực kỳ khó đọc.
*   **Dùng Object Literal thay cho `switch...case` dài:** Nếu có quá nhiều case, việc dùng một Object để ánh xạ (Mapping) giá trị sẽ làm code gọn gàng và chạy nhanh hơn.
*   **Kỹ thuật Early Return (Guard Clause):** Thay vì viết `if...else` lồng nhau sâu hoắm (Pyramid of Doom), hãy kiểm tra các trường hợp lỗi/ngoại lệ và `return` (thoát hàm) ngay lập tức ở đầu. Phần code logic chính sẽ được đẩy ra ngoài cùng, giúp hàm phẳng và cực kỳ dễ theo dõi.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. TOÁN TỬ BA NGÔI (Ternary Operator) ---
const age = 20;
// Tốt: Gán giá trị nhanh gọn
const status = age >= 18 ? "Người lớn" : "Trẻ em"; 

// Xấu: Không nên lồng nhau như thế này
// const category = age < 12 ? "Nhi đồng" : age < 18 ? "Thiếu niên" : "Người lớn";

// --- 2. SWITCH...CASE VÀ FALL-THROUGH ---
const role = "editor";

switch (role) {
  case "admin":
    console.log("Quyền cao nhất: Xem, Thêm, Sửa, Xóa");
    break;
  case "editor":
  case "author": // Fall-through có chủ ý: editor và author có chung quyền này
    console.log("Quyền trung bình: Xem, Thêm, Sửa");
    break;
  default:
    console.log("Quyền cơ bản: Chỉ xem");
}

// --- 3. KỸ THUẬT EARLY RETURN (RẤT QUAN TRỌNG) ---

// ❌ CÁCH VIẾT TỒI (Nested if - Lồng nhau quá sâu):
function processOrderBad(order) {
  if (order) {
    if (order.isPaid) {
      if (order.items.length > 0) {
        return "Giao hàng thành công!";
      } else {
        return "Lỗi: Đơn hàng không có sản phẩm.";
      }
    } else {
      return "Lỗi: Đơn hàng chưa thanh toán.";
    }
  } else {
    return "Lỗi: Không tìm thấy đơn hàng.";
  }
}

// ✅ CÁCH VIẾT TỐT (Early Return - Trả về sớm):
function processOrderGood(order) {
  // Loại trừ mọi trường hợp lỗi ngay từ đầu
  if (!order) return "Lỗi: Không tìm thấy đơn hàng.";
  if (!order.isPaid) return "Lỗi: Đơn hàng chưa thanh toán.";
  if (order.items.length === 0) return "Lỗi: Đơn hàng không có sản phẩm.";
  
  // Logic chính nằm ở ngoài cùng, rất dễ đọc
  return "Giao hàng thành công!";
}

// --- 4. OBJECT MAPPING (Thay thế Switch/If dài) ---
const getStatusMessage = (statusCode) => {
  const statusMap = {
    "200": "Thành công",
    "400": "Lỗi dữ liệu đầu vào",
    "404": "Không tìm thấy",
    "500": "Lỗi máy chủ"
  };
  
  // Dùng toán tử ?? để trả về giá trị mặc định nếu không khớp code nào
  return status
```

## 06. Loops - Vòng lặp

**📝 Giới thiệu & Lý thuyết cơ bản:**
Vòng lặp giúp thực thi một đoạn mã nhiều lần dựa trên một điều kiện. JavaScript cung cấp nhiều loại vòng lặp để phục vụ các cấu trúc dữ liệu khác nhau:
1.  **`for`**: Vòng lặp đếm cơ bản, dùng khi biết trước số lần lặp. Cấu trúc gồm 3 phần: *Khởi tạo; Điều kiện; Bước nhảy*.
2.  **`while` / `do...while`**: Dùng khi không biết trước số lần lặp, vòng lặp chạy miễn là điều kiện còn đúng (`do...while` đảm bảo code bên trong chạy ít nhất 1 lần trước khi kiểm tra điều kiện).
3.  **`for...of` (ES6)**: Dùng để duyệt qua các **giá trị (value)** của một Iterable object (Array, String, Map, Set).
4.  **`for...in`**: Dùng để duyệt qua các **khóa (key/property)** của một Object.

*Từ khóa điều khiển:* 
*   `break`: Thoát hẳn ra khỏi vòng lặp ngay lập tức.
*   `continue`: Bỏ qua lần lặp hiện tại, lập tức nhảy sang lần lặp tiếp theo.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Tuyệt đối KHÔNG dùng `for...in` để duyệt Mảng (Array):** Vì `for...in` duyệt qua các keys (trong mảng là các index dạng string như "0", "1"), nó không đảm bảo thứ tự duyệt và tệ hơn là nó sẽ duyệt qua cả các thuộc tính được kế thừa từ prototype. Hãy luôn dùng `for...of` cho Mảng.
*   **Ưu tiên Array Methods thay vì `for` truyền thống:** Trong code JavaScript hiện đại (đặc biệt khi làm việc với React/Vue), thay vì dùng vòng lặp `for(let i=0;...)`, hãy ưu tiên dùng các hàm như `forEach`, `map`, `filter`, `reduce`. Chúng tuân thủ nguyên tắc lập trình hàm, giúp code dễ đọc, dễ bảo trì và không cần phải theo dõi biến đếm `i`.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. FOR...OF (Khuyên dùng cho Array/String) ---
const fruits = ["Apple", "Orange", "Plum"];

for (const fruit of fruits) {
  console.log(fruit); // "Apple", "Orange", "Plum"
}

// --- 2. FOR...IN (Khuyên dùng cho Object) ---
const user = { name: "Alice", age: 25, role: "admin" };

for (const key in user) {
  // Bắt buộc dùng bracket notation object[key] khi key là một biến
  console.log(`${key}: ${user[key]}`); 
}

// --- 3. ĐIỀU KHIỂN VÒNG LẶP (Break & Continue) ---
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue; // Bỏ qua số 3
  if (i === 5) break;    // Dừng vòng lặp khi chạm đến số 5
  
  console.log(i);        // Kết quả in ra: 1, 2, 4
}

// --- 4. SỰ KHÁC BIỆT CỐT LÕI (for...of vs for...in) ---
const arr = ["a", "b", "c"];
arr.customProperty = "Lỗi ngầm"; // Cố tình thêm 1 thuộc tính tùy chỉnh vào mảng

console.log("Dùng for...in với Mảng (SAI CÁCH):");
for (const index in arr) {
  // In ra: "0", "1", "2", "customProperty" (Rất nguy hiểm vì duyệt cả thuộc tính thừa)
  console.log(index); 
}

console.log("Dùng for...of với Mảng (ĐÚNG CÁCH):");
for (const item of arr) {
  // In ra: "a", "b", "c" (Chỉ lấy đúng các giá trị của mảng)
  console.log(item);  
}
```
## 07. Functions - Hàm

**📝 Giới thiệu & Lý thuyết cơ bản:**
Hàm (Function) là một trong những khối xây dựng (building blocks) quan trọng nhất của JavaScript. Trong JS, hàm được coi là **First-class citizens (Công dân hạng nhất)**, nghĩa là bạn có thể đối xử với hàm như một biến bình thường: gán hàm vào một biến, truyền hàm làm đối số (Callback) cho một hàm khác, hoặc trả về một hàm từ một hàm khác.

Có 3 cách chính để định nghĩa một hàm:
1.  **Function Declaration (Khai báo hàm):** Bắt đầu bằng từ khóa `function`. Có tính chất **Hoisting** (có thể gọi hàm trước khi khai báo trong file).
2.  **Function Expression (Biểu thức hàm):** Gán một hàm (thường là hàm ẩn danh - anonymous) vào một biến. Không có tính chất Hoisting.
3.  **Arrow Function (Hàm mũi tên - ES6):** Cú pháp cực kỳ ngắn gọn, không có từ khóa `function`. **Quan trọng nhất:** Arrow function không tạo ra ngữ cảnh `this` riêng của nó, mà nó kế thừa `this` từ phạm vi (scope) bọc bên ngoài nó (Lexical scoping).

*Các khái niệm đi kèm:*
*   **Parameters (Tham số):** Là các biến được liệt kê trong ngoặc đơn khi *định nghĩa* hàm (ví dụ `a, b`).
*   **Arguments (Đối số):** Là các giá trị thực tế được truyền vào khi *gọi* hàm (ví dụ `1, 2`).
*   **Callback:** Là một hàm được truyền vào làm *đối số* cho một hàm khác để thực thi sau.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Dùng Arrow Function mặc định cho các Callback:** Khi dùng `map()`, `filter()`, `setTimeout`, hoặc các event listener trong React, hãy luôn dùng Arrow Function để code ngắn gọn và tránh lỗi mất ngữ cảnh của từ khóa `this`.
*   **Tên hàm phải là Động từ:** Vì hàm đại diện cho một hành động, hãy bắt đầu tên hàm bằng các từ như `get...`, `calc...`, `create...`, `check...`, `validate...`.
*   **Nguyên tắc Đơn trách nhiệm (SRP - Single Responsibility Principle):** Đừng viết một hàm khổng lồ dài 200 dòng (ví dụ `processEverything()`). Hãy chia nhỏ nó thành các hàm nhỏ (ví dụ `validateInput()`, `formatData()`, `saveToDatabase()`).
*   **Luôn return giá trị:** Nếu hàm không có từ khóa `return`, nó sẽ ngầm định trả về `undefined`.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. FUNCTION DECLARATION (Được Hoisting) ---
console.log(sum(5, 5)); // Chạy bình thường (Ra 10) dù gọi trước khi khai báo

function sum(a, b) {
  return a + b;
}

// --- 2. FUNCTION EXPRESSION (Không được Hoisting) ---
// console.log(multiply(2, 3)); // LỖI: ReferenceError!

const multiply = function(a, b) {
  return a * b;
};

// --- 3. ARROW FUNCTION & CÁC CÚ PHÁP RÚT GỌN ---
// Nếu chỉ có 1 tham số, có thể bỏ ngoặc đơn ()
const square = x => x * x; 

// Nếu chỉ có 1 dòng return, có thể bỏ ngoặc nhọn {} và chữ return
const add = (a, b) => a + b; 

// NẾU MUỐN RETURN 1 OBJECT NHANH: Phải bọc trong ngoặc đơn ()
const createUser = (name, age) => ({ name: name, age: age });

// --- 4. DEFAULT PARAMETERS & REST PARAMETERS ---
// Default (Gán giá trị mặc định nếu không truyền đối số)
function greet(name = "Guest", time = "Morning") {
  return `Good ${time}, ${name}!`;
}

// Rest (...args) - Gom tất cả đối số truyền vào thành một Mảng (Array)
function calculateTotal(discount, ...prices) {
  // prices lúc này là một mảng: [100, 200, 300]
  const sum = prices.reduce((total, p) => total + p, 0);
  return sum - (sum * discount);
}
console.log(calculateTotal(0.1, 100, 200, 300)); // Tính tổng 3 món, giảm 10%

// --- 5. SỰ KHÁC BIỆT CỰC LỚN VỀ TỪ KHÓA `this` ---
const user = {
  name: "John",
  hobbies: ["Coding", "Reading"],
  
  // Dùng function thông thường cho phương thức của Object
  showHobbies() {
    // Bên trong callback của forEach, nếu dùng function() thường, 
    // `this` sẽ bị rơi vào Global/Window (ra undefined).
    // Giải pháp là dùng ARROW FUNCTION vì nó lấy `this` của hàm showHobbies() bên ngoài.
    this.hobbies.forEach((hobby) => {
      console.log(`${this.name} likes ${hobby}`);
    });
  }
};
user.showHobbies();

// --- 6. CALLBACK FUNCTION ---
// Hàm processData nhận hàm `logResult` làm tham số (callback)
function processData(data, callback) {
  const processed = data.toUpperCase();
  callback(processed); // Gọi hàm callback sau khi xử lý xong
}

function logResult(result) {
  console.log("Kết quả là:", result);
}

// Truyền hàm logResult (KHÔNG CÓ CẶP NGOẶC () ở đuôi)
processData("hello world", logResult);
```
## 08. Scope & Closure - Phạm vi & Bao đóng

**📝 Giới thiệu & Lý thuyết cơ bản:**

**1. Scope (Phạm vi hoạt động của biến):**
Quyết định xem một biến (hoặc hàm) có thể được truy cập từ những đâu trong mã nguồn. JavaScript có 3 loại Scope chính:
*   **Global Scope (Phạm vi toàn cục):** Biến khai báo ngoài cùng, không nằm trong bất kỳ hàm hay khối `{}` nào. Có thể truy cập từ mọi nơi.
*   **Function Scope (Phạm vi hàm):** Biến khai báo bên trong một hàm (bằng `var`, `let`, `const`) chỉ có thể được sử dụng bên trong hàm đó.
*   **Block Scope (Phạm vi khối - Từ ES6):** Khối là những gì nằm trong cặp ngoặc nhọn `{}` (ví dụ: `if`, `for`). Các biến khai báo bằng `let` và `const` bị giới hạn trong khối này, trong khi `var` thì không (đây là lý do ta hạn chế dùng `var`).

*Lưu ý:* JavaScript sử dụng **Lexical Scope (Phạm vi từ vựng)**, nghĩa là phạm vi của một biến được quyết định bởi **vị trí bạn viết code** lúc ban đầu, chứ không phải vị trí lúc hàm được gọi.

**2. Closure (Bao đóng):**
Closure là một hiện tượng kỳ diệu trong JavaScript. Nó xảy ra khi **một hàm con "ghi nhớ" và tiếp tục truy cập được các biến của hàm cha (outer function)**, ngay cả khi hàm cha đã thực thi xong và bị xóa khỏi bộ nhớ (Call Stack).
Bản chất: Hàm con luôn mang theo một "chiếc balo" (Lexical Environment) chứa tất cả các biến xung quanh nơi nó được sinh ra.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Tạo Private Data (Dữ liệu riêng tư):** Trong JS, trước khi có private class fields (`#`), người ta dùng Closure để che giấu biến, không cho phép bên ngoài can thiệp trực tiếp mà phải thông qua các hàm getter/setter.
*   **Hàm Factory / Currying:** Tạo ra các hàm động dựa trên cấu hình ban đầu (ví dụ: tạo hàm tính thuế với các mức thuế suất khác nhau).
*   **Ghi nhớ trạng thái (State retention):** Rất hay dùng trong React (như hook `useState`), hoặc trong các kỹ thuật Debounce/Throttle, event listeners để đếm số lần click.
*   *Lưu ý:* Tránh lạm dụng Closure chứa các object quá lớn nếu không cần thiết vì có thể gây rò rỉ bộ nhớ (Memory Leak), do bộ thu gom rác (Garbage Collector) không thể xóa các biến vẫn đang được Closure tham chiếu tới.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. MINH HỌA SCOPE (Phạm vi) ---
const globalVar = "Tôi ở toàn cục";

function checkScope() {
  const functionVar = "Tôi ở trong hàm";
  
  if (true) {
    let blockVar = "Tôi ở trong khối if";
    var fakeBlockVar = "Tôi dùng var, tôi sẽ thoát ra ngoài khối if";
    
    console.log(blockVar); // Chạy bình thường
  }
  
  // console.log(blockVar); // LỖI: ReferenceError (Block scope)
  console.log(fakeBlockVar); // In ra được! (Vì var chỉ bị chặn bởi Function, không bị chặn bởi Block)
}

// --- 2. CLOSURE CƠ BẢN (Ghi nhớ trạng thái) ---
function createCounter() {
  let count = 0; // Biến này nằm trong hàm cha
  
  // Hàm con (Closure) được trả về
  return function() {
    count++; // Hàm con vẫn truy cập và thay đổi được biến count
    return count;
  };
}

const counter1 = createCounter(); // Hàm createCounter chạy xong và kết thúc
console.log(counter1()); // 1 (Biến count vẫn sống trong Closure)
console.log(counter1()); // 2
console.log(counter1()); // 3

// --- 3. ỨNG DỤNG CLOSURE: DATA ENCAPSULATION (Bảo mật dữ liệu) ---
function createBankAccount(initialBalance) {
  let balance = initialBalance; // Biến private, bên ngoài không thể chạm tới
  
  return {
    deposit(amount) {
      balance += amount;
      console.log(`Đã nạp ${amount}. Số dư: ${balance}`);
    },
    withdraw(amount) {
      if (amount > balance) {
        console.log("Số dư không đủ!");
        return;
      }
      balance -= amount;
      console.log(`Đã rút ${amount}. Số dư: ${balance}`);
    },
    getBalance() {
      return balance;
    }
  };
}

const myWallet = createBankAccount(100);
myWallet.deposit(50); // Đã nạp 50. Số dư: 150
console.log(myWallet.balance); // undefined (Bảo mật tuyệt đối, không thể đọc trực tiếp)

// --- 4. CÂU HỎI PHỎNG VẤN KINH ĐIỂN VỀ CLOSURE & SCOPE ---
// Đề bài: In ra 0, 1, 2 sau mỗi giây
// CÁCH SAI (Dùng var):
for (var i = 0; i < 3; i++) {
  setTimeout(() => {
    // In ra toàn số 3, vì var không có block scope, biến i bị đè lên nhau
    console.log("Var:", i); 
  }, 1000);
}

// CÁCH ĐÚNG (Dùng let):
for (let j = 0; j < 3; j++) {
  setTimeout(() => {
    // In ra 0, 1, 2 vì let có block scope. Ở mỗi vòng lặp, Closure "nhớ" một biến j riêng biệt.
    console.log("Let:", j); 
  }, 1000);
}
```
## 09. Objects - Đối tượng

**📝 Giới thiệu & Lý thuyết cơ bản:**
Trong JavaScript, Object (Đối tượng) là một cấu trúc dữ liệu phức hợp dùng để lưu trữ các tập hợp dữ liệu dưới dạng cặp **Key - Value (Khóa - Giá trị)**. 
*   **Key (Khóa):** Còn được gọi là thuộc tính (property name), luôn luôn là kiểu `String` hoặc `Symbol`. Kể cả khi bạn gán key là một số, JS cũng sẽ ngầm định chuyển nó thành chuỗi.
*   **Value (Giá trị):** Có thể là bất kỳ kiểu dữ liệu nào (String, Number, Array, hoặc thậm chí là một Object khác). Nếu value là một hàm (function), ta gọi nó là **Method (Phương thức)** của đối tượng đó.

Khác với các ngôn ngữ lập trình hướng đối tượng truyền thống (như Java, C#) yêu cầu phải có Class mới tạo được Object, trong JavaScript, bạn có thể tạo Object trực tiếp (Object Literal) bằng cặp ngoặc nhọn `{}` bất cứ lúc nào.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Dot Notation vs Bracket Notation:** Dùng dấu chấm (`object.key`) khi bạn biết chính xác tên thuộc tính. Dùng dấu ngoặc vuông (`object["key"]`) khi tên thuộc tính được lưu trong một biến động, hoặc khi tên thuộc tính chứa ký tự đặc biệt (ví dụ có khoảng trắng hoặc dấu gạch ngang).
*   **Property Value Shorthand (Cú pháp viết tắt):** Khi tên biến và tên key giống hệt nhau, bạn có thể viết gộp lại để code gọn hơn.
*   **Không dùng Arrow Function cho Method:** Khi viết một phương thức bên trong Object và muốn sử dụng từ khóa `this` để trỏ tới chính Object đó, hãy dùng hàm thông thường (`sayHi() { ... }`). Arrow function sẽ làm mất ngữ cảnh `this` và trỏ nhầm ra Window/Global.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. KHỞI TẠO VÀ TRUY CẬP CƠ BẢN ---
const user = {
  name: "John Doe",
  age: 30,
  "is verified": true // Key có chứa khoảng trắng bắt buộc phải bọc trong nháy
};

console.log(user.name); // "John Doe" (Dot notation - Thường dùng)
console.log(user["is verified"]); // true (Bracket notation - Bắt buộc trong trường hợp này)

// --- 2. THÊM, SỬA, XÓA THUỘC TÍNH ---
user.email = "john@gmail.com"; // Thêm mới
user.age = 31;                 // Cập nhật
delete user["is verified"];    // Xóa thuộc tính

// --- 3. CÚ PHÁP HIỆN ĐẠI (ES6+) ---
const role = "admin";
const dynamicKey = "department";

const employee = {
  // Property Shorthand (Tương đương role: role)
  role, 
  
  // Computed Property (Tên key được tính toán động từ biến)
  [dynamicKey]: "IT", 
  
  // Method Shorthand (Rút gọn chữ function)
  getProfile() {
    // `this` trỏ tới đối tượng employee
    return `${this.role} làm việc tại phòng ${this.department}`; 
  },

  // ❌ LỖI THƯỜNG GẶP: Dùng Arrow Function cho Method
  badMethod: () => {
    // `this` lúc này trỏ ra ngoài (Global/Window) thay vì employee
    console.log(this.role); // undefined
  }
};

console.log(employee.getProfile()); // "admin làm việc tại phòng IT"

// --- 4. CÁC HÀM TIỆN ÍCH CỦA OBJECT (Static Methods) ---
const settings = { theme: "dark", notifications: true, volume: 80 };

// Lấy ra mảng các Keys
console.log(Object.keys(settings)); 
// ["theme", "notifications", "volume"]

// Lấy ra mảng các Values
console.log(Object.values(settings)); 
// ["dark", true, 80]

// Lấy ra mảng chứa các cặp [Key, Value] (Rất hữu ích để duyệt bằng for...of)
for (const [key, value] of Object.entries(settings)) {
  console.log(`Cấu hình ${key} có giá trị là ${value}`);
}
```
## 10. References & Copying - Tham chiếu & Sao chép

**📝 Giới thiệu & Lý thuyết cơ bản:**
Trong JavaScript, cách dữ liệu được lưu trữ và sao chép phụ thuộc hoàn toàn vào kiểu dữ liệu của nó:
1.  **Primitive (Kiểu nguyên thủy - Truyền theo Giá trị):** Các kiểu như `String`, `Number`, `Boolean` khi được gán sang một biến khác, JavaScript sẽ tạo ra một bản sao độc lập hoàn toàn về mặt giá trị. Sửa biến này không ảnh hưởng đến biến kia.
2.  **Reference (Kiểu tham chiếu - Truyền theo Địa chỉ):** `Object`, `Array`, `Function` không lưu trực tiếp giá trị vào biến, mà lưu **địa chỉ ô nhớ** trỏ đến nơi chứa dữ liệu đó. Khi bạn gán `objectA = objectB`, bạn chỉ đang copy cái "địa chỉ" chứ không tạo ra một object mới. Cả hai biến lúc này cùng trỏ chung vào một dữ liệu, sửa một cái là cái kia cũng bị đổi theo.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Không bao giờ dùng dấu `=` để copy Object/Array:** Nếu bạn muốn tạo một bản sao để chỉnh sửa mà không làm hỏng dữ liệu gốc, tuyệt đối không gán trực tiếp.
*   **Shallow Copy (Sao chép nông):** Sử dụng Spread Operator (`...`) hoặc `Object.assign()`. Cách này rất nhanh gọn nhưng chỉ copy được lớp ngoài cùng. Nếu bên trong Object có chứa các Object/Array lồng nhau (nested), các phần tử lồng bên trong vẫn bị dính tham chiếu.
*   **Deep Copy (Sao chép sâu):** Để clone an toàn 100% mọi lớp lồng nhau, hãy sử dụng hàm Native chuẩn của JavaScript hiện đại là `structuredClone()`. (Lưu ý: Cách cũ `JSON.parse(JSON.stringify())` sẽ làm mất các kiểu dữ liệu đặc biệt như `undefined`, `Date`, `Map`, `Set`).
*   **So sánh Object:** Hai Object dù trông giống hệt nhau nhưng sẽ luôn trả về `false` khi so sánh (`===`) vì chúng nằm ở 2 ô nhớ khác nhau. Chúng chỉ bằng nhau khi cùng tham chiếu đến 1 ô nhớ.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```javascript
// --- 1. PRIMITIVE (Copy theo giá trị - An toàn) ---
let a = 10;
let b = a;  // b nhận giá trị 10
b = 20;     // Sửa b không ảnh hưởng tới a
console.log(a); // 10

// --- 2. REFERENCE (Copy theo tham chiếu - Nguy hiểm) ---
const user1 = { name: "John" };
const user2 = user1; // user2 và user1 cùng trỏ về 1 vùng nhớ

user2.name = "Pete"; // Sửa user2
console.log(user1.name); // "Pete" (user1 cũng bị thay đổi theo!)

// --- 3. SO SÁNH OBJECT ---
console.log({} === {}); // false (Hai vùng nhớ độc lập)
console.log(user1 === user2); // true (Cùng trỏ về một vùng nhớ)

// --- 4. SỰ THẬT VỀ TỪ KHÓA `const` VỚI OBJECT ---
const admin = { role: "admin" };
// admin = {}; // ❌ LỖI: const cấm gán lại (re-assign) một địa chỉ vùng nhớ khác
admin.role = "super_admin"; // ✅ HỢP LỆ: const không cấm việc sửa đổi nội dung bên trong vùng nhớ đó

// --- 5. SHALLOW COPY (Sao chép nông bằng Spread ...) ---
const original = { 
  name: "Alice", 
  address: { city: "Hanoi" } // Nested object (Object lồng bên trong)
};

const shallowCopy = { ...original };
shallowCopy.name = "Bob"; // Đổi lớp ngoài cùng -> An toàn
shallowCopy.address.city = "Danang"; // Đổi lớp lồng bên trong -> Dính lỗi tham chiếu!

console.log(original.name); // "Alice" (Không bị ảnh hưởng)
console.log(original.address.city); // "Danang" (BỊ ẢNH HƯỞNG BỞI BẢN COPY!)

// --- 6. DEEP COPY (Sao chép sâu tuyệt đối) ---
const deepOriginal = { 
  name: "Alice", 
  address: { city: "Hanoi" },
  hobbies: new Set(["reading"])
};

// Sử dụng API hiện đại của trình duyệt/Node.js
const deepCopy = structuredClone(deepOriginal);

deepCopy.address.city = "HCM";
console.log(deepOriginal.address.city); // "Hanoi" (An toàn 100%, bản gốc không bị đổi)
```
## 11: Thao tác Dữ liệu Thông minh (Data Manipulation)

**📝 Giới thiệu & Lý thuyết cơ bản:**
Trong JavaScript hiện đại, việc xử lý dữ liệu (đặc biệt là Object và Array) đã chuyển dịch từ tư duy thủ tục (dùng vòng lặp `for`, thay đổi dữ liệu trực tiếp) sang tư duy **Lập trình hàm (Functional Programming)**. Cốt lõi của chủ đề này bao gồm:
1.  **Destructuring, Spread & Rest:** Bộ ba cú pháp "ma thuật" giúp bóc tách, sao chép và gộp dữ liệu cực kỳ ngắn gọn mà không cần khởi tạo nhiều biến trung gian.
2.  **Tính bất biến (Immutability) - Mutating vs Non-mutating:** 
    *   *Mutating:* Các hàm làm thay đổi trực tiếp cấu trúc dữ liệu gốc (như `push`, `splice`, `sort`). Rất dễ gây ra lỗi ngầm (side-effects).
    *   *Non-mutating:* Các hàm luôn trả về một dữ liệu mới tinh, giữ nguyên bản gốc (như `map`, `filter`, `slice`). Đây là tiêu chuẩn bắt buộc khi làm việc với các framework như React.
3.  **Cấu trúc dữ liệu hiện đại (Map & Set):** Bổ sung sức mạnh cho Object và Array truyền thống trong các bài toán đặc thù (lọc trùng lặp, dùng Object làm key).

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Luôn Destructuring sớm:** Ngay khi nhận được tham số là Object (ví dụ `props` trong React hoặc dữ liệu từ API), hãy bóc tách nó ngay ở phần khai báo hàm để code ngắn hơn.
*   **Pipeline xử lý dữ liệu (Chaining):** Kết hợp liên hoàn các Array/String Methods. Ví dụ: Lọc danh sách (`filter`) $\rightarrow$ Biến đổi dữ liệu (`map`) $\rightarrow$ Tính toán tổng (`reduce`) trên cùng một chuỗi lệnh.
*   **Tránh xa `sort()` và `reverse()` trực tiếp:** Vì chúng là Mutating. Hãy luôn dùng Spread (`[...arr].sort()`) hoặc các hàm mới (`toSorted()`, `toReversed()`) để tạo mảng mới trước khi sắp xếp.
*   **Dùng Set để lọc trùng:** Thay vì viết vòng lặp kiểm tra phức tạp, chỉ cần bọc mảng vào `new Set()` là bạn đã có một danh sách duy nhất siêu tốc.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```javascript
// ==========================================
// 1. DESTRUCTURING & SPREAD/REST VỚI OBJECT
// ==========================================
const rawUser = { id: 101, name: "Alice", role: "admin", status: "active" };

// Destructuring & Rest: Lấy name và role, gom phần còn lại vào biến `others`
const { name, role, ...others } = rawUser; 
console.log(name);   // "Alice"
console.log(others); // { id: 101, status: "active" }

// Spread: Tạo một user mới, copy toàn bộ từ rawUser nhưng ghi đè/thêm thuộc tính
const updatedUser = { 
  ...rawUser, 
  status: "inactive", 
  lastLogin: "2024-01-01" 
};


// ==========================================
// 2. TƯ DUY NON-MUTATING & ARRAY METHODS
// ==========================================
const cart = [
  { item: "Laptop", price: 1500, qty: 1 },
  { item: "Mouse", price: 50, qty: 2 },
  { item: "Keyboard", price: 100, qty: 1 }
];

// ❌ CÁCH CŨ (Mutating & Imperative - KHUYÊN BỎ)
// let total = 0;
// for (let i = 0; i < cart.length; i++) {
//   if (cart[i].price > 50) {
//     total += cart[i].price * cart[i].qty;
//   }
// }

// ✅ CÁCH MỚI (Non-mutating & Declarative - CHUẨN HIỆN ĐẠI)
const expensiveTotal = cart
  .filter(product => product.price > 50) // Bước 1: Lọc sp giá > 50 (Laptop, Keyboard)
  .map(product => product.price * product.qty) // Bước 2: Chuyển thành mảng tiền [1500, 100]
  .reduce((sum, currentVal) => sum + currentVal, 0); // Bước 3: Tính tổng = 1600

console.log(`Tổng tiền hàng cao cấp: $${expensiveTotal}`);

// Xử lý sắp xếp an toàn (Không làm thay đổi mảng cart gốc)
const sortedByPrice = [...cart].sort((a, b) => b.price - a.price); // Giảm dần


// ==========================================
// 3. XỬ LÝ CHUỖI LIÊN HOÀN (STRING METHODS)
// ==========================================
const searchKeyword = "   macbook PRO  ";

// Chuẩn hóa: Cắt khoảng trắng 2 đầu -> Chữ thường -> Tách thành mảng
const normalizedKeywords = searchKeyword.trim().toLowerCase().split(" ");
console.log(normalizedKeywords); // ["macbook", "pro"]


// ==========================================
// 4. SỨC MẠNH CỦA SET & MAP
// ==========================================
// Lọc phần tử trùng lặp trong Array chỉ bằng 1 dòng code
const duplicateCategories = ["Tech", "Fashion", "Tech", "Food", "Fashion"];
const uniqueCategories = [...new Set(duplicateCategories)];
console.log(uniqueCategories); // ["Tech", "Fashion", "Food"]

// Dùng Map để lưu trữ dữ liệu với Key là một Object (Điều mà Object thường không làm được)
const userNode = { htmlId: "user-123" };
const nodeData = new Map();

nodeData.set(userNode, { clicks: 5, timeOnPage: "2m" });
console.log(nodeData.get(userNode).clicks); // 5
```
## 12: Kiểm soát Luồng Bất đồng bộ & Xử lý Lỗi (Async & Error Handling)

**📝 Giới thiệu & Lý thuyết cơ bản:**
JavaScript là ngôn ngữ đơn luồng (Single-threaded). Nghĩa là tại một thời điểm, nó chỉ làm được một việc. Tuy nhiên, nhờ cơ chế **Event Loop** và **Web APIs**, nó có thể đẩy các tác vụ tốn thời gian (như lấy dữ liệu từ máy chủ, đọc file, hẹn giờ) ra chạy ngầm.

Sự tiến hóa của xử lý bất đồng bộ trong JS:
1.  **Callback (Liên kết Mục 07 - Hàm):** Truyền một hàm vào một hàm khác để chạy sau. Dễ dẫn đến "Callback Hell" (các khối code lồng nhau hình chữ V, vi phạm Scope và rất khó debug).
2.  **Promise (ES6):** Một Object (Liên kết Mục 09) đại diện cho một tác vụ chưa hoàn thành. Nó có 3 trạng thái: `Pending` (Đang chờ), `Fulfilled` (Thành công) hoặc `Rejected` (Thất bại).
3.  **Async/Await (ES8):** Cú pháp "đường hóa" (syntax sugar) xây dựng trên nền Promise. Giúp code bất đồng bộ trông giống hệt code đồng bộ tuần tự, dễ dàng áp dụng các khối điều kiện (Liên kết Mục 05 - Conditionals).
4.  **Try...Catch (Mục 16):** Khối lệnh để "bắt" các lỗi runtime (ví dụ: mất mạng, sai kiểu dữ liệu), ngăn không cho ứng dụng bị crash.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Kết hợp Early Return (Mục 05):** Khi gọi API, luôn kiểm tra lỗi trước và `return` sớm. Đừng lồng `if...else` quá sâu trong `try...catch`.
*   **Bảo toàn Kiểu dữ liệu (Mục 02 & 03):** Dữ liệu fetch từ API về thường là định dạng JSON (bản chất là String). Bạn phải dùng `.json()` để ép kiểu (Type Conversion) nó thành Object hoặc Array để có thể chấm tới các thuộc tính.
*   **Optional Chaining & Nullish Coalescing (Mục 04):** Dữ liệu từ API luôn tiềm ẩn rủi ro trả về `null` hoặc thiếu field. Luôn dùng `?.` và `??` khi bóc tách dữ liệu để tránh lỗi "Cannot read properties of undefined".
*   **Tránh lỗi Tham chiếu (Mục 10):** Dữ liệu từ API là Object/Array. Nếu bạn lưu nó vào một biến Global (Mục 08 - Scope) và thay đổi trực tiếp, bạn đang làm hỏng dữ liệu gốc (Mutating). 

**💻 Cách dùng & Code minh họa chuyên sâu:**

```javascript
// ==========================================
// 1. TỪ CALLBACK ĐẾN PROMISE (Hiểu bản chất)
// ==========================================
// Trả về một Promise Object. Bên trong chứa Callback functions (resolve, reject)
const checkInventory = (itemCode) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      // Dùng Toán tử so sánh nghiêm ngặt (Mục 04)
      if (itemCode === "LAPTOP") {
        resolve({ id: 1, name: "Macbook", stock: 10 }); // Thành công trả về Object
      } else {
        reject(new Error("Không tìm thấy sản phẩm trong kho!")); // Thất bại trả về Error
      }
    }, 1000);
  });
};

// ==========================================
// 2. ASYNC/AWAIT & TRY...CATCH (Kết hợp 10 mục nền tảng)
// ==========================================
// Khai báo hàm bất đồng bộ (Liên kết Mục 07)
async function fetchAndProcessProduct(productId) {
  // Biến local block-scope (Liên kết Mục 01 & 08)
  let productData = null; 
  
  try {
    console.log("Đang kết nối Server...");
    
    // Await buộc JS tạm dừng hàm này để chờ kết quả (Trả về Object)
    productData = await checkInventory(productId); 
    
    // --- ÁP DỤNG KIẾN THỨC MỤC 01-10 VÀO DỮ LIỆU ---
    
    // 1. Dùng Destructuring (Mục 11) & Đặt default parameter (Mục 07)
    const { name, stock, price = 0 } = productData;
    
    // 2. Ép kiểu tường minh (Mục 03) để đảm bảo tính toán đúng
    const validStock = Number(stock);
    
    // 3. Early Return (Mục 05) nếu hết hàng
    if (validStock <= 0) {
      return "Sản phẩm đã hết hàng."; 
    }
    
    // 4. Toán tử hiện đại (Mục 04) - Lấy mô tả, nếu undefined thì dùng chuỗi mặc định
    const desc = productData?.details?.description ?? "Chưa có mô tả";
    
    return `Đặt mua thành công ${name}. Tồn kho còn: ${validStock - 1}. Mô tả: ${desc}`;
    
  } catch (error) {
    // Bắt lỗi: Nếu promise gọi reject() hoặc có lỗi logic
    console.error("🚨 [LỖI HỆ THỐNG]:", error.message);
    
    // Luôn return một giá trị fallback để UI không bị treo
    return "Giao dịch thất bại. Vui lòng thử lại!";
    
  } finally {
    // Luôn chạy ở cuối cùng, thường dùng để ẩn màn hình Loading (Trạng thái UI)
    console.log("Đã đóng kết nối API.");
  }
}

// Gọi hàm và xử lý kết quả (Vì hàm async luôn trả về một Promise ẩn)
fetchAndProcessProduct("LAPTOP").then(result => console.log(result));
// fetchAndProcessProduct("IPHONE").then(result => console.log(result)); // Sẽ trigger khối catch
```
## 13: Kiến trúc Hệ thống & Tương tác Trình duyệt (Architecture & DOM)

**📝 Giới thiệu & Lý thuyết cơ bản:**
Khi JavaScript chạy trên trình duyệt, nó không chỉ tính toán dữ liệu mà còn tương tác trực tiếp với giao diện HTML thông qua **DOM (Document Object Model)**. Trình duyệt biến toàn bộ trang HTML thành một Cây Đối Tượng (Liên kết Mục 09). Nghĩa là, mọi thẻ `<div>`, `<button>` hay `<input>` đều là một Object có chứa các thuộc tính (properties) và phương thức (methods).

Để quản lý một ứng dụng lớn tương tác với DOM, chúng ta cần tư duy kiến trúc:
1.  **Modules (ES Modules):** Kỹ thuật chia nhỏ mã nguồn thành nhiều file (ví dụ: `api.js`, `ui.js`, `main.js`). Điều này giúp giải quyết triệt để vấn đề "ô nhiễm Global Scope" (Liên kết Mục 08 - Scope), vì mỗi module có một phạm vi (scope) hoàn toàn độc lập.
2.  **Classes & Prototype:** Cách tiếp cận Hướng đối tượng (OOP). Class thực chất là một "bản thiết kế" (blueprint) để tạo ra nhiều Object (Mục 09) có cấu trúc giống nhau, giúp đóng gói dữ liệu và các hàm (Mục 07) xử lý dữ liệu đó vào chung một nơi.
3.  **Event Bubbling & Delegation:** Sự kiện (Event) trong DOM có tính chất "nổi bọt" (Bubbling) từ thẻ con lên thẻ cha. Lợi dụng điều này, thay vì gắn sự kiện cho 100 nút bấm nhỏ, ta chỉ cần gắn 1 sự kiện duy nhất cho thẻ cha chứa chúng (Event Delegation).

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Tách biệt logic (Separation of Concerns):** Đừng viết code tính toán logic (Business Logic) chung với code đổi màu thẻ HTML (UI Logic). Hãy tách chúng ra các module riêng biệt.
*   **Bảo vệ dữ liệu gốc (Liên kết Mục 10):** Khi lấy dữ liệu từ Class hoặc API để in ra DOM, hãy tạo ra các DOM Element dựa trên một bản sao của dữ liệu, đừng để người dùng sửa giao diện làm biến đổi luôn cấu trúc dữ liệu ngầm.
*   **Luôn dùng `event.preventDefault()` đối với Form:** Trình duyệt mặc định sẽ tải lại trang (reload) khi submit Form, điều này làm mất toàn bộ trạng thái (State) và các biến JS hiện tại.
*   **Lắng nghe sự kiện bằng Arrow Function (Liên kết Mục 07):** Giúp tránh lỗi lạc mất ngữ cảnh `this` khi truyền callback vào `addEventListener`.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```javascript
// ==========================================
// 1. MODULES (Quản lý Scope và Tái sử dụng)
// ==========================================
// File: utils/math.js (Module độc lập)
// Hàm này không lọt ra Global Scope, chỉ file nào import mới dùng được
export const calculateTax = (price, taxRate = 0.1) => price + (price * taxRate);


// ==========================================
// 2. CLASSES & OOP (Bản thiết kế Object)
// ==========================================
class UserProfile {
  // Hàm khởi tạo chạy ngay khi dùng từ khóa 'new'
  constructor(name, role) {
    this.name = name;
    this.role = role; 
  }

  // Method (Liên kết Mục 07 & 09)
  getBadge() {
    // Toán tử 3 ngôi (Mục 05)
    return this.role === "admin" ? "⭐ Admin" : "👤 Member";
  }
}

// Tạo ra một Object mới từ Class
const currentUser = new UserProfile("Alice", "admin");


// ==========================================
// 3. DOM & EVENT DELEGATION (Thực chiến giao diện)
// ==========================================
/* GIẢ ĐỊNH HTML:
  <form id="user-form">
    <input type="text" id="username" placeholder="Nhập tên" />
    <button type="submit">Thêm</button>
  </form>
  <ul id="user-list">
    <!-- Các item sẽ được JS thêm vào đây -->
  </ul>
*/

// Tìm các DOM Elements (Bản chất chúng là các Object)
const formEl = document.querySelector("#user-form");
const inputEl = document.querySelector("#username");
const listEl = document.querySelector("#user-list");

// --- XỬ LÝ SỰ KIỆN FORM SUBMIT ---
// Truyền Callback Arrow Function (Mục 07)
formEl.addEventListener("submit", (event) => {
  // 1. Chặn reload trang mặc định (Cực kỳ quan trọng)
  event.preventDefault(); 
  
  // 2. Lấy giá trị chuỗi (String - Mục 02) và chuẩn hóa (Mục 14)
  const inputValue = inputEl.value.trim();
  
  // 3. Early Return (Mục 05) nếu chuỗi rỗng (Falsy - Mục 03)
  if (!inputValue) {
    alert("Vui lòng không để trống!");
    return; 
  }

  // 4. Khởi tạo một thực thể Class mới
  const newUser = new UserProfile(inputValue, "user");
  
  // 5. Thao tác DOM: Tạo thẻ <li> mới
  const li = document.createElement("li");
  li.className = "user-item";
  // Template Literal (Mục 02)
  li.innerHTML = `
    <span>${newUser.name} - ${newUser.getBadge()}</span>
    <button class="btn-delete">Xóa</button>
  `;
  
  listEl.appendChild(li); // Thêm vào danh sách UI
  inputEl.value = "";     // Reset input
});

// --- EVENT DELEGATION (Ủy quyền sự kiện) ---
// Thay vì gắn sự kiện cho từng nút Xóa, ta gắn vào thẻ cha <ul>
listEl.addEventListener("click", (event) => {
  const clickedTarget = event.target; // Element thực tế bị click
  
  // Dùng Optional Chaining (Mục 04) kiểm tra an toàn
  if (clickedTarget?.classList?.contains("btn-delete")) {
    
    // Tìm thẻ <li> cha gần nhất chứa nút Xóa này
    const itemToRemove = clickedTarget.closest(".user-item");
    
    if (itemToRemove) {
      itemToRemove.remove(); // Xóa khỏi DOM
      console.log("Đã xóa phần tử thành công!");
    }
  }
});
```
## 14: Quy chuẩn, Bẫy Lập trình & Tư duy Giải quyết vấn đề (Conventions & Mindset)

**📝 Giới thiệu & Lý thuyết cơ bản:**
Viết code chạy được là một chuyện, nhưng viết code để đồng nghiệp đọc hiểu, dễ bảo trì và không chứa lỗi ngầm lại là chuyện khác. Chủ đề này tập trung vào cách định hình phong cách viết code chuyên nghiệp và né tránh các "cú lừa" kinh điển của JavaScript.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Quy tắc đặt tên (Naming Conventions):**
    *   Biến & Hàm: Dùng `camelCase` (vd: `userData`, `fetchProducts()`). Tên hàm phải là động từ.
    *   Biến logic (Boolean): Phải có tiền tố trạng thái `is`, `has`, `should`, `can` (vd: `isLoading`, `hasError`).
    *   Lớp (Class): Dùng `PascalCase` (vd: `UserProfile`, `ShoppingCart`).
    *   Hằng số cấu hình: Dùng `UPPER_SNAKE_CASE` (vd: `MAX_RETRY_COUNT`, `API_BASE_URL`).
*   **Hiểu rõ các khái niệm dễ nhầm (Pitfalls):**
    *   `==` (So sánh lỏng - Tự ép kiểu) **vs** `===` (So sánh chặt - Kiểm tra cả kiểu dữ liệu). *Quy tắc: Luôn dùng `===`*.
    *   `null` (Chủ động gán rỗng) **vs** `undefined` (Biến chưa có giá trị).
    *   `map` (Trả về mảng mới để gán vào biến) **vs** `forEach` (Chỉ lặp để thực hiện side-effect, không trả về gì).
*   **Tư duy giải quyết vấn đề (Problem-Solving Mindset):**
    1.  **Phân tích Input/Output:** Dữ liệu đầu vào là dạng gì (String, Array of Objects)? Đầu ra cần dạng gì?
    2.  **Chia để trị (Divide & Conquer):** Không viết toàn bộ logic vào một hàm. Viết các hàm phụ trợ nhỏ (Helper functions).
    3.  **Bắt Edge Cases:** Luôn tự hỏi: "Nếu mảng rỗng thì sao?", "Nếu API trả về null thì sao?". Bọc code trong `try...catch` và dùng Early Return.

**💻 Code minh họa chuyên sâu (Tổng hợp):**

```javascript
// ==========================================
// 1. CODING CONVENTIONS VÀ CÁC "BẪY" KINH ĐIỂN
// ==========================================
const MAX_ITEMS = 10; // Chuẩn: Cấu hình cố định

// ❌ Cách viết TỒI (Khó hiểu, dễ dính bẫy Mutating và Ép kiểu)
function calc(arr, check) {
  let res = [];
  if (check == "1") { // Bẫy == (Tự ép kiểu số 1 thành chuỗi)
    arr.forEach(i => res.push(i * 2)); // Bẫy Mutating res
  }
  return res;
}

// ✅ Cách viết CHUẨN (Tên rõ ràng, Non-mutating, So sánh chặt)
function getDoubledPrices(prices, isActive) {
  if (isActive === false) return []; // Early return & So sánh ===
  
  // Dùng map thay cho forEach + push
  return prices.map(price => price * 2); 
}


// ==========================================
// 2. TƯ DUY GIẢI QUYẾT VẤN ĐỀ THỰC TẾ
// ==========================================
/* YÊU CẦU: Từ danh sách user lộn xộn, tìm email của các user đang active 
   và trên 18 tuổi, trả về chữ thường. Nếu không có dữ liệu, trả về mảng rỗng. */

const rawUsers = [
  { name: "John", age: 20, status: "active", email: " JOHN@gmail.com " },
  { name: "Alice", age: 17, status: "active", email: "alice@gmail.com" },
  null, 
  { name: "Bob", age: 25, status: "inactive", email: "bob@gmail.com" }
];

// Giải quyết bằng Functional Programming Pipeline
const getActiveAdultEmails = (usersList) => {
  // 1. Edge Case: Nếu input không hợp lệ -> Trả về []
  if (!Array.isArray(usersList) || usersList.length === 0) return [];

  return usersList
    .filter(user => user !== null) // Loại bỏ dữ liệu rác
    .filter(user => user.status === "active" && user.age >= 18) // Lọc điều kiện
    .map(user => user.email.trim().toLowerCase()); // Biến đổi & Chuẩn hóa
};

console.log(getActiveAdultEmails(rawUsers)); // ["john@gmail.com"]
