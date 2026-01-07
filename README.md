# E-Learning Frontend (Fladev LMS) ✅

**Overview:** Đây là giao diện frontend của một hệ thống E-Learning (LMS) được xây dựng bằng **React + Vite**, sử dụng **Tailwind CSS**, **Ant Design**, **Redux Toolkit** và kết nối tới một backend .NET qua API REST.

---

## 🚀 Tính năng chính

- Danh sách khóa học, trang chi tiết khóa học và trang học (course learning)
- Giỏ hàng (Cart), Thanh toán (hỗ trợ MoMo / ZaloPay thông qua backend)
- Quản lý người dùng / dashboard cho Admin
- Bài viết (Blog), Bình luận / Đánh giá (Reviews)
- Quản lý đơn hàng, voucher, liên hệ, thông báo
- Tải lên media (ảnh, video) và theo dõi tiến độ học tập (Progress)
- Xác thực người dùng (login/register), lưu token trong localStorage

---

## 🧰 Công nghệ & Thư viện chính

- Vite
- React 18
- Tailwind CSS
- Ant Design (antd)
- Redux Toolkit + react-redux
- react-router-dom
- Axios (wrapper trong `src/apis/api.js`)
- react-quill / quill (rich text)
- react-player (video)
- socket.io-client (tùy cấu hình backend)

---

## ⚙️ Cài đặt & Chạy (Local)

Yêu cầu:

- Node.js (>= 16/18 recommended)
- npm / yarn / pnpm

1. Clone repository

```bash
git clone <repo-url>
cd e-learning-frontend
```

2. Cài dependencies

```bash
npm install
# hoặc
# yarn
```

3. Chạy development server

```bash
npm run dev
```

Mặc định Vite dev server chạy ở cổng 3000 (cấu hình trong `vite.config.js`). Proxy `/api` được thiết lập tới backend (xem `vite.config.js`).

4. Build cho production

```bash
npm run build
npm run preview   # kiểm tra bản build cục bộ
```

5. Lint

```bash
npm run lint
```

---

## 🧩 Biến môi trường (env)

File client sẽ đọc giá trị sau (nếu có):

- `REACT_APP_API_BASE_URL` — (tuỳ chọn) URL gốc của API (ví dụ `https://api.example.com/api`). Nếu không đặt, client sẽ fallback sang `/api` và sử dụng proxy dev trong `vite.config.js`.
- `BUILD_MODE` — (sử dụng trong scripts) `dev` | `production` (được set bằng `cross-env` trong scripts).

Lưu ý bảo mật: không commit các file chứa secrets (xem `SECURITY_SETUP.md`). Các khoá thanh toán (MoMo, ZaloPay), Cloudinary, DB connection nên đặt ở backend/secret manager.

---

## 🗂 Cấu trúc thư mục (tóm tắt)

- `src/` - mã nguồn frontend
  - `apis/` - axios instance và các endpoint
  - `components/` - các component UI tái sử dụng
  - `hooks/` - custom hooks
  - `pages/` - các trang (Admin, Auth, Courses, Blog, ...)
  - `redux/` - store & slices
  - `utils/` - constants, helpers
- `public/` - static assets
- `vite.config.js`, `package.json`, `tailwind.config.js`

---

## 🔧 Lưu ý phát triển

- `src/apis/api.js` tạo instance axios; interceptor sẽ tự động thêm header `Authorization: Bearer <token>` nếu có `localStorage.token` và endpoint yêu cầu xác thực.
- `src/utils/constants.js` chứa `API_ROOT` mặc định (hiện đang set tới một URL cụ thể). Bạn có thể thay đổi bằng biến env hoặc cấu hình proxy dev.
- Để phát triển tính năng thanh toán / callback, đảm bảo `REACT_APP_API_BASE_URL` trỏ tới backend phù hợp hoặc cập nhật `notifyUrl` tương ứng trong backend.

---

## 📦 Triển khai (Deployment)

- Repo chứa `vercel.json` để deploy tĩnh (rewrite tất cả về `/`).
- Trước khi deploy, cẩn thận cấu hình biến môi trường production (API base URL, keys) trong môi trường hosting (Vercel, Netlify, Azure, ...).

---
