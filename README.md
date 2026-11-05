# HCM_KS26_CNTT2_IT108_Session20_Ex06
# Bài 6: Bảo mật mã nguồn trước khi Push lên GitHub

## 1. Pre-push Checklist

- Kiểm tra code có chứa API Key, mật khẩu hoặc Token không.
- Thêm `.env` vào `.gitignore`.
- Chỉ Push `.env.example`, không chứa thông tin thật.
- Dùng Gitleaks quét Secrets trước khi Push.
- Kiểm tra lại bằng `git status`.
- Đảm bảo các thành viên đã bật 2FA.

## 2. Cấu hình file

File `.env.example`:

```env
# Development
DEV_DB_URL=your_dev_db

# Testing
TEST_DB_URL=your_test_db

# Production
PROD_DB_URL=your_prod_db

API_KEY=your_api_key
JWT_SECRET=your_jwt_secret
```

File `.gitignore`:

```gitignore
.env
.env.*
!.env.example
node_modules/
```

## 3. Bật 2FA trên GitHub

1. Vào GitHub → Settings → Password and authentication.
2. Bật 2FA bằng Google Authenticator.
3. Lưu mã khôi phục để phòng trường hợp mất điện thoại.
4. Chủ Organization bật yêu cầu 2FA trong phần Authentication security để áp dụng cho cả team.

## 4. Rủi ro khi thiếu `.gitignore`

- Lộ API Key: Hacker có thể sử dụng API trái phép.
- Lộ Database: Có nguy cơ bị đánh cắp dữ liệu nếu lộ thông tin đăng nhập.
- Lộ JWT Secret: Hacker có thể tạo Token giả mạo.
- Lộ `.env`: Các thông tin bảo mật có thể bị công khai trên GitHub.
