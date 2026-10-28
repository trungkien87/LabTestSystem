---
doc: Thuật ngữ, mã tự sinh, trạng thái
---

# Glossary

| Thuật ngữ | Nhãn UI (VI) | Định nghĩa |
|---|---|---|
| Stage | Công đoạn | Công đoạn sản xuất yêu cầu đo; có Stage Code S01… và Loại mẫu |
| Sample Type | Loại mẫu | Sheet / Block / Pcs |
| Machine | Máy | Máy sản xuất thuộc 1 công đoạn, 1 nhà máy (F1–F5); Machine Code M001… |
| Factory | Nhà máy | F1 … F5 |
| Build | Build | Giai đoạn sản phẩm; Type NPI hoặc MP |
| Item Name / Item Code | Sản phẩm | Tên & mã sản phẩm; Item Code thuộc Item Name, gắn Build |
| Indication Number (Indi Number) | Indi Number | Mã tem lô; hệ thống cắt ra Item Code + Lot No |
| Lot No | Lô sản xuất | Cắt từ Indi Number |
| Sequence | Trình tự | Mã bước đo của Item trong công đoạn (vd 0020, 0120); khoá Spec |
| Leadtime | Thời gian thực hiện (phút) | Dùng tính Thời hạn (Deadline) request |
| Location | Vị trí | Phòng đo: Factory + Department; Location Code `F<f>L<nn>` |
| Equipment Type | Loại thiết bị | Loại máy đo; có Kiểu LogFile |
| LogFile Type | Kiểu LogFile | Template · VHX · Laser · Manual Input |
| Equipment | Thiết bị | Máy đo cụ thể (Mã thiết bị), thuộc Vị trí + Loại thiết bị |
| Rack / Layer / Position | Tủ đựng / Tầng tủ / Vị trí theo tầng | Nơi lưu mẫu chờ đo |
| IPQC Content | Nội dung IPQC | Chỉ tiêu đo của công đoạn |
| Side A / Side B | Mặt A / Mặt B | Hai mặt mẫu đo |
| X Spec | X SPEC | LL, LCL, CENTER, UCL, UL cho giá trị trung bình |
| R Spec | R SPEC | CENTER LINE, UCL cho biên độ |
| SPC Rule | SPC Rule | Rule 1–8 áp dụng cho nội dung |
| Common / Individual | Trạng thái spec ItemCode | Common = sinh từ ItemName; Individual = đã sửa riêng |
| Set / Not Set | Trạng thái spec ItemName | Đã/chưa có spec |
| Service Auto | Service Auto | Trạng thái dịch vụ tự động (hiển thị ở Trang chủ) |
| Ca | Ca | Ca làm việc hiện tại |

## Mã tự sinh
| Đối tượng | Định dạng | Ví dụ |
|---|---|---|
| Request No | `RYYMMDD_XXXX` | R261028_0008 |
| Stage Code | `S` + 2 số | S01 |
| Machine Code | `M` + 3 số | M001 |
| Equipment Type Code | `ET` + 3 số | ET001 |
| Equipment Code | `E` + 3 số | E001 |
| Build Code | `B` + 3 số | B001 |
| Location Code | `F<factory>L<nn>` | F1L02 |
| Rack Code | `F<factory>-RCK-<nnnn>` | F1-RCK-0001 |
| Layer Code | `<Rack>-<nn>` | F1-RCK-0001-03 |
| Position Code | `<Layer>-<row>.<col>` | F1-RCK-0001-03-01.02 |

## Trạng thái Request
| Cấp request | Cấp chi tiết (Vị trí + Loại thiết bị) | Chuyển trạng thái do |
|---|---|---|
| Đã yêu cầu | Chờ nhận mẫu | Tạo yêu cầu |
| Đang xử lý | Đã nhận mẫu | Tiếp nhận (scan QR tại Vị trí) |
| Đang xử lý | Đang đo | Service scan request + mã nhân viên |
| Hoàn thành (OK/NG) | Hoàn thành | Service đọc file thành công |
| Quá hạn | — | Hiện tại > Thời hạn |
| Đã huỷ | — | Hủy yêu cầu |
Làm mới trên Service: Đang đo → Đã nhận mẫu.
