# Website Đăng ký Thông tin Khách hàng (Static + Formspree)

Website đăng ký thông tin khách hàng sử dụng **GitHub Pages** + **Formspree** (không cần server/PHP/Database).

## 🌐 Demo
- **Link:** `https://regis.dodoanloc.github.io`
- **Form:** `https://regis.dodoanloc.github.io/index.html`

---

## 📁 Cấu trúc dự án

```
customer-registration-static/
├── index.html       # Trang đăng ký (form)
├── thank-you.html   # Trang thông báo thành công
├── error.html       # Trang thông báo lỗi
├── README.md        # Hướng dẫn này
└── .nojekyll        # (Tùy chọn) Disable Jekyll processing
```

---

## 🚀 Hướng dẫn cài đặt

### Bước 1: Tạo tài khoản Formspree (QUAN TRỌNG)

1. Truy cập: https://formspree.io
2. Click "Sign Up" để tạo tài khoản (có thể dùng GitHub login)
3. Tạo form mới:
   - Click "New Form"
   - Đặt tên: "Customer Registration"
   - Email nhận thông báo: `[email-cua-ban]`
4. Copy **Form ID** (dạng: `xrgjewkn`)

### Bước 2: Cập nhật Form ID trong code

Mở file `index.html`, tìm dòng:
```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

Thay `YOUR_FORM_ID` bằng ID thực tế của bạn:
```html
<form action="https://formspree.io/f/xrgjewkn" method="POST">
```

### Bước 3: Tạo GitHub Repository

1. Đăng nhập GitHub
2. Tạo repo mới: `regis`
3. Set public
4. **KHÔNG** tick "Initialize with README"

### Bước 4: Upload files lên GitHub

**Cách 1: Dùng Git command line**
```bash
cd customer-registration-static
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/dodoanloc/regis.git
git push -u origin main
```

**Cách 2: Upload trực tiếp trên GitHub**
1. Vào repo `regis`
2. Click "Add file" → "Upload files"
3. Kéo thả 3 file: `index.html`, `thank-you.html`, `error.html`
4. Click "Commit changes"

### Bước 5: Bật GitHub Pages

1. Vào repo → Settings → Pages
2. Source: Chọn "Deploy from a branch"
3. Branch: Chọn `main` / `master` → `/ (root)`
4. Click Save
5. Đợi 2-5 phút để GitHub build site

### Bước 6: Test website

Truy cập: `https://regis.dodoanloc.github.io`

---

## ✨ Tính năng

### Form đăng ký (index.html)
- ✅ Responsive design (mobile + desktop)
- ✅ Validation: Số tài khoản (chỉ số), SĐT (10-11 số)
- ✅ UI đẹp với gradient
- ✅ Thông báo privacy

### Dữ liệu nhận được
Khi khách hàng submit form, bạn nhận được email với:
- Số tài khoản
- Số điện thoại
- Tên khách hàng
- Thờì gian submit
- IP address

### Trang thành công (thank-you.html)
- Animation đẹp
- Thông báo rõ ràng
- Button quay lại

### Trang lỗi (error.html)
- Thông báo lỗi thân thiện
- Button thử lại

---

## 📧 Quản lý submissions

### Trên Formspree Dashboard
1. Đăng nhập: https://formspree.io
2. Vào form của bạn
3. Xem tất cả submissions
4. Export data ra CSV/Excel

### Qua Email
- Mỗi submission sẽ gửi email thông báo
- Có thể reply trực tiếp từ email

---

## 🎨 Tùy chỉnh

### Đổi màu sắc
Trong `index.html`, tìm CSS:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```
Thay `#667eea` và `#764ba2` bằng màu bạn thích.

### Thêm trường mới
Thêm vào form trong `index.html`:
```html
<div class="form-group">
    <label for="email">Email</label>
    <input type="email" id="email" name="email" required>
</div>
```

### Thêm CAPTCHA
Trong Formspree dashboard:
1. Vào form → Settings
2. Bật "reCAPTCHA"
3. Thêm site key từ Google reCAPTCHA

---

## 💰 Chi phí

### Formspree Free Plan
- ✅ 50 submissions/tháng
- ✅ 1 form
- ✅ Email notifications
- ✅ CSV export

### Nếu cần nhiều hơn
- **Gold Plan:** $10/tháng → 1,000 submissions/tháng
- **Platinum Plan:** $40/tháng → 10,000 submissions/tháng

---

## 🔒 Bảo mật

- ✅ Formspree mã hóa dữ liệu (HTTPS)
- ✅ Không lưu data trên GitHub (chỉ HTML)
- ✅ Có thể bật CAPTCHA chống spam
- ✅ IP logging để tracking

---

## 🐛 Troubleshooting

### Form không submit được
- Kiểm tra Form ID đã đúng chưa
- Đảm bảo form action có `https://`

### Không nhận được email
- Kiểm tra spam folder
- Trong Formspree dashboard, xem tab "Submissions"

### GitHub Pages không hoạt động
- Đảm bảo repo public
- Đợi 5-10 phút sau khi bật Pages
- Kiểm tra Settings → Pages → có link chưa

---

## 📞 Hỗ trợ

- **Formspree Docs:** https://formspree.io/docs/
- **GitHub Pages Docs:** https://docs.github.com/en/pages

---

*Created by Beta 🦊 - AI Assistant*
