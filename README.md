# 📚 App Đọc Truyện – Android

> Ứng dụng đọc truyện trên Android được xây dựng bằng Java, tích hợp SQLite để lưu trữ dữ liệu nội bộ, hỗ trợ phân quyền người dùng và quản trị viên.

---

## 📌 Giới Thiệu

Dự án Android native thể hiện khả năng xây dựng ứng dụng di động hoàn chỉnh với đầy đủ luồng người dùng: từ đăng ký, đăng nhập, đọc truyện, đánh giá, yêu thích cho đến quản trị nội dung (Admin).

---

## 🛠️ Công Nghệ Sử Dụng

| Thành phần | Công nghệ |
|---|---|
| Ngôn ngữ | Java |
| Nền tảng | Android (API 21+) |
| Cơ sở dữ liệu | SQLite (local) |
| Load ảnh | Picasso |
| UI Navigation | BottomNavigationView + SNavigationDrawer |
| Danh sách | RecyclerView (GridLayout, LinearLayout) |
| Hiệu ứng banner | ViewFlipper + Animation |
| IDE | Android Studio |

---

## ✨ Tính Năng

### 👤 Người Dùng
- 🔐 **Đăng ký / Đăng nhập / Đăng xuất** — xác thực bằng SQLite
- 🏠 **Màn hình chính** — banner quảng cáo tự động (ViewFlipper), danh sách truyện mới & nổi bật
- 📖 **Xem nội dung truyện** — cuộn nội dung dài với ScrollingMovementMethod
- 🔍 **Tìm kiếm truyện** — lọc theo tên theo thời gian thực (TextWatcher)
- ❤️ **Yêu thích** — lưu và xem danh sách truyện yêu thích (GridLayout 2 cột)
- 📋 **Tất cả truyện** — duyệt toàn bộ danh sách
- ⭐ **Đánh giá truyện** — viết và xem đánh giá
- 📧 **Chia sẻ qua Email** — gửi truyện bằng Intent email
- ℹ️ **Thông tin ứng dụng** — giới thiệu nhóm phát triển

### 🛡️ Quản Trị Viên (Admin – Phân quyền 2)
- ➕ **Đăng bài** — thêm truyện mới (tiêu đề, nội dung, ảnh URL)
- ✏️ **Cập nhật truyện** — chỉnh sửa thông tin truyện đã đăng
- 🗑️ **Xóa truyện** — xóa qua Dialog xác nhận

---

## 🗃️ Cơ Sở Dữ Liệu (SQLite)

| Bảng | Mô tả |
|---|---|
| `TaiKhoan` | Tài khoản người dùng (tên, mật khẩu, email, phân quyền) |
| `Truyen` | Truyện (tên, nội dung, ảnh, id tài khoản) |
| `DanhGia` | Đánh giá truyện (nội dung, tên tài khoản, tên truyện) |
| `YeuThich` | Danh sách truyện yêu thích theo tài khoản |

---

## 📁 Cấu Trúc Dự Án

```
appdoctruyen_v2/
├── adapter/
│   ├── adapterTruyen.java          # Adapter danh sách truyện (tìm kiếm, tất cả)
│   ├── adapterTruyenV2.java        # Adapter dạng lưới (trang chủ)
│   ├── adapterTruyenYeuThich.java  # Adapter yêu thích (long-click để bỏ yêu thích)
│   ├── adapterDangBai.java         # Adapter Admin (xóa, cập nhật)
│   ├── DanhGiaAdapter.java         # Adapter danh sách đánh giá
│   ├── adapterchuyenmuc.java       # Adapter chuyên mục
│   ├── adapterthongtin.java        # Adapter thông tin tài khoản
│   └── ViewPagerAdapter.java       # Adapter ViewPager (Home + Account)
│
├── database/
│   └── databasedoctruyen.java      # SQLiteOpenHelper – toàn bộ CRUD
│
├── model/
│   ├── Truyen.java                 # Model truyện
│   ├── TaiKhoan.java               # Model tài khoản
│   ├── DanhGia.java                # Model đánh giá
│   ├── chuyenmuc.java              # Model chuyên mục
│   └── main/
│       ├── MainAdmin.java          # Màn hình quản trị
│       ├── MainWait.java           # Splash screen (3 giây)
│       └── MainThongTin.java       # Thông tin ứng dụng
│
├── MainActivity.java               # Màn hình chính – Navigation Drawer + Bottom Nav
├── MainDangNhap.java               # Đăng nhập
├── MainDangKy.java                 # Đăng ký
├── MainDangBai.java                # Đăng bài (Admin)
├── MainCapNhat.java                # Cập nhật truyện (Admin)
├── MainNoiDungTruyen.java          # Đọc nội dung truyện
├── MainTimKiem.java                # Tìm kiếm
├── MainDanhGia.java                # Viết đánh giá
├── MainXemDanhGia.java             # Xem đánh giá
├── MainChiaSe.java                 # Chia sẻ qua email
├── HomeFragment.java               # Fragment trang chủ
├── DangBaiFragment.java            # Fragment đăng bài
├── YeuThichFragment.java           # Fragment yêu thích
├── TatcatruyenFragment.java        # Fragment tất cả truyện
├── AccountFragmment.java           # Fragment tài khoản
└── thongtinappFragment.java        # Fragment thông tin app
```

---

## 🚀 Cài Đặt & Chạy

### Yêu cầu
- Android Studio Flamingo trở lên
- Android SDK API 21+
- Kết nối internet (để load ảnh bìa truyện qua Picasso)

### Các bước

```bash
# 1. Clone repository
git clone https://github.com/hunghayhoc/<tên-repo>.git

# 2. Mở bằng Android Studio
# File → Open → chọn thư mục dự án

# 3. Sync Gradle để tải dependencies

# 4. Chạy trên máy ảo hoặc thiết bị thật (API 21+)
```

### Tài khoản thử nghiệm
| Loại | Tài khoản | Mật khẩu |
|---|---|---|
| Người dùng | `user` | `123` |
| Quản trị viên | `admin` | `123` |

*(Hoặc tự đăng ký tài khoản mới trong ứng dụng)*


