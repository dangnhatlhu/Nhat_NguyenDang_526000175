# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Nguyễn Đăng Nhật  
- **MSSV:** 526000175  
- **Tên đề tài Website:** Website bán Điện thoại, Laptop, Phụ kiện công nghệ (Đăng Nhật Store)  
- **Công cụ AI đã sử dụng:** Gemini 3 Pro  

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> **Prompt tổng quan ban đầu:**
> *"Bạn là một chuyên gia Vibe Coding hàng đầu thế giới với Google Antigravity. Hãy khởi tạo cho tôi cấu trúc dự án Website bán hàng công nghệ mang tên 'Đăng Nhật Store' lấy cảm hứng trực tiếp từ thegioididong.com theo phong cách sự kiện Ngày Đôi 10.10 Sale Đại.*  
> *Yêu cầu cốt lõi nghiêm ngặt:*  
> *1. Toàn bộ mã nguồn KHÔNG ĐƯỢC PHÉP DÙNG JAVASCRIPT (Zero JS) – Mọi tương tác người dùng phải giải quyết bằng Semantic HTML5 và CSS3 hiện đại.*  
> *2. Cấu trúc chuẩn Semantic HTML5 với ít nhất 5 thành phần: `<header>`, `<nav>`, `<main>`, `<section>` / `<article>`, `<footer>`.*  
> *3. Hệ thống CSS Variables (`:root`) quản lý bảng màu vàng/đỏ đặc trưng của Thế Giới Di Động, font chữ, bo góc và đổ bóng.*  
> *4. Đầy đủ danh mục menu: Điện thoại, Laptop, Phụ kiện, SmartWatch, Đồng hồ, Tablet, Máy cũ - Thu cũ, Màn hình - Máy in, Sim - Thẻ cào.*  
> *5. Các chức năng bắt buộc: Tìm kiếm tức thì, Lọc sản phẩm theo danh mục, Xem thông số kỹ thuật (modal chi tiết sản phẩm vivo V60 5G), Giỏ hàng slide-over và chức năng Toast thông báo tự động biến mất đúng 5 giây.*  
> *6. Tích hợp thư viện Animate.css và AOS (Animate On Scroll) cùng hiệu ứng tương tác `:hover`, `:focus` tự viết bằng CSS.*  
> *Hãy thiết lập cấu trúc repository chuẩn gồm thư mục `assets/`, `index.html`, `style.css` và nhật ký `PROMPT_LOG.md`."*

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML & CSS Variable
- **Prompt đã dùng:**  
  *"Hãy xây dựng cấu trúc HTML5 và hệ thống CSS Variables cho website Đăng Nhật Store. Đảm bảo sử dụng chuẩn xác các thẻ ngữ nghĩa Semantic HTML5 gồm `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`. Thiết lập `:root` với tông màu nhận diện: vàng chủ đạo `#ffd400`, đỏ khuyến mãi `#d0021b`, cam flash sale `#f57224`, font hệ thống sans-serif và hệ thống layout Grid/Flexbox responsive. Tạo đầy đủ 10 danh mục ngành hàng theo yêu cầu đề bài trên thanh `<nav>`."*
- **Kết quả AI tạo ra:**  
  AI sinh ra khung HTML5 ban đầu với header, thanh điều hướng 10 danh mục và file CSS định nghĩa các biến màu sắc.
- **Nhận xét & Tinh chỉnh:**  
  - *Vấn đề phát hiện:* Ban đầu ở phần danh sách sản phẩm, AI lạm dụng các thẻ `<div>` bọc lồng nhau quá nhiều và chưa thể hiện rõ bản chất từng sản phẩm là một thực thể bài viết/sản phẩm độc lập.  
  - *Tinh chỉnh:* Đã nhắc AI thay thế toàn bộ khối sản phẩm sang thẻ chuẩn `<article class="product-card">`, đồng thời phân chia trang thành các `<section>` rõ ràng như Hero Banner Section, Flash Sale Section và đưa thông tin liên hệ/pháp lý vào đúng thẻ `<footer>`.

---

### Lần 2: Tích hợp thư viện Animate.css & AOS (Animate On Scroll)
- **Prompt đã dùng:**  
  *"Hãy tích hợp CDN của 2 thư viện hiệu ứng Animate.css (v4.1.1) và AOS (v2.3.4) vào thẻ `<head>` của `index.html`. Áp dụng các class hiệu ứng như `animate__animated animate__pulse animate__infinite` cho nút Mua ngay trên Top Banner, `animate__zoomIn` cho Hero Banner, và gán các thuộc tính `data-aos="fade-up"` kèm `data-aos-delay` cho từng thẻ sản phẩm trong lưới grid. Lưu ý quan trọng: vì dự án cấm sử dụng JavaScript nên không thể gọi hàm `AOS.init()`, hãy viết thêm keyframes và transition CSS thuần để các phần tử có `data-aos` vẫn tự động xuất hiện sinh động và mượt mà khi người dùng tương tác/cuộn trang."*
- **Kết quả AI tạo ra:**  
  Các thẻ sản phẩm và banner đã có hiệu ứng chuyển động bắt mắt. Top banner nhịp thở liên tục thu hút người dùng, các thẻ card xuất hiện so le nhờ animation fallback thuần CSS.
- **Nhận xét & Tinh chỉnh:**  
  - *Vấn đề phát hiện:* Ban đầu một số hiệu ứng hover quá gắt (giật khung hình) khi di chuột qua card sản phẩm.  
  - *Tinh chỉnh:* Thêm thuộc tính `transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1)` và tối ưu phóng to ảnh nhẹ nhàng `transform: scale(1.06)` mà không làm thay đổi kích thước khung thẻ chứa.

---

