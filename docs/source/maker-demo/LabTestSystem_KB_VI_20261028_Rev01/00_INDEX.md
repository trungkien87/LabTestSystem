---
doc: LAB TEST SYSTEM – Knowledge Base cho người dùng & AI Agent
system: SEEV-SSG LAB TEST SYSTEM
base_url: http://10.212.9.242:8082
language: vi (giữ nguyên thuật ngữ/nhãn UI tiếng Anh)
revision: Rev01
date: 2026-10-28
source_baseline: "SEEV-SSG User Guide_ Lab Test System 2026.xlsx" (23 sheet)
verification: Rà soát read-only trên hệ thống ngày 2026-10-28 (UI ngôn ngữ VI, tài khoản quyền Administrator). Không thực hiện Lưu/Xoá/Nhận mẫu/Upload.
---

# LAB TEST SYSTEM – Mục lục & Hướng dẫn sử dụng tài liệu

## 1. Hệ thống làm gì

LAB TEST SYSTEM quản lý vòng đời **yêu cầu đo mẫu IPQC** giữa sản xuất và phòng đo (Lab):

1. Công đoạn (Stage) tạo **Request** đo cho một Indication Number + Sequence.
2. Phòng đo (Location) **tiếp nhận mẫu** bằng scan QR → hệ thống phân bổ vị trí trên **tủ (Rack) / tầng (Layer) / ô (Position)**.
3. **Service** cài trên máy đo đọc file log kết quả theo **Cấu hình IPQC** (Template/VHX/Laser) → so với **Spec** (LL/LCL/CENTER/UCL/UL) → phán định OK/NG.
4. Kết quả xem ở web: Request Detail Content, Trang chủ (báo cáo chất lượng), Thống kê (X/R chart).

## 2. Cách AI Agent nên dùng bộ tài liệu này

- Mỗi file `.md` = 1 màn hình hoặc 1 nhóm chức năng, có YAML frontmatter (`route`, `menu`, `permission_key`, `change_status`).
- Tra theo **route** hoặc **tên menu VI/EN** ở bảng Sitemap bên dưới.
- Mức tin cậy trong nội dung:
  - Không đánh dấu = **đã quan sát trực tiếp** trên hệ thống ngày 2026-10-28.
  - `[Từ tài liệu cũ]` = lấy từ xlsx, chưa kiểm chứng lại (thường là hành vi khi Lưu/Xoá – không được thao tác trong lần rà soát read-only).
  - `[Suy luận]` = suy ra từ giao diện/dữ liệu, cần xác nhận với đội phát triển.
  - `[Chưa xác minh]` = có dấu hiệu trên UI nhưng chưa rõ chức năng.
- Phát hiện/rủi ro: xem `98_Findings.md`. Thay đổi so với xlsx: `99_Changelog.md`.

## 3. Sitemap (menu trái → route)

