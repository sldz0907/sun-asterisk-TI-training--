## 01. HTML là gì?

**📝 Giới thiệu & Lý thuyết cơ bản:**
HTML (HyperText Markup Language) là ngôn ngữ đánh dấu siêu văn bản. Lưu ý: **HTML không phải là ngôn ngữ lập trình** (nó không có vòng lặp hay câu lệnh điều kiện). Nhiệm vụ duy nhất của nó là xây dựng bộ khung (cấu trúc) cho trang web.
HTML sử dụng các "thẻ" (tags) để bao bọc các thành phần, báo cho trình duyệt biết phần nào là tiêu đề, phần nào là đoạn văn, phần nào là hình ảnh.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Viết thường toàn bộ:** Mặc dù trình duyệt không phân biệt hoa/thường (`<DIV>` vẫn chạy giống `<div>`), nhưng chuẩn mực hiện đại bắt buộc bạn phải viết chữ thường cho tất cả các thẻ để code đồng nhất.
*   **Đóng thẻ cẩn thận:** Một thẻ thường có thẻ mở `<p>` và thẻ đóng `</p>`. Nếu quên đóng thẻ, trình duyệt sẽ tự đoán và có thể làm vỡ toàn bộ giao diện của bạn.
*   **Thẻ tự đóng (Empty Elements):** Một số thẻ không chứa nội dung bên trong thì không cần thẻ đóng, ví dụ như `<img>`, `<br>`, `<input>`. Bạn có thể viết `<img />` cho an toàn và rõ ràng.

**💻 Cách dùng & Code minh họa chuyên sâu:**
```html
<!-- Cú pháp cơ bản của một thẻ HTML -->
<tagname attribute="value">Nội dung nằm ở giữa</tagname>

<!-- Ví dụ thực tế -->
<h1>Chào mừng đến với Website của tôi</h1>
<p>Đây là một đoạn văn bản. Dùng thẻ p để bọc nó lại.</p>

<!-- Thẻ tự đóng (Không có thẻ đóng </img hay </br>) -->
<img src="logo.png" alt="Logo công ty" />
<hr /> <!-- Tạo một đường kẻ ngang -->
```
## 02. Cấu trúc một HTML Document - Cấu trúc tài liệu HTML

**📝 Giới thiệu & Lý thuyết cơ bản:**
Mọi trang web hợp lệ và hoạt động ổn định trên trình duyệt đều bắt buộc phải tuân theo một bộ khung xương tiêu chuẩn. Bộ khung này giúp trình duyệt hiểu cách phân tích cú pháp (parse) và hiển thị nội dung chính xác.

Một tài liệu HTML chuẩn gồm các thành phần cốt lõi sau:
1.  **`<!DOCTYPE html>`:** Không phải là một thẻ HTML, mà là lời khai báo (Declaration) với trình duyệt biết rằng đây là tài liệu sử dụng chuẩn **HTML5** mới nhất, giúp trình duyệt không bị chuyển về chế độ hiển thị cũ (Quirks Mode).
2.  **`<html lang="vi">`:** Thẻ gốc (Root element) bao bọc toàn bộ trang web. Thuộc tính `lang` chỉ định ngôn ngữ chính của trang (ví dụ `vi` là tiếng Việt).
3.  **`<head>` (Phần đầu):** Nơi chứa các siêu dữ liệu (Metadata) **không hiển thị trực tiếp** trên màn hình chính của người dùng. Nó bao gồm tiêu đề trang, liên kết tới file CSS, bảng mã ký tự, và các thẻ tối ưu SEO.
4.  **`<body>` (Phần thân):** Nơi chứa toàn bộ **nội dung hữu hình** mà người dùng sẽ nhìn thấy và tương tác trực tiếp khi truy cập vào trang web (văn bản, hình ảnh, nút bấm, form...).

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Luôn khai báo `lang="..."`:** Việc thiết lập đúng ngôn ngữ (ví dụ `lang="vi"` cho tiếng Việt) là tiêu chuẩn bắt buộc trong Accessibility (a11y) để các công cụ đọc màn hình (Screen Readers) phát âm chính xác, đồng thời giúp các công cụ tìm kiếm như Google hiểu rõ đối tượng mục tiêu của trang web.
*   **Khai báo chuẩn mã hóa `charset="UTF-8"`:** Phải được đặt ngay ở những dòng đầu tiên của thẻ `<head>`. Nếu thiếu, trang web của bạn sẽ gặp lỗi hiển thị ký tự tiếng Việt có dấu (bị lỗi font thành các ký tự lạ).
*   **Bắt buộc có Viewport Meta Tag:** Thẻ `<meta name="viewport" content="width=device-width, initial-scale=1.0">` là chìa khóa để trang web hiển thị co giãn hoàn hảo trên các thiết bị di động (Responsive Web Design).

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <!-- 1. Bảng mã ký tự tiếng Việt -->
    <meta charset="UTF-8" />
    
    <!-- 2. Thiết lập hiển thị Responsive trên thiết bị di động -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    
    <!-- 3. Mô tả ngắn cho SEO (Hiển thị dưới tiêu đề trên Google) -->
    <meta name="description" content="Học lập trình HTML từ cơ bản đến nâng cao cùng cẩm nang chi tiết." />
    
    <!-- 4. Tiêu đề trang xuất hiện trên tab trình duyệt -->
    <title>Trang Web Chuẩn HTML5</title>
  </head>
  
  <body>
    <!-- Mọi giao diện người dùng nhìn thấy đều nằm ở đây -->
    <header>
      <h1>Chào mừng bạn đến với Website!</h1>
    </header>
    
    <main>
      <p>Nội dung cốt lõi của trang web được đặt trong thẻ main.</p>
    </main>

    <footer>
      <p>&copy; 2026 Bản quyền thuộc về tôi.</p>
    </footer>
  </body>
