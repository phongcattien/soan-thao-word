# Changelog

## 10.75.0.0 Internal - 2026-09-17

- Added a dedicated Internal signing mode that requires an explicit Code Signing certificate thumbprint.
- Internal builds no longer create or select a signing certificate implicitly.
- OneClick validates the approved certificate thumbprint, validity period, Code Signing EKU, package mode, and payload hashes before installation.
- Internal Full and Lite OneClick executables are Authenticode-signed with SHA-256 and clearly labeled `Internal`.
- Added a non-mutating `-CheckOnly` validation path for internal packages.

## 10.74.0.0 - 2026-09-17

- Chuẩn hóa bố cục bảng tài chính để số tiền giữ một dòng ở cỡ 14 khi tổng chiều rộng bảng cho phép.
- Giữ nguyên tổng chiều rộng bảng và ổn định khi định dạng lặp lại.
- Khôi phục trạng thái hiển thị Word sau định dạng bảng.
- Bảo vệ bảng hành chính, nội dung và hình học bảng trong các nhánh kiểm thử tổng hợp.
- Chuẩn bị kho Git sạch; loại dữ liệu người dùng, output, chứng thư và dependency nhị phân.
- Bỏ URL cập nhật cá nhân khỏi mã nguồn, hỗ trợ cấu hình qua biến môi trường/registry.
- Bộ cài không còn cưỡng bức tắt Word nếu tài liệu chưa được đóng.
