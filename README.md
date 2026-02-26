# Website Đăng ký Thông tin Khách hàng (Airtable Integration)

Website đăng ký thông tin khách hàng sử dụng **GitHub Pages** + **Airtable** (không cần server/PHP/Database).

## 🌐 LINK WEBSITE:
- **Form đăng ký:** https://dodoanloc.github.io/regis/
- **Trang quản lý:** https://dodoanloc.github.io/regis/admin.html

---

## 📋 CẤU HÌNH AIRTABLE (BẮT BUỘC)

Để website hoạt động, bạn **PHẢI** làm theo các bước sau:

### **BƯỚC 1: Tạo Airtable Base**

1. Đăng nhập vào [Airtable](https://airtable.com)
2. Click **"Create a base"** → Chọn **"Start from scratch"**
3. Đặt tên base: `Customer Registration`

### **BƯỚC 2: Thiết lập Table**

Trong base vừa tạo, đổi tên table từ "Table 1" thành **"Customers"**

Tạo các cột sau:

| Tên cột | Kiểu dữ liệu | Ghi chú |
|---------|--------------|---------|
| **Số tài khoản** | Single line text | Số tài khoản khách hàng |
| **Số điện thoại** | Single line text | SĐT 10-11 số |
| **Tên khách hàng** | Single line text | Họ và tên |
| **Ngày đăng ký** | Created time | Tự động ghi lại thờì gian |

**Cách tạo cột "Ngày đăng ký":**
1. Click dấu **+** để thêm cột mới
2. Chọn field type: **"Created time"**
3. Đặt tên: **"Ngày đăng ký"**

### **BƯỚC 3: Lấy Base ID**

1. Mở base "Customer Registration" trong trình duyệt
2. Nhìn vào URL: `https://airtable.com/appXXXXXXXXXXXXXX/tbl...`
3. Copy phần `appXXXXXXXXXXXXXX` (bắt đầu bằng **app**)
   - Ví dụ: `app1234567890abcd`

### **BƯỚC 4: Cập nhật Base ID trong code**

**Cách 1: Edit trực tiếp trên GitHub (Dễ nhất)**

1. Vào: https://github.com/dodoanloc/regis/edit/main/index.html
2. Tìm dòng: `baseId: ''`
3. Sửa thành: `baseId: 'appXXXXXXXXXXXXXX'` (thay X bằng ID của bạn)
4. Tương tự sửa trong file `admin.html`
5. Click **"Commit changes"**

**Cách 2: Edit local rồi push**

```bash
cd ~/.openclaw/workspace/customer-registration-static

# Sửa file index.html và admin.html
# Thay baseId: '' thành baseId: 'appXXXXXXXXXXXXXX'

git add .
git commit -m "Update Airtable Base ID"
git push origin main
```

---

## 📁 CẤU TRÚC DỰ ÁN

```
customer-registration-static/
├── index.html       # Form đăng ký (gửi data đến Airtable)
├── admin.html       # Trang quản lý (xem data từ Airtable)
├── thank-you.html   # Trang thông báo thành công
├── error.html       # Trang thông báo lỗi
└── README.md        # Hướng dẫn này
```

---

## ✨ TÍNH NĂNG

### Form đăng ký (index.html)
- ✅ Giao diện đẹp, gradient UI, responsive
- ✅ Validation: Số tài khoản (chỉ số), SĐT (10-11 số)
- ✅ Gửi trực tiếp đến Airtable qua JavaScript API
- ✅ Thông báo thành công/lỗi ngay lập tức
- ✅ Chuyển hướng đến trang thank-you sau khi đăng ký

### Trang quản lý (admin.html)
- ✅ Xem toàn bộ danh sách khách hàng
- ✅ Thống kê: Tổng số KH, KH đăng ký hôm nay
- ✅ Sắp xếp theo thờì gian mới nhất
- ✅ Nút làm mới dữ liệu

---

## 🔒 BẢO MẬT

**Lưu ý quan trọng:**
- Token Airtable được hardcode trong file HTML
- Repo này là **public** → Mọi ngườì đều có thể xem token
- Đây là **demo/prototype**, không nên dùng cho production thực tế

**Nếu cần bảo mật hơn:**
- Chuyển repo sang **private**
- Hoặc dùng server-side proxy để giấu token
- Hoặc dùng Airtable OAuth thay vì Personal Token

---

## 💰 CHI PHÍ

| Dịch vụ | Free Tier | Paid |
|---------|-----------|------|
| **GitHub Pages** | Miễn phí | Miễn phí |
| **Airtable** | 1,200 records/tháng | $20/tháng |

---

## 🐛 XỬ LÝ LỖI

### "Chưa cấu hình Base ID"
- Bạn chưa cập nhật `baseId` trong file HTML
- Làm theo Bước 4 ở trên

### "401 Unauthorized"
- Token không hợp lệ hoặc đã hết hạn
- Kiểm tra lại token trong Airtable settings

### "Could not find table Customers"
- Tên table không đúng (phải là "Customers")
- Hoặc tên cột không khớp (xem Bước 2)

### "Network error"
- Kiểm tra kết nối internet
- Airtable API có thể tạm thờì bị lỗi

---

## 📝 EXPORT DỮ LIỆU

Từ Airtable, bạn có thể:
1. Export CSV: Click **...** → **Download CSV**
2. Export Excel: Dùng Airtable desktop app
3. API access: Sử dụng Airtable API để lấy data

---

## 🚀 TÙY CHỈNH

### Thêm trường mới

1. Thêm cột trong Airtable
2. Sửa file `index.html` để thêm input field
3. Cập nhật JavaScript để gửi field mới

### Đổi màu sắc

Trong CSS, tìm:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```
Thay đổi mã màu theo ý muốn.

---

## 📞 HỖ TRỢ

- **Airtable Docs:** https://airtable.com/developers/web/api/introduction
- **GitHub Pages Docs:** https://docs.github.com/en/pages

---

*Created by Beta 🦊 - AI Assistant*