</html>
```
## 03. Text & Typography - Xử lý Văn bản

**📝 Giới thiệu & Lý thuyết cơ bản:**
HTML cung cấp một hệ thống thẻ phong phú để cấu trúc và định dạng văn bản. Việc chọn đúng thẻ không chỉ giúp hiển thị đẹp mắt mà còn báo cho Google (Search Engine) và các trình đọc màn hình (Screen Readers) biết chính xác nội dung đó đóng vai trò gì trong trang web.

Các nhóm thẻ văn bản chính bao gồm:
1.  **Headings (Tiêu đề - `<h1>` đến `<h6>`):** Xác định cấu trúc phân cấp của bài viết. `<h1>` là tiêu đề to nhất, `<h6>` là nhỏ nhất.
2.  **Paragraph (`<p>`):** Dành cho các đoạn văn bản thông thường. Mỗi thẻ `<p>` sẽ tự động tạo khoảng trống (margin) ở trên và dưới.
3.  **Semantic Formatting (Định dạng có ngữ nghĩa):** 
    *   `<strong>`: Nhấn mạnh phần văn bản quan trọng (thường in đậm).
    *   `<em>`: Nhấn mạnh bằng giọng điệu (thường in nghiêng).
    *   *Lưu ý:* Thẻ `<b>` (bold) và `<i>` (italic) cũng làm chữ đậm/nghiêng nhưng không mang ý nghĩa Semantic. Khuyên dùng `<strong>` và `<em>` trong HTML5.
4.  **Citations & Quotes (Trích dẫn):** `<blockquote>` (trích dẫn khối lớn), `<q>` (trích dẫn ngắn trên cùng một dòng), `<cite>` (tên tác phẩm, tác giả).
5.  **Preformatted Text (`<pre>`, `<code>`):** Dùng để hiển thị các đoạn mã nguồn lập trình. Thẻ `<pre>` sẽ giữ nguyên mọi khoảng trắng và dấu xuống dòng của bạn.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Chỉ duy nhất một thẻ `<h1>` trên mỗi trang:** Thẻ `<h1>` là tiêu đề chính của trang. Việc dùng nhiều thẻ `<h1>` sẽ làm rối cấu trúc SEO, khiến Google khó hiểu nội dung chính của trang web là gì.
*   **Không nhảy cóc tiêu đề:** Cấu trúc Heading phải đi tuần tự. Không được dùng `<h3>` ngay sau `<h1>` mà bỏ qua `<h2>`.
*   **Đừng dùng thẻ Heading chỉ để làm to chữ:** Nếu bạn muốn một dòng chữ to ra, hãy dùng thẻ `<p>` và chỉnh kích thước bằng CSS. Chỉ dùng `<h1>` - `<h6>` khi dòng chữ đó thực sự là một "Tiêu đề".
*   **Dùng `<br>` đúng cách:** Chỉ dùng `<br>` (line break) khi bạn bắt buộc phải ngắt dòng trong cùng một đoạn văn (ví dụ: viết một bài thơ, địa chỉ nhà). Không dùng nhiều thẻ `<br>` liên tiếp để tạo khoảng trắng giữa các khối; hãy dùng CSS Margin.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     1. HEADINGS & PARAGRAPHS
=========================================== -->
<h1>Hành trình trở thành Web Developer</h1>
<p>Đây là một đoạn văn bản tóm tắt nội dung của toàn bộ bài viết.</p>

<h2>Giai đoạn 1: Học HTML & CSS</h2>
<p>Trong giai đoạn này, bạn sẽ học cách cấu trúc giao diện.</p>

<!-- ==========================================
     2. SEMANTIC FORMATTING (Định dạng ngữ nghĩa)
=========================================== -->
<p>
  Chương trình học này <strong>bắt buộc</strong> phải hoàn thành đúng hạn. 
  Nếu bạn có câu hỏi, hãy liên hệ <em>ngay lập tức</em>.
</p>

<!-- ==========================================
     3. BLOCKQUOTES & CITATIONS (Trích dẫn)
=========================================== -->
<!-- Trích dẫn một đoạn dài (Thường thụt lề vào so với văn bản thường) -->
<blockquote cite="[https://en.wikipedia.org/wiki/Steve_Jobs](https://en.wikipedia.org/wiki/Steve_Jobs)">
  Stay hungry, stay foolish.
</blockquote>
<p>Câu nói nổi tiếng của <cite>Steve Jobs</cite>.</p>

<!-- ==========================================
     4. KÝ TỰ ĐẶC BIỆT VÀ NGẮT DÒNG
=========================================== -->
<p>
  Địa chỉ công ty:<br />
  Số 1, đường ABC, quận 1<br />
  TP. Hồ Chí Minh
</p>

<!-- Thẻ <hr> tạo ra một đường kẻ ngang phân cách nội dung -->
<hr />

<!-- ==========================================
     5. HIỂN THỊ MÃ NGUỒN (CODE)
=========================================== -->
<!-- Kết hợp <pre> và <code> để code giữ nguyên định dạng -->
<p>Dưới đây là một hàm JavaScript cơ bản:</p>
<pre>
  <code>
    function sayHello() {
      console.log("Hello HTML5!");
    }
  </code>
</pre>
```
## 04. Links & Navigation - Liên kết & Điều hướng

**📝 Giới thiệu & Lý thuyết cơ bản:**
Chữ "H" trong HTML viết tắt cho *HyperText* (Siêu văn bản), và sức mạnh thực sự của trang web nằm ở khả năng liên kết các tài liệu lại với nhau. Để tạo một liên kết, chúng ta sử dụng thẻ **`<a>`** (Anchor tag).

Thẻ `<a>` hoạt động dựa vào thuộc tính quan trọng nhất là **`href`** (Hypertext REFerence - Tham chiếu siêu văn bản), dùng để chỉ định đích đến của liên kết. Đích đến này có thể là:
1.  **Đường dẫn tuyệt đối (Absolute URL):** Dẫn tới một trang web khác hoàn toàn (ví dụ: `https://google.com`).
2.  **Đường dẫn tương đối (Relative URL):** Dẫn tới một trang khác bên trong cùng dự án/website của bạn (ví dụ: `/about.html` hoặc `../contact.html`).
3.  **Điểm neo (Anchor fragment):** Cuộn trang đến một phần tử cụ thể trên cùng một trang bằng cách gọi ID của phần tử đó (ví dụ: `#section-2`).
4.  **Giao thức đặc biệt:** Mở ứng dụng gửi email (`mailto:`) hoặc gọi điện thoại (`tel:`).

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Bảo mật khi mở tab mới:** Khi bạn muốn link mở ở một tab mới, bạn dùng `target="_blank"`. Tuy nhiên, **bắt buộc** phải đi kèm với thuộc tính `rel="noopener noreferrer"` để ngăn chặn trang web đích tấn công (phishing) tab hiện tại của bạn thông qua đối tượng `window.opener`.
*   **Văn bản liên kết (Link Text) có ý nghĩa:** Tuyệt đối tránh đặt tên link là "Bấm vào đây" (Click here). Hãy viết mô tả rõ ràng để tốt cho SEO và người khiếm thị. (Ví dụ chuẩn: "Xem thêm về Chính sách bảo mật").
*   **Semantic Navigation (Điều hướng ngữ nghĩa):** Đừng chỉ vứt các thẻ `<a>` nằm rải rác. Nếu đó là menu điều hướng chính của trang, hãy bọc chúng trong thẻ `<nav>` kết hợp với danh sách `<ul>`, `<li>` để cấu trúc trở nên chuyên nghiệp và chuẩn SEO.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     1. CÁC LOẠI ĐƯỜNG DẪN CƠ BẢN
=========================================== -->
<!-- Đường dẫn tuyệt đối (Absolute Link) - Đi ra ngoài website -->
<a href="[https://www.wikipedia.org](https://www.wikipedia.org)">Đọc thêm trên Wikipedia</a>

<!-- Đường dẫn tương đối (Relative Link) - Chuyển trang nội bộ -->
<a href="/about-us.html">Về chúng tôi</a>
<a href="../images/portfolio.html">Xem hồ sơ năng lực</a>

<!-- ==========================================
     2. THUỘC TÍNH TARGET VÀ BẢO MẬT (RẤT QUAN TRỌNG)
=========================================== -->
<!-- Mở ở tab mới cần đi kèm rel="noopener noreferrer" để bảo mật -->
<a href="[https://facebook.com](https://facebook.com)" target="_blank" rel="noopener noreferrer">
  Truy cập Fanpage của chúng tôi (Mở thẻ mới)
</a>

<!-- ==========================================
     3. ĐIỂM NEO (JUMP LINKS) - CUỘN TRANG CỤC BỘ
=========================================== -->
<!-- Link điều hướng đến 1 khối có id="contact" trên cùng trang -->
<a href="#contact">Cuộn xuống phần Liên hệ</a>

<!-- ... Rất nhiều nội dung ở giữa ... -->

<!-- Đích đến của điểm neo -->
<h2 id="contact">Thông tin liên hệ</h2>
<p>Hãy gửi tin nhắn cho chúng tôi.</p>

<!-- ==========================================
     4. GIAO THỨC ĐẶC BIỆT (EMAIL & ĐIỆN THOẠI)
=========================================== -->
<!-- Tự động mở ứng dụng Email (Outlook, Mail, Gmail) -->
<a href="mailto:support@example.com?subject=Hỗ trợ kỹ thuật">Gửi Email cho Support</a>

<!-- Tự động mở màn hình gọi điện (Hoạt động tốt trên Mobile) -->
<a href="tel:+84123456789">Gọi ngay: 0123.456.789</a>

<!-- ==========================================
     5. CẤU TRÚC SEMANTIC NAVIGATION (MENU CHUẨN)
=========================================== -->
<!-- Dùng thẻ <nav> bao bọc menu chính -->
<nav aria-label="Menu chính">
  <ul>
    <li><a href="/">Trang chủ</a></li>
    <li><a href="/products.html">Sản phẩm</a></li>
    <li><a href="/blog.html">Bài viết</a></li>
    <li><a href="/contact.html">Liên hệ</a></li>
  </ul>
