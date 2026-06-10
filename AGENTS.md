# 🤖 VibeSpace Studio - AI Agent Development Guidelines (AGENTS.md)

Chào mừng bạn, AI Coding Agent, đến với dự án **VibeSpace Studio**. Tài liệu này được thiết kế riêng để cung cấp bối cảnh kỹ thuật, các nguyên tắc bắt buộc, và quy trình phát triển nhằm đảm bảo tính nhất quán 100% khi bạn tham gia lập trình và bảo trì dự án này.

---

## 1. 🌌 Tổng quan dự án (Project Overview)

*   **Tên dự án:** VibeSpace Studio (Focus Station & Healing Sound Dashboard)
*   **Mô tả:** Không gian làm việc và âm thanh chữa lành cá nhân hóa tối giản và thẩm mỹ (Aesthetic Glassmorphism & Cyberpunk-dark) dành cho Lập trình viên, Nhà thiết kế, Nhà văn và Học sinh.
*   **Trạng thái hiện tại:** `Development` (Khởi tạo dự án & Phát triển MVP).
*   **Repository gốc:** [vibe-space](file:///Users/thanhdo/Documents/Project/vibe-space) / [GitHub Repo](https://github.com/thanhmati/vibespace-studio).

---

## 2. 🛠️ Stack công nghệ (Tech Stack)

Khi phát triển dự án này, bạn **BẮT BUỘC** phải tuân thủ và sử dụng đúng các công nghệ sau:

| Layer | Công nghệ sử dụng | Lưu ý triển khai |
| :--- | :--- | :--- |
| **Framework & Build** | ReactJS v18+ (Vite) | Không sử dụng Next.js trừ khi có yêu cầu đặc biệt. |
| **Ngôn ngữ** | TypeScript | Cấu hình `strict: true`. Tuyệt đối không dùng `any`. |
| **CSS & Giao diện** | Tailwind CSS | Styling tùy biến với cấu hình Glassmorphic (backdrop-blur, border-white/10). |
| **BaaS (Backend)** | Supabase | Auth, Database (PostgreSQL) và Real-time Sync. |
| **Quản lý Route** | React Router v7 | Hỗ trợ Nested Routing và Auth Guards. |
| **State Management** | Zustand | Nhẹ, hiệu năng cao, tối ưu hóa re-render tốt hơn Redux. |
| **Audio Processing** | Vanilla HTML5 Audio | Tích hợp thông qua Singleton Audio Manager tự viết. |

---

## 3. 📐 Quy ước lập trình & Quy tắc viết Code (Coding Conventions)

### 3.1. TypeScript & Type Safety
*   Luôn bật `strict: true` trong `tsconfig.json`.
*   **Không sử dụng `any`:** Sử dụng `unknown` nếu không xác định được kiểu dữ liệu, hoặc định nghĩa Type/Interface rõ ràng.
*   Luôn khai báo kiểu trả về cho các hàm (đặc biệt là API calls và custom hooks).
*   Sử dụng TypeScript `enum` hoặc `union type` cho các trạng thái cố định (ví dụ: `ThemeMode = 'cozy-room' | 'rainy-window' | 'space-dark'`).

### 3.2. Quy ước đặt tên (Naming Conventions)
*   **Component & Page:** PascalCase (ví dụ: `AudioMixer.tsx`, `PomodoroTimer.tsx`).
*   **Hook:** camelCase và có tiền tố `use` (ví dụ: `useAutosaveNote.ts`).
*   **Helper / Service:** camelCase (ví dụ: `audioManager.ts`, `supabaseClient.ts`).
*   **Database Table & Column:** snake_case (ví dụ: `audio_presets`, `volume_config`).
*   **TypeScript Interface/Type:** PascalCase (ví dụ: `AudioPreset`, `VolumeConfig`).

### 3.3. Cấu trúc Import & Module Alias
*   Sử dụng module alias `@/` thay vì path tương đối dài (`../../components`).
*   Thứ tự import chuẩn:
    1. React core & external libraries (Zustand, React Router, v.v.).
    2. Components của dự án.
    3. Hooks, Services, Utilities.
    4. Types & Interfaces.
    5. CSS/Asset files.

---

## 4. 🚨 Các quy tắc bất di bất dịch (Critical Rules)

> [!CAUTION]
> **Quy tắc 1: Quản lý Audio Engine ngoài React Lifecycle**
> *   **Cấm:** Khởi tạo hoặc lưu đối tượng `HTMLAudioElement` trực tiếp trong component state (`useState`). Điều này gây re-render liên tục khi thay đổi volume và gây rò rỉ bộ nhớ.
> *   **Giải pháp:** Mọi track âm thanh phải được quản lý tập trung bởi [AudioManager](file:///Users/thanhdo/Documents/Project/vibe-space/TECH_SPECS.md#L159-L215) (Singleton Class).
> *   **Volume Control:** Sử dụng uncontrolled slider với `useRef` và gọi hàm trực tiếp `audioManager.setVolume(trackId, value)` từ sự kiện `onChange`.

> [!WARNING]
> **Quy tắc 2: Tối ưu hóa Lưu lượng & Đồng bộ Dữ liệu**
> *   **Cấm:** Lưu trực tiếp dữ liệu ghi chú lên Database sau mỗi ký tự gõ phím.
> *   **Giải pháp:** Sử dụng cơ chế trì hoãn (Debounce 2 giây) bằng Custom Hook `useAutosaveNote` kết hợp lưu tạm thời vào `localStorage` ở Client để đảm bảo tốc độ phản hồi UI lập tức và bảo vệ API Supabase.

> [!IMPORTANT]
> **Quy tắc 3: Xử lý bảo mật Row Level Security (RLS) của Supabase**
> *   Mọi truy vấn dữ liệu từ Client tới Supabase phải gắn liền với User Session hiện tại thông qua `auth.uid()`.
> *   Tuyệt đối không sử dụng `service_role` key ở Client. Chỉ sử dụng `anon_key` công khai.

---

## 5. 🔑 Biến môi trường (Environment Variables)

Dự án sử dụng các biến môi trường để cấu hình kết nối tới Supabase. Mọi biến môi trường dành cho client chạy trên Vite phải bắt đầu bằng tiền tố `VITE_`.

### 5.1. File cấu hình `.env.example`
Tạo file `.env.local` tại thư mục gốc với các khóa sau:

```bash
# Supabase Configuration
VITE_SUPABASE_URL=https://your-supabase-project-id.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

### 5.2. Cách đọc biến môi trường trong code
```typescript
const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

if (!supabaseUrl || !supabaseAnonKey) {
  throw new Error("Missing Supabase environment variables.");
}
```

---

## 6. 🔄 Trạng thái & Luồng dữ liệu (State Management & Data Flow)

Dữ liệu của ứng dụng được chia làm 2 tầng rõ rệt:

```
[Local State / localStorage]   ◄──►   [Zustand Store (Client)]   ◄──►   [Supabase Database (Cloud)]
- Tiết kiệm băng thông               - Giao diện đồng bộ cực nhanh      - Lưu trữ lâu dài
- Chạy offline mượt mà               - Dùng cho Timer, Preset đang phát  - Bảo mật qua RLS
```

### 6.1. Quản lý State bằng Zustand Store
*   **Trạng thái Layout & Tiện ích:** Quản lý việc ẩn/hiện các Widget (Pomodoro, Todo, Notepad).
*   **Trạng thái Audio Mixer:** Lưu trữ danh sách track đang phát và mức âm lượng hiện tại.
*   **Trạng thái Pomodoro:** Lưu chu kỳ Pomodoro hiện tại, thời gian đếm ngược còn lại để đồng bộ âm thanh thông báo.

### 6.2. Đồng bộ hóa Local-to-Cloud (Optimistic UI)
Khi có sự thay đổi dữ liệu từ phía người dùng (VD: Thêm task, hoàn thành task, đổi theme):
1.  **Bước 1 (Optimistic Update):** Cập nhật ngay lập tức giao diện người dùng (Zustand State) để tạo cảm giác mượt mà tức thì (Zero-latency).
2.  **Bước 2 (Local Storage Backup):** Ghi đè nhanh cấu hình vào `localStorage`.
3.  **Bước 3 (Background Sync):** Thực hiện cuộc gọi API không đồng bộ (Asynchronous call) lên Supabase Database để lưu trữ vĩnh viễn. Nếu cuộc gọi lỗi, tiến hành khôi phục lại trạng thái cũ (Rollback) và hiển thị thông báo lỗi nhẹ ở góc màn hình.

---

Hãy luôn đối chiếu mã nguồn của bạn viết với tài liệu [PRD](file:///Users/thanhdo/Documents/Project/vibe-space/PRD.md) và [Tech Specs](file:///Users/thanhdo/Documents/Project/vibe-space/TECH_SPECS.md) để đảm bảo chất lượng kỹ thuật cao nhất cho dự án **VibeSpace Studio**!