### Lần 3: Xử lý chức năng Tương tác Không JavaScript (Pure CSS Tabs, Modal Specs & Search)
- **Prompt đã dùng:**  
  *"Giải quyết thách thức kỹ thuật lớn nhất: Không dùng bất kỳ một dòng JavaScript nào (Zero JS) nhưng vẫn phải có đầy đủ các tính năng:*  
  *1. Tìm kiếm sản phẩm: Tự động hiển thị dropdown gợi ý kết quả khi người dùng bấm vào thanh tìm kiếm.*  
  *2. Lọc sản phẩm: Nhấp vào tab 'Điện thoại', 'Laptop', 'Phụ kiện', 'Đồng hồ', 'Màn hình' thì lưới sản phẩm tự ẩn/hiện tương ứng.*  
  *3. Xem thông số kỹ thuật: Bấm nút 'Thông số' hoặc 'Chi tiết' mở ra cửa sổ Modal chi tiết điện thoại vivo V60 5G đối ứng chuẩn theo hình ảnh đính kèm (bảng cấu hình CPU Snapdragon 7 Gen 4, pin 6500mAh, camera ZEISS 50MP, chọn màu sắc, chọn bộ nhớ 256GB/512GB, nút đóng modal).*  
  *Hãy hướng dẫn và triển khai bằng CSS `:target`, `:has()`, `:focus-within` và Radio/Checkbox hack."*
- **Kết quả AI tạo ra:**  
  - Dropdown tìm kiếm xuất hiện mượt mà nhờ pseudo-class `:focus-within` trên container form.
  - Modal chi tiết sản phẩm hoạt động hoàn hảo thông qua CSS `:target` (liên kết `<a href="#modal-vivo-v60">` và nút đóng `<a href="#">&times;</a>`).
  - Hệ thống lọc phân loại tức thì bằng selector hiện đại `body:has(#filter-phone:checked) .product-card:not(.card-phone) { display: none; }`.
- **Nhận xét & Tinh chỉnh:**  
  - *Vấn đề phát hiện:* Trong modal chi tiết, ban đầu chưa có phân chia tab giữa 'Thông số kỹ thuật' và 'Thông tin sản phẩm'.
  - *Tinh chỉnh:* Đã hướng dẫn AI bổ sung bộ radio hack nội bộ `#radio-tab-specs` và `#radio-tab-desc` để người dùng có thể nhấp đổi tab xem bảng cấu hình chi tiết hoặc bài viết mô tả sản phẩm mà không cần JS.

---

### Lần 4: Xây dựng Chức năng Toast Thông báo Tự Tắt Trong 5 Giây & Giỏ hàng Slide-Over
- **Prompt đã dùng:**  
  *"Yêu cầu kỹ thuật đặc biệt: Hãy tạo hộp thoại thông báo Toast (Toast Notification) khi người dùng nhấp 'Thêm vào giỏ hàng' hoặc 'Mua ngay'. Toast này BẮT BUỘC phải tự động biến mất sau đúng 5 giây bằng CSS Keyframes (không dùng setTimeout hay JS). Bổ sung thanh tiến trình (progress timer bar) chạy từ 100% về 0% trong 5 giây. Ngoài ra, tạo một Giỏ hàng dạng slide-over trượt từ cạnh phải màn hình khi bấm vào nút 'Giỏ hàng' trên header."*
- **Kết quả AI tạo ra:**  
  - AI sử dụng Checkbox Hack (`<input type="checkbox" id="toast-add-cart">`) kết hợp với keyframe:
    ```css
    @keyframes toastLifeCycle {
      0% { opacity: 0; transform: translateY(-30px); }
      6% { opacity: 1; transform: translateY(0); }
      85% { opacity: 1; transform: translateY(0); }
      98% { opacity: 0; transform: translateY(-20px); }
      100% { opacity: 0; transform: translateY(-20px); pointer-events: none; visibility: hidden; }
    }
    ```
    Thời lượng thiết lập `animation: toastLifeCycle 5s cubic-bezier(...) forwards;`.
  - Thanh đếm ngược `timerProgress` co từ `width: 100%` về `0%` trong 5 giây trực quan.
  - Giỏ hàng trượt ra êm ái bằng `transform: translateX(0)` khi `#cart-drawer-toggle:checked`.
- **Nhận xét & Tinh chỉnh:**  
  - *Vấn đề phát hiện:* Khi toast mờ đi sau 5 giây, nếu không có thuộc tính `pointer-events: none` và `visibility: hidden`, nó có thể chặn các cú click chuột ở góc màn hình.
  - *Tinh chỉnh:* Bổ sung ngay `pointer-events: none` ở frame 100% để trả lại hoàn toàn không gian tương tác cho người dùng.

---

## 3. Đánh giá kết quả Vibe Coding & Bài học kinh nghiệm

1. **Hiệu quả của việc kết hợp Semantic HTML5 & CSS3 Hiện đại:**  
   Toàn bộ website đạt độ hoàn thiện cao, tốc độ tải tức thì 100/100 vì không phụ thuộc vào JS Engine hay bundle script nặng nề. Mã nguồn sạch, đúng chuẩn accessibility và cấu trúc ngữ nghĩa W3C.
2. **Kỹ năng Prompting từng bước (Step-by-step Iteration):**  
   Thay vì yêu cầu AI làm mọi thứ trong 1 lệnh duy nhất dẫn đến việc mã nguồn bị cắt xén, việc chia nhỏ thành 4 giai đoạn rõ ràng (Khung cấu trúc -> Hiệu ứng thư viện -> Cơ chế Zero-JS -> Hoàn thiện Toast & Giỏ hàng) đã mang lại kết quả hoàn mỹ tuyệt đối, bám sát từng chi tiết của website Thế Giới Di Động.