</nav>
```
## 05. Lists - Danh sách

**📝 Giới thiệu & Lý thuyết cơ bản:**
Danh sách (Lists) là công cụ hoàn hảo để nhóm các thông tin có liên quan lại với nhau, giúp nội dung trở nên dễ đọc, dễ quét (scan) và có cấu trúc rõ ràng. Có 3 loại danh sách chính trong HTML:
1.  **Unordered List (`<ul>` - Danh sách không có thứ tự):** Sử dụng các dấu chấm tròn (bullet points) ở đầu dòng. Dùng khi thứ tự của các mục không quan trọng.
2.  **Ordered List (`<ol>` - Danh sách có thứ tự):** Sử dụng chữ số hoặc chữ cái đánh dấu ở đầu dòng. Dùng khi các mục cần tuân theo một trình tự nhất định (ví dụ: các bước nấu ăn, bảng xếp hạng).
    *   Cả `<ul>` và `<ol>` đều sử dụng thẻ **`<li>`** (List Item) để định nghĩa từng mục bên trong.
3.  **Description List (`<dl>` - Danh sách mô tả):** Dùng để hiển thị các cặp từ khóa - mô tả (giống như từ điển). Bao gồm thẻ `<dt>` (Data Term - Từ khóa) và `<dd>` (Data Description - Mô tả).

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Menu Điều hướng (Navigation):** Thực tế 99% các thanh menu trên website hiện đại đều được cấu trúc bằng thẻ `<ul>` và `<li>` (kết hợp với CSS để xóa dấu chấm tròn và dàn hàng ngang).
*   **Danh sách lồng nhau (Nested Lists):** Khi muốn tạo một danh sách con bên trong một danh sách cha, bạn **bắt buộc** phải đặt danh sách con đó **bên trong một thẻ `<li>`**, tuyệt đối không đặt lửng lơ giữa các thẻ `<li>` với nhau.
*   **Các thuộc tính ẩn của `<ol>`:** Thẻ `<ol>` rất mạnh mẽ, bạn có thể đảo ngược thứ tự đếm với thuộc tính `reversed`, hoặc bắt đầu đếm từ một số bất kỳ với thuộc tính `start`.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     1. UNORDERED LIST (Không thứ tự)
=========================================== -->
<h3>Danh sách mua sắm</h3>
<ul>
  <li>Sữa tươi</li>
  <li>Bánh mì</li>
  <li>Trứng gà</li>
</ul>

<!-- ==========================================
     2. ORDERED LIST (Có thứ tự & Nâng cao)
=========================================== -->
<h3>Các bước pha cà phê</h3>
<!-- Thuộc tính type="I" (đếm bằng số La Mã), type="A" (đếm bằng chữ cái), type="1" (số) -->
<ol type="1">
  <li>Đun sôi nước</li>
  <li>Cho cà phê vào phin</li>
  <li>Đổ nước sôi và đợi 5 phút</li>
</ol>

<h3>Bảng xếp hạng Top 3 (Đếm ngược)</h3>
<!-- Thuộc tính reversed giúp đếm ngược: 3, 2, 1 -->
<ol reversed>
  <li>Nguyễn Văn A</li>
  <li>Trần Thị B</li>
  <li>Lê Văn C</li>
</ol>

<!-- Bắt đầu đếm từ một số cụ thể (Start) -->
<h3>Phần tiếp theo của danh sách</h3>
<ol start="4">
  <li>Mục số bốn</li>
  <li>Mục số năm</li>
</ol>

<!-- ==========================================
     3. NESTED LIST (Danh sách lồng nhau)
=========================================== -->
<h3>Danh mục sản phẩm</h3>
<ul>
  <li>Điện thoại
    <!-- Danh sách con nằm BÊN TRONG thẻ <li> của "Điện thoại" -->
    <ul>
      <li>iPhone 15</li>
      <li>Samsung Galaxy S24</li>
    </ul>
  </li> <!-- Kết thúc thẻ <li> Điện thoại -->
  
  <li>Laptop
    <ul>
      <li>MacBook Pro</li>
      <li>Dell XPS</li>
    </ul>
  </li>
</ul>

<!-- ==========================================
     4. DESCRIPTION LIST (Danh sách mô tả)
=========================================== -->
<h3>Từ điển thuật ngữ Frontend</h3>
<dl>
  <dt>HTML</dt>
  <dd>Ngôn ngữ đánh dấu siêu văn bản, dùng để xây dựng bộ khung website.</dd>
  
  <dt>CSS</dt>
  <dd>Ngôn ngữ tạo kiểu, dùng để trang trí và dàn bố cục cho HTML.</dd>
  
  <dt>JavaScript</dt>
  <dd>Ngôn ngữ lập trình giúp website có tính tương tác.</dd>
</dl>
```
## 06. Images & Media - Hình ảnh & Đa phương tiện

**📝 Giới thiệu & Lý thuyết cơ bản:**
Một trang web toàn chữ sẽ rất nhàm chán. HTML cung cấp các thẻ để nhúng trực tiếp các nội dung đa phương tiện vào trang web:
1.  **Hình ảnh (`<img>`):** Là thẻ tự đóng (empty element). Cần 2 thuộc tính bắt buộc là `src` (đường dẫn tới file ảnh) và `alt` (văn bản thay thế).
2.  **Figure & Figcaption (`<figure>`, `<figcaption>`):** Cặp thẻ Semantic dùng để bao bọc một bức ảnh (hoặc biểu đồ, đoạn code) kèm theo chú thích (caption) của nó, giúp Google hiểu rõ ngữ cảnh của bức ảnh hơn.
3.  **Âm thanh (`<audio>`):** Nhúng các file âm thanh (thường là định dạng `.mp3`). 
4.  **Video (`<video>`):** Nhúng video trực tiếp vào trang web (thường là định dạng `.mp4`) mà không cần thông qua bên thứ 3 như YouTube.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Thuộc tính `alt` là BẮT BUỘC:** Không bao giờ được quên thuộc tính `alt` trong thẻ `<img>`. Nó giúp người khiếm thị biết bức ảnh nói về gì (thông qua trình đọc màn hình), hiển thị khi ảnh bị lỗi không tải được, và là yếu tố số 1 để SEO hình ảnh trên Google.
*   **Chống "giật" giao diện (CLS - Cumulative Layout Shift):** Luôn khai báo `width` và `height` (hoặc tỷ lệ khung hình) cho ảnh/video. Nếu không, khi ảnh tải xong nó sẽ đẩy các phần chữ bên dưới xuống, gây trải nghiệm người dùng rất tệ và bị Google trừ điểm SEO.
*   **Lazy Loading (Tải lười biếng):** Thêm thuộc tính `loading="lazy"` vào các bức ảnh nằm tít phía dưới trang web. Trình duyệt sẽ chỉ tải ảnh đó khi người dùng cuộn chuột tới gần, giúp trang web load nhanh hơn gấp nhiều lần.
*   **Video Autoplay:** Nếu bạn muốn video tự động phát, bắt buộc phải thêm thuộc tính `muted` (tắt tiếng). Trình duyệt hiện đại sẽ chặn mọi video tự động phát mà có âm thanh để tránh làm phiền người dùng.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     1. HÌNH ẢNH CƠ BẢN VÀ TỐI ƯU HIỆU SUẤT
=========================================== -->
<!-- Ảnh chuẩn SEO: Có alt, có kích thước cố định, có tải lười biếng -->
<img 
  src="images/hero-banner.jpg" 
  alt="Khách hàng đang sử dụng sản phẩm trên điện thoại" 
  width="800" 
  height="400" 
  loading="lazy" 
/>

<!-- ==========================================
     2. HÌNH ẢNH CÓ NGỮ NGHĨA KÈM CHÚ THÍCH (FIGURE)
=========================================== -->
<figure>
  <img src="images/chart.png" alt="Biểu đồ tăng trưởng doanh thu quý 1 năm 2026" />
  <figcaption>Biểu đồ 1.1: Tăng trưởng doanh thu Quý 1/2026</figcaption>
</figure>

<!-- ==========================================
     3. NHÚNG ÂM THANH (AUDIO)
=========================================== -->
<!-- Thuộc tính 'controls' sẽ hiển thị thanh tiến trình, nút Play, Loa -->
<audio controls>
  <!-- Có thể cung cấp nhiều định dạng để dự phòng -->
  <source src="audio/podcast-ep1.mp3" type="audio/mpeg" />
  <source src="audio/podcast-ep1.ogg" type="audio/ogg" />
  <!-- Dòng chữ này chỉ hiện nếu trình duyệt quá cũ không hỗ trợ thẻ audio -->
  Trình duyệt của bạn không hỗ trợ phát âm thanh. Vui lòng tải xuống file mp3.
</audio>

<!-- ==========================================
     4. NHÚNG VIDEO CỤC BỘ
=========================================== -->
<!-- 
  controls: Hiện thanh điều khiển
  autoplay: Tự động phát
  muted: Bắt buộc đi kèm autoplay (tắt tiếng)
  poster: Ảnh nền hiển thị trước khi video được Play 
