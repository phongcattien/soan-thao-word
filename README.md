# SOẠN THẢO AQ

SOẠN THẢO AQ là add-in VSTO cho Microsoft Word, hỗ trợ định dạng văn bản hành chính Việt Nam, bảng biểu, ngày tháng, số thành chữ, mã QR, dấu văn bản và các thao tác kiểm tra an toàn nội dung.

Kho này chứa mã nguồn sạch của phiên bản `10.75.0.0 Internal`. Tài liệu thực tế của người dùng, khóa ký riêng, bộ cài đã sinh, thư viện Poppler và dữ liệu kiểm thử có thông tin cá nhân không được lưu trong Git.

## Cấu trúc

- `TienIchAiQuoc/src`: mã nguồn add-in.
- `TienIchAiQuoc/config`: cấu hình mặc định không chứa dữ liệu người dùng.
- `TienIchAiQuoc/assets`: ảnh dấu phân loại văn bản đi kèm sản phẩm.
- `TienIchAiQuoc/tests`: kiểm thử Word COM bằng tài liệu tổng hợp.
- `TienIchAiQuoc/deployment`: kịch bản đóng gói/cài đặt.
- `installer`: nguồn tạo bộ cài OneClick; các project nhúng payload được sinh khi build.
- `docs`: quy trình phát hành và kiểm tra bảo mật.

## Yêu cầu phát triển

- Windows 10/11 x64.
- Microsoft Word desktop.
- .NET Framework 4.8 Developer Pack.
- Visual Studio 2022 có Office/SharePoint development tools hoặc MSBuild tương ứng.
- VSTO Runtime.
- .NET SDK 8 theo cấu hình trong `TienIchAiQuoc/build.ps1`.

## Build cục bộ

```powershell
$thumbprint = '<approved Code Signing certificate thumbprint>'
.\TienIchAiQuoc\build.ps1 -Configuration Release -Version 10.75.0.0 -SigningMode Internal -CertificateThumbprint $thumbprint
.\installer\Build-OneClick.ps1 -Version 10.75.0.0 -Distribution Internal -CertificateThumbprint $thumbprint
```

Poppler không được đưa vào Git. Khi tạo bản Full, đặt dependency đã kiểm tra checksum tại `TienIchAiQuoc\tools\poppler` trước khi chạy quy trình đóng gói.

## Kiểm thử Word

Các kiểm thử trong `TienIchAiQuoc/tests` tạo tài liệu tổng hợp trong bộ nhớ, không dùng hồ sơ thực tế. Ví dụ:

```powershell
.\TienIchAiQuoc\tests\test-table-safety-141.ps1
.\TienIchAiQuoc\tests\test-table-geometry-1070.ps1
.\TienIchAiQuoc\tests\test-table-ui-refresh-1072.ps1
.\TienIchAiQuoc\tests\test-money-columns-1073.ps1
.\TienIchAiQuoc\tests\test-financial-layout-1074.ps1
```

Không chạy đồng thời các kiểm thử Word COM với phiên Word đang chứa tài liệu chưa lưu.

## Cấu hình cập nhật

URL `latest.json` không được hard-code. Cấu hình bằng một trong hai cách:

1. Biến môi trường `SOANTHAOAQ_UPDATE_MANIFEST_URL`.
2. Giá trị registry `HKCU\Software\AIQUOC\SoanThaoAQ\UpdateManifestUrl`.

## Phát hành

Bộ cài không được commit vào lịch sử Git. Tạo release từ đúng tag, ký số DLL/manifest/bộ cài bằng chứng thư phát hành, ghi SHA-256, rồi đính kèm file vào GitHub Release. Bản `Internal` chỉ được phát hành trong kho private cho người được cấp quyền. Xem [quy trình phát hành](docs/RELEASE.md) và [hướng dẫn bản nội bộ](docs/INTERNAL-RELEASE.md).

## Bảo mật và quyền riêng tư

Kho được thiết kế để lưu ở chế độ private. Không commit hồ sơ hành chính, chữ ký/dấu cá nhân, URL SharePoint cá nhân, chứng thư có private key hoặc nhật ký chứa đường dẫn người dùng. Xem [SECURITY.md](SECURITY.md).

Copyright © SOẠN THẢO AQ. All rights reserved.
