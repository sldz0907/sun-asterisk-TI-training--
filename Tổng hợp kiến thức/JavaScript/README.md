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