-->
<video controls autoplay muted poster="images/video-thumbnail.jpg" width="100%" height="auto">
  <source src="videos/intro.mp4" type="video/mp4" />
  <source src="videos/intro.webm" type="video/webm" />
  Trình duyệt của bạn không hỗ trợ thẻ video.
</video>
```
## 07. Tables - Bảng biểu

**📝 Giới thiệu & Lý thuyết cơ bản:**
Thẻ `<table>` được sử dụng để hiển thị dữ liệu dưới dạng lưới 2 chiều gồm các hàng (rows) và cột (columns). Một cấu trúc bảng cơ bản được cấu thành từ các thẻ:
*   **`<table>`**: Thẻ gốc bao bọc toàn bộ bảng.
*   **`<tr>` (Table Row)**: Tạo ra một hàng ngang trong bảng.
*   **`<th>` (Table Heading)**: Ô chứa tiêu đề của cột hoặc hàng. Trình duyệt mặc định sẽ in đậm và căn giữa nội dung trong thẻ này.
*   **`<td>` (Table Data)**: Ô chứa dữ liệu thông thường.

Ngoài ra, HTML5 cung cấp các thẻ Semantic để chia bảng thành các khu vực logic rõ ràng:
*   **`<caption>`**: Tiêu đề/chú thích của toàn bộ bảng (luôn đặt ngay dưới thẻ `<table>`).
*   **`<thead>`**: Phần đầu bảng (thường chứa các thẻ `<th>`).
*   **`<tbody>`**: Phần thân bảng (chứa nội dung dữ liệu chính).
*   **`<tfoot>`**: Phần chân bảng (thường dùng để tính tổng, thống kê ở hàng cuối cùng).

**🎯 Trường hợp sử dụng & Best Practices:**
*   **TUYỆT ĐỐI KHÔNG dùng Table để dàn bố cục (Layout):** Vào những năm 2000, người ta dùng bảng để chia cột giao diện trang web. Hiện nay, điều này là sai chuẩn nghiêm trọng, gây hại cho SEO và làm web tải chậm. Chỉ dùng Table để **hiển thị dữ liệu dạng bảng** (ví dụ: báo cáo tài chính, thời khóa biểu, so sánh thông số sản phẩm).
*   **Sử dụng thuộc tính `scope` cho a11y:** Luôn thêm `scope="col"` (nếu là tiêu đề cột) hoặc `scope="row"` (nếu là tiêu đề hàng) vào các thẻ `<th>`. Điều này giúp trình đọc màn hình đọc bảng chính xác cho người khiếm thị.
*   **Gộp ô (Merge Cells):** Sử dụng thuộc tính `colspan` để gộp các cột theo chiều ngang, và `rowspan` để gộp các hàng theo chiều dọc.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     1. BẢNG DỮ LIỆU CHUẨN SEMANTIC VÀ A11Y
=========================================== -->
<table>
  <!-- Tiêu đề chung của bảng (Rất tốt cho Accessibility) -->
  <caption>Bảng lương nhân viên tháng 08/2026</caption>
  
  <!-- Phần đầu bảng -->
  <thead>
    <tr>
      <th scope="col">Mã NV</th>
      <th scope="col">Họ và tên</th>
      <th scope="col">Chức vụ</th>
      <th scope="col">Lương cơ bản</th>
    </tr>
  </thead>
  
  <!-- Phần thân bảng (Chứa dữ liệu chính) -->
  <tbody>
    <tr>
      <!-- Đây có thể coi là tiêu đề của hàng này, dùng th với scope="row" -->
      <th scope="row">NV01</th>
      <td>Nguyễn Văn A</td>
      <td>Developer</td>
      <td>$2,000</td>
    </tr>
    <tr>
      <th scope="row">NV02</th>
      <td>Trần Thị B</td>
      <td>Designer</td>
      <td>$1,800</td>
    </tr>
  </tbody>
  
  <!-- Phần chân bảng (Thường dùng để chốt số liệu/tính tổng) -->
  <tfoot>
    <tr>
      <!-- Dùng colspan="3" để gộp 3 cột đầu tiên làm 1 -->
      <th scope="row" colspan="3">Tổng cộng quỹ lương:</th>
      <td><strong>$3,800</strong></td>
    </tr>
  </tfoot>
</table>

<!-- ==========================================
     2. GỘP HÀNG (ROWSPAN) VÀ GỘP CỘT (COLSPAN)
=========================================== -->
<h3>Thời khóa biểu (Ví dụ gộp ô)</h3>
<table border="1"> <!-- border="1" chỉ để dễ nhìn viền, thực tế sẽ dùng CSS -->
  <tr>
    <th>Thứ</th>
    <th>Sáng</th>
    <th>Chiều</th>
  </tr>
  <tr>
    <td>Thứ 2</td>
    <td>Toán</td>
    <!-- rowspan="2" gộp ô này với ô ngay dưới nó (hàng tiếp theo) -->
    <td rowspan="2">Tự học tại thư viện</td> 
  </tr>
  <tr>
    <td>Thứ 3</td>
    <td>Văn</td>
    <!-- Ô "Chiều" của Thứ 3 đã bị gộp từ trên xuống nên không cần viết thẻ td ở đây nữa -->
  </tr>
  <tr>
    <td>Thứ 4</td>
    <!-- colspan="2" gộp 2 ô theo chiều ngang -->
    <td colspan="2">Nghỉ lễ toàn trường</td>
  </tr>
</table>
```
## 08. Forms - Biểu mẫu

**📝 Giới thiệu & Lý thuyết cơ bản:**
Thẻ `<form>` được sử dụng để tạo một biểu mẫu thu thập dữ liệu từ người dùng. Một Form hoạt động dựa trên 2 thuộc tính cốt lõi của thẻ `<form>`:
*   **`action`**: Đường dẫn (URL) tới Server nơi dữ liệu sẽ được gửi đến để xử lý.
*   **`method`**: Phương thức gửi dữ liệu. Có 2 loại chính:
    *   `GET`: Dữ liệu được đính kèm trực tiếp lên thanh địa chỉ URL (ví dụ: `?search=html`). Dùng khi lấy dữ liệu, tìm kiếm, không dùng cho dữ liệu bảo mật (như mật khẩu).
    *   `POST`: Dữ liệu được đóng gói ngầm bên trong phần "Body" của HTTP Request. Dùng khi gửi dữ liệu nhạy cảm (đăng nhập, thanh toán) hoặc dữ liệu dung lượng lớn.

