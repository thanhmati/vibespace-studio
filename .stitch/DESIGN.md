# Design System: vibespace-studio (Cyber-Zen)
**Project ID:** 10170342307040932036

---

## 1. Visual Theme & Atmosphere

*   **Aesthetic Theme:** **Cyber-Zen** (A blending of dark cybernetic neon aesthetics and cozy, minimalist zen spaces).
*   **Atmosphere:** Deeply immersive, calm, and sleek. Giao diện tối mờ ảo (dark-cyberpunk) giúp giảm mỏi mắt kết hợp với các hiệu ứng kính mờ (glassmorphism) tinh tế nhằm tạo chiều sâu thị giác.
*   **Materiality:** Toàn bộ bảng điều khiển widget sử dụng cấu trúc **Frosted Glass (Kính mờ)** xếp chồng lên lớp nền động (Video background). Các cạnh viền siêu nhỏ và tinh xảo giúp giao diện có cảm giác như một mặt kính lơ lửng trên không gian vũ trụ.

---

## 2. Color Palette & Roles

Hệ thống màu sắc Cyber-Zen sử dụng các mã màu có độ tương phản cao trên nền tối, đại diện cho cả yếu tố công nghệ (Cyber) và sự bình yên, ấm áp (Zen):

| Tên màu thiết kế (Descriptive Name) | Mã Hex (Hex Code) | Vai trò chức năng (Functional Role) |
| :--- | :--- | :--- |
| **Primary Cyber Dark (Deep Space)** | `#0B0F19` | Màu nền gốc của trang, màu lấp các container đặc và vùng tối chính. |
| **Translucent Glass Background** | `rgba(255, 255, 255, 0.05)` | Lớp kính mờ nền cho tất cả thẻ Widgets và Popovers. |
| **Glass Border (White Whispers)** | `rgba(255, 255, 255, 0.10)` | Đường viền siêu nhỏ (1px) tạo hiệu ứng phản chiếu ánh sáng cho thẻ kính. |
| **Cyber Neon Cyan (Teal Glow)** | `#00F2FE` | Màu nhấn chính. Dùng cho trạng thái hoạt động (Active), liên kết (Links), và viền sáng (Glow). |
| **Zen Cozy Amber (Campfire Orange)** | `#F59E0B` | Màu nhấn phụ ấm áp. Dùng cho đồng hồ Pomodoro lúc nghỉ ngơi (Break) và chỉ số thư giãn. |
| **Zen Warm Rose (Campfire Fire)** | `#EF4444` | Màu cảnh báo, nút dừng, hoặc thời gian Focus Pomodoro cần tập trung cao độ. |
| **Bright White (Primary Text)** | `#F3F4F6` | Văn bản chính, tiêu đề, và các văn bản có độ tương phản cao. |
| **Soft Muted Gray (Secondary Text)** | `#9CA3AF` | Văn bản phụ, nhãn (labels), và gợi ý ẩn (placeholders). |

---

## 3. Typography Rules

*   **Primary Font Family:** **Inter** hoặc **Outfit** (Font chữ không chân hiện đại, sạch sẽ và tối giản).
*   **Headers (Tiêu đề):** Sử dụng font `Outfit` hoặc `Inter` với độ dày Medium/Semibold (`font-medium` / `font-semibold`), khoảng cách chữ hơi rộng (`tracking-wide`) để tạo cảm giác thoáng đãng của không gian Zen.
*   **Body (Văn bản thường):** Sử dụng font `Inter` với độ dày Light/Regular (`font-light` / `font-normal`), khoảng cách dòng rộng rãi (`leading-relaxed`) giúp dễ đọc.
*   **Numerical/Timer Display (Đồng hồ số):** Sử dụng font chữ Monospace như **JetBrains Mono** hoặc **DM Mono** để các chữ số không bị dịch chuyển bề ngang (width jitter) khi đếm ngược thời gian.

---

## 4. Component Stylings

### 🔘 Buttons (Nút bấm)
*   **Primary Action Button:** Dạng kẹp thuốc viên (Pill-shaped - `rounded-full`), nền Cyber Neon Cyan (`#00F2FE`), chữ Primary Cyber Dark (`#0B0B19`), hiệu ứng đổi màu mượt mà kèm hiệu ứng bóng sáng neon dịu (`shadow-[0_0_15px_rgba(0,242,254,0.3)]`) khi hover.
*   **Secondary Glass Button:** Bo góc nhẹ (`rounded-lg`), không nền (transparent), viền Glass Border (`rgba(255,255,255,0.1)`), chữ trắng sáng (`#F3F4F6`), khi di chuột hover đổi sang nền `rgba(255,255,255,0.1)`.

### 🎴 Cards/Containers (Thẻ chứa Widgets)
*   **General Widget Card:** Bo góc bo tròn rộng (`rounded-2xl` - 16px), nền Translucent Glass (`rgba(255,255,255,0.05)`), hiệu ứng mờ nền (`backdrop-blur-md` - 12px), viền microscopic `border-white/10`, đổ bóng sâu mềm mại (`shadow-2xl`).

### 📝 Inputs/Forms (Ô nhập liệu)
*   **Text Input Field:** Bo góc tinh tế (`rounded-lg` - 8px), nền tối đen bán trong suốt (`rgba(0,0,0,0.3)`), viền Glass Border (`rgba(255,255,255,0.1)`), chữ trắng (`#F3F4F6`). Khi focus chuyển đổi viền sang màu Cyber Neon Cyan (`#00F2FE`) và có vòng sáng nhẹ xung quanh.

---

## 5. Layout Principles

*   **Whitespace Strategy:** Sử dụng khoảng trống thông thoáng làm chủ đạo. Khoảng cách giữa các widgets tối thiểu là `gap-6` (24px) trên desktop để tránh cảm giác ngột ngạt.
*   **Widget Grid:** Bố trí theo CSS Grid hoặc Flexbox linh hoạt. Widgets có thể ẩn/hiện tự do, khi ẩn đi thì các widgets còn lại tự động điều chỉnh vị trí để giữ sự cân bằng thị giác.
*   **Focus Priority:** Đồng hồ Pomodoro được đặt ở vị trí trung tâm hoặc có kích thước lớn nổi bật, các widget phụ trợ như Todo và Notepad bao quanh với kích thước nhỏ hơn.
