# 🎓 ONLINE COURSE MANAGEMENT SYSTEM - Frontend

**Ứng dụng Frontend của hệ thống quản lý khóa học trực tuyến toàn diện**

---

## 📌 Giới thiệu

Đây là phần giao diện người dùng (Frontend) của **Online Course Management System** - một nền tảng quản lý khóa học trực tuyến hiện đại. Hệ thống được xây dựng với kiến trúc **Decoupled Architecture**, giao tiếp với Backend thông qua **RESTful API**.

**Tính năng chính:**
- 📚 Quản lý khóa học trực tuyến
- 👥 Quản lý người dùng (Admin, Giáo viên, Học viên)
- 📝 Hệ thống bài giảng và trắc nghiệm
- 💳 Xử lý thanh toán và ghi danh khóa học
- 📊 Theo dõi tiến độ học tập
- 🔐 Xác thực và phân quyền người dùng

---

## 🛠 Công nghệ sử dụng

| Công nghệ | Phiên bản | Mục đích |
|:---|:---|:---|
| **Vue.js** | 3.x | Framework Frontend chính |
| **Vite** | - | Build tool & Dev server |
| **Vue Router** | 4.x | Routing và Navigation |
| **Pinia** | - | State Management |
| **Axios** | - | HTTP Client |
| **Bootstrap / Tailwind CSS** | - | Styling & Responsive Design |
| **Node.js** | 14+ | Runtime Environment |

---

## 📦 Cài đặt và Chạy

### 1. Yêu cầu hệ thống
- **Node.js:** v14 trở lên
- **npm:** v6 trở lên hoặc **yarn**
- **Git:** để clone repository

### 2. Clone repository
```bash
git clone <URL-repo-frontend>
cd FE_20
```

### 3. Cài đặt dependencies
```bash
npm install
```

### 4. Cấu hình biến môi trường

Tạo file `.env` trong thư mục gốc dự án:
```env
VITE_API_URL=http://localhost:8000/api
VITE_BASE_URL=http://localhost:5173
```

### 5. Chạy development server
```bash
npm run dev
```

Ứng dụng sẽ khả dụng tại: **http://localhost:5173**

### 6. Build cho production
```bash
npm run build
```

---

## 📁 Cấu trúc thư mục

```
FE_20/
├── public/                 # Tài nguyên tĩnh
├── src/
│   ├── assets/            # CSS, JS, Fonts, Images
│   ├── components/        # Vue Components
│   │   ├── Admin/        # Các component Admin
│   │   ├── Client/       # Các component Client
│   │   └── KhachHang/    # Các component Khách hàng
│   ├── layout/           # Layout Components
│   ├── router/           # Vue Router Configuration
│   ├── App.vue           # Root Component
│   ├── main.js           # Entry point
│   └── style.css         # Global styles
├── index.html            # HTML chính
├── vite.config.js        # Vite Configuration
├── package.json          # Dependencies & Scripts
└── README.md             # File này
```

---

## 🚀 Các lệnh hữu ích

| Lệnh | Mô tả |
|:---|:---|
| `npm run dev` | Chạy development server |
| `npm run build` | Build cho production |
| `npm run preview` | Xem preview build production |
| `npm run lint` | Check code quality (nếu có) |

---

## 🔑 Các Tính năng Chính

### 👨‍💼 Quản lý Admin
- Dashboard thống kê
- Quản lý khóa học
- Quản lý người dùng (Giáo viên, Học viên)
- Quản lý bài viết và bài giảng
- Quản lý trắc nghiệm
- Báo cáo và Analytics

### 👨‍🎓 Giao diện Học viên
- Duyệt danh sách khóa học
- Ghi danh khóa học
- Xem bài giảng video
- Làm bài trắc nghiệm
- Theo dõi tiến độ học tập
- Quản lý hồ sơ cá nhân

### 👨‍🏫 Giao diện Giáo viên
- Quản lý khóa học của mình
- Tạo bài giảng
- Quản lý bài trắc nghiệm
- Theo dõi tiến độ học viên

---

## 🔐 Xác thực và Phân quyền

Hệ thống sử dụng **JWT Token** để xác thực người dùng:

- **Admin:** Toàn quyền quản lý hệ thống
- **Giáo viên:** Quản lý khóa học và bài giảng của mình
- **Học viên:** Truy cập khóa học đã ghi danh

---

## 📝 API Integration

Frontend giao tiếp với Backend thông qua Axios. Các endpoint API cần thiết:

**Authentication:**
- `POST /api/login` - Đăng nhập
- `POST /api/register` - Đăng ký
- `POST /api/logout` - Đăng xuất

**Courses:**
- `GET /api/courses` - Lấy danh sách khóa học
- `GET /api/courses/:id` - Chi tiết khóa học
- `POST /api/courses/:id/enroll` - Ghi danh khóa học

**Users:**
- `GET /api/users/profile` - Thông tin người dùng
- `PUT /api/users/profile` - Cập nhật hồ sơ
- `POST /api/users/change-password` - Đổi mật khẩu

---

## 🐛 Troubleshooting

### 1. Lỗi kết nối API
- Kiểm tra Backend đang chạy tại cổng chính xác
- Verify `VITE_API_URL` trong file `.env`
- Kiểm tra CORS settings trên Backend

### 2. Lỗi Module không tìm thấy
```bash
npm install
rm -rf node_modules package-lock.json
npm install

### 3. Port 5173 đã được sử dụng
```bash
npm run dev -- --port 3000

---

## 📚 Tài liệu tham khảo

- [Vue 3 Documentation](https://vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
- [Vue Router](https://router.vuejs.org/)
- [Pinia](https://pinia.vuejs.org/)
- [Axios](https://axios-http.com/)

---

## 📄 License

Project này được sử dụng cho mục đích giáo dục.

---

**Phiên bản:** 1.0.0  
**Cập nhật lần cuối:** 2025  
**Tác giả:** [Võ Hưng Tĩnh]

---