Bên trong Form chứa các "Controls" (Phần tử điều khiển) như `<input>`, `<textarea>` (khung nhập văn bản nhiều dòng), `<select>` (danh sách thả xuống), và `<button>`. 
Mỗi input **bắt buộc phải có thuộc tính `name`**, vì Server sẽ dựa vào `name` để nhận diện giá trị mà người dùng nhập vào.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **LUÔN SỬ DỤNG `<label>`:** Mọi thẻ `<input>` đều phải đi kèm với một thẻ `<label>`. Thuộc tính `for` của label phải trùng khớp với `id` của input. Điều này không chỉ giúp trình đọc màn hình hoạt động đúng (a11y) mà còn giúp tăng Trải nghiệm người dùng (UX): khi click vào chữ (label), con trỏ chuột sẽ tự động nhảy vào ô nhập liệu.
*   **Sử dụng đúng Input Type:** Thay vì dùng `type="text"` cho mọi thứ, hãy dùng `type="email"`, `type="number"`, `type="tel"`, `type="date"`. Trình duyệt (đặc biệt trên điện thoại) sẽ tự động hiển thị bàn phím phù hợp (ví dụ: gõ email sẽ hiện phím `@`, gõ số sẽ hiện bàn phím số) và tự động báo lỗi (Validation) nếu nhập sai định dạng.
*   **Gom nhóm Checkbox và Radio:** Các nút Radio (chọn 1) phải có *cùng* thuộc tính `name` thì chúng mới hoạt động như một nhóm (chọn cái này thì cái kia tự tắt).

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     FORM ĐĂNG KÝ (Sử dụng method POST bảo mật)
=========================================== -->
<form action="/api/register" method="POST">
  
  <!-- 1. TEXT INPUT (Cơ bản) -->
  <!-- Thuộc tính for của label phải khớp với id của input -->
  <div class="form-group">
    <label for="username">Tên đăng nhập:</label>
    <input type="text" id="username" name="username" placeholder="Nhập tên của bạn" required />
  </div>

  <!-- 2. EMAIL & PASSWORD (Tự động validate và bảo mật) -->
  <div class="form-group">
    <label for="userEmail">Email:</label>
    <!-- type="email" bắt buộc người dùng nhập có chữ @ -->
    <input type="email" id="userEmail" name="email" required />
  </div>

  <div class="form-group">
    <label for="userPassword">Mật khẩu:</label>
    <!-- type="password" tự động mã hóa ký tự thành dấu chấm tròn -->
    <input type="password" id="userPassword" name="password" minlength="8" required />
  </div>

  <!-- 3. RADIO BUTTON (Chỉ được chọn 1) -->
  <!-- Các input radio phải CÙNG name là "gender" để gom nhóm -->
  <fieldset>
    <legend>Giới tính:</legend>
    <input type="radio" id="genderMale" name="gender" value="male" />
    <label for="genderMale">Nam</label>

    <input type="radio" id="genderFemale" name="gender" value="female" />
    <label for="genderFemale">Nữ</label>
  </fieldset>

  <!-- 4. CHECKBOX (Được chọn nhiều) -->
  <div class="form-group">
    <input type="checkbox" id="subscribe" name="newsletter" value="yes" checked />
    <label for="subscribe">Đăng ký nhận tin tức qua email</label>
  </div>

  <!-- 5. SELECT DROPDOWN (Danh sách thả xuống) -->
  <div class="form-group">
    <label for="country">Quốc gia:</label>
    <select id="country" name="country">
      <option value="">-- Chọn quốc gia --</option>
      <option value="vn">Việt Nam</option>
      <option value="us">Hoa Kỳ</option>
      <option value="jp">Nhật Bản</option>
    </select>
  </div>

  <!-- 6. TEXTAREA (Nhập văn bản dài) -->
  <div class="form-group">
    <label for="bio">Giới thiệu bản thân:</label>
    <!-- Textarea không dùng thuộc tính value, nội dung nằm giữa 2 thẻ -->
    <textarea id="bio" name="bio" rows="4" cols="50"></textarea>
  </div>

  <!-- 7. BUTTON SUBMIT -->
  <!-- type="submit" sẽ tự động kích hoạt hành động gửi form -->
  <button type="submit">Đăng ký tài khoản</button>

</form>
```
## 09. Semantic HTML - HTML Ngữ nghĩa

**📝 Giới thiệu & Lý thuyết cơ bản:**
"Semantic" có nghĩa là *ngữ nghĩa*. Semantic HTML là việc sử dụng các thẻ HTML để **mô tả chính xác ý nghĩa của nội dung** chứa bên trong nó, thay vì chỉ dùng để tạo bố cục giao diện.
*   **Thẻ Non-semantic (Vô nghĩa):** `<div>` và `<span>`. Chúng không cung cấp bất kỳ thông tin gì về nội dung bên trong (đó là bài viết, hay là thanh menu, hay là phần chân trang?).
*   **Thẻ Semantic (Có ngữ nghĩa):** `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>`. Khi nhìn vào các thẻ này, cả Lập trình viên, Google (Search Engine) và Trình đọc màn hình (Screen Reader) đều hiểu ngay khối nội dung đó đóng vai trò gì.

**Lợi ích khổng lồ:**
1.  **SEO (Tối ưu hóa công cụ tìm kiếm):** Googlebot ưu tiên cào (crawl) và index các nội dung nằm trong thẻ `<article>`, `<main>` hơn là các `<div>` lộn xộn.
2.  **Accessibility (a11y):** Người khiếm thị sử dụng phím tắt để nhảy thẳng đến vùng `<nav>` hoặc `<main>` mà không cần nghe đọc toàn bộ trang.
3.  **Dễ bảo trì:** Code của bạn sẽ trong vắt, dễ đọc như đọc một cuốn sách.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Thoát khỏi hội chứng "Div Soup" (Cháo Div):** Đừng bao giờ dùng `<div class="header">`, hãy dùng `<header>`. Chỉ sử dụng `<div>` khi bạn cần tạo ra một khối thuần túy để trang trí bằng CSS (CSS Wrapper) và không có thẻ Semantic nào phù hợp.
*   **Phân biệt `<article>` và `<section>`:**
    *   `<article>`: Là một khối nội dung **độc lập hoàn toàn**. Nếu bạn cắt `<article>` này đem sang một trang web khác, nó vẫn mang ý nghĩa trọn vẹn (Ví dụ: Một bài viết Blog, một thẻ Sản phẩm, một bài đăng Forum).
    *   `<section>`: Là một khối nội dung nhóm theo **chủ đề**. Thường dùng để chia một trang dài thành các phần nhỏ (Ví dụ: Phần "Về chúng tôi", Phần "Dịch vụ", Phần "Liên hệ").
*   **Quy tắc `<main>`:** Mỗi trang web (document) chỉ được phép có **DUY NHẤT MỘT** thẻ `<main>`, và nó không được nằm ẩn bên trong `<article>`, `<aside>`, `<header>`, hay `<footer>`.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     ❌ CÁCH VIẾT CŨ (TỒI): HỘI CHỨNG "DIV SOUP"
     (Không tốt cho SEO và Accessibility)
=========================================== -->
<div class="header">
  <div class="logo">My Blog</div>
  <div class="menu">...</div>
</div>
<div class="content">
  <div class="post">Bài viết số 1...</div>
</div>
<div class="footer">Bản quyền 2026</div>

<!-- ==========================================
     ✅ CÁCH VIẾT CHUẨN SEMANTIC HTML5 (HIỆN ĐẠI)
=========================================== -->
<!-- 1. HEADER: Phần đầu trang (Chứa Logo, Menu) -->
<header>
  <h1>Logo Công Ty</h1>
  
  <!-- NAV: Khối Điều hướng chính -->
  <nav aria-label="Menu chính">
    <ul>
      <li><a href="/">Trang chủ</a></li>
      <li><a href="/blog">Blog</a></li>
    </ul>
  </nav>
</header>

<!-- 2. MAIN: Vùng chứa nội dung quan trọng nhất của trang -->
<main>
  
  <!-- SECTION: Chia nhóm theo chủ đề (Ví dụ: Phần Bài viết mới nhất) -->
  <section id="latest-posts">
    <h2>Bài viết mới nhất</h2>
    
    <!-- ARTICLE: Một bài viết độc lập -->
    <article>
      <header>
        <h3>Cách học HTML5 chuẩn</h3>
        <!-- Thẻ <time> báo cho Google biết đây là ngày tháng -->
        <p>Đăng ngày: <time datetime="2026-08-27">27/08/2026</time></p>
      </header>
      <p>Semantic HTML giúp code của bạn trở nên tuyệt vời hơn...</p>
      <a href="/doc-tiep">Đọc tiếp...</a>
    </article>
    
    <article>
      <!-- Bài viết thứ 2... -->
    </article>
  </section>

</main>

<!-- 3. ASIDE: Nội dung phụ trợ (Sidebar, Quảng cáo, Link liên quan) -->
<!-- Lưu ý: Nội dung aside có thể bị ẩn đi mà không làm mất đi ý nghĩa của trang chính -->
<aside>
  <h2>Quảng cáo</h2>
  <p>Mua khóa học Web Frontend ngay hôm nay!</p>
</aside>

<!-- 4. FOOTER: Chân trang (Thông tin bản quyền, Tác giả, Link phụ) -->
<footer>
  <p>&copy; 2026 Bản quyền thuộc về WebMaster. All rights reserved.</p>
  <address>
    Liên hệ: <a href="mailto:admin@example.com">admin@example.com</a>
  </address>
</footer>
```
## 10. Attributes - Thuộc tính

**📝 Giới thiệu & Lý thuyết cơ bản:**
Thuộc tính (Attributes) cung cấp **thông tin bổ sung** cho các thẻ HTML. Chúng luôn luôn được viết bên trong **thẻ mở** và thường đi theo cặp `tên_thuộc_tính="giá_trị"`.

