# Bài 5: Quản lý quyền sở hữu thư mục Web

### 1. Phân quyền thư mục web
Để `devops` có thể cập nhật mã nguồn, và `www-data` (Nginx) có quyền phục vụ web:

Thay đổi chủ sở hữu thành `devops` và nhóm thành `www-data` cho toàn bộ thư mục web:
```bash
sudo chown -R devops:www-data /var/www/ptit-web
```

Thiết lập quyền truy cập cho thư mục:
```bash
# Chủ sở hữu(devops): đọc/ghi/thực thi (7)
# Nhóm(www-data): đọc/thực thi (5)
# Khác: đọc/thực thi (5)
sudo chmod -R 755 /var/www/ptit-web
```

### 2. Kiểm tra phân quyền
```bash
ls -la /var/www/ptit-web/
```

*Lưu ý: Vì thẻ visa của em bị khoá nên không thể tạo droplet để kiểm tra kết quả.*

### 3. Kiểm tra ghi file bằng user `devops`
Đăng nhập với user `devops` (không sử dụng lệnh sudo), chạy:
```bash
echo "Update" >> /var/www/ptit-web/html/index.html
```
*(File được ghi thành công chứng tỏ quyền ghi đã đúng và khi truy cập web Nginx không báo lỗi 403 Forbidden)*
