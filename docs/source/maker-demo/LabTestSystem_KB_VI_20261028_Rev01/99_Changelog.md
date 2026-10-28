---
doc: Changelog so với "SEEV-SSG User Guide_ Lab Test System 2026.xlsx"
revision: Rev01 – 2026-10-28
---

# Changelog

## Màn hình / menu mới
| Mục | Route | Ghi chú |
|---|---|---|
| Cấu hình IPQC | /LogConfig | Cấu hình đọc log theo Kiểu LogFile (Template/VHX/Laser), công thức, import/export Excel |
| Đổi mật khẩu | /changepassword | Menu mới |
| Cài đặt chung | /setting | Chính sách mật khẩu, máy chủ FTP |
| Sơ đồ Tủ Rack (thiết kế lại) | /Rack/Diagram | Tổng quan tủ, mức đầy theo màu, danh sách request tại ô |
| Chọn ngôn ngữ | Header | EN / VI |
| Tài liệu mới cho màn đã có | /statistics, /group, /account, /Department | xlsx trước đây chưa có hướng dẫn |

## Thay đổi trên màn hiện có
| Màn hình | Thay đổi chính |
|---|---|
| Trang chủ | Ca, Service Auto; 5 thẻ KPI có link; Báo cáo chất lượng OK/NG + %; mặc định 30 ngày |
| Yêu cầu | Thẻ KPI; cột Kết quả đo; trạng thái Quá hạn; Mã nhân viên trong chi tiết; mặc định 30 ngày |
| Tiếp nhận yêu cầu | Thẻ KPI theo vị trí (có NG); cột Tủ đựng/Vị trí; Thời gian nhận/đo |
| Chi tiết nội dung yêu cầu | Vị trí; "Kết quả lần đo mới nhất"; cột Số lượng; modal giá trị đo đủ UL/UCL/Avg/LCL/LL/Value_R |
| Công đoạn, Máy, Loại TB, Thiết bị, Build | Cột Code tự sinh (S/M/ET/E/B); sắp xếp cột |
| Loại thiết bị | Trường **Kiểu LogFile** |
| Vị trí | Thêm **Sửa**; checkbox **Nhận mẫu** |
| Tủ đựng | Nút Xem tầng, Sơ đồ; nút Sơ đồ Tủ Rack |
| Tầng tủ | Nút **Xóa tầng** ở khu lọc; Xem vị trí; Trạng thái Hoạt động/Không hoạt động trên form |
| Vị trí theo tầng | Position Code dạng `…-hh.cc`; không còn Thêm mới (tự sinh) |
| Nội dung IPQC | Bảng phân bổ "Location & Equipment Type Allocation" + Add Location; SPC Rule 1–8 |
| Bố cục IPQC | Lọc Vị trí → Công đoạn → Loại TB; upload **File Template**; nhãn "Hướng ghi" |
| Spec ItemName | Bộ lọc Trạng thái Set/Not Set; cột Trạng thái |
| Spec ItemCode | Cột Trạng thái Common/Individual |

## Không đổi / không xác minh lại
- Sản phẩm (Item): giữ nguyên.
- Service đọc file (4 sheet): chuyển nguyên nội dung, đánh dấu chưa xác minh.

## Định dạng
- Chuyển từ Excel dạng ảnh sang Markdown có frontmatter cho AI Agent + Excel Rev mới.
- Ảnh chụp mới (53 ảnh) trong thư mục `images/`; giá trị FTP đã che.