Có 3 nhóm thuộc tính chính trong HTML:
1.  **Thuộc tính đặc thù (Specific Attributes):** Chỉ có tác dụng với một vài thẻ nhất định. Ví dụ: `src` và `alt` chỉ dùng cho `<img>`, `href` chỉ dùng cho `<a>`, `type` dùng cho `<input>`.
2.  **Thuộc tính toàn cục (Global Attributes):** Là những thuộc tính có thể áp dụng cho **bất kỳ thẻ HTML nào**.
    *   `id`: Định danh duy nhất cho một phần tử trên toàn bộ trang.
    *   `class`: Phân loại phần tử, dùng để gom nhóm nhiều phần tử lại để style bằng CSS.
    *   `title`: Hiển thị chú thích (tooltip) khi người dùng di chuột qua phần tử.
    *   `hidden`: Ẩn phần tử khỏi giao diện.
    *   `tabindex`: Quản lý thứ tự focus khi người dùng nhấn phím Tab trên bàn phím.
3.  **Thuộc tính tùy chỉnh (`data-*` Attributes):** Do lập trình viên tự định nghĩa để lưu trữ dữ liệu ngầm trên giao diện, cực kỳ hữu ích khi cần lấy dữ liệu bằng JavaScript.
4.  **Thuộc tính Boolean:** Chỉ cần sự xuất hiện của tên thuộc tính là đủ để kích hoạt (mang giá trị `true`), không cần gán giá trị (như `disabled`, `checked`, `required`, `readonly`).

**🎯 Trường hợp sử dụng & Best Practices:**
*   **ID là duy nhất - Class là tái sử dụng:** Tuyệt đối không dùng một `id` (ví dụ `id="btn-submit"`) cho 2 thẻ khác nhau trên cùng một trang. Nếu muốn CSS hoặc JS tác động đến nhiều thẻ giống nhau, hãy dùng `class`.
*   **Luôn dùng dấu ngoặc kép:** Mặc dù HTML5 cho phép viết `class=container` (không có ngoặc kép), nhưng chuẩn mực code chuyên nghiệp (và để tránh lỗi khi giá trị có khoảng trắng) bắt buộc bạn phải viết `class="container"`.
*   **Tránh dùng thuộc tính `style` nội tuyến (Inline Style):** Trừ khi bạn dùng JavaScript để thay đổi style động, còn lại tuyệt đối không viết `<p style="color: red;">`. Hãy tách biệt việc trang trí ra file CSS để dễ bảo trì.
*   **Sức mạnh của `data-*`:** Đừng cố giấu dữ liệu vào class hoặc id. Nếu bạn muốn gắn ID của sản phẩm vào một nút bấm để JS lấy được khi click, hãy dùng `<button data-product-id="123">`.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     1. THUỘC TÍNH TOÀN CỤC (GLOBAL ATTRIBUTES)
=========================================== -->
<!-- id: Duy nhất; class: Có thể tái sử dụng cho thẻ khác -->
<p id="welcome-message" class="text-bold highlight">
  Xin chào, đây là thông điệp chào mừng!
</p>

<!-- title: Tạo tooltip khi hover chuột; hidden: Ẩn thẻ này đi -->
<div title="Đây là thông tin bổ sung khi di chuột vào" hidden>
  Nội dung này đang bị ẩn, người dùng không nhìn thấy.
</div>

<!-- tabindex: Giúp thẻ <div> (vốn không focus được) có thể focus khi nhấn Tab -->
<div tabindex="0">Bạn có thể dùng phím Tab để focus vào hộp này.</div>

<!-- ==========================================
     2. THUỘC TÍNH BOOLEAN (Không cần giá trị)
=========================================== -->
<form>
  <!-- required: Bắt buộc nhập; readonly: Chỉ đọc, không được sửa -->
  <input type="text" value="Dữ liệu cố định" readonly required />
  
  <!-- checked: Tự động đánh dấu tick; disabled: Vô hiệu hóa nút -->
  <input type="checkbox" checked /> Đồng ý điều khoản
  <button type="submit" disabled>Gửi (Đang bị khóa)</button>
</form>

<!-- ==========================================
     3. DATA ATTRIBUTES (Lưu trữ dữ liệu tùy chỉnh)
=========================================== -->
<!-- Lưu trữ ngầm giá, màu sắc và ID của sản phẩm -->
<button 
  class="btn-buy" 
  data-product-id="A99" 
  data-price="500000" 
  data-color="red"
>
  Mua Ngay
</button>

<!-- 
  [DÀNH CHO JAVASCRIPT]: 
  Sau này trong file JS, bạn có thể lấy dữ liệu cực kỳ dễ dàng:
  const btn = document.querySelector('.btn-buy');
  console.log(btn.dataset.productId); // "A99"
  console.log(btn.dataset.price); // "500000"
-->
```
## 11. HTML Layout & Page Structure - Bố cục & Cấu trúc trang

**📝 Giới thiệu & Lý thuyết cơ bản:**
Bố cục trang web (Page Layout) là khung sườn tổng thể định hình cách các thành phần chính (Header, Sidebar, Nội dung chính, Footer) được sắp xếp trên màn hình. 

Trước đây, lập trình viên dùng thẻ `<table>` hoặc lạm dụng `<div>` gắn các class như `<div id="header">` để chia bố cục. Trong HTML5, nhờ có các thẻ Semantic (đã học ở Mục 09), việc cấu trúc bố cục trở nên rõ ràng và tiêu chuẩn hóa hơn rất rất nhiều.

Một mô hình cấu trúc trang web tiêu chuẩn bao gồm:
1.  **Header (Đầu trang):** Logo, tiêu đề website, menu điều hướng (`<nav>`).
2.  **Hero Section / Banner:** Phần giới thiệu nổi bật nằm ngay dưới header để thu hút người dùng.
3.  **Main Content (Nội dung chính):** Chứa các phần bài viết (`<article>`) hoặc các phân đoạn (`<section>`). Có thể kết hợp thêm Sidebar (`<aside>`) nếu cần hiển thị các mục phụ.
4.  **Footer (Chân trang):** Thông tin bản quyền, liên hệ, liên kết mạng xã hội, các chính sách bảo mật.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Tránh dùng quá nhiều thẻ `<div>` bọc lồng nhau:** Trước khi viết một thẻ `<div>`, hãy tự hỏi: *"Có thẻ Semantic nào phù hợp hơn không?"*. Chỉ dùng `<div>` làm "khung chứa" thuần túy để CSS căn chỉnh (ví dụ: bọc chung một nhóm nút bấm).
*   **Cấu trúc Wrapper / Container:** Luôn có một thẻ chứa tổng thể (thường đặt class là `.container` hoặc `.wrapper`) bên trong các thẻ như `<header>`, `<main>`, `<footer>` để giới hạn chiều rộng tối đa (max-width) của trang web trên màn hình máy tính lớn, giúp nội dung không bị trải dài quá khổ.
*   **Thứ tự mã nguồn (DOM Order) phải logic:** Trình đọc màn hình (Screen Readers) và Googlebot đọc trang web từ trên xuống dưới theo thứ tự xuất hiện trong file HTML. Đừng dùng CSS để đảo lộn giao diện hiển thị một đằng mà mã nguồn HTML một nẻo, điều này sẽ làm hỏng trải nghiệm a11y và SEO.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Bố cục trang web chuẩn HTML5</title>
  </head>
  
  <body>

    <!-- ==========================================
         1. HEADER (ĐẦU TRANG)
    =========================================== -->
    <header class="site-header">
      <div class="container">
        <!-- Logo thương hiệu -->
        <div class="logo">
          <a href="/">MyWebsite</a>
        </div>
        
        <!-- Menu điều hướng -->
        <nav class="main-nav" aria-label="Điều hướng chính">
          <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/services">Dịch vụ</a></li>
            <li><a href="/about">Về chúng tôi</a></li>
            <li><a href="/contact">Liên hệ</a></li>
          </ul>
        </nav>
      </div>
    </header>

    <!-- ==========================================
         2. HERO SECTION (BANNER NỔI BẬT)
    =========================================== -->
    <section class="hero-banner">
      <div class="container">
        <h1>Giải pháp Công nghệ Hàng đầu</h1>
        <p>Chúng tôi giúp doanh nghiệp chuyển đổi số nhanh chóng và hiệu quả.</p>
        <a href="#contact" class="btn">Khám phá ngay</a>
      </div>
    </section>

    <!-- ==========================================
         3. MAIN CONTENT (NỘI DUNG CHÍNH & SIDEBAR)
    =========================================== -->
    <main class="site-main">
      <div class="container layout-grid">
        
        <!-- Phần nội dung chính bên trái -->
        <div class="content-area">
          <article>
            <h2>Bài viết nổi bật: Xu hướng Web 2026</h2>
            <p>Nội dung chi tiết của bài viết nằm ở đây...</p>
          </article>
        </div>

        <!-- Phần sidebar phụ trợ bên phải -->
        <aside class="sidebar">
          <h3>Bài viết liên quan</h3>
          <ul>
            <li><a href="#">Cách tối ưu SEO HTML5</a></li>
            <li><a href="#">Lập trình JavaScript cơ bản</a></li>
          </ul>
        </aside>

      </div>
    </main>

    <!-- ==========================================
         4. FOOTER (CHÂN TRANG)
    =========================================== -->
    <footer class="site-footer">
      <div class="container">
        <p>&copy; 2026 MyWebsite. Bảo lưu mọi quyền.</p>
        <ul class="footer-links">
          <li><a href="/privacy">Chính sách bảo mật</a></li>
          <li><a href="/terms">Điều khoản sử dụng</a></li>
        </ul>
      </div>
    </footer>

  </body>
</html>
```
## 12. Head, Meta & SEO - Đầu trang, Siêu dữ liệu & Tối ưu

