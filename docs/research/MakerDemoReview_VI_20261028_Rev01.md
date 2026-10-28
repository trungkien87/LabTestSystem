# Đối chiếu bản demo của maker với tài liệu nguồn

**Version:** 20261028 Rev.01 · **Ticket:** [#5 Lấy quyền truy cập bản demo hiện có của maker](https://github.com/trungkien87/LabTestSystem/issues/5)

**Nguồn demo:** [docs/source/maker-demo/](../source/maker-demo/README.md), gồm KB (rà soát read-only web demo ngày 2026-10-28) và User Guide Rev01. Không có quyền truy cập trực tiếp web, repo hay database của maker.

**Nguồn so sánh:**
- `docs/source/`: 37 requirement, Concept, IPQC master data.
- Các quyết định đã chốt: `GLOSSARY.md`, map [#1](https://github.com/trungkien87/LabTestSystem/issues/1), `AGENTS.md`.

**Phân loại thông tin:**

| Nhãn | Ý nghĩa |
|---|---|
| **Dữ kiện** | Thấy trên ảnh chụp, hoặc KB ghi là quan sát trực tiếp. |
| **Tài liệu cũ** | Lấy từ User Guide Rev00 của maker, chưa kiểm lại. |
| **Suy luận** | Do người viết báo cáo này suy ra; cần maker xác nhận. |

## 1. Kết luận

1. **Demo đã đi xa hơn một bản "xem thử".** Web đã có đủ luồng MVP Request → Receive → Measure → Judge → Result và đang chạy với dữ liệu thật (Dữ kiện):
   - có request từ 2026-08-27 trên ảnh Service; request 2026-10-28 trên web;
   - KPI: 32 hoàn thành, 275 quá hạn;
   - các công đoạn UV laser, RTR Etching, RTR Copper Plating.
2. **Đã làm:** 28/37 requirement ở mức "Có", 7 ở mức "Một phần", req 23 là thao tác tay (bảng mục 3). **Chưa có:**
   - Abnormal (req 36);
   - Calibration gate;
   - tích hợp Plus A và Training;
   - đánh giá SPC rule;
   - thông báo.
3. **Khác biệt với quyết định đã chốt:**
   - Location của demo là `Department - Factory`, mã `F1L01`, không có tầng. Quyết định ngày 2026-10-27 là **Measurement Location** `Nhà máy-Tầng-Phòng`.
   - Giao diện demo chưa theo DESIGN_EN_20261027_Rev01 (mục 5).
4. **Stack chưa xác nhận được.** Chỉ có suy luận: web .NET (ASP.NET MVC), Service là ứng dụng Windows nối thẳng vào database tên "SaoMai" (mục 4).
5. **Hệ quả cho map:** đích hiện tại của map giả định maker sẽ viết hệ thống từ bộ hồ sơ bàn giao. Thực tế maker đã có hệ thống chạy được. Chủ dự án cần quyết định lại dạng đích, xem mục 7.

## 2. Demo có những gì

### Web (route theo [00_INDEX.md](../source/maker-demo/LabTestSystem_KB_VI_20261028_Rev01/00_INDEX.md))

| Nhóm | Màn hình |
|---|---|
| Giám sát | Trang chủ (KPI, Ca, Service Auto ON/OFF, báo cáo OK/NG); Yêu cầu và Tạo yêu cầu; Tiếp nhận yêu cầu; Chi tiết nội dung yêu cầu |
| Thống kê | Biểu đồ X/R theo Lot |
| Cài đặt hệ thống | Vai trò và ma trận quyền View/Add/Edit/Delete (23 dòng); Người dùng; Phòng ban; Đổi mật khẩu; Cài đặt chung (chính sách mật khẩu, FTP) |
| Danh mục | Công đoạn, Máy, Loại thiết bị (có Kiểu LogFile), Thiết bị, Build, Sản phẩm (Item), Vị trí, Tủ/Tầng/Ô và Sơ đồ tủ |
| IPQC | Nội dung IPQC (phân bổ Loại thiết bị × Vị trí, số lượng NPI/MASS, SPC Rule 1–8); Bố cục IPQC; Cấu hình IPQC (đọc log, công thức, import/export Excel); Spec theo Item Name (Set/Not Set) và theo Item Code (Common/Individual) |
| Chung | Chọn ngôn ngữ EN/VI ở header; mọi Sửa/Xoá bắt buộc nhập Lý do và ghi lịch sử |

### Service trên PC thiết bị đo

Tên cửa sổ "QALab Process Log" (Tài liệu cũ, ảnh Rev00):
- **Màn hình chính:** scan Mã yêu cầu và Mã nhân viên; nút Đọc tệp (F5), Thư mục, Làm mới; Nhật ký thực thi.
- **Pending Requests**, **Tóm tắt lịch sử** (xem từng lần đo).
- **Cài đặt:** Location → Equipment Type → Equipment; Local/Server Folder Path; Số lần đo lại tối đa.
- **Header:**
  - trạng thái kết nối `DB SaoMai`, `PathLocal`, `PathServer`;
  - chọn ngôn ngữ (đang hiển thị "TIẾNG VIỆT").

**Mã tự sinh:** `RYYMMDD_XXXX`, `S01`, `M001`, `ET001`, `E001`, `B001`, `F1L01`, `F1-RCK-0001`, `F1-RCK-0001-03`, `F1-RCK-0001-03-01.02` ([90_Glossary.md](../source/maker-demo/LabTestSystem_KB_VI_20261028_Rev01/90_Glossary.md)).

## 3. Độ phủ 37 requirement

Mức: **Có** = có màn/chức năng tương ứng; **Một phần** = có nhưng thiếu ý trong requirement; **Chưa** = không thấy. Đánh giá dựa trên ảnh và KB, chưa thao tác thử.

| Req | Chức năng | Demo | Ghi chú |
|---|---|---|---|
| 1 | Vai trò | Có | Không có dòng quyền cho Cấu hình IPQC (KB F-02) |
| 2 | Người dùng | Một phần | Nhập tay, không lấy từ Training. Chính sách mật khẩu 180 ngày, nhắc trước 30 ngày. Trường Phòng ban là text tự do |
| 3 | Máy chủ FTP | Có | Ai có quyền xem màn đều thấy thông tin FTP (KB F-11) |
| 4 | Công đoạn | Có | |
| 5 | Máy | Một phần | Nhập tay, không lấy từ Plus A |
| 6 | Build | Một phần | Nhập tay. Type dùng `NPI`/`MP`, requirement viết MASS/NPI |
| 7 | Build + Item | Một phần | Import file tạm thời, chưa đồng bộ Plus A (Tài liệu cũ) |
| 8 | Location | Có, theo requirement cũ | Trái với quyết định Measurement Location, xem mục 6 (#2) |
| 9 | Loại thiết bị | Có | Một loại thiết bị gắn nhiều vị trí; requirement ghi "tự gắn với location đã chọn" |
| 10 | Thiết bị | Có | Dữ liệu mồ côi `ET002` (KB F-05) |
| 11–13 | Rack, Layer, Position | Có | Không thấy rule mặc định Max Qty = 10, Sheet (req 13) |
| 14 | Nội dung IPQC | Có | SPC Rule chỉ là checkbox, không có định nghĩa rule (KB F-08) |
| 15 | Layout | Có | Bổ sung màn Cấu hình IPQC hợp nhất |
| 16 | Spec | Có | Không thấy link "Item name → danh sách Item code" (ý 5); chưa rõ version/snapshot (KB F-01) |
| 17 | Theo dõi trạng thái | Có | Màn Yêu cầu không có lọc nhanh 1 ngày/1 tuần/1 tháng; chỉ Trang chủ có |
| 18–21 | Tạo request | Có | Sequence chọn từ danh sách, không scan. Chặn trùng Stage + Indi + Sequence |
| 22 | In QR | Có | Khổ A5 và các trường in chưa kiểm |
| 23 | Mang mẫu | (thao tác tay) | |
| 24 | Theo dõi tại LAB | Có | KPI theo vị trí có NG |
| 25 | Vị trí nhận theo user | Một phần | Có dropdown Vị trí; chưa kiểm mặc định theo phân quyền |
| 26 | Quét nhận mẫu | Có | |
| 27 | Phân bổ rack | Có | Thuật toán chưa được mô tả (KB ghi Suy luận) |
| 28 | Service: kết nối, pending | Có | Tự cập nhật danh sách chưa kiểm |
| 29–32 | Service: scan, folder, đọc tệp | Có | Tài liệu cũ |
| 33 | Đánh giá sau đọc tệp | Một phần | Có OK/NG. Không thấy trạng thái phán định "Error": đọc lỗi thì request vẫn "Đang đo". Đo lại giới hạn bằng cài đặt từng máy (ảnh: 10 lần) |
| 34 | Copy lên server | Có | Cấu trúc thư mục khớp req 34; ảnh cho thấy thư mục server là `D:\Saomai\QALab\Server\...` |
| 35 | Lịch sử tại máy | Có | Tài liệu cũ |
| 36 | Abnormal | Chưa | |
| 37 | SPC Control chart | Một phần | Có biểu đồ X/R theo Lot; không đánh giá SPC rule; không lọc theo Machine ID |

**Ngoài 37 requirement:**
- **Concept:** demo chưa có Calibration gate, thông báo cho PR, xuất dữ liệu kèm 4M, tích hợp WCS.
- **Demo có thêm:** Ca, Service Auto, Sơ đồ tủ, cờ "Nhận mẫu", Kiểu LogFile `Manual Input`, công thức tính, upload file template, màn Đổi mật khẩu.

## 4. Stack

| Thành phần | Dữ kiện | Suy luận |
|---|---|---|
| Web | `http://10.212.9.242:8082` chạy HTTP, chưa HTTPS. Route kiểu `/account/logout`, `/Request/detail?PKID=…&ReturnUrl=1`, `/Rack/AddUpdate`. Một màn hiện ngày dạng `10/23/2026 3:27:00 AM`, màn khác dạng `2026-10-23 03:27:00`. Footer "©2025" | ASP.NET MVC (C#), giao diện Bootstrap |
| Service | Ứng dụng cửa sổ Windows "QALab Process Log"; header hiện trạng thái `DB SaoMai`; đường dẫn `D:\Saomai\...` | .NET desktop (WinForms/WPF), kết nối **thẳng** vào database tên SaoMai, không qua API |
| Database | Không có thông tin | |
| Maker | Biên bản họp ghi DRI "SMS Long", "SM Hiếu" | Maker là đơn vị "Sao Mai" |

Cần maker xác nhận: ngôn ngữ và framework, database, cách Service kết nối (DB trực tiếp hay API), môi trường test tách khỏi môi trường đang chạy.

## 5. Giao diện so với DESIGN_EN_20261027_Rev01

Nhận xét từ ảnh chụp, chưa đo màu chính xác:
- **Màu nút sai quy tắc:**
  - Nút chính "Lưu" màu xanh lá, nút "In QR Code" màu cam.
  - DESIGN quy định thao tác dùng Primary Blue `#0067E6`; màu ấm chỉ dành cho cảnh báo/lỗi.
- **Màu phán định:** ô OK/NG tô kín màu bão hoà. DESIGN dùng màu như tín hiệu, bề mặt chủ yếu đen/trắng/xám.
- **Ngôn ngữ chưa đủ:** nhiều tiêu đề chưa Việt hoá khi chọn VI (KB F-03). Trái tiêu chí F1, là tiêu chí Bắt buộc.
- **Định dạng ngày không thống nhất** giữa các màn (mục 4).
- **Pattern nên giữ khi làm mockup** (khuyến nghị):
  - thẻ KPI có link sang danh sách đã lọc;
  - sơ đồ tủ theo mức đầy;
  - lọc phân cấp Vị trí → Công đoạn → Loại thiết bị.

## 6. Khác biệt cần đưa vào ticket quyết định

| Ticket | Demo đang làm | Khác với | Cần quyết định |
|---|---|---|---|
| [#2](https://github.com/trungkien87/LabTestSystem/issues/2) Thuật ngữ | Location = `Department - Factory`, mã `F1L01`, cờ "Nhận mẫu" | Measurement Location `Nhà máy-Tầng-Phòng` (GLOSSARY) | Mã và tên chuẩn của Measurement Location; có giữ cờ "Nhận mẫu" không |
| #2 | "Department" mang 3 nghĩa: ô phòng trong Location; phòng ban ở Cài đặt phòng ban (phạm vi Vị trí + Công đoạn); text tự do ở Người dùng | | Tách thuật ngữ |
| #2 | Spec khoá theo Stage + Item Name + Sequence. Sequence chọn từ danh sách spec đã khai | Câu hỏi Q9, Q10 đang mở | Xác nhận hoặc đổi |
| #2 | Mỗi request có các dòng con, mỗi dòng = 1 Vị trí × 1 Loại thiết bị, có trạng thái và kết quả riêng | Chưa có thuật ngữ | Đặt tên khái niệm này |
| #2 | Ví dụ Indi Number `4M002401000B00094` = Item Code `4M002401000B` + Lot `00094` | Câu hỏi Q1 | Quy tắc cắt chính thức |
| [#6](https://github.com/trungkien87/LabTestSystem/issues/6) State machine | Hai cấp trạng thái. Cấp request: Đã yêu cầu / Đang xử lý / Hoàn thành / Quá hạn / Đã huỷ. Cấp dòng: Chờ nhận mẫu / Đã nhận mẫu / Đang đo / Hoàn thành. "Quá hạn" là một trạng thái riêng (275 request). "Làm mới" đưa Đang đo về Đã nhận mẫu. Huỷ chỉ khi chưa nhận mẫu hoặc quá hạn | Req 17, 24, 33 | Quá hạn là trạng thái hay cờ; trạng thái Error; điều kiện huỷ |
| [#7](https://github.com/trungkien87/LabTestSystem/issues/7) Spec | Common/Individual đã làm. Sửa spec Item Name ghi đè các Item Code còn Common. Xoá spec Item Name xoá luôn mọi spec Item Code, kể cả Individual. KB F-01: request hiện LL = 81, spec hiện tại LL = 0.81 | Req 16 | Request có snapshot spec tại lúc tạo không; quy tắc xoá |
| [#8](https://github.com/trungkien87/LabTestSystem/issues/8) Tạo request | Deadline = lúc chọn Sequence + Leadtime (phút). Chặn trùng Stage + Indi + Sequence. Số mẫu theo NPI/MASS (Suy luận: theo Build Type). Ảnh: người tạo request có Mã nhân viên `00000` | Req 18–21 | Mốc tính deadline; định danh người tạo |
| [#9](https://github.com/trungkien87/LabTestSystem/issues/9) Rack | Phân bổ theo Stages Allowed của tủ + Loại mẫu + Max Qty của ô (Suy luận) | Req 27 | Thuật toán và thứ tự ưu tiên |
| [#10](https://github.com/trungkien87/LabTestSystem/issues/10) Phân quyền | Vai trò × 23 màn × V/A/E/D. Phòng ban giới hạn Vị trí + Công đoạn. Thiếu dòng quyền Cấu hình IPQC. Màn Đổi mật khẩu chọn được tài khoản khác, không hỏi mật khẩu hiện tại (KB F-04) | Req 1, 2 | Mô hình phạm vi dữ liệu; tự đổi và reset mật khẩu |
| [#11](https://github.com/trungkien87/LabTestSystem/issues/11) Abnormal | Chưa có | Req 36 | Giữ nguyên phạm vi ticket |
| [#12](https://github.com/trungkien87/LabTestSystem/issues/12) Calibration | Chưa có | Biên bản 2026-10-09 | Giữ nguyên phạm vi ticket |
| [#13](https://github.com/trungkien87/LabTestSystem/issues/13) Kiến trúc | Service nối DB trực tiếp (Suy luận). Web HTTP. Thư mục server là ổ `D:` của máy chủ. FTP cấu hình trên web. Heartbeat "Service Auto". Cấu hình đọc log theo Vị trí × Công đoạn × Loại thiết bị, có công thức | Concept, req 3, 34 | Ranh giới Web–Service; giao thức; lưu file |
| [#15](https://github.com/trungkien87/LabTestSystem/issues/15) Mockup | Giao diện chưa theo DESIGN Rev01; tiêu đề chưa Việt hoá | DESIGN, F1 | Mockup theo DESIGN, tham khảo pattern ở mục 5 |
| [#16](https://github.com/trungkien87/LabTestSystem/issues/16) MVP | Luồng MVP đã chạy cho UV laser, RTR Etching, RTR Copper Plating | Đích map #1 | Phụ thuộc quyết định ở mục 7 |
| [#17](https://github.com/trungkien87/LabTestSystem/issues/17) Logfile | Cấu hình thật đã có, ví dụ: UV laser/VHX file `[x].csv` ô C6/C7; RTR Etching/Laser Microscope 42 nội dung, file `B_Plane(Point height…)` | | Xin maker các file log mẫu đã dùng để cấu hình |
| [#18](https://github.com/trungkien87/LabTestSystem/issues/18) NFR | HTTP không mã hoá. Dữ liệu test lẫn môi trường đang chạy (KB F-06). Dữ liệu mồ côi (F-05). Có audit Lý do + lịch sử. Mật khẩu 180/30 ngày | Checklist nhóm B, D, I | Ngưỡng và tiêu chí áp dụng |

## 7. Câu hỏi cho chủ dự án

- **Dạng đích của map.** Có hai hướng:
  - Giữ đích cũ: bộ hồ sơ bàn giao để maker viết hệ thống.
  - Đổi sang: spec "to-be" cộng danh sách thay đổi (gap/change request) so với hệ thống maker đang chạy, kèm tiêu chí nghiệm thu để chủ dự án verify.
  
  Quyết định này ảnh hưởng #13, #15, #16 và cách viết mọi ticket còn lại.
- **Phát hiện cần kiểm tra thêm** (Dữ kiện, chưa rõ nguyên nhân): request `R261022_0007` có kết quả NG ở danh sách và ở dòng chi tiết. Nhưng bảng Mặt A ở màn Chi tiết nội dung có 4/4 nội dung OK, và ảnh chụp không cho thấy Mặt B. Cần maker giải thích phán định NG đến từ đâu.
