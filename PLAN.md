# 🗺️ VibeSpace Studio - Development Plan (PLAN.md)

Tài liệu này là **Checklist Tiến độ Động** của dự án **VibeSpace Studio**. Mỗi khi bắt đầu thực hiện một nhiệm vụ, AI Coding Agent cần cập nhật trạng thái tương ứng:
*   `- [ ]` : Chưa bắt đầu (Not Started)
*   `- [/]` : Đang thực hiện (In Progress)
*   `- [x]` : Đã hoàn thành và xác minh (Completed & Verified)

---

## 📊 Tổng quan Tiến trình (Progress Dashboard)

| Giai đoạn (Phase) | Nội dung công việc | Tiến độ (Progress) |
| :--- | :--- | :--- |
| **Phase 1** | Khởi động & Tài liệu đặc tả đặc tính | 100% (Completed) |
| **Phase 2** | Thiết lập môi trường & Khung xương dự án | 0% (Not Started) |
| **Phase 3** | Phát triển Giao diện lõi & Tiện ích Tĩnh (MVP UI) | 0% (Not Started) |
| **Phase 4** | Tích hợp Supabase & Luồng đồng bộ Đám mây (Cloud Sync) | 0% (Not Started) |
| **Phase 5** | Tối ưu hóa hiệu năng, Đánh bóng & Triển khai (Polish & Deploy) | 0% (Not Started) |

---

## 🛠️ Danh sách chi tiết các công việc (Checklist)

### 📌 Phase 1: Project Initiation & Specifications (Khởi động & Đặc tả)
*Mục tiêu: Thiết lập tài liệu nền tảng và chuẩn bị không gian làm việc.*

- [x] Phân tích yêu cầu và viết tài liệu **[PRD.md](file:///Users/thanhdo/Documents/Project/vibe-space/PRD.md)**.
- [x] Thiết kế kiến trúc dữ liệu và giải pháp kỹ thuật **[TECH_SPECS.md](file:///Users/thanhdo/Documents/Project/vibe-space/TECH_SPECS.md)**.
- [x] Tạo tài liệu phát triển dành cho Agent **[AGENTS.md](file:///Users/thanhdo/Documents/Project/vibe-space/AGENTS.md)**.
- [x] Tạo tài liệu kiến trúc cấu trúc hệ thống **[ARCHITECTURE.md](file:///Users/thanhdo/Documents/Project/vibe-space/ARCHITECTURE.md)**.
- [x] Khởi tạo Git Repository trên GitHub: `https://github.com/thanhmati/vibespace-studio`.
- [x] Viết file `.gitignore` tiêu chuẩn cho dự án NodeJS/Vite.

---

### 📌 Phase 2: Environment Setup & Scaffolding (Thiết lập & Khung dự án)
*Mục tiêu: Cấu hình khung xương mã nguồn, các thư viện dùng chung và thiết kế hệ thống CSS tokens.*

- [ ] Khởi tạo dự án React + TypeScript sử dụng công cụ build **Vite**.
- [ ] Cấu hình Tailwind CSS và khai báo các mã màu Glassmorphism đặc thù trong `tailwind.config.js`.
- [ ] Cài đặt các gói thư viện cốt lõi: `react-router-dom@7`, `zustand`, `@supabase/supabase-js`, `lucide-react`, `lodash` (for debounce).
- [ ] Thiết lập Module Alias `@/` trong `tsconfig.json` và `vite.config.ts`.
- [ ] Xây dựng cấu trúc thư mục chuẩn theo đặc tả trong `ARCHITECTURE.md`.
- [ ] Tạo file cấu hình môi trường mẫu `.env.example` và `.env.local`.

---

### 📌 Phase 3: Core UI & Static Widgets (Giao diện lõi & Tiện ích Tĩnh)
*Mục tiêu: Xây dựng các components, widgets chạy offline (local) và kiểm soát hoàn hảo phần Audio.*

- [ ] Phát triển component `VideoBackground` hỗ trợ phát video lặp mượt mà không ngốn tài nguyên.
- [ ] Viết Singleton Class `AudioManager` để phát và kiểm soát nhiều track âm thanh song song bằng JavaScript thuần.
- [ ] Xây dựng widget `AudioMixer` với các thanh trượt `AudioSlider` (sử dụng uncontrolled inputs + refs).
- [ ] Phát triển widget `PomodoroTimer` kiểm soát thời gian đếm ngược (Focus/Break) và hỗ trợ âm báo khi kết thúc.
- [ ] Phát triển widget `TodoList` cho phép thêm, xóa, check hoàn thành các tasks lưu trữ tạm thời qua `localStorage`.
- [ ] Phát triển widget `ZenNotepad` tối giản hỗ trợ đếm số từ và lưu trữ nháp cục bộ.
- [ ] Thiết kế bố cục lưới Grid chung cho Dashboard có khả năng ẩn/hiện widget tùy chỉnh.

---

### 📌 Phase 4: Database Integration & Cloud Sync (Tích hợp Supabase & Đồng bộ)
*Mục tiêu: Đưa dữ liệu lên đám mây, xử lý xác thực người dùng và đồng bộ trạng thái thời gian thực.*

- [ ] Viết file khởi tạo client kết nối Supabase `src/lib/supabaseClient.ts`.
- [ ] Chạy các migration script để cấu hình tables, triggers và chính sách RLS trên Supabase.
- [ ] Phát triển các trang Đăng nhập / Đăng ký (`AuthPage`) tích hợp Supabase Auth.
- [ ] Viết Route Guard `AuthGuard` để kiểm soát các route được bảo vệ.
- [ ] Triển khai hook Custom `useAutosaveNote` áp dụng cơ chế Debounce 2 giây để đồng bộ tự động notepad lên Supabase.
- [ ] Đồng bộ hóa trạng thái Widget Grid và Theme cài đặt của người dùng dựa theo bảng `profiles`.
- [ ] Liên kết danh sách Todo (`TodoList`) và lịch sử phiên tập trung (`pomodoro_sessions`) với Supabase API.

---

### 📌 Phase 5: Polish, Optimization & Deployment (Đánh bóng, Tối ưu & Triển khai)
*Mục tiêu: Tối ưu hiệu năng rendering, cải thiện UX/UI và đưa ứng dụng lên môi trường production.*

- [ ] Thực hiện tối ưu hóa hiệu năng render: Bật hardware acceleration cho canvas/video nền, sử dụng `CSS will-change`.
- [ ] Kiểm tra tính thích ứng giao diện (Responsive Design) trên mọi loại kích thước màn hình (Mobile, Tablet, Desktop).
- [ ] Thêm các hiệu ứng micro-animations, hover effects mượt mà và âm thanh nhỏ khi hoàn thành Task/Pomodoro.
- [ ] Thiết lập chạy thử nghiệm quy trình build production cục bộ (`npm run build`) để kiểm tra lỗi TypeScript/Linter.
- [ ] Triển khai ứng dụng lên nền tảng đám mây (Vercel hoặc Netlify) tích hợp deploy tự động qua GitHub Actions.
- [ ] Xác minh và bàn giao hệ thống, viết tài liệu hướng dẫn vận hành cuối cùng `README.md`.