**📝 Giới thiệu & Lý thuyết cơ bản:**
Thẻ `<head>` trong HTML là nơi chứa toàn bộ các siêu dữ liệu (Metadata) – tức là dữ liệu *về* dữ liệu. Hầu hết nội dung bên trong `<head>` không hiển thị trực tiếp ra màn hình cho người dùng xem, mà nó giao tiếp ngầm với:
1.  **Trình duyệt:** Hướng dẫn cách hiển thị trang (bảng mã, độ rộng màn hình responsive).
2.  **Công cụ tìm kiếm (Googlebot, Bingbot):** Đọc tiêu đề, mô tả để hiểu trang web nói về cái gì và xếp hạng nó trên kết quả tìm kiếm (SEO).
3.  **Mạng xã hội (Facebook, Twitter, LinkedIn):** Đọc cấu trúc Open Graph để hiển thị hình ảnh, tiêu đề đẹp mắt khi có người chia sẻ link website của bạn.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Tiêu đề trang (`<title>`):** Là thẻ SEO quan trọng nhất. Nên giữ độ dài trong khoảng từ 50-60 ký tự, chứa từ khóa chính và đặt tên thương hiệu ở cuối.
*   **Thẻ mô tả (`<meta name="description">`):** Độ dài chuẩn từ 150-160 ký tự. Đây là đoạn văn bản ngắn hiển thị dưới tiêu đề trên Google, hãy viết thật hấp dẫn để tăng tỷ lệ người dùng click vào trang (CTR).
*   **Canonical URL (`<link rel="canonical">`):** Bắt buộc phải có để chống lỗi trùng lặp nội dung (Duplicate Content) khi một trang web có thể truy cập bằng nhiều đường dẫn khác nhau (`http`, `https`, `www`, không `www`).
*   **Open Graph (OG Tags):** Nếu thiếu các thẻ `og:title`, `og:image`, khi bạn chia sẻ link lên Facebook, bài đăng sẽ trống trơn hoặc lấy nhầm ảnh ngẫu nhiên rất thiếu chuyên nghiệp.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <!-- ==========================================
         1. CÁC THẺ CƠ BẢN BẮT BUỘC
    =========================================== -->
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    
    <!-- Tiêu đề trang (Cực kỳ quan trọng cho SEO) -->
    <title>Học HTML5 Cùng Tôi - Cẩm Nang Frontend Toàn Diện</title>
    
    <!-- Mô tả trang (Hiển thị trên kết quả tìm kiếm Google) -->
    <meta name="description" content="Khám phá cẩm nang học HTML5 từ cơ bản đến nâng cao. Xây dựng website chuẩn SEO, Accessibility và Responsive chuyên nghiệp." />
    
    <!-- Từ khóa phụ trợ (Ít quan trọng với Google hiện đại nhưng vẫn dùng) -->
    <meta name="keywords" content="html5, hoc html, frontend, lap trinh web, seo html" />
    
    <!-- Tác giả của trang web -->
    <meta name="author" content="WebMaster Developer" />

    <!-- ==========================================
         2. CHỐNG TRÙNG LẶP NỘI DUNG (CANONICAL) -->
    <!-- Báo cho Google biết đâu là URL chính thống duy nhất của trang này -->
    <link rel="canonical" href="[https://example.com/hoc-html-co-ban](https://example.com/hoc-html-co-ban)" />

    <!-- ==========================================
         3. MẠNG XÃ HỘI (OPEN GRAPH CHO FACEBOOK, ZALO, LINKEDIN)
    =========================================== -->
    <meta property="og:type" content="website" />
    <meta property="og:url" content="[https://example.com/hoc-html-co-ban](https://example.com/hoc-html-co-ban)" />
    <meta property="og:title" content="Học HTML5 Cùng Tôi - Cẩm Nang Frontend Toàn Diện" />
    <meta property="og:description" content="Tài liệu tự học HTML5 chuyên sâu, chuẩn SEO và thực chiến." />
    <meta property="og:image" content="[https://example.com/images/share-banner.jpg](https://example.com/images/share-banner.jpg)" />

    <!-- ==========================================
         4. THẺ TWITTER CARD (CHO X/TWITTER)
    =========================================== -->
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="Học HTML5 Cùng Tôi" />
    <meta name="twitter:image" content="[https://example.com/images/share-banner.jpg](https://example.com/images/share-banner.jpg)" />

    <!-- ==========================================
         5. LIÊN KẾT TÀI NGUYÊN (CSS, FAVICON, FONT)
    =========================================== -->
    <!-- Favicon (Biểu tượng hiển thị trên tab trình duyệt) -->
    <link rel="icon" type="image/png" href="/favicon.png" />
    
    <!-- File định dạng CSS -->
    <link rel="stylesheet" href="/css/style.css" />
    
    <!-- Tải trước font chữ để tăng tốc độ load trang -->
    <link rel="preconnect" href="[https://fonts.googleapis.com](https://fonts.googleapis.com)">
    <link href="[https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap](https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap)" rel="stylesheet">
  </head>
  
  <body>
    <!-- Nội dung trang web -->
  </body>
