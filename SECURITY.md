# Security policy

## Dữ liệu không được đưa vào Git

- Tài liệu Word/PDF thực tế, kể cả bản đã định dạng.
- Chữ ký, con dấu cá nhân/cơ quan hoặc ảnh nhận dạng người dùng.
- Chứng thư ký và private key (`.pfx`, `.p12`, `.key`, `.pem`, `.snk`).
- URL chia sẻ cá nhân, token, mật khẩu, API key và tệp `.env`.
- Log, dump, registry export, bản sao ClickOnce/VSTO và thư mục sao lưu cài đặt.

## Quy tắc phát hành

- Bộ cài phải được tạo từ commit có tag.
- Không dùng chứng thư development để phát hành công khai.
- Kiểm tra chữ ký số và SHA-256 trước khi đăng release.
- Bộ cài không được cưỡng bức kết thúc `WINWORD`; người dùng phải lưu và đóng Word.
- Tệp cập nhật phải được tải qua HTTPS và đối chiếu SHA-256 từ manifest.

## Báo cáo lỗi bảo mật

Không mở issue công khai chứa dữ liệu nhạy cảm. Báo cáo riêng cho chủ sở hữu kho, kèm mô tả tái hiện tối thiểu và dữ liệu tổng hợp đã ẩn danh.

