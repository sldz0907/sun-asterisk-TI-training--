## 01. Variables - Biến
**📝 Giới thiệu & Lý thuyết:** 
Biến là một định danh để lưu trữ giá trị trong bộ nhớ. JS hiện đại sử dụng `const` (hằng số, block-scope) và `let` (có thể gán lại, block-scope). `var` là cách cũ (function-scope, bị hoisting).

**🎯 Trường hợp sử dụng:**
*   Dùng `const` mặc định cho 95% trường hợp để code an toàn, khó bị lỗi ghi đè.
*   Dùng `let` khi chắc chắn biến đó sẽ thay đổi (ví dụ: biến đếm trong vòng lặp, trạng thái thay đổi).
<img width="942" height="122" alt="image" src="https://github.com/user-attachments/assets/56ce8162-2044-49dc-9238-eae7311fd317" />
02. Data Types - Kiểu dữ liệu

📝 Giới thiệu & Lý thuyết:

JavaScript là ngôn ngữ có kiểu dữ liệu động (Dynamic Typing). Một biến có thể chứa các kiểu dữ liệu khác nhau trong quá trình thực thi chương trình.

Các kiểu dữ liệu được chia thành 2 nhóm chính:

Primitive (kiểu nguyên thủy): string, number, boolean, null, undefined, bigint, symbol.
Reference (kiểu tham chiếu): object và các cấu trúc dựa trên object như array, function.

🎯 Trường hợp sử dụng:

Dùng null khi bạn chủ động muốn biểu diễn trạng thái "không có giá trị".
Với các biến cần sử dụng trong chương trình, nên khởi tạo giá trị rõ ràng để tránh trạng thái undefined không mong muốn.