| # | Nhóm menu (VI) | Màn hình (VI menu) | Tên trên trang | Route | File | Trạng thái so với xlsx |
|---|---|---|---|---|---|---|
| 1 | — | Trang chủ | Trang chủ | `/home` | 01_Home.md | Thay đổi lớn |
| 2 | GIÁM SÁT | Yêu cầu | Yêu cầu / Tạo yêu cầu | `/request`, `/request/add` | 02_Request.md | Thay đổi |
| 3 | GIÁM SÁT | Tiếp nhận yêu cầu | Tiếp nhận yêu cầu | `/RequestReceive` | 03_Receive.md | Thay đổi |
| 4 | (từ Request/Receive) | — | Chi tiết nội dung yêu cầu | `/Request/detail?PKID=…` | 04_Request_Detail_Content.md | Thay đổi |
| 5 | THỐNG KÊ | Thống kê | Thống kê | `/statistics` | 05_Statistics.md | Mới (xlsx chưa có hướng dẫn) |
| 6 | CÀI ĐẶT HỆ THỐNG | Cài đặt vai trò | Cài đặt vai trò | `/group` | 06_System_Settings.md | Mới |
| 7 | CÀI ĐẶT HỆ THỐNG | Cài đặt người dùng | Cài đặt người dùng | `/account` | 06_System_Settings.md | Mới |
| 8 | CÀI ĐẶT HỆ THỐNG | Cài đặt phòng ban | Cài đặt phòng ban | `/Department` | 06_System_Settings.md | Mới |
| 9 | CÀI ĐẶT HỆ THỐNG | Đổi mật khẩu | Đổi mật khẩu | `/changepassword` | 06_System_Settings.md | Mới (menu mới) |
| 10 | CÀI ĐẶT HỆ THỐNG | Cài đặt chung | Chính sách mật khẩu / FTP | `/setting` | 06_System_Settings.md | Mới (menu mới) |
| 11 | DỮ LIỆU DANH MỤC | Công đoạn | Quản lý công đoạn | `/Stage` | 07_MasterData_Production.md | Thay đổi |
| 12 | DỮ LIỆU DANH MỤC | Máy | Quản lý máy | `/Machine` | 07_MasterData_Production.md | Thay đổi |
| 13 | DỮ LIỆU DANH MỤC | Loại thiết bị | Quản lý loại thiết bị | `/EquipmentType` | 08_MasterData_Lab.md | Thay đổi |
| 14 | DỮ LIỆU DANH MỤC | Thiết bị | Quản lý thiết bị | `/Equipment` | 08_MasterData_Lab.md | Thay đổi |
| 15 | DỮ LIỆU DANH MỤC | Build | Build Management | `/Build` | 07_MasterData_Production.md | Thay đổi |
| 16 | DỮ LIỆU DANH MỤC | Sản phẩm | Quản lý Item | `/item` | 07_MasterData_Production.md | Ít thay đổi |
| 17 | DỮ LIỆU DANH MỤC | Vị trí | Location Management | `/Location` | 08_MasterData_Lab.md | Thay đổi |
| 18 | DỮ LIỆU DANH MỤC | Tủ đựng | Rack Management / Sơ đồ Tủ Rack | `/Rack`, `/Rack/Diagram` | 09_Rack_Storage.md | Thay đổi |
| 19 | DỮ LIỆU DANH MỤC | Tầng tủ | Quản lý tầng tủ | `/RackShelf` | 09_Rack_Storage.md | Thay đổi |
| 20 | DỮ LIỆU DANH MỤC | Vị trí theo tầng | Quản lý vị trí tầng tủ | `/ShelfPosition` | 09_Rack_Storage.md | Thay đổi |
| 21 | IPQC | Nội dung IPQC | IPQC Content Management | `/IPQCContent` | 10_IPQC_Content_Layout_Config.md | Thay đổi |
| 22 | IPQC | Bố cục IPQC | IPQC Layout Management | `/Layout` | 10_IPQC_Content_Layout_Config.md | Thay đổi |
| 23 | IPQC | Cấu hình IPQC | Cấu hình IPQC | `/LogConfig` | 10_IPQC_Content_Layout_Config.md | **Mới** |
| 24 | IPQC › Tiêu chuẩn IPQC | Thông số IPQC theo tên sản phẩm | IPQC Spec for ItemName | `/spec/itemname` | 11_IPQC_Spec.md | Thay đổi |
| 25 | IPQC › Tiêu chuẩn IPQC | Thông số IPQC theo mã sản phẩm | IPQC Spec for ItemCode | `/spec/itemcode` | 11_IPQC_Spec.md | Thay đổi |
| 26 | (App desktop) | Service đọc file | Màn hình chính / Pending / Lịch sử / Cài đặt | — | 12_Service_ReadFile.md | Giữ nguyên từ xlsx, chưa xác minh |
| — | Header | Ngôn ngữ EN/VI; menu người dùng → Đăng xuất | — | `/account/logout` | 00_INDEX.md | Mới (chọn ngôn ngữ) |

Tài liệu bổ trợ: `90_Glossary.md` (thuật ngữ, mã tự sinh, trạng thái), `91_Workflow_Setup_Order.md` (luồng nghiệp vụ & thứ tự khai báo), `98_Findings.md`, `99_Changelog.md`.

## 4. Quy ước giao diện chung (áp dụng cho mọi màn danh mục)

| Thành phần | Mô tả |
|---|---|
| `+ Thêm mới` (góc phải) | Mở trang `…/Add`, `…/AddUpdate` hoặc modal thêm mới |
| Icon tài liệu (góc phải) – "Lịch sử tổng quát" | Lịch sử thay đổi toàn bộ danh mục, gồm cả bản ghi đã xoá |
| Icon phễu – "Bộ lọc tìm kiếm" | Ẩn/hiện khu vực lọc; nút `Tìm kiếm`, `Đặt lại` |
| Cột HÀNH ĐỘNG | `Sửa` (bút), `Xoá` (thùng rác), `Lịch sử` (tài liệu) – một số màn có thêm nút riêng |
| Xoá / Sửa | Bắt buộc nhập **Lý do (Reason)**; được ghi vào lịch sử cùng Mã nhân viên & ngày giờ |
| Phân trang | "Hiển thị 10/25/50/75/100 dòng mỗi trang"; nhiều bảng có sắp xếp cột ↑↓ |
| Mã tự sinh | Hầu hết danh mục có cột Code tự sinh (S01, M001, ET001, E001, B001, F1L01, F1-RCK-0001…) – xem Glossary |
| Ngôn ngữ | Dropdown `Ngôn ngữ` EN/VI ở header. Một số tiêu đề trang vẫn tiếng Anh khi chọn VI (vd "Build Management", "Machine Management - Insert") |

## 5. Phân quyền

Phân quyền theo **Vai trò** × **Tên danh sách** × {View, Add, Edit, Delete} (màn `/group` → Phân quyền). Danh sách quyền hiện có (23 dòng): Request, Receive Request, Statistics, User Role Setting, User Setting, Department Setting, Stage, Machine, Equipment Type, Equipment, Build, Item, Location, Rack, Rack Layer, Layer Position, IPQC Content, IPQC Layout, IPQC Spec ItemName, IPQC Spec ItemCode, Home, Cài đặt chung, Change Password.

Ngoài ra **Cài đặt phòng ban** giới hạn phạm vi dữ liệu (Vị trí, Công đoạn) theo phòng ban `[Suy luận]`.
