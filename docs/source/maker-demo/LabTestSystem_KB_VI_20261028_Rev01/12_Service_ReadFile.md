---
screen: Service đọc file kết quả đo (ứng dụng desktop trên máy đo)
route: (không phải web)
menu: Menu trái của Service: Màn hình chính · Pending Request · Tóm tắt lịch sử · Cài đặt
change_status: unverified (chuyển nguyên từ xlsx – KHÔNG rà soát lại trong Rev01)
xlsx_sheet: [Service Monitor, Pending List, History Result, Service Configuration]
---

# Service đọc dữ liệu `[Toàn bộ: Từ tài liệu cũ]`

> Lưu ý Rev01: Trang chủ web hiện có chỉ báo **Service Auto: ON/OFF (Last time …)** và loại thiết bị có **Kiểu LogFile** + màn **Cấu hình IPQC** mới → hành vi Service có thể đã thay đổi. Cần rà soát trực tiếp trên máy đo.

## 1. Màn hình chính – đọc file & phán định
Khu vực: (1) thông tin cài đặt, trạng thái kết nối; (2) ô Mã yêu cầu, Mã nhân viên; (3) nút thao tác. **Danh sách yêu cầu**: request tại Location + Equipment Type. **Nhật ký thực thi**: thao tác/lỗi.

| Bước | Thao tác | Kết quả mong đợi |
|---|---|---|
| 1 | Scan QR Request No (chỉ nhận request đã **nhận mẫu**) | |
| 2 | Scan Mã nhân viên người đo | Tự tạo thư mục chứa file; web cập nhật **Đang đo** |
| 3 | Nhấn **Thư mục** → lưu file kết quả & thư mục liên quan vào thư mục hiển thị | Nút **Đọc tệp** xuất hiện |
| 4 | Nhấn **Đọc tệp** | Đọc file + copy từ link Local sang link Server |
| 5a | Thành công → **Đồng ý** | Request rời danh sách; trạng thái **Hoàn thành**; file đã copy lên Server |
| 5b | Thất bại | Lỗi ở Nhật ký thực thi; request vẫn **Đang đo** |

**Đo lại**: scan request đã đo → xác nhận đo lại (**Đồng ý** / **Bỏ qua**) → scan Mã nhân viên → danh sách hiển thị số lần đã đo và kết quả lần trước. Số lần đo lại tối đa theo Cài đặt.
**Làm mới**: khi đang đo nhấn **Làm mới** → **Đồng ý** → request về **Received**.

## 2. Pending Request
Menu Pending Request → danh sách chờ đo → nhấn đúp request → Service điền sẵn Mã yêu cầu → đo như mục 1. **Đóng** để thoát.

## 3. Tóm tắt lịch sử
Tìm theo Mã yêu cầu, Từ ngày – Đến ngày (mặc định 7 ngày), Kết quả (Tất cả/OK/NG) → **Tìm kiếm** / **Đặt lại**. Nhấn đúp request → kết quả; nhấn dòng/cột Judgment Side A/B → chi tiết; xem các lần đo trước; **Đóng**.

## 4. Cài đặt Service
| Bước | Thao tác |
|---|---|
| 1 | Menu **Cài đặt** |
| 2 | Chọn **Location** → **Equipment Type** (lọc theo Location) → **Equipment** (lọc theo Equipment Type) |
| 3 | **Local Folder Path**: dán đường dẫn hoặc Browse |
| 4 | **Server Folder Path**: dán đường dẫn hoặc Browse |
| 5 | Nhập **Số lần đo lại tối đa** |
| 6 | **Lưu cài đặt** (hoặc **Hủy**) |
