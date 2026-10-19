# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Nguyễn Phan Bảo Thy
- **MSSV:** [125002572]
- **Tên đề tài Website:** Landing Page Giới Thiệu & Đặt Lịch Dịch Vụ - The Midnight Veil (Gothic Lenormand & Tarot Studio)
- **Công cụ AI đã sử dụng:** Gemini, ChatGPT, Claude

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> *"Tôi muốn xây dựng một website Landing Page chuyên nghiệp cho 'The Midnight Veil' - Studio dịch vụ đọc bài Lenormand, Tarot và phân tích biểu đồ Chiêm tinh. Phong cách thiết kế mang định hướng Dark Gothic/Monochrome tinh tế, sang trọng, huyền bí.*
> 
> *Yêu cầu kỹ thuật bắt buộc:*
> 1. *Sử dụng chuẩn Semantic HTML5 (có đủ <header>, <nav>, <main>, <section>, <article>, <footer>).*
> 2. *Sử dụng CSS Variables (:root) để quản lý màu sắc, font chữ và spacing.*
> 3. *Dùng CSS Flexbox và CSS Grid cho layout responsive.*
> 4. *Tích hợp Animate.css cho các phần tử chính và AOS (Animate On Scroll) cho hiệu ứng cuộn trang.*
> 5. *Đảm bảo không lạm dụng thẻ <div> vô nghĩa.*
> 
> *Hãy tạo cho tôi khung mã nguồn ban đầu gồm index.html và style.css."*

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML & CSS Variable

- **Prompt đã dùng:**
  > *"Hãy kiểm tra lại mã nguồn HTML và CSS vừa tạo. Tôi thấy bạn đang dùng quá nhiều thẻ <div> cho các khung nội dung chính và các thẻ bài viết dịch vụ. Hãy sửa lại:*
  > *- Thay thế các <div> bao bọc nội dung chính bằng <main>, <section>.*
  > *- Dùng thẻ <article> cho các khối thẻ bài viết dịch vụ (service cards).*
  > *- Khai báo hệ thống CSS Variables trong :root quản lý mã màu Gothic (tông đen huyền bí --bg-color kết hợp điểm nhấn vàng kim --primary-color), font chữ nghệ thuật (Cinzel & Plus Jakarta Sans)."*

- **Kết quả AI tạo ra:**
  AI đã tái cấu trúc lại mã nguồn:
  1. Loại bỏ các thẻ `<div>` bừa bãi, chia rõ ràng cấu trúc `<header>`, `<nav>`, `<main>`, `<section id="hero">`, `<section id="about">`, `<section id="services">`, `<section id="contact">`, và `<footer>`.
  2. Các gói dịch vụ tư vấn được bao bọc chuẩn bằng thẻ `<article class="service-card">`.
  3. Trong `style.css`, hệ thống `:root` đã khai báo đầy đủ các biến `--bg-color`, `--surface-color`, `--primary-color`, `--font-heading`, `--font-body`.

- **Nhận xét & Tinh chỉnh của SV:**
  - Khung Semantic HTML5 đã chuẩn ngữ nghĩa và hợp lệ, không còn bị lạm dụng `<div>`.
  - Tuy nhiên, phần khoảng cách giữa các section chưa đồng đều và nút bấm CTA chưa có trạng thái `:hover` rõ ràng. Tôi đã tự chỉnh sửa bổ sung `:hover`, `:focus` với hiệu ứng chuyển màu `--primary-hover` và đổ bóng nhẹ trong CSS.

---

### Lần 2: Tích hợp thư viện Animate.css & AOS

- **Prompt đã dùng:**
  > *"Bây giờ hãy tích hợp thư viện Animate.css vào tiêu đề chính (Hero section) và nút CTA để tạo hiệu ứng xuất hiện ấn tượng khi tải trang. Sau đó, nhúng CDN thư viện AOS (Animate On Scroll) và gán thuộc tính `data-aos` vào các khối <article> dịch vụ và <form> liên hệ để tạo hiệu ứng cuộn trang sinh động."*

- **Thách thức gặp phải:**
  Sau khi nhúng CDN AOS vào HTML, hiệu ứng cuộn trang vẫn không hoạt động khi cuộn xuống các phần tử chứa `data-aos`.

- **Cách sửa prompt (Debug prompt):**
  > *"Hiệu ứng AOS không chạy khi cuộn trang. Nguyên nhân là do chưa gọi đoạn mã JavaScript khởi tạo thư viện. Hãy bổ sung thẻ `<script>` gọi `AOS.init()` ngay trước thẻ đóng `</body>` với cấu hình duration thích hợp (khoảng 1000ms) và thiết lập thuộc tính `once: true` để hiệu ứng diễn ra mượt mà, không bị lặp lại gây rối mắt."*

- **Kết quả sau khi debug:**
  AI đã bổ sung đúng đoạn script `AOS.init({ duration: 1000, once: true });`. Hiệu ứng cuộn trang chuyển động mượt mà, chuẩn kỹ thuật theo yêu cầu bài thi.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

- **AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?**
  AI giúp tiết kiệm tối đa thời gian ở khâu dựng khung HTML ban đầu, viết CSS Grid/Flexbox responsive phức tạp và thiết lập liên kết các thư viện bên ngoài (Animate.css, AOS, Google Fonts). Thay vì tốn hàng giờ tra cứu cú pháp CDN và thuộc tính CSS, AI chỉ mất vài giây để tạo xong bộ khung hoàn chỉnh.

- **Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?**
  1. **Đưa ra ràng buộc kỹ thuật rõ ràng ngay từ đầu:** Cần chỉ định cụ thể các chuẩn mực kỹ thuật (như Semantic HTML, CSS Variables, cấu trúc thư mục) để AI không tự ý sinh code kém chất lượng hay lạm dụng thẻ `<div>`.
  2. **Tư duy tinh chỉnh từng bước (Iterative Prompting):** Không nên bắt AI làm toàn bộ website phức tạp trong một lệnh duy nhất. Chia nhỏ quy trình thành các bước: *Dựng khung Semantic -> Quản lý CSS Variables -> Thiết lập Layout Grid/Flexbox -> Tích hợp hiệu ứng/thư viện -> Debug lỗi*.
  3. **Làm chủ và sửa lỗi AI:** Đội ngũ phát triển (người đặt prompt) bắt buộc phải hiểu bản chất code để nhận biết sự cố (như thiếu lệnh khởi tạo JS của thư viện AOS) và đưa ra prompt debug chính xác.