</html>
```
## 13. Accessibility (a11y) - Khả năng tiếp cận

**📝 Giới thiệu & Lý thuyết cơ bản:**
Accessibility (thường được viết tắt là **a11y** vì có 11 chữ ký tự ở giữa chữ A và Y) là nguyên tắc thiết kế và lập trình website sao cho **tất cả mọi người đều có thể sử dụng được**, bao gồm cả những người khuyết tật (khiếm thị, mù màu, liệt tay không dùng được chuột, khiếm thính).

Trong HTML, a11y chủ yếu dựa vào 3 yếu tố cốt lõi:
1.  **Semantic HTML (Mục 09):** Trình đọc màn hình (Screen Readers) dựa hoàn toàn vào các thẻ chuẩn như `<nav>`, `<main>`, `<button>` để định hướng cho người khiếm thị.
2.  **ARIA Attributes (Accessible Rich Internet Applications):** Các thuộc tính mở rộng bắt đầu bằng tiền tố `aria-*` dùng để bổ sung ngữ nghĩa hoặc trạng thái cho các thành phần phức tạp mà HTML thuần chưa thể hiện hết (ví dụ: thông báo một menu đang đóng hay mở).
3.  **Keyboard Navigation (Điều hướng bằng bàn phím):** Đảm bảo người dùng không thể dùng chuột vẫn có thể lướt toàn bộ website mượt mà chỉ bằng phím `Tab`, `Enter` và các phím mũi tên.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Không bao giờ bỏ quên `alt` cho ảnh:** Như đã nhắc ở Mục 06, trình đọc màn hình sẽ đọc đoạn văn bản trong `alt` để người mù biết bức ảnh đó chứa nội dung gì. Nếu ảnh chỉ mang tính trang trí thuần túy, hãy để `alt=""` (rỗng) để trình đọc màn hình tự động bỏ qua.
*   **Độ tương phản màu sắc (Contrast Ratio):** Dù phần này thuộc về CSS, nhưng trong HTML bạn phải đảm bảo văn bản và màu nền có độ tương phản đủ cao để người bị thị lực kém hoặc mù màu vẫn đọc được.
*   **Quản lý Focus bằng Tabindex:** Tuyệt đối không làm mất khung viền focus mặc định (`outline: none` mà không thay thế bằng hiệu ứng khác trong CSS). Người dùng bàn phím cần biết họ đang đứng ở ô nào trên trang.
*   **Sử dụng nhãn rõ ràng cho Form:** Thay vì dùng thẻ `<input>` trơ trọi kèm placeholder (vì placeholder sẽ biến mất khi người dùng gõ chữ, gây khó khăn cho người hay quên), hãy luôn dùng thẻ `<label>` đi kèm.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     1. HÌNH ẢNH VÀ ALT TEXT CHO NGƯỜI KHIẾM THỊ
=========================================== -->
<!-- Ảnh có ý nghĩa thông tin: Bắt buộc có alt chi tiết -->
<img src="chart.png" alt="Biểu đồ thể hiện doanh thu tăng 50% trong quý 2 năm 2026" />

<!-- Ảnh chỉ mang tính trang trí: Để alt rỗng để trình đọc bỏ qua -->
<img src="decorative-flower.png" alt="" />

<!-- ==========================================
     2. ĐIỀU HƯỚNG BẰNG BÀN PHÍM (KEYBOARD NAVIGATION)
=========================================== -->
<!-- Các thẻ tương tác như <a>, <button>, <input> tự động nhận focus khi nhấn Tab.
     Nếu bạn bắt buộc phải dùng thẻ <div> làm nút bấm, phải thêm tabindex="0" -->
<div role="button" tabindex="0" class="custom-button">
  Nhấn vào tôi bằng phím Enter hoặc Space
</div>

<!-- ==========================================
     3. SỬ DỤNG ARIA LABELS CHO ICON BUTTONS
=========================================== -->
<!-- Nút chỉ chứa icon (không có chữ) sẽ khiến người khiếm thị không biết nút làm gì.
     Phải dùng aria-label để mô tả chức năng của nút đó. -->
<button aria-label="Đóng cửa sổ thông báo">
  <!-- Icon X (SVG hoặc FontIcon) -->
  <svg>...</svg>
</button>

<!-- ==========================================
     4. ARIA EXPANDED & CONTROLS CHO DROPDOWN / ACCORDION
=========================================== -->
<!-- Báo cho trình đọc màn hình biết menu này đang ĐÓNG (false) hay MỞ (true) -->
<button aria-expanded="false" aria-controls="dropdown-menu">
  Tài khoản của tôi ▾
</button>

<ul id="dropdown-menu" hidden>
  <li><a href="/profile">Hồ sơ</a></li>
  <li><a href="/logout">Đăng xuất</a></li>
</ul>
```
## 14. HTML nâng cao - Advanced HTML

**📝 Giới thiệu & Lý thuyết cơ bản:**
HTML không chỉ dừng lại ở các thẻ cơ bản như văn bản hay hình ảnh. Ở cấp độ nâng cao, HTML cung cấp các công cụ mạnh mẽ để tối ưu hóa hiệu suất, nhúng nội dung động, và xây dựng các thành phần giao diện phức tạp mà không cần viết quá nhiều mã lệnh rườm rà:
1.  **Iframe (`<iframe>`):** Cho phép nhúng một trang web độc lập (hoặc video từ YouTube, Google Maps) vào bên trong trang web hiện tại của bạn.
2.  **Template (`<template>`):** Thẻ HTML dùng để chứa các khối HTML "ẩn" không hiển thị khi trang vừa tải. Nó được thiết kế để JavaScript có thể nhân bản (clone) và chèn ra giao diện khi cần thiết (cực kỳ tối ưu cho việc render danh sách sản phẩm, tin nhắn).
3.  **Dialog (`<dialog>`):** Thẻ gốc chuẩn HTML5 dùng để tạo các hộp thoại Modal, Popup thông báo mà không cần dùng các thư viện JavaScript phức tạp bên ngoài.
4.  **Custom Data Attributes & Web Components:** Mở rộng khả năng của HTML bằng cách tự định nghĩa các thẻ tùy chỉnh của riêng bạn.

**🎯 Trường hợp sử dụng & Best Practices:**
*   **Bảo mật với Iframe (`sandbox`):** Khi nhúng trang web của bên thứ ba qua `<iframe>`, hãy luôn sử dụng thuộc tính `sandbox` để giới hạn quyền hạn của trang đó (ví dụ: chặn chạy mã JavaScript độc hại, chặn bật popup).
*   **Tận dụng `<dialog>` gốc:** Thay vì tự viết `<div>` cố định vị trí (`position: fixed`) rồi dùng JS bật/tắt hiển thị, hãy dùng thẻ `<dialog>` kết hợp với hàm `.showModal()` để trình duyệt tự quản lý lớp phủ (backdrop) và phím `Esc` để đóng cực kỳ mượt mà.
*   **Template sạch sẽ:** Không bao giờ dùng chuỗi HTML cộng dồn (string concatenation) quá dài trong JavaScript để tạo giao diện. Hãy dùng `<template>` kết hợp với `document.importNode()` để code sạch sẽ, an toàn và chống lỗi bảo mật XSS.

**💻 Cách dùng & Code minh họa chuyên sâu:**

```html
<!-- ==========================================
     1. NHÚNG BẢN ĐỒ VÀ VIDEO VỚI IFRAME
=========================================== -->
<!-- Nhúng bản đồ Google Maps -->
<iframe 
  src="[https://www.google.com/maps/embed?pb=](https://www.google.com/maps/embed?pb=)..." 
  width="100%" 
  height="300" 
  style="border:0;" 
  allowfullscreen="" 
  loading="lazy"
  title="Bản đồ vị trí công ty"
></iframe>

<!-- ==========================================
     2. TẠO POPUP MODAL CHUẨN HTML5 VỚI THẺ <DIALOG>
=========================================== -->
<!-- Mặc định thẻ này sẽ bị ẩn đi -->
<div id="my-dialog-container">
  <button id="open-modal-btn">Mở Hộp Thoại</button>

  <dialog id="custom-dialog">
    <form method="dialog"> <!-- method="dialog" giúp nút bấm tự động đóng modal -->
      <h3>Thông báo quan trọng</h3>
      <p>Bạn có chắc chắn muốn xóa tài khoản này không?</p>
      
      <div class="dialog-actions">
        <button value="cancel">Hủy bỏ</button>
        <button value="confirm" class="btn-danger">Đồng ý</button>
      </div>
    </form>
  </dialog>
</div>

<!-- (Minh họa JS ngắn gọn cho dialog) -->
<!--
  const dialog = document.querySelector('#custom-dialog');
  document.querySelector('#open-modal-btn').onclick = () => dialog.showModal();
-->


<!-- ==========================================
     3. SỬ DỤNG THẺ <TEMPLATE> CHO JAVASCRIPT RENDERING
=========================================== -->
<!-- Khung mẫu này hoàn toàn ẩn đối với người dùng -->
<template id="product-card-template">
  <div class="card">
    <img class="card-img" src="" alt="Ảnh sản phẩm" />
    <h4 class="card-title"></h4>
    <span class="card-price"></span>
  </div>
</template>

<!-- 
  [DÀNH CHO JAVASCRIPT]: Cách nhân bản template cực kỳ nhanh chóng:
  const template = document.querySelector('#product-card-template');
  const clone = template.content.cloneNode(true);
  
  // Điền dữ liệu vào bản clone
  clone.querySelector('.card-title').textContent = "Áo thun nam cao cấp";
  clone.querySelector('.card-price').textContent = "250.000đ";
  
  // Đưa ra giao diện thật
  document.body.appendChild(clone);
-->
<!-- 1. KIỂM TRA TÍNH HỢP LỆ (VALIDATION) CỦA FORM TRONG HTML -->
<input type="text" pattern="[A-Za-z]{3}" title="Chỉ nhập 3 chữ cái" required />

<!-- 2. TỐI ƯU HÌNH ẢNH RESPONSIVE VỚI PICTURE -->
<picture>
  <source media="(min-width: 1024px)" srcset="large.jpg">
  <source media="(min-width: 768px)" srcset="medium.jpg">
  <img src="small.jpg" alt="Ảnh linh hoạt theo màn hình">
</picture>

<!-- 3. GHI CHÚ AN TOÀN TRONG HTML -->
<!-- Đây là bình luận (comment), trình duyệt sẽ bỏ qua dòng này -->
