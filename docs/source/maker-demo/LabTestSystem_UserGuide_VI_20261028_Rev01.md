# User Guide của bản demo maker (Rev01)

> Nguồn: `LabTestSystem_UserGuide_VI_20261028_Rev01.xlsx` (34 sheet), nhận ngày 2026-10-28. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Tọa độ ô ghi trong cột `Row` và tên cột. Xem [README.md](README.md) về nguồn gốc và mức tin cậy.

## Mục lục

- [Summary](#summary)
- [Revision](#revision)
- [Rev01_Changes](#rev01_changes)
- [Rev01_Findings](#rev01_findings)
- [Login_Dashboard](#login_dashboard)
- [Request](#request)
- [Receive](#receive)
- [Request Detail Content](#request-detail-content)
- [Statistics](#statistics)
- [Role Setting](#role-setting)
- [User Setting](#user-setting)
- [Department Setting](#department-setting)
- [Change Password](#change-password)
- [General Setting](#general-setting)
- [Stage](#stage)
- [Machine](#machine)
- [Equipment Type](#equipment-type)
- [Equipment](#equipment)
- [Build](#build)
- [Item](#item)
- [Location](#location)
- [Rack](#rack)
- [Rack Diagram](#rack-diagram)
- [Rack Layer](#rack-layer)
- [Layer Position](#layer-position)
- [IPQC Content](#ipqc-content)
- [IPQC Layout_Draft](#ipqc-layout_draft)
- [IPQC Config](#ipqc-config)
- [IPQC Spec ItemName_draft](#ipqc-spec-itemname_draft)
- [IPQC Spec ItemCode_draft](#ipqc-spec-itemcode_draft)
- [Service Monitor](#service-monitor)
- [Pending List](#pending-list)
- [History Result](#history-result)
- [Service Configuration](#service-configuration)

## Summary

TÀI LIỆU HƯỚNG DẪN SỬ DỤNG HỆ THỐNG LAB TEST SYSTEM<br>GUIDELINES USE LAB TEST SYSTEM <!-- A1 -->

| Row | A: No. | B: Module | C: Screen / Function | D | E: Ref | F: Pending Reason | G: Trạng thái Rev01 | H: Ghi chú thay đổi Rev01 | I: File Markdown (KB) |
|---|---|---|---|---|---|---|---|---|---|
| 4 | 1 | I, HOME | Home |  | #Home |  | Thay đổi | KPI, Ca, Service Auto, Báo cáo chất lượng | 01_Home.md |
| 5 | 2 | II, MONITOR | Request |  | #Request |  | Thay đổi | KPI, cột Kết quả đo, Quá hạn | 02_Request.md |
| 6 | 3 |  | Request Status |  | #Status |  | Thay đổi | Trạng thái: xem Glossary | 02_Request.md |
| 7 | 4 |  | Receive Request |  | #Receive |  | Thay đổi | KPI theo vị trí, Tủ đựng/Vị trí | 03_Receive.md |
| 8 | 5 |  | Request Content Detail |  | #Detail |  | Thay đổi | Vị trí, Số lượng, lần đo | 04_Request_Detail_Content.md |
| 9 | 6 | III, STATISTICS | Statistics |  | #Statistics |  | Tài liệu mới | Sheet Statistics | 05_Statistics.md |
| 10 | 7 | IV, SYSTEM SETTING | User Role Setting |  | #RoleSetting |  | Tài liệu mới | Sheet Role Setting | 06_System_Settings.md |
| 11 | 8 |  | User Setting |  | #UserSetting |  | Tài liệu mới | Sheet User Setting | 06_System_Settings.md |
| 12 | 9 |  | Department Setting |  | #DepartmentSetting |  | Tài liệu mới | Sheet Department Setting | 06_System_Settings.md |
| 13 | 10 | V, MASTER DATA | Stage |  | #Stage |  | Thay đổi | Stage Code | 07_MasterData_Production.md |
| 14 | 11 |  | Machine |  | #Machine |  | Thay đổi | Machine Code | 07_MasterData_Production.md |
| 15 | 12 |  | Equipment Type |  | #EquipmentType |  | Thay đổi | Code + Kiểu LogFile | 08_MasterData_Lab.md |
| 16 | 13 |  | Equipment |  | #Equipment |  | Thay đổi | Equipment Code | 08_MasterData_Lab.md |
| 17 | 14 |  | Build |  | #Build |  | Thay đổi | Build Code | 07_MasterData_Production.md |
| 18 | 15 |  | Item |  | #Item |  | Không đổi | Ref cũ trỏ nhầm #Build → sửa sang Item | 07_MasterData_Production.md |
| 19 | 16 |  | Location |  | #Location |  | Thay đổi | Sửa + Nhận mẫu | 08_MasterData_Lab.md |
| 20 | 17 | VI, MASTER DATA > RACK DEFINE | Rack |  | #Rack |  | Thay đổi | Sơ đồ thiết kế lại (sheet Rack Diagram) | 09_Rack_Storage.md |
| 21 | 18 |  | Rack Layer |  | #Layer | Chưa hoàn thiện lịch sử | Thay đổi | Xóa tầng, Disable/Enable | 09_Rack_Storage.md |
| 22 | 19 |  | Layer Position |  | #Position | Chưa hoàn thiện lịch sử | Thay đổi | Position Code hàng.cột | 09_Rack_Storage.md |
| 23 | 20 | VII, IPQC | IPQC Content |  | #Content |  | Thay đổi | Phân bổ Location & Equipment Type | 10_IPQC_Content_Layout_Config.md |
| 24 | 21 |  | IPQC Layout |  | #Layout |  | Thay đổi | File Template; xem thêm IPQC Config | 10_IPQC_Content_Layout_Config.md |
| 25 | 22 |  | IPQC Spec | IPQC Spec for ItemName | #SpecItemName |  | Thay đổi | Set/Not Set | 11_IPQC_Spec.md |
| 26 | 23 |  |  | IPQC Spec for ItemCode | #SpecItemCode |  | Thay đổi | Common/Individual | 11_IPQC_Spec.md |
| 27 | 24 | VIII, SERVICE READ FILE | Màn hình chính |  | #Monitor |  | Chưa xác minh | Service desktop | 12_Service_ReadFile.md |
| 28 | 25 |  | Pending Request |  | #PendingList |  | Chưa xác minh |  | 12_Service_ReadFile.md |
| 29 | 26 |  | History Request |  | #HistoryResult |  | Chưa xác minh |  | 12_Service_ReadFile.md |
| 30 | 27 |  | Config Service |  | #SettingConfig |  | Chưa xác minh |  | 12_Service_ReadFile.md |
| 31 | 28 | IV, SYSTEM SETTING (bổ sung) | Change Password |  | #ChangePassword |  | Màn mới | /changepassword | 06_System_Settings.md |
| 32 | 29 |  | General Setting |  | #GeneralSetting |  | Màn mới | Chính sách mật khẩu, FTP – /setting | 06_System_Settings.md |
| 33 | 30 | VII, IPQC (bổ sung) | IPQC Config (Cấu hình IPQC) |  | #IPQCConfig |  | Màn mới | /LogConfig – cấu hình đọc log | 10_IPQC_Content_Layout_Config.md |
| 34 | 31 | VI, RACK DEFINE (bổ sung) | Rack Diagram |  | #RackDiagram |  | Thiết kế lại | /Rack/Diagram | 09_Rack_Storage.md |
| 35 | 32 | TỔNG HỢP Rev01 | Rev01 Changes / Findings / Revision |  | #Rev01_Changes |  | Mới | Xem thêm Rev01_Findings, Revision | 99_Changelog.md / 98_Findings.md |

## Revision

LỊCH SỬ PHIÊN BẢN TÀI LIỆU <!-- A1 -->

| Row | A: Rev | B: Ngày | C: Nội dung | D: Phương pháp | E: Người thực hiện |
|---|---|---|---|---|---|
| 4 | Rev00 | (trước 2026-10-28) | SEEV-SSG User Guide_ Lab Test System 2026.xlsx – 23 sheet | — | — |
| 5 | Rev01 | 2026-10-28 | Thêm ghi chú cập nhật (cột R) cho 22 sheet cũ; thêm 8 sheet hướng dẫn mới (Statistics, Role Setting, User Setting, Department Setting, Change Password, General Setting, IPQC Config, Rack Diagram); thêm Rev01_Changes, Rev01_Findings; cập nhật Summary. Ảnh mới nằm trong bộ KB Markdown (thư mục images/), cột "Hình ảnh" ghi tên file | Rà soát read-only trên http://10.212.9.242:8082 (UI VI); không thao tác Lưu/Xoá. Phần Service desktop chưa xác minh | Claude (theo yêu cầu Đoàn Trung Kiên) |

## Rev01_Changes

TỔNG HỢP THAY ĐỔI Rev01 (rà soát 2026-10-28, read-only) <!-- A1 -->

| Row | A: Màn hình | B: Route | C: Trạng thái | D: Thay đổi chính | E: Sheet tương ứng | F: File Markdown (KB) |
|---|---|---|---|---|---|---|
| 4 | Home | /home | Thay đổi | Ca, Service Auto; 5 thẻ KPI có link; Báo cáo chất lượng OK/NG + %; mặc định 30 ngày | Login_Dashboard | 01_Home.md |
| 5 | Request | /request, /request/add | Thay đổi | Thẻ KPI; cột Kết quả đo; trạng thái Quá hạn; Mã nhân viên trong chi tiết; mặc định 30 ngày | Request | 02_Request.md |
| 6 | Receive Request | /RequestReceive | Thay đổi | Thẻ KPI theo vị trí (NG); cột Tủ đựng/Vị trí; Thời gian nhận/đo | Receive | 03_Receive.md |
| 7 | Request Detail Content | /Request/detail?PKID= | Thay đổi | Vị trí; Kết quả lần đo mới nhất; cột Số lượng; modal giá trị đo đầy đủ | Request Detail Content | 04_Request_Detail_Content.md |
| 8 | Statistics | /statistics | Tài liệu mới | Biểu đồ X/R theo Lot; lọc Công đoạn→Item Name→Item Code→Sequence | Statistics (mới) | 05_Statistics.md |
| 9 | User Role Setting | /group | Tài liệu mới | Vai trò + ma trận quyền View/Add/Edit/Delete (23 màn) | Role Setting (mới) | 06_System_Settings.md |
| 10 | User Setting | /account | Tài liệu mới | Người dùng; quy tắc mật khẩu; Thời hạn mật khẩu | User Setting (mới) | 06_System_Settings.md |
| 11 | Department Setting | /Department | Tài liệu mới | Gán Vị trí & Công đoạn cho phòng ban; lịch sử | Department Setting (mới) | 06_System_Settings.md |
| 12 | Change Password | /changepassword | Màn mới | Đổi/đặt lại mật khẩu theo tài khoản | Change Password (mới) | 06_System_Settings.md |
| 13 | General Setting | /setting | Màn mới | Chính sách mật khẩu; máy chủ FTP | General Setting (mới) | 06_System_Settings.md |
| 14 | Stage | /Stage | Thay đổi | Stage Code S01…; sắp xếp cột | Stage | 07_MasterData_Production.md |
| 15 | Machine | /Machine | Thay đổi | Machine Code M001… | Machine | 07_MasterData_Production.md |
| 16 | Equipment Type | /EquipmentType | Thay đổi | Equipment Type Code ET001…; Kiểu LogFile | Equipment Type | 08_MasterData_Lab.md |
| 17 | Equipment | /Equipment | Thay đổi | Equipment Code E001… | Equipment | 08_MasterData_Lab.md |
| 18 | Build | /Build | Thay đổi | Build Code B001… | Build | 07_MasterData_Production.md |
| 19 | Item | /item | Không đổi | Menu "Sản phẩm" | Item | 07_MasterData_Production.md |
| 20 | Location | /Location | Thay đổi | Thêm Sửa; checkbox Nhận mẫu | Location | 08_MasterData_Lab.md |
| 21 | Rack | /Rack, /Rack/Diagram | Thay đổi | Xem tầng; Sơ đồ thiết kế lại | Rack + Rack Diagram (mới) | 09_Rack_Storage.md |
| 22 | Rack Layer | /RackShelf | Thay đổi | Nút Xóa tầng ở khu lọc; Xem vị trí; Disable/Enable | Rack Layer | 09_Rack_Storage.md |
| 23 | Layer Position | /ShelfPosition | Thay đổi | Position Code hàng.cột; tự sinh; form Update | Layer Position | 09_Rack_Storage.md |
| 24 | IPQC Content | /IPQCContent | Thay đổi | Bảng phân bổ Location & Equipment Type; SPC Rule 1–8 | IPQC Content | 10_IPQC_Content_Layout_Config.md |
| 25 | IPQC Layout | /Layout | Thay đổi | Lọc Vị trí→Công đoạn→Loại TB; File Template | IPQC Layout_Draft | 10_IPQC_Content_Layout_Config.md |
| 26 | IPQC Config | /LogConfig | Màn mới | Cấu hình đọc log theo Kiểu LogFile; công thức; import/export Excel | IPQC Config (mới) | 10_IPQC_Content_Layout_Config.md |
| 27 | IPQC Spec ItemName | /spec/itemname | Thay đổi | Trạng thái Set/Not Set | IPQC Spec ItemName_draft | 11_IPQC_Spec.md |
| 28 | IPQC Spec ItemCode | /spec/itemcode | Thay đổi | Trạng thái Common/Individual | IPQC Spec ItemCode_draft | 11_IPQC_Spec.md |
| 29 | Service (4 màn) | (desktop) | Chưa xác minh | Giữ nguyên nội dung cũ | Service Monitor, Pending List, History Result, Service Configuration | 12_Service_ReadFile.md |
| 30 | Header | — | Mới | Chọn ngôn ngữ EN/VI | — | 00_INDEX.md |

## Rev01_Findings

PHÁT HIỆN TRONG QUÁ TRÌNH RÀ SOÁT Rev01 <!-- A1 -->

| Row | A: ID | B: Mức | C: Màn hình | D: Dữ kiện quan sát | E: Suy luận / Rủi ro | F: Đề xuất |
|---|---|---|---|---|---|---|
| 4 | F-01 | Cao | Chi tiết nội dung yêu cầu | R261022_0007 "Tỷ lệ đường kính lỗ 75 Bottom/Top": hiển thị LL = 81, Avg 0.88, OK; Spec hiện tại LL = 0.81 | Lỗi hiển thị số hoặc spec sửa sau khi tạo request | Dev kiểm tra hiển thị/snapshot spec |
| 5 | F-02 | Trung bình | Cài đặt vai trò | Không có dòng quyền cho Cấu hình IPQC; "Cài d?t chung" lỗi encoding | Không phân quyền riêng màn cấu hình đọc log | Bổ sung permission; sửa encoding |
| 6 | F-03 | Thấp | Nhiều màn | Tiêu đề/nhãn chưa Việt hoá khi chọn VI | Không nhất quán | Bổ sung resource VI |
| 7 | F-04 | Trung bình | Đổi mật khẩu | Không có ô mật khẩu hiện tại; chọn được tài khoản khác | Phụ thuộc phân quyền (chưa thử) | Xác nhận phân quyền; yêu cầu mật khẩu hiện tại khi tự đổi |
| 8 | F-05 | Trung bình | Thiết bị | Nhiều thiết bị Loại thiết bị = "ET002" (không tồn tại) | Dữ liệu mồ côi | Gán lại loại thiết bị |
| 9 | F-06 | Thấp | Danh mục | Dữ liệu test trong môi trường đang dùng (TestFullF5, TestDF1, Stage Test 1609, Rack test, TestRole…) | Lẫn vào báo cáo | Dọn dữ liệu/tách môi trường |
| 10 | F-07 | Thấp | Tầng tủ | Nhãn "Tầng 01" nhưng dữ liệu "Layer 01" | Không nhất quán | Thống nhất |
| 11 | F-08 | Thấp | Nội dung IPQC | Icon (?) SPC Rule không hiển thị giải thích | Thiếu hướng dẫn | Bổ sung mô tả rule |
| 12 | F-09 | Thông tin | Yêu cầu | Bộ lọc Mã máy, Item Code có dấu * | Gây hiểu nhầm | Bỏ * |
| 13 | F-10 | Thông tin | Nhiều màn | Nút/modal ẩn: Save Selected, Delete Row/Column, Model/SN/Maker | Chức năng dở dang | Xác nhận với dev |
| 14 | F-11 | Thông tin | Cài đặt chung | Thông tin FTP hiển thị cho người có quyền xem | Lộ thông tin kết nối | Giới hạn quyền; che giá trị |

## Login_Dashboard

> Sheet có 14 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN ĐĂNG NHẬP VÀ XEM THÔNG TIN TRANG CHỦ<br>GUIDELINES FOR LOGGING IN AND VIEWING THE HOME PAGE <!-- A1 -->

I, Hướng dẫn Đăng nhập và Xem thông tin Trang chủ <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Trang chủ thay đổi: thêm Ca, Service Auto ON/OFF; 5 thẻ KPI (Yêu cầu/Đã nhận mẫu/Đang đo/Đã hoàn thành/Đã huỷ) có link Chi tiết → màn Yêu cầu; biểu đồ đổi thành "Báo cáo chất lượng" OK/NG + % theo 1 Công đoạn; mặc định 30 ngày. Ảnh mới: images/01_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Truy cập: 10.212.9.242:8082<br>Đăng nhập hệ thống bằng tài khoản và mật khẩu được cấp |  |  |  |
| 6 | 2 | Sau khi đăng nhập, màn Home của hệ thống hiển thị |  |  |  |
| 7 | 2. Search |  |  |  |  |
| 8 | 2.1 | Chọn các thông tin trên biểu đồ<br>\- Stage: Các công đoạn sử dụng trong hệ thống<br>\- Machine: hiển thị các máy thuộc Stage |  |  |  |
| 9 | 2.2 | Biểu đồ hiển thị các dữ liệu trùng với Stage và các Machine đã chọn |  |  |  |
| 10 | 2.3 | Lọc dữ liệu theo ngày<br>\- Chọn các thông tin From date - To date<br>\- Chọn thông tin Quick Select:<br>\+ Today: Ngày hiện tại<br>\+ This week: Tuần hiện tại<br>\+ This month: Tháng hiện tại<br>\+ Last 30 Days: 30 ngày gần nhất |  |  |  |
| 11 | 2.4 | Nhấn Search |  |  |  |
| 12 | 2.5 | Biểu đồ hiển thị các dữ liệu theo ngày đã chọn |  |  |  |
| 13 | 3. Xem chi tiết dữ liệu trong biểu đồ |  |  |  |  |
| 14 | 3.1 | Nhấn Cột dữ liệu Machine trên biểu đồ |  |  |  |
| 15 | 3.2 | Hiển thị các ItemName theo Machine > Nhấn Cột dữ liệu Machine trên biểu đồ |  |  |  |
| 16 | 3.3 | Hiển thị các ItemCode theo ItemName > Nhấn Cột dữ liệu ItemCode trên biểu đồ |  |  |  |
| 17 | 3.4 | Hiển thị các IPQC Content theo ItemCode |  |  |  |
| 18 | 3.5 | Trên biểu đồ hiển thị các Lot No, Value, các tiêu chuẩn được set cho content |  |  |  |
| 19 | 4. Truy cập các màn hình khác |  |  |  |  |
| 20 | 4.1 | Tại màn hình đang truy cập, Nhấn trên thanh menu |  |  |  |
| 21 | 4.2 | Các tên hiển thị tương ứng với chức năng |  |  |  |

## Request

> Sheet có 37 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ YÊU CẦU ĐO<br>GUIDELINES FOR USING THE MEASUREMENT REQUEST MANAGEMENT FUNCTION <!-- A1 -->

II, Hướng dẫn sử dụng các màn hình Monitor > Quản lý Yêu cầu đo <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm thẻ KPI (Yêu cầu/Đang xử lý/Đã hoàn thành/Quá hạn/Đã huỷ), cột KẾT QUẢ ĐO, bộ lọc Trạng thái có "Quá hạn", mặc định 30 ngày (bước 2.2 ghi 7 ngày – đã cũ). Form Tạo yêu cầu: trường auto bị khoá, nhãn "Thời hạn". Modal Chi tiết thêm Mã nhân viên. Ảnh: images/02_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Request<br>Request No. được tự động tạo theo định dạng RYYMMDD_XXXX, trong đó<br>\+ YY là 2 số cuối của năm<br>\+ MM là tháng<br>\+ DD là ngày<br>\+ XXXX là số thứ tự Request trong ngày.<br>Ví dụ: Request thứ 12 ngày 01/07/2026 → R260701_0012 |  |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Có thể nhập thông tin tìm kiếm:<br>\- Nhập Request No<br>\- Chọn Stage Name<br>\- Chọn Machine ID theo công đoạn<br>\- Nhập Indi Number<br>\- Chọn Item Code<br>\- Chọn Status<br>\- Chọn ngày From - To nếu không chọn mặc định 7 ngày gần nhất |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Tạo yêu cầu/Create Request |  |  |  |  |
| 12 | 3.1 | Nhấn Create Request trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Create Request hiển thị |  |  |  |
| 14 |  | Có thể nhấn View Detail để xem các nội dung đo và tiêu chuẩn được cài đặt cho Stage Name + Item Code + Sequence khi tạo yêu cầu |  |  |  |
| 15 | 3.3.1 | Nhấn chọn vào Machine ID > Scan Machine ID |  |  |  |
| 16 | 3.4.1 | Scan thành công, hệ thống tự động lấy được dữ liệu Machine Name và Stage Name |  |  |  |
| 17 | 3.5.1 | Scan Indication Number tại ô nhập tương ứng |  |  |  |
| 18 | 3.6.1 | Scan thành công, hệ thống tự động lấy được dữ liệu:<br>\+ Item Name: Check từ Item Code<br>\+ Item Code: Cắt từ Indication Number<br>\+ Lot No: Cắt từ Indication Number<br>\+ Build: Được nhập theo Item Code (đã nhập tại màn Quản lý Item) |  |  |  |
| 19 | 3.7.1 | Dựa trên thông tin Stage Name + Item Code > Hệ thống hiển thị danh sách Sequence (đã khai báo tại IPQC Spec) |  |  |  |
| 20 | 3.8.1 | Chọn Sequence cần tạo Request |  |  |  |
| 21 | 3.9.1 | Dựa trên nhóm dữ liệu Stage Name + ItemCode + Sequence, hệ thống lấy dữ liệu như sau:<br>1. Stage Name → Nội dung đo / Thiết bị / Vị trí<br>2. Stage Name + ItemCode + Sequence → Tiêu chuẩn / Leadtime<br>3. Deadline = Thời điểm chọn Sequence + Leadtime (phút) |  |  |  |
| 22 | 3.10.1 | Có thể nhập Comment hoặc bỏ trống |  |  |  |
| 23 | 3.11.1 | Kiểm tra các thông tin hiển thị > Nhấn Save để tạo Request<br>Lưu ý: Nếu Stage + IndiNumber + Sequence này đã được tạo Request trước đấy (trừ các request đã Cancel) → hệ thống sẽ chặn không cho tạo lại |  |  |  |
| 24 | 3.12.1 | Yêu cầu được tạo thành công, có trạng thái Requested |  |  |  |
| 25 | 3.11.2 | Nhấn Clear để xóa các thông tin nhanh chóng |  |  |  |
| 26 | 3.3.2 | Nhấn Back để quay lại màn hình theo dõi yêu cầu |  |  |  |
| 27 | 4. In mã yêu cầu đính kèm mẫu đo/Print QR Code |  |  |  |  |
| 28 | 4.1 | Tại màn Request, tích vào ô vuông ☐ bên trái Request cần tạo QR Code |  |  |  |
| 29 | 4.2 | Nhấn Print QR Code để thực hiện in mã QR của Request |  |  |  |
| 30 | 4.3 | Hệ thống hiển thị hộp thoại in trên trình duyệt FireFox |  |  |  |
| 31 | 4.3 | Hệ thống hiển thị hộp thoại in trên trình duyệt Microsoft Edge |  |  |  |
| 32 | 4.5.1 | Kiểm tra các thông tin  > Nhấn Print tại máy có kết nối tới máy in QR |  |  |  |
| 33 | 4.5.2 | Nếu người dùng không in nữa, hoặc bổ sung thêm QR để in > Nhấn Cancel và thực hiện chọn lại |  |  |  |
| 34 | 5. Xem thông tin chi tiết của yêu cầu và các trạng thái hiển thị/Detail and Status |  |  |  |  |
| 35 | 5.1 | Có thể thực hiện tìm kiếm để có thể rút gọn số lượng hiển thị trên màn hình |  |  |  |
| 36 | 5.2 | Nhấn Detail tại request cần xem thông tin |  |  |  |
| 37 | 5.3 | Hộp thoại thông tin chi tiết hiển thị<br>1 Location + 1 Equipment Type = 1 Detail của Request |  |  |  |
| 38 | 5.4 | Với Request mới tạo yêu cầu, chưa nhận mẫu tại Location nào sẽ hiển thị Requested<br>Hiển thị nút Cancel Request cho phép người dùng hủy yêu cầu |  |  |  |
| 39 | 5.5 | Request Detail đã nhận mẫu, chưa thực hiện đo hiển thị Received |  |  |  |
| 40 | 5.6 | Request Detail đã được scan tại Service để thực hiện đo hiển thị Measuring:<br>\+ Equipment ID: Mã của thiết bị đã scan mẫu<br>\+ Operator ID: Của người thực hiện đo<br>\+ Error Log: Nếu quá trình đọc file bị lỗi sẽ hiển thị |  |  |  |
| 41 | 5.7 | Request Detail đã hoàn thành đo, có kết quả trả về hiển thị Finished:<br>\+ Equipment ID: Mã của thiết bị đo<br>\+ Operator ID: của người thực hiện đo cuối cùng<br>\+ Judgment: Kết quả khi đọc file thành công |  |  |  |
| 42 | 5.8 | Thời điểm hiện tại > Deadline, Request chuyển sang Delayed → Nhấn Cancel Request để hủy |  |  |  |
| 43 | 5.9.1 | Nhấn ngoài hộp thoại > Hệ thống đóng hộp thoại Detail |  |  |  |
| 44 | 5.9.2 | Nhấn Detail tại cột Action để xem chi tiết kết quả đo |  |  |  |
| 45 | 5.10.2 | Màn hình Request Detail Content hiển thị:<br>\+ Hiển thị các thông tin của Request<br>\+ Nội dung đo của Request<br>\+ Các giá trị đo và kết quả phán định (nếu đã thực hiện đo) |  |  |  |

## Receive

> Sheet có 20 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG NHẬN MẪU ĐO<br>GUIDELINES FOR USING THE SAMPLE RECEIVING FUNCTION <!-- A1 -->

II, Hướng dẫn sử dụng các màn hình Monitor > Chức năng Nhận mẫu tại vị trí đo <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm thẻ KPI theo Vị trí (có NG), cột TỦ ĐỰNG/VỊ TRÍ; modal chi tiết thêm Thời gian nhận/Thời gian đo. Lưu ý: đánh số bước mục 3 "Tìm kiếm" đang dùng 2.x. Ảnh: images/03_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Receive |  |  |  |
| 6 | 2 | Người dùng chọn Location tại vị trí cần thực hiện các thao tác |  |  |  |
| 7 |  | Có thể nhấn các Tab Uncompleted/Completed để kiểm tra trạng thái hoàn thành các Request đo tại Location |  |  |  |
| 8 | 3. Tìm kiếm/Search |  |  |  |  |
| 9 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 10 | 2.2 | Có thể nhập thông tin tìm kiếm:<br>\- Nhập Request No<br>\- Chọn Stage Name<br>\- Chọn Machine ID theo công đoạn<br>\- Chọn Item Code<br>\- Chọn ngày From - To nếu không chọn mặc định 7 ngày gần nhất |  |  |  |
| 11 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 12 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 13 | 3. Nhận mẫu theo vị trí đo/Receive Sample |  |  |  |  |
| 14 | 3.1 | Người dùng chọn Location tại vị trí cần thực hiện nhận mẫu |  |  |  |
| 15 | 3.2 | Nhấn chuột vào ô Request No và Scan QR của request |  |  |  |
| 16 | 3.3 | Khi nhận được thông tin, hệ thống hiển thị hộp thoại xác nhận |  |  |  |
| 17 | 3.4.1 | Xác nhận nhận mẫu đo tại Location > Nhấn YES<br>Người dùng không thể hoàn tác thao tác này |  |  |  |
| 18 | 3.5.1 | Nhận mẫu thành công hệ thống hiển thị thông báo cho người dùng:<br>\+ Request No đã được nhận mẫu<br>\+ Trạng thái Request thay đổi từ Requested → Received<br>\+ Cập nhật thông tin Rack chứa mẫu<br>\+ Cập nhật vị trí Position trong Rack chứa mẫu |  | Sau đó người dùng cần đặt mẫu đo tại vị trí phân bổ đã được thông báo |  |
| 19 | 3.4.2 | Cần scan lại mẫu khác, chưa nhận được mẫu > Nhấn Cancel |  |  |  |
| 20 | 3.5.1 | Hộp thoại xác nhận được đóng lại, màn hình hiển thị thông tin nhận mẫu của Location hiện tại |  |  |  |
| 21 | 4. Xem thông tin chi tiết của yêu cầu và các trạng thái hiển thị/Detail and Status |  |  |  |  |
| 22 | 4.1 | Có thể thực hiện tìm kiếm để có thể rút gọn số lượng hiển thị trên màn hình |  |  |  |
| 23 | 4.2 | Nhấn nút xem tại cột Action của request cần xem thông tin |  |  |  |
| 24 | 4.3 | Hộp thoại hiển thị chi tiết các nội dung đo ItemCode của công đoạn tại Location<br>1 Equipment Type = 1 Detail của Request |  |  |  |
| 25 | 4.4.1 | Nhấn Detail tại cột Action để xem chi tiết kết quả đo |  |  |  |
| 26 | 4.5.1 | Màn hình Request Detail Content hiển thị:<br>\+ Hiển thị các thông tin của Request<br>\+ Nội dung đo của Request<br>\+ Các giá trị đo và kết quả phán định (nếu đã thực hiện đo) |  |  |  |
| 27 | 4.4.2 | Nhấn ngoài hộp thoại > Hệ thống đóng hộp thoại Detail |  |  |  |

## Request Detail Content

> Sheet có 15 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN TRUY CẬP VÀ XEM CHI TIẾT THÔNG TIN YÊU CẦU VÀ GIÁ TRỊ ĐO<br>GUIDELINES FOR ACCESSING AND VIEWING REQUEST DETAILS AND MEASUREMENT RESULTS <!-- A1 -->

II, Hướng dẫn sử dụng các màn hình Monitor > Truy cập và xem chi tiết thông tin yêu cầu <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm trường Vị trí, "Kết quả lần đo mới nhất: N", cột SỐ LƯỢNG; modal giá trị đo hiển thị UL_X/UCL_X/Avg_X/LCL_X/LL_X/Value_R và nút chuyển Lần đo. Phát hiện F-01 (LL hiển thị 81 vs spec 0.81). Ảnh: images/04_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1. Cách truy cập màn hình |  |  |  |  |
| 6 | 1.1.1 | Cách truy cập từ màn Request > Nhấn Detail ở cột Action |  |  |  |
| 7 | 1.2.1 | Hộp thoại Detail của Request hiển thị > Nhấn Detail tại cột Action |  |  |  |
| 8 | 1.1.2 | Cách truy cập từ màn Receive > Người dùng cần thực hiện chọn Location > Nhấn nút xem tại cột Action |  |  |  |
| 9 | 1.2.2 | Hộp thoại Detail của Request tại Location hiển thị > Nhấn Detail tại cột Action |  |  |  |
| 10 | 2 | Màn hình Request Detail Content hiển thị:<br>\+ Hiển thị các thông tin của Request<br>\+ Nội dung đo của Request<br>\+ Các giá trị đo và kết quả phán định (nếu đã thực hiện đo) |  |  |  |
| 11 | 3. Các thông tin hiển thị trên màn hình |  |  |  |  |
| 12 | 3.1 | Hiển thị thông tin chung:<br>\+ Request No: Mã yêu cầu<br>\+ Stage Name: Công đoạn yêu cầu<br>\+ Machine ID: Máy yêu cầu đo<br>\+ Indication Number: Thông tin Indi cần đo<br>\+ Item Name: Item Name yêu cầu đo<br>\+ Item Code: Item Code yêu cầu đo<br>\+ Lot No: Lot yêu cầu đo<br>\+ Build: Thông tin Build của Item Code<br>\+ Sequence: Sequence nội dung đo cho Item của công đoạn<br>\+ Status: Trạng thái của Detail <br>\+ Comment (nếu có nhập tại bước tạo yêu cầu) |  |  |  |
| 13 | 3.2 | Khi màn Request Detail ở trạng thái Requested, Received sẽ bỏ trống ô:<br>\+ Equipment ID: Mã thiết bị đo<br>\+ Dir Path Server: Đường dẫn thư mục lưu trữ kết quả đo lần cuối trên Server |  |  |  |
| 14 | 3.3 | Khi màn Request Detail ở trạng thái Measuring, Completed sẽ có các thông tin:<br>\+ Equipment ID: Mã thiết bị đo<br>\+ Dir Path Server: Đường dẫn thư mục lưu trữ kết quả đo lần cuối trên Server<br>\+ Nếu trạng thái là Completed → Cột Judgment của các Side hiển thị kết quả OK/NG |  |  |  |
| 15 | 3.4 | Có thể nhấn icon copy để copy path server |  |  |  |
| 16 | 4. Cách xem các giá trị đo/Value Detail |  |  |  |  |
| 17 | 4.1 | Tại màn Request Detail Content |  |  |  |
| 18 | 4.2 | Người dùng nhấn vào dòng IPQC Content tại Side A/B |  |  |  |
| 19 | 4.3 | Hộp thoại các giá trị đo của IPQC Content hiển thị |  |  |  |
| 20 | 4.4.1 | Nếu nội dung đã đo thành công<br>→ Hộp thoại hiển thị các Value đã đọc tại Service, tự động tính giá trị trung bình của các Value |  |  |  |
| 21 | 4.5.1 | Có thể nhấn vào các lần đo để xem lại các giá trị đo |  |  |  |
| 22 | 4.4.2 | Nếu nội dung chưa thực hiện đo lần nào<br>→ Hộp thoại sẽ trống các giá trị |  |  |  |

## Statistics

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG THỐNG KÊ<br>GUIDELINES FOR USING THE STATISTICS FUNCTION <!-- A1 -->

III, Hướng dẫn sử dụng Thống kê > Biểu đồ X/R theo Lot  (route /statistics) <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Chọn menu THỐNG KÊ > Thống kê → màn hình Thống kê hiển thị | images/05_statistics_empty.jpg |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Chọn lần lượt (bắt buộc):<br>\- Tên công đoạn<br>\- Item Name (lọc theo công đoạn)<br>\- Item Code (lọc theo Item Name)<br>\- Sequence (lọc theo Item Code) |  | Danh sách Sequence lấy từ Tiêu chuẩn IPQC đã khai báo |  |
| 8 | 2.2 | Tuỳ chọn: chọn Nội dung IPQC (bỏ trống = tất cả); chỉnh Từ ngày* – Đến ngày* (mặc định 7 ngày gần nhất) |  |  |  |
| 9 | 2.3 | Nhấn Tìm kiếm |  |  |  |
| 10 | 2.4 | Nhấn Đặt lại > hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Đọc kết quả/Result |  |  |  |  |
| 12 | 3.1 | Kết quả chia panel Side A / Side B (nút Thu gọn). Mỗi Nội dung IPQC có 2 biểu đồ:<br>\+ "<Nội dung> - X (Side A)": trục Y = X (Avg Value), trục X = LotNo; series X Value, LL, UL<br>\+ "<Nội dung> - R (Side A)": biểu đồ R | images/05_statistics_result.jpg | Không có dữ liệu trong khoảng ngày → biểu đồ trống |  |

## Role Setting

HƯỚNG DẪN CÀI ĐẶT VAI TRÒ VÀ PHÂN QUYỀN<br>GUIDELINES FOR USER ROLE SETTING <!-- A1 -->

IV, Hướng dẫn Cài đặt hệ thống > Cài đặt vai trò  (route /group) <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Chọn CÀI ĐẶT HỆ THỐNG > Cài đặt vai trò → danh sách vai trò: # \| VAI TRÒ \| HÀNH ĐỘNG [Phân quyền (chìa khoá) \| Sửa \| Xoá] | images/06_role_list.jpg |  |  |
| 6 | 2 | Tìm kiếm: nhập Vai trò → Tìm kiếm; Đặt lại để về mặc định |  |  |  |
| 7 | 3. Thêm vai trò/Insert Role |  |  |  |  |
| 8 | 3.1 | Nhấn + Thêm mới → màn "Cài đặt vai trò - Thêm mới" | images/06_role_add.jpg |  |  |
| 9 | 3.2 | Nhập Vai trò* → nhấn Thêm mới để lưu; Quay lại để huỷ |  | Tên vai trò không trùng (suy luận) |  |
| 10 | 4. Phân quyền/Permission |  |  |  |  |
| 11 | 4.1 | Nhấn icon chìa khoá tại vai trò → hộp thoại "Phân quyền vai trò: <tên>" | images/06_role_permission.jpg |  |  |
| 12 | 4.2 | Tích quyền VIEW (XEM) / ADD (THÊM) / EDIT (SỬA) / DELETE (XÓA) cho từng màn hình. Tích ô tiêu đề cột = chọn cả cột |  | Danh sách 23 màn: Request, Receive Request, Statistics, User Role Setting, User Setting, Department Setting, Stage, Machine, Equipment Type, Equipment, Build, Item, Location, Rack, Rack Layer, Layer Position, IPQC Content, IPQC Layout, IPQC Spec ItemName, IPQC Spec ItemCode, Home, Cài đặt chung, Change Password |  |
| 13 | 4.3 | Nhấn Lưu để áp dụng; nhấn X để đóng không lưu |  | Cảnh báo: không bỏ quyền của chính vai trò Administrator đang dùng. Chưa có dòng quyền cho "Cấu hình IPQC" (F-02) |  |
| 14 | 5. Sửa / Xoá vai trò |  |  |  |  |
| 15 | 5.1 | Nhấn Sửa để đổi tên; nhấn Xoá để xoá vai trò |  | Chưa xác minh điều kiện xoá khi còn người dùng thuộc vai trò |  |

## User Setting

HƯỚNG DẪN CÀI ĐẶT NGƯỜI DÙNG<br>GUIDELINES FOR USER SETTING <!-- A1 -->

IV, Hướng dẫn Cài đặt hệ thống > Cài đặt người dùng  (route /account) <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Danh sách: # \| MÃ NHÂN VIÊN \| HỌ TÊN \| EMAIL \| PHÒNG BAN \| VAI TRÒ \| NGÀY TẠO \| HÀNH ĐỘNG [Sửa \| Xoá] |  |  |  |
| 6 | 2 | Tìm kiếm: Họ tên, Mã nhân viên, Phòng ban, Vai trò → Tìm kiếm / Đặt lại |  |  |  |
| 7 | 3. Thêm người dùng/Insert User |  |  |  |  |
| 8 | 3.1 | Nhấn + Thêm mới → "Cài đặt người dùng - Thêm mới" | images/07_user_add.jpg |  |  |
| 9 | 3.2 | Nhập:<br>\- Họ tên*<br>\- Mã nhân viên*<br>\- Mật khẩu*<br>\- Email<br>\- Phòng ban (nhập tự do)<br>\- Vai trò* (chọn)<br>\- Thời hạn mật khẩu (checkbox, mặc định tích) |  | Quy tắc mật khẩu: ≥8 ký tự; có chữ hoa & chữ thường; ≥1 số; ≥1 ký tự đặc biệt ! @ # $ % ^ & * ( ) _ + - = [ ] { } \| ; ' : " , . < > / ? |  |
| 10 | 3.3 | Nhấn Lưu; Đặt lại để xoá nhập; Quay lại để về danh sách |  |  |  |
| 11 | 4. Cập nhật/Update |  |  |  |  |
| 12 | 4.1 | Nhấn Sửa → "Cài đặt người dùng - Cập nhật": Họ tên*, Mã nhân viên*, Email, Phòng ban, Vai trò*, Thời hạn mật khẩu → Lưu |  | Không có ô mật khẩu; đặt lại mật khẩu dùng màn Đổi mật khẩu |  |

## Department Setting

HƯỚNG DẪN CÀI ĐẶT PHÒNG BAN<br>GUIDELINES FOR DEPARTMENT SETTING <!-- A1 -->

IV, Hướng dẫn Cài đặt hệ thống > Cài đặt phòng ban  (route /Department) <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Danh sách: # \| PHÒNG BAN \| VỊ TRÍ \| CÔNG ĐOẠN \| MÔ TẢ \| MÃ NHÂN VIÊN \| HÀNH ĐỘNG [Sửa \| Lịch sử \| Xoá]; lọc theo Phòng ban | images/08_department_list.jpg | Mục đích (suy luận): giới hạn Vị trí & Công đoạn mà phòng ban được thao tác/xem |  |
| 6 | 2. Thêm cấu hình/Insert |  |  |  |  |
| 7 | 2.1 | Nhấn + Thêm mới → hộp thoại "Thêm mới cấu hình Phòng Ban" | images/08_department_add.jpg |  |  |
| 8 | 2.2 | Chọn Phòng ban*; chọn Vị trí (Multi-Select) và Công đoạn (Multi-Select) – có Select All / Đặt lại / "-- Tất cả --"; nhập Mô tả |  | Vị trí hiển thị kèm mã, vd QA Lab - F1 (F1L01); Công đoạn kèm mã, vd 2DID (S01) |  |
| 9 | 2.3 | Nhấn Lưu; Cancel để huỷ |  |  |  |
| 10 | 3. Sửa / Xoá / Lịch sử |  |  |  |  |
| 11 | 3.1 | Sửa hoặc Xoá: bắt buộc nhập Lý do* |  |  |  |
| 12 | 3.2 | Lịch sử (từng dòng hoặc icon tổng quát "Department Change History"): Phòng ban \| Hành động \| Vị trí \| Công đoạn \| Chi tiết thay đổi \| Mô tả \| Lý do \| Mã nhân viên \| Ngày tạo |  |  |  |

## Change Password

HƯỚNG DẪN ĐỔI MẬT KHẨU<br>GUIDELINES FOR CHANGING PASSWORD <!-- A1 -->

IV, Hướng dẫn Cài đặt hệ thống > Đổi mật khẩu  (route /changepassword) <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Chọn CÀI ĐẶT HỆ THỐNG > Đổi mật khẩu | images/09_change_password.jpg |  |  |
| 6 | 2 | Tài khoản: mặc định tài khoản đang đăng nhập; người có quyền có thể chọn tài khoản khác để đặt lại mật khẩu |  | Không có ô "Mật khẩu hiện tại" (F-04) |  |
| 7 | 3 | Nhập Mật khẩu mới theo Quy tắc đặt mật khẩu |  |  |  |
| 8 | 4 | Nhập Xác nhận mật khẩu mới (trùng mật khẩu mới) → nhấn Lưu |  |  |  |

## General Setting

HƯỚNG DẪN CÀI ĐẶT CHUNG<br>GUIDELINES FOR GENERAL SETTING <!-- A1 -->

IV, Hướng dẫn Cài đặt hệ thống > Cài đặt chung  (route /setting) <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1. Chính sách mật khẩu/Password Policy |  |  |  |  |
| 6 | 1.1 | Số ngày hết hạn mật khẩu: số nguyên > 0 (hiện tại 180 ngày) | images/10_general_setting.jpg |  |  |
| 7 | 1.2 | Số ngày nhắc trước khi hết hạn: > 0 và < số ngày hết hạn (hiện tại 30 ngày) |  |  |  |
| 8 | 1.3 | Thay đổi mật khẩu sau khi reset bởi admin: tích → bắt buộc đổi ở lần đăng nhập tiếp theo |  |  |  |
| 9 | 1.4 | Áp dụng quy tắc đặt mật khẩu: tích → bắt buộc quy tắc phức tạp; không tích → tự do |  |  |  |
| 10 | 1.5 | Nhấn Lưu |  |  |  |
| 11 | 2. Cài đặt máy chủ FTP/FTP Server |  |  |  |  |
| 12 | 2.1 | Nhập IP Server*, Port Server*, User*, Mật khẩu*, Remote Directory* → Lưu |  | Cảnh báo: ghi lại giá trị cũ trước khi sửa (rollback); kiểm tra đồng bộ sau khi lưu. Không ghi giá trị thật vào tài liệu |  |

## Stage

> Sheet có 29 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ THÔNG TIN CÔNG ĐOẠN<br>GUIDELINES FOR USING THE STAGE MANAGEMENT FUNCTION <!-- A1 -->

V, Hướng dẫn sử dụng chức năng Quản lý Master Data > Quản lý Công đoạn <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm cột STAGE CODE tự sinh (S01…), sắp xếp cột; form "Quản lý Công đoạn - Thêm mới": Tên công đoạn*, Loại mẫu* (Sheet/Block/Pcs), Mô tả. Ảnh: images/11_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Stage Management |  |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Nhập Stage Name |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm công đoạn mới/Insert Stage |  |  |  |  |
| 12 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Insert hiển thị |  |  |  |
| 14 | 3.3.1 | Nhập Stage Name (bắt buộc) |  | Chú ý: Thông tin Stage Name là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 15 | 3.4.1 | Chọn Sample Type (bắt buộc) |  |  |  |
| 16 | 3.5.1 | Nhập Description hoặc bỏ qua |  |  |  |
| 17 | 3.6.1 | Nhấn Save để lưu thông tin |  |  |  |
| 18 | 3.7.1 | Lưu thông tin thành công, hiển thị màn hình quản lý, dữ liệu được chèn vào bảng |  |  |  |
| 19 | 3.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 20 | 4. Cập nhật thông tin công đoạn/Update Stage |  |  |  |  |
| 21 | 4.1 | Nhấn Edit tại dòng cần thay đổi |  |  |  |
| 22 | 4.2 | Hệ thống hiển thị form và fill các thông tin cũ chính xác |  |  |  |
| 23 | 4.3.1 | Nhập các thông tin sau:<br>\- Nhập Stage Name<br>\- Chọn Sample Type<br>\- Nhập Description (nếu có) |  | Chú ý: Thông tin Stage Name là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 24 | 4.4.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 25 | 4.5.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 26 | 4.6.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 27 | 4.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 28 | 5. Xóa dữ liệu công đoạn/Delete Stage |  |  |  |  |
| 29 | 5.1 | Nhấn Delete tại dòng có dữ liệu cần xóa, yêu cầu:<br>\- Không có Machine nào phụ thuộc<br>\- Chưa khai báo IPQC Content nào |  |  |  |
| 30 | 5.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 31 | 5.3.1 | Nhấn Save > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 32 | 5.3.2 | Nhấn ngoài hộp thoại > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 33 | 6. Xem lịch sử chỉnh sửa của Công đoạn/History Record |  |  |  |  |
| 34 | 6.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 35 | 6.2.1 | Hộp thoại lịch sử của Công đoạn hiển thị |  | Chú ý: Với các công đoạn đã xóa khỏi hệ thống, người dùng vào màn lịch sử tổng hợp để kiểm tra |  |
| 36 | 6.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 37 | 6.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 38 | 6.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý Công đoạn |  |  |  |

## Machine

> Sheet có 27 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ THÔNG TIN MÁY<br>GUIDELINES FOR USING THE MACHINE MANAGEMENT FUNCTION <!-- A1 -->

V, Hướng dẫn sử dụng chức năng Quản lý Master Data > Quản lý Máy <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm cột MACHINE CODE (M001…); bộ lọc thêm Machine Code. Tiêu đề form "Machine Management - Insert" chưa Việt hoá. Ảnh: images/12_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Machine Management |  |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Nhập thông tin tìm kiếm:<br>\- Chọn Factory Name<br>\- Chọn Stage Name<br>\- Nhập Machine ID<br>\- Nhập Machine Name |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm máy mới/Insert Machine |  |  |  |  |
| 12 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Insert hiển thị |  |  |  |
| 14 | 3.3.1 | Nhập các thông tin sau:<br>\- Chọn Stage Name (đã khai báo tại chức năng Stage)<br>\- Chọn Factory Name (hiển thị mặc định từ F1 > F5)<br>\- Nhập Machine ID<br>\- Nhập Machine Name<br>\- Nhập Descripton (không bắt buộc) |  | Chú ý: Thông tin Machine ID là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 15 | 3.4.1 | Nhấn Save để lưu thông tin |  |  |  |
| 16 | 3.5.1 | Lưu thông tin thành công, hiển thị màn hình quản lý, dữ liệu được chèn vào bảng |  |  |  |
| 17 | 3.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 18 | 4. Cập nhật thông tin máy/Update Machine |  |  |  |  |
| 19 | 4.1 | Nhấn Edit tại dòng cần thay đổi |  |  |  |
| 20 | 4.2 | Hệ thống hiển thị form và fill các thông tin cũ chính xác |  |  |  |
| 21 | 4.3.1 | Cập nhật các thông tin sau:<br>\- Chọn Stage Name (đã khai báo tại chức năng Stage)<br>\- Chọn Factory Name (hiển thị mặc định từ F1 > F5)<br>\- Nhập Machine ID<br>\- Nhập Machine Name<br>\- Nhập Descripton (không bắt buộc) |  | Chú ý: Thông tin Machine ID là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 22 | 4.4.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 23 | 4.5.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 24 | 4.6.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 25 | 4.3.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 26 | 5. Xóa dữ liệu máy/Delete Machine |  |  |  |  |
| 27 | 5.1 | Nhấn Delete tại dòng có dữ liệu cần xóa |  |  |  |
| 28 | 5.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 29 | 5.3.1 | Nhấn Save > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 30 | 5.3.2 | Nhấn ngoài hộp thoại > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 31 | 6. Xem lịch sử chỉnh sửa của Máy/History Record |  |  |  |  |
| 32 | 6.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 33 | 6.2.1 | Hộp thoại lịch sử của Máy hiển thị |  | Chú ý: Với các máy đã xóa khỏi hệ thống, người dùng vào màn lịch sử tổng hợp để kiểm tra |  |
| 34 | 6.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 35 | 6.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 36 | 6.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý Máy |  |  |  |

## Equipment Type

> Sheet có 27 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ THÔNG TIN LOẠI THIẾT BỊ<br>GUIDELINES FOR USING THE EQUIPMENT TYPE MANAGEMENT FUNCTION <!-- A1 -->

V, Hướng dẫn sử dụng chức năng Quản lý Master Data > Quản lý Loại thiết bị <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm cột EQUIPMENT TYPE CODE (ET001…) và trường bắt buộc KIỂU LOGFILE (Template/VHX/Laser/Manual Input) – quyết định cách cấu hình ở màn Cấu hình IPQC. Ảnh: images/13_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Equipment Type Management |  |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Nhập thông tin tìm kiếm:<br>\- Chọn Location (đã được khai báo tại màn Quản lý vị trí)<br>\- Nhập Equipment Type |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm loại thiết bị đo mới/Insert Equipment Type |  |  |  |  |
| 12 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Insert hiển thị |  |  |  |
| 14 | 3.3.1 | Nhập các thông tin sau:<br>\- Nhập Equipment Type<br>\- Chọn Location cho loại thiết bị, có thể chọn nhiều (đã được khai báo tại màn Quản lý vị trí)<br>\- Nhập Description (không bắt buộc) |  | Chú ý: Thông tin Equipment Type là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 15 | 3.4.1 | Nhấn Save để lưu thông tin |  |  |  |
| 16 | 3.5.1 | Lưu thông tin thành công, hiển thị màn hình quản lý, dữ liệu được chèn vào bảng |  |  |  |
| 17 | 3.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 18 | 4. Cập nhật thông tin Loại thiết bị/Update Equipment Type |  |  |  |  |
| 19 | 4.1 | Nhấn Edit tại dòng cần thay đổi |  |  |  |
| 20 | 4.2 | Hệ thống hiển thị màn hình cập nhật và fill các thông tin cũ chính xác |  |  |  |
| 21 | 4.3.1 | Cập nhật các thông tin sau:<br>\- Nhập Equipment Type<br>\- Chọn Location cho loại thiết bị, có thể chọn nhiều (đã được khai báo tại màn Quản lý vị trí)<br>\- Nhập Description (không bắt buộc) |  | Chú ý: Thông tin Equipment Type là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 22 | 4.4.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 23 | 4.5.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 24 | 4.6.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 25 | 4.3.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 26 | 5. Xóa dữ liệu Loại thiết bị/Delete Equipment Type |  |  |  |  |
| 27 | 5.1 | Nhấn Delete tại dòng có dữ liệu cần xóa |  |  |  |
| 28 | 5.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 29 | 5.3.1 | Nhấn Save > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 30 | 5.3.2 | Nhấn ngoài hộp thoại > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 31 | 6. Xem lịch sử chỉnh sửa của Loại thiết bị/History Record |  |  |  |  |
| 32 | 6.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 33 | 6.2.1 | Hộp thoại lịch sử của Loại thiết bị hiển thị |  | Chú ý: Với các loại thiết bị đã xóa khỏi hệ thống, người dùng vào màn lịch sử tổng hợp để kiểm tra |  |
| 34 | 6.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 35 | 6.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 36 | 6.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý Loại thiết bị |  |  |  |

## Equipment

> Sheet có 27 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ THÔNG TIN THIẾT BỊ ĐO<br>GUIDELINES FOR USING THE EQUIPMENT MANAGEMENT FUNCTION <!-- A1 -->

V, Hướng dẫn sử dụng chức năng Quản lý Master Data > Quản lý Thiết bị đo <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm cột EQUIPMENT CODE (E001…). Form có trường ẩn Model/SN/Maker. Phát hiện F-05: nhiều thiết bị có Loại thiết bị = "ET002" (mã không tồn tại). Ảnh: images/14_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Equipment Management |  |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Nhập thông tin tìm kiếm:<br>\- Chọn Location<br>\- Chọn Equipment Type (Đã khai báo tại màn Quản lý loại thiết bị)<br>\- Nhập Equipment ID<br>\- Nhập Equipment Name |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm thiết bị đo mới/Insert Equipment |  |  |  |  |
| 12 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Insert hiển thị |  |  |  |
| 14 | 3.3.1 | Nhập các thông tin sau:<br>\- Nhập Equipment ID<br>\- Nhập Equipment Name<br>\- Chọn Location cho thiết bị<br>\- Chọn Equipment Type (đã khai báo tại màn quản lý loại thiết bị)<br>\- Nhập Description (không bắt buộc) |  | Chú ý: Thông tin Equipment là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 15 | 3.4.1 | Nhấn Save để lưu thông tin |  |  |  |
| 16 | 3.5.1 | Lưu thông tin thành công, hiển thị màn hình quản lý, dữ liệu được chèn vào bảng |  |  |  |
| 17 | 3.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 18 | 4. Cập nhật thông tin thiết bị/Update Equipment |  |  |  |  |
| 19 | 4.1 | Nhấn Edit tại dòng cần thay đổi |  |  |  |
| 20 | 4.2 | Hệ thống hiển thị màn hình cập nhật và fill các thông tin cũ chính xác |  |  |  |
| 21 | 4.3.1 | Cập nhật các thông tin sau:<br>\- Nhập Equipment ID<br>\- Nhập Equipment Name<br>\- Chọn Location cho thiết bị<br>\- Chọn Equipment Type (đã khai báo tại màn quản lý loại thiết bị)<br>\- Nhập Description (không bắt buộc) |  | Chú ý: Thông tin Equipment là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 22 | 4.4.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 23 | 4.5.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 24 | 4.6.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 25 | 4.3.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 26 | 5. Xóa dữ liệu thiết bị/Delete Equipment |  |  |  |  |
| 27 | 5.1 | Nhấn Delete tại dòng có dữ liệu cần xóa |  |  |  |
| 28 | 5.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 29 | 5.3.1 | Nhấn Save > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 30 | 5.3.2 | Nhấn ngoài hộp thoại > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 31 | 6. Xem lịch sử chỉnh sửa của thiết bị/History Record |  |  |  |  |
| 32 | 6.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 33 | 6.2.1 | Hộp thoại lịch sử của Thiết bị hiển thị |  | Chú ý: Với các thiết bị đã xóa khỏi hệ thống, người dùng vào màn lịch sử tổng hợp để kiểm tra |  |
| 34 | 6.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 35 | 6.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 36 | 6.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý Thiết bị |  |  |  |

## Build

> Sheet có 27 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ DỮ LIỆU BUILD<br>GUIDELINES FOR USING THE BUILD MANAGEMENT FUNCTION <!-- A1 -->

V, Hướng dẫn sử dụng chức năng Quản lý Master Data > Quản lý Build <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm cột BUILD CODE (B001…); bộ lọc thêm Build Code. Ảnh: images/15_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Build Management |  |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Nhập thông tin tìm kiếm:<br>\- Nhập Build Name<br>\- Chọn Type (dữ liệu gồm 2 loại NPI và MP) |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm Build mới/Insert Build |  |  |  |  |
| 12 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Insert hiển thị |  |  |  |
| 14 | 3.3.1 | Nhập các thông tin sau:<br>\- Nhập Build Name<br>\- Chọn Type (dữ liệu gồm 2 loại NPI và MP)<br>\- Nhập Description (không bắt buộc) |  | Chú ý: Thông tin Build là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 15 | 3.4.1 | Nhấn Save để lưu thông tin |  |  |  |
| 16 | 3.5.1 | Lưu thông tin thành công, hiển thị màn hình quản lý, dữ liệu được chèn vào bảng |  |  |  |
| 17 | 3.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 18 | 4. Cập nhật thông tin Build/Update Build |  |  |  |  |
| 19 | 4.1 | Nhấn Edit tại dòng cần thay đổi |  |  |  |
| 20 | 4.2 | Hệ thống hiển thị màn hình cập nhật và fill các thông tin cũ chính xác |  |  |  |
| 21 | 4.3.1 | Cập nhật các thông tin sau:<br>\- Nhập Build Name<br>\- Chọn Type (dữ liệu gồm 2 loại NPI và MP)<br>\- Nhập Description (không bắt buộc) |  | Chú ý: Thông tin Build là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 22 | 4.4.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 23 | 4.5.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 24 | 4.6.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 25 | 4.3.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 26 | 5. Xóa dữ liệu Build/Delete Build |  |  |  |  |
| 27 | 5.1 | Nhấn Delete tại dòng có dữ liệu cần xóa |  |  |  |
| 28 | 5.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 29 | 5.3.1 | Nhấn Save > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 30 | 5.3.2 | Nhấn ngoài hộp thoại > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 31 | 6. Xem lịch sử chỉnh sửa của Build/History Record |  |  |  |  |
| 32 | 6.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 33 | 6.2.1 | Hộp thoại lịch sử của Build hiển thị |  | Chú ý: Với các Build đã xóa khỏi hệ thống, người dùng vào màn lịch sử tổng hợp để kiểm tra |  |
| 34 | 6.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 35 | 6.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 36 | 6.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý Build |  |  |  |

## Item

> Sheet có 8 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ DỮ LIỆU ITEM<br>GUIDELINES FOR USING THE ITEM MANAGEMENT FUNCTION <!-- A1 -->

V, Hướng dẫn sử dụng chức năng Quản lý Master Data > Quản lý Item <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Item Management |  |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Nhập thông tin tìm kiếm:<br>\- Nhập Item Name<br>\- Nhập Item Code<br>\- Nhập Build |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Nhập thêm Item/Import File Item |  |  |  |  |
| 12 | 3.1 | Nhấn Import File trên góc phải màn hình |  | Sau hệ thống sẽ thực hiện link trực tiếp dữ liệu Item từ hệ thống bên Nhật, chức năng được tạo để sử dụng tạm thời |  |
| 13 | 3.2 | Có 2 cách tải file lên:<br>Cách 1: Kéo file trực tiếp vào vùng được khoanh<br>Cách 2: Nhấn Browse để duyệt file lên |  |  |  |
| 14 | 3.3 | Nhấn Upload để lưu thông tin |  |  |  |

## Location

> Sheet có 20 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ THÔNG TIN VỊ TRÍ<br>GUIDELINES FOR USING THE LOCATION MANAGEMENT FUNCTION <!-- A1 -->

V, Hướng dẫn sử dụng chức năng Quản lý Master Data > Quản lý vị trí <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Có thêm nút Sửa; form thêm checkbox "Nhận mẫu" (mặc định tích). Nhãn vẫn tiếng Anh (Factory, Department (Room), Description). Ảnh: images/17_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Location Management |  | Thông tin Equipment Type sẽ được tự động cập nhật ở đây, khi người dùng thay đổi thông tin Location tại màn khai báo Equipment Type |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Nhập thông tin tìm kiếm:<br>\- Chọn Factory <br>\- Nhập Department |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm vị trí mới/Insert Location |  |  |  |  |
| 12 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Insert hiển thị |  |  |  |
| 14 | 3.3.1 | Nhập các thông tin sau:<br>\- Chọn Factory<br>\- Nhập Department<br>\- Nhập Descripton (không bắt buộc) |  | Chú ý: Thông tin Location + Factory là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 15 | 3.4.1 | Nhấn Save để lưu thông tin |  |  |  |
| 16 | 3.5.1 | Lưu thông tin thành công, hiển thị màn hình quản lý, dữ liệu được chèn vào bảng<br>Hệ thống tự động tạo:<br>\- Location Code: F(Factory)L(Thứ tự Department)<br>\- Location Name, kết hợp Department - Factory |  |  |  |
| 17 | 3.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 18 | 4. Xóa dữ liệu vị trí/Delete Location |  |  |  |  |
| 19 | 4.1 | Nhấn Delete tại dòng có dữ liệu cần xóa |  |  |  |
| 20 | 4.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 21 | 4.3.1 | Nhấn Save > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 22 | 4.3.2 | Nhấn ngoài hộp thoại hoặc nhấn nút X trên góc phải > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 23 | 5. Xem lịch sử chỉnh sửa của vị trí/History Record |  |  |  |  |
| 24 | 5.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 25 | 5.2.1 | Hộp thoại lịch sử của vị trí hiển thị |  | Chú ý: Hệ thống vẫn sử dụng lại Location Code theo thứ tự nên dữ liệu bị xóa vẫn hiển thị |  |
| 26 | 5.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 27 | 5.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 28 | 5.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý vị trí |  |  |  |

## Rack

> Sheet có 38 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ THÔNG TIN KỆ CHỨA MẪU<br>GUIDELINES FOR USING THE RACK MANAGEMENT FUNCTION <!-- A1 -->

VI, Hướng dẫn sử dụng chức năng Quản lý Master Data > Khai báo kệ Rack > Quản lý Kệ chứa <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Thêm nút "Sơ đồ Tủ Rack", hành động Xem tầng & Sơ đồ. Sơ đồ thiết kế lại: tổng số tầng/vị trí/request, màu Trống/Đang dùng(<80%)/Gần đầy(>=80%)/Đầy(100%), ô hiển thị Position Code + Loại mẫu + x/max Request. Xem sheet "Rack Diagram". Ảnh: images/18_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Rack Management |  | Khai báo thông tin các kệ chứa mẫu tại các phòng đo. Phân bổ vị trí chứa theo từng công đoạn. |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Nhấn vào Search Filter để hiển thị các thông tin tìm kiếm |  |  |  |
| 8 | 2.2 | Nhập thông tin tìm kiếm:<br>\- Chọn Location<br>\- Nhập Rack Name |  |  |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm kệ chứa mẫu mới/Insert Rack |  |  |  |  |
| 12 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Insert hiển thị |  |  |  |
| 14 | 3.3.1 | Nhập các thông tin sau:<br>\- Nhập Rack Name<br>\- Nhập Location<br>\- Chọn Stages Allowed (Có thể chọn nhiều rack được chứa tại kệ này)<br>\- Nhập Descripton (không bắt buộc) |  | Chú ý: Thông tin rack Name là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 15 | 3.6.1 | Nhấn Save để lưu thông tin |  |  |  |
| 16 | 3.7.1 | Lưu thông tin thành công, hiển thị màn hình quản lý, dữ liệu được chèn vào bảng<br>Dữ liệu Rack Code tự động tạo theo cấu trúc:<br>Factory-RCK-Số thứ tự kệ |  |  |  |
| 17 | 3.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 18 | 4. Cập nhật thông tin kệ chứa/Update rack |  |  |  |  |
| 19 | 4.1 | Nhấn Edit tại dòng cần thay đổi |  |  |  |
| 20 | 4.2 | Hệ thống hiển thị màn hình chỉnh sửa và fill các thông tin cũ chính xác |  |  |  |
| 21 | 4.3.1 | Cập nhật các thông tin sau:<br>\- Nhập Rack Name<br>\- Chọn Stages Allowed (Có thể chọn nhiều rack được chứa tại kệ này)<br>\- Nhập Descripton (không bắt buộc) |  | Chú ý: Thông tin Rack Name là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 22 | 4.4.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 23 | 4.5.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 24 | 4.6.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 25 | 4.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 26 | 5. Xóa dữ liệu kệ chứa/Delete rack |  |  |  |  |
| 27 | 5.1 | Nhấn Delete tại dòng có dữ liệu cần xóa, yêu cầu:<br>\- Chưa khai báo Layer nào |  |  |  |
| 28 | 5.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 29 | 5.3.1 | Nhấn Save > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 30 | 5.3.2 | Nhấn ngoài hộp thoại > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 31 | 6. Xem sơ đồ của kệ chứa/Rack Diagram |  |  |  |  |
| 32 | 6.1.1 | Để xem trực tiếp chi tiết của 1 kệ chứa > Nhấn Diagram tại kệ cần xem |  |  |  |
| 33 | 6.2.1 | Màn hình Diagram hiển thị sơ đồ kệ chứa |  |  |  |
| 34 | 6.1.2 | Để tìm kiếm kệ chứa > Nhấn Rack Dỉgram ở góc trên bên phải màn hình |  |  |  |
| 35 | 6.2.2 | Màn hình Diagram hiển thị |  |  |  |
| 36 | 6.3.2 | Chọn thông tin của Rack cần xem:<br>\- Chọn Location<br>\- Chọn Rack |  |  |  |
| 37 | 6.4.2 | Nhấn Search > Hiển thị sơ đồ của kệ chứa |  |  |  |
| 38 | 6.5 | Nhấn vào vị trí chứa mẫu |  |  |  |
| 39 | 6.6 | Thông tin các Request đang chứa tại vị trí đó hiển thị |  |  |  |
| 40 | 6.7 | Nhấn ra ngoài hoặc nhấn Close để đóng hộp thoại |  |  |  |
| 41 |  | Nếu kệ chưa khai báo Layer > Không hiển thị sơ đồ, thông báo chưa khai báo Layer |  |  |  |
| 42 | 6.8 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 43 | 7. Xem lịch sử chỉnh sửa của kệ chứa/History Record |  |  |  |  |
| 44 | 7.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 45 | 7.2.1 | Hộp thoại lịch sử của kệ chứa hiển thị |  | Chú ý: Các Rack Code được tái sử dụng, thứ tự tăng lên khi đã dùng hết Code cũ |  |
| 46 | 7.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 47 | 7.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 48 | 7.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý kệ chứa |  |  |  |

## Rack Diagram

HƯỚNG DẪN XEM SƠ ĐỒ TỦ RACK (THIẾT KẾ LẠI)<br>GUIDELINES FOR RACK DIAGRAM <!-- A1 -->

VI, Hướng dẫn Master Data > Tủ đựng > Sơ đồ Tủ Rack  (route /Rack/Diagram) <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Tại Rack Management: nhấn "Sơ đồ Tủ Rack" (góc phải) hoặc icon Sơ đồ ở dòng tủ | images/18_rack_list.jpg |  |  |
| 6 | 2 | Chọn Vị trí, Tủ đựng → Tìm kiếm (Đặt lại để xoá chọn) | images/18_rack_diagram.jpg |  |  |
| 7 | 3 | Thông tin tóm tắt: Vị trí tủ, Tên Tủ Rack, Tổng số tầng, Tổng vị trí, Tổng Request. Chú giải: Trống / Đang dùng (<80%) / Gần đầy (>=80%) / Đầy (100%) |  |  |  |
| 8 | 4 | Mỗi Layer: "<r> Dòng x <c> Cột", số vị trí; mỗi ô: Position Code (vd F1-RCK-0001-02-01.01), Loại mẫu, "x / max Request" |  |  |  |
| 9 | 5 | Nhấn vào ô → "Danh sách Request tại vị trí": Mã yêu cầu, Item Name, Item Code, Lô sản xuất, Build, Số lượng, Trình tự, Thiết bị, Trạng thái, Operator, Ngày tạo → Đóng |  |  |  |
| 10 | 6 | Nhấn Quay lại để về Rack Management |  |  |  |

## Rack Layer

> Sheet có 36 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ THÔNG TIN TẦNG KỆ CHỨA MẪU<br>GUIDELINES FOR USING THE RACK LAYER MANAGEMENT FUNCTION <!-- A1 -->

VI, Hướng dẫn sử dụng chức năng Quản lý Master Data > Khai báo kệ Rack > Quản lý Tầng kệ chứa <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Nút "Xóa tầng" chuyển lên khu vực lọc (modal Delete Layer, Lý do*); thêm hành động Xem vị trí, Disable/Enable; form có Trạng thái Hoạt động/Không hoạt động; Tên tầng tự sinh. Ảnh: images/19_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Rack Layer Management |  |  |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.2 | Nhập thông tin tìm kiếm:<br>\- Chọn Location<br>\- Chọn Rack |  |  |  |
| 8 | 2.3 | Màn hình hiển thị các Layer đã được khai báo |  |  |  |
| 9 |  | Cần tìm chi tiết 1 tầng → Nhập Layer Name → Nhấn Search |  |  |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm tầng chứa mới trong kệ/Insert Layer |  |  |  |  |
| 12 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 13 | 3.2 | Màn hình Insert hiển thị |  |  |  |
| 14 | 3.3.1 | Nhập các thông tin sau:<br>\- Chọn Location: Nếu đã được chọn tại màn quản lý → Auto fill<br>\- Chọn Rack: Nếu đã được chọn tại màn quản lý → Auto fill<br>\- Nhập Layer Name: Nếu không nhập hệ thống sẽ tự động tạo tên Layer_số thứ tự<br>\- Nhập Row Count<br>\- Nhập Column Count<br>\- Nhập Descripton (không bắt buộc)<br>\- Chọn Status: gồm 2 trạng thái Active (sử dụng) và Inactive (không sử dụng) |  | Chú ý: Thông tin layer Name là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 15 | 3.6.1 | Nhấn Save để lưu thông tin |  |  |  |
| 16 | 3.7.1 | Lưu thông tin thành công, hiển thị màn hình quản lý, dữ liệu được chèn vào bảng<br>Dữ liệu Layer Code tự động tạo theo cấu trúc:<br>Factory-RCK-Số thứ tự kệ-Số thứ tự tầng |  |  |  |
| 17 | 3.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 18 | 4. Cập nhật thông tin tầng chứa của kệ/Update layer |  |  |  |  |
| 19 | 4.1 | Thực hiện chọn Location, Rack để view dữ liệu |  |  |  |
| 20 | 4.1 | Nhấn Edit tại dòng cần thay đổi |  |  |  |
| 21 | 4.2 | Hệ thống hiển thị màn hình chỉnh sửa và fill các thông tin cũ chính xác |  |  |  |
| 22 | 4.3.1 | Cập nhật các thông tin sau:<br>\- Nhập Rack Name<br>\- Chọn Stages Allowed (Có thể chọn nhiều rack được chứa tại kệ này)<br>\- Nhập Descripton (không bắt buộc) |  | Chú ý: Thông tin Layer Name là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 23 | 4.4.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 24 | 4.5.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 25 | 4.6.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 26 | 4.3.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 27 | 5. Xóa dữ liệu tầng chứa mẫu/Delete layer |  |  |  |  |
| 28 | 5.1 | Nhấn Delete tại vị trí được khoanh, yêu cầu:<br>\- Không có vị trí nào trong tầng được chứa mẫu<br>\- Xóa từ tầng lớn nhất |  |  |  |
| 29 | 5.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 30 | 5.3.1 | Nhấn Delete > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 31 | 5.3.2 | Nhấn ngoài hộp thoại > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 32 | 6. Chỉnh sửa trạng thái sử dụng tầng chứa mẫu/Update Status |  |  |  |  |
| 33 | 6.1.1 | Tại màn Update → Thay đổi tại Status |  |  |  |
| 34 | 6.2.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 35 | 6.3.1 | Nhấn Save |  |  |  |
| 36 | 6.4.1 | Dữ liệu được cập nhật trạng thái đã lưu |  |  |  |
| 37 | 6.1.2 | Tại màn hình quản lý, đã hiển thị dữ liệu |  |  |  |
| 38 | 6.2.2 | Thay đổi trạng thái sử dụng bằng cách nhấn các nút:<br>1. Disable: Nếu thay đổi từ Active > Inactive<br>1. Enable: Nếu thay đổi từ Inactive > Active |  |  |  |
| 39 | 6.3.2 | Hộp thoại xác nhận hiển thị tương ứng với trạng thái mong muốn |  |  |  |
| 40 | 6.4.2 | Xác nhận thay đổi trạng thái > Nhấn Yes |  |  |  |
| 41 | 6.5.2 | Trạng thái tầng được thay đổi, nút hiển thị tương ứng trạng thái |  |  |  |
| 42 | 6.6.2 | Không thay đổi trạng thái/Đổi trạng thái của tầng khác > Nhấn Cancel để đóng hộp thoại |  |  |  |
| 43 | 6. Xem lịch sử chỉnh sửa của kệ chứa/History Record |  |  |  |  |
| 44 | 6.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 45 | 6.2.1 | Hộp thoại lịch sử của kệ chứa hiển thị |  | Chú ý: Layer Code có thể được tái sử dụng |  |
| 46 | 6.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 47 | 6.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 48 | 6.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý kệ chứa |  |  |  |

## Layer Position

> Sheet có 11 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ VỊ TRÍ ĐẶT MẪU TRONG KỆ<br>GUIDELINES FOR USING THE LAYER POSITION MANAGEMENT FUNCTION <!-- A1 -->

VI, Hướng dẫn sử dụng chức năng Quản lý Master Data > Khai báo kệ Rack > Quản lý Vị trí đặt mẫu trong kệ chứa mẫu <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Position Code dạng F1-RCK-0001-03-01.02 (hàng.cột); không có Thêm mới (tự sinh khi sửa tầng); form Update: Loại mẫu*, Max Qty*, Description, Reason*. Ảnh: images/20_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình Layer Position Management<br>\- Số lượng vị trí chứa tại màn hình này dựa trên số lượng cột - dòng khai báo tại màn Rack Layer<br>\+ Layer tăng cột/dòng > Thêm vị trí chứa mẫu<br>\+ Layer giảm cột/dòng > Giảm vị trí chứa mẫu |  |  |  |
| 6 | 2 | Chọn các thông tin để hiển thị dữ liệu<br>\- Chọn Location<br>\- Chọn Rack<br>\- Chọn Layer<br>\- Chọn Sample Type |  |  |  |
| 7 | 3. Cập nhật điều kiện nhận mẫu tại vị trí chứa/Update Layer position |  |  |  |  |
| 8 | 3.2 | Nhấn Edit tại vị trí trong tầng cần cập nhật |  |  |  |
| 9 | 3.3 | Hệ thống hiển thị màn hình chỉnh sửa và fill các thông tin cũ chính xác |  |  |  |
| 10 | 3.4.1 | Cập nhật các thông tin sau:<br>\- Chọn Sample Type<br>\- Nhập số lượng chứa tối đa Max Qty<br>\- Nhập Description (không bắt buộc) |  |  |  |
| 11 | 3.6.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 12 | 3.7.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 13 | 3.8.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 14 | 3.4.2 | Nhấn Back để quay lại màn hình quản lý |  |  |  |
| 15 | 4. Xem lịch sử chỉnh sửa của bố cục file IPQC/History Record |  |  |  |  |
| 16 | 6.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 17 | 6.2.1 | Hộp thoại lịch sử của kệ chứa hiển thị |  |  |  |
| 18 | 6.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 19 | 6.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 20 | 6.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý kệ chứa |  |  |  |

## IPQC Content

> Sheet có 36 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ NỘI DUNG IPQC<br>GUIDELINES FOR USING THE IPQC CONTENT MANAGEMENT FUNCTION <!-- A1 -->

VII, Hướng dẫn sử dụng chức năng IPQC > Quản lý Nội dung IPQC <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Form có bảng "Location & Equipment Type Allocation" (LOẠI THIẾT BỊ* + VỊ TRÍ* + nút Add Location), Quantity NPI*/MASS*, Order tự tăng, SPC Rule 1–8. Ảnh: images/21_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình IPQC Content Management |  | Khai báo các nội dung đo cho Công đoạn, phân bổ vị trí đo nội dung và loại thiết bị sử dụng để thực hiện đo. |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Chọn Stage Name để hệ thống hiển thị các thông tin |  |  |  |
| 8 | 2.2 | Nhập thêm thông tin tìm kiếm (không bắt buộc):<br>\- Chọn Equipment Type<br>\- Chọn Location |  | Các dữ liệu Equipment Type và Location đã được khai báo tại màn quản lý tương ứng |  |
| 9 | 2.3 | Nhấn Search > Hiển thị các thông tin trùng khớp |  | Hệ thống hiện tại đang hiển thị theo các thông tin chọn ngay lập tức |  |
| 10 | 2.4 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 11 | 3. Thêm nội dung IPQC mới/Insert IPQC Content |  |  |  |  |
| 12 | 3.1 | Chọn Stage Name tại màn quản lý |  |  |  |
| 13 | 3.2 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 14 | 3.3 | Màn hình Insert nội dung hiển thị |  |  |  |
| 15 | 3.4.1 | Người dùng nhập các thông tin:<br>\- Nhập IPQC Content<br>\- Nhập Quantity NPI và MASS<br>\- Nhập Order (không chỉnh sửa, hệ thống tự tăng)<br>\- Nhập Description (không bắt buộc)<br>\- Chọn các SPC Rule (nếu không thay đổi, mặc định chọn 1) |  | Chú ý: Thông tin IPQC Content là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 16 | 3.5.1 | Thực hiện phân bổ thiết bị đo và vị trí thực hiện:<br>1. Chọn Equipment Type<br>2. Chọn Location chứa Loại thiết bị<br>\- Thêm vị trí/loại máy đo: <br>\- Xóa vị trí/loại máy đo: | e | Không được khai báo<br>\- Cùng Equipment Type nhưng tại nhiều Location<br>\- Các dữ liệu phân bổ là duy nhất, các dòng không được trùng nhau |  |
| 17 | 3.6.1 | Nhấn Save để lưu lại dữ liệu khai báo |  |  |  |
| 18 | 3.7.1 | Khi dữ liệu lưu thành công, sẽ hiển thị tại vị trí đã nhập Order |  |  |  |
| 19 | 3.4.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 20 | 4. Cập nhật thông tin nội dung IPQC/Update IPQC Content |  |  |  |  |
| 21 | 4.1 | Chọn Stage Name tại màn quản lý |  |  |  |
| 22 | 4.2 | Nhấn Edit tại content cần chỉnh sửa |  |  |  |
| 23 | 4.3 | Hệ thống hiển thị form và fill các thông tin cũ chính xác |  |  |  |
| 24 | 4.4.1 | Câp nhật các thông tin:<br>\- Nhập IPQC Content<br>\- Nhập Quantity NPI và MASS<br>\- Nhập Order (không chỉnh sửa, hệ thống tự tăng)<br>\- Nhập Description (không bắt buộc)<br>\- Chọn các SPC Rule (nếu không thay đổi, mặc định chọn 1) |  | Chú ý: Thông tin IPQC Content là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 25 | 4.5.1 | Thực hiện cập nhật phân bổ:<br>1. Chọn Equipment Type<br>2. Chọn Location chứa Loại thiết bị<br>\- Thêm vị trí/loại máy đo: <br>\- Xóa vị trí/loại máy đo: | e | Không được khai báo<br>\- Cùng Equipment Type nhưng tại nhiều Location<br>\- Các dữ liệu phân bổ là duy nhất, các dòng không được trùng nhau |  |
| 26 | 4.6.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 27 | 4.7.1 | Nhấn Save để lưu thông tin thay đổi |  |  |  |
| 28 | 7.8.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 29 | 4.4.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 30 | 5. Xóa dữ liệu nội dung IPQC/Delete IPQC Content |  |  |  |  |
| 31 | 5.1 | Chọn Stage Name tại màn hình quản lý |  |  |  |
| 32 | 5.1 | Nhấn Delete tại dòng có dữ liệu cần xóa |  |  |  |
| 33 | 5.2 | Hệ thống hiển thị hộp thoại xác nhận<br>Bắt buộc người dùng nhập Reason/Lý do xóa |  |  |  |
| 34 | 5.3.1 | Nhấn Save > Hệ thống thực hiện xóa dữ liệu |  |  |  |
| 35 | 5.3.2 | Nhấn ngoài hộp thoại > Hệ thống không xóa dữ liệu đó, đóng hộp thoại xác nhận |  |  |  |
| 36 | 6. Xem lịch sử chỉnh sửa của nội dung IPQC/History Record |  |  |  |  |
| 37 | 6.1.1 | Nhấn History tại dòng cần xem lịch sử chỉnh sửa |  |  |  |
| 38 | 6.2.1 | Hộp thoại lịch sử của nội dung IPQC hiển thị |  | Chú ý: Với các nội dung IPQC đã xóa khỏi hệ thống, người dùng vào màn lịch sử tổng hợp để kiểm tra |  |
| 39 | 6.1.2 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 40 | 6.2.2 | Màn hình History Summary hiển thị |  |  |  |
| 41 | 6.3.2 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý nội dung IPQC |  |  |  |

## IPQC Layout_Draft

> Sheet có 18 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ BỐ CỤC FILE IPQC<br>GUIDELINES FOR USING THE IPQC LAYOUT MANAGEMENT FUNCTION <!-- A1 -->

VII, Hướng dẫn sử dụng chức năng IPQC > Quản lý Bố cục file IPQC <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Bộ lọc đổi thứ tự Vị trí → Tên công đoạn → Loại thiết bị, nút Edit; thêm upload File Template (.xltx/.xltm/.xlt/.xlsm/.xlsx ≤5 MB); nhãn "Hướng ghi". Màn mới "Cấu hình IPQC" bao trùm chức năng này – xem sheet "IPQC Config". Ảnh: images/22_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình IPQC Layout Management<br>\- Số lượng nội dung tại màn hình này dựa trên khai báo tại màn IPQC Content<br>\+ IPQC Content thêm nội dung/phân bổ > Thêm dòng khai báo layout<br>\+ IPQC Content xóa nội dung/thay đổi phân bổ > Xóa khai báo layout |  | Khai báo format của file báo báo tại từng công đoạn, từng Phòng đo, theo từng loại máy.<br>Phục vụ cho hệ thống xác định vị trí bắt đầu, hướng di chuyển để đọc dữ liệu từ báo cáo. |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Chọn Stage Name để hệ thống hiển thị các thông tin, các ô nhập Position và Direction không thể chỉnh sửa |  |  |  |
| 8 | 2.2 | Nhập thêm thông tin tìm kiếm (không bắt buộc):<br>\- Chọn Location<br>\- Chọn Equipment Type |  | Các dữ liệu Equipment Type và Location đã được khai báo tại màn quản lý tương ứng |  |
| 9 | 2.3 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 10 | 3. Cập nhật bố cục file đo nội dung IPQC/Update IPQC Layout |  |  |  |  |
| 11 | 3.1 | Chọn Stage Name tại màn quản lý |  |  |  |
| 12 | 3.2 | Nhấn Edit tại vị trí trong ảnh |  |  |  |
| 13 | 3.3 | Các ô nhập Position và Direction hiển thị cho phép thực hiện chỉnh sửa |  |  |  |
| 14 | 3.4.1 | Câp nhật các thông tin theo các IPQC Content + Equipment Type<br>\- Nhập Position Side A hoặc Side B:<br>Vị trí bắt đầu đọc trong file Excel (VD: Cột 3 dòng 7 trong file -> C7) |  |  |  |
| 15 | 3.5.1 | \- Chọn Direction Side A hoặc Side B:<br>Chiều đọc của dữ liệu<br>\+ Horizontal - Ngang: Đọc theo chiều ngang, bắt đầu từ vị trí Position tương ứng<br>\+ Vertical - Dọc: Đọc theo chiều dọc, bắt đầu từ vị trí Position tương ứng | e |  |  |
| 16 | 3.6.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 17 | 3.7.1 | Nhấn Save để lưu thông tin thay đổi |  | Phải nhập đủ Position + Direction theo cặp mới được phép lưu và nhập đủ của 1 Side |  |
| 18 |  | Lưu ý khi lưu Layout:<br>1. Cùng 1 nội dung, 2 Location, mỗi Location 1 Equipment Type -> 2 Layout khác nhau<br>2. Cùng 1 nội dung, cùng Location nhưng 2 Equipment Type khác nhau -> 2 Layout khác nhau<br>3. Phải nhập hết Side A hoặc Side B của 1 layout mới thực hiện lưu thay đổi |  | Công đoạn RTR Etching có 3 layout: <br>\+ Đo mạch F1 - VHX<br>\+ Đo mạch F1 - Laser Microscope<br>\+ QA Lab F5 - VHX |  |
| 19 | 3.8.1 | Hệ thống lưu thông tin thay đổi thành công |  |  |  |
| 20 | 3.4.2 | Nhấn Clear để hủy thao tác cập nhật và hiển thị màn hình mặc định |  |  |  |
| 21 | 4. Xem lịch sử chỉnh sửa của bố cục file IPQC/History Record |  |  |  |  |
| 22 | 4.1 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 23 | 4.2 | Màn hình History Summary hiển thị |  |  |  |
| 24 | 4.3 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý nội dung IPQC |  | Các Layout bị xóa do thay đổi nội dung đo vẫn được lưu tại màn lịch sử |  |

## IPQC Config

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG CẤU HÌNH IPQC (MỚI)<br>GUIDELINES FOR IPQC LOG CONFIGURATION <!-- A1 -->

VII, Hướng dẫn IPQC > Cấu hình IPQC  (route /LogConfig) <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Không đổi đáng kể. Menu hiển thị "Sản phẩm". Ảnh: images/16_item_list.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Chọn IPQC > Cấu hình IPQC. Chọn lần lượt Vị trí → Tên công đoạn → Loại thiết bị | images/23_ipqc_config_empty.jpg | Công đoạn chỉ hiện các công đoạn có Nội dung IPQC tại Vị trí |  |
| 6 | 2 | Hệ thống hiển thị "Kiểu LogFile: <Template\|VHX\|Laser\|Manual Input>" và nút Quản lý Loại thiết bị |  | Kiểu LogFile khai báo ở màn Loại thiết bị |  |
| 7 | 3. Kiểu Template |  |  |  |  |
| 8 | 3.1 | Giao diện như Bố cục IPQC: File Template (.xltx/.xltm/.xlt/.xlsm/.xlsx ≤5 MB; để trống = giữ cũ) + bảng Mặt A/B (Vị trí ô, Hướng ghi Horizontal/Vertical) → Edit → nhập → Lưu |  | Xem sheet IPQC Layout_Draft |  |
| 9 | 4. Kiểu VHX / Laser |  |  |  |  |
| 10 | 4.1 | Quản lý bằng Excel: Tải file mẫu (2 sheet Side_A & Side_B) → sửa → Import file | images/23_ipqc_config_vhx.jpg |  |  |
| 11 | 4.2 | Bảng Cấu hình Side A/B, các cột:<br>\- ĐƯỜNG DẪN THƯ MỤC: thư mục con chứa file log (trống nếu ở thư mục gốc)<br>\- TÊN FILE: tên cố định (B_Plane…) hoặc dùng [x] = số bất kỳ, vd [x]-TH → 3-TH.csv; không nhập đuôi<br>\- ĐỊNH DẠNG FILE: .csv/.txt/.xlsx/.xls<br>\- CÔNG THỨC: #n = dòng n; vd #1 - #2, AVG(#1), #1/#2*100, ROUND(#1-#2,3)<br>\- CỘT TÌM KIẾM, TÊN MẪU ĐO: chỉ cho Laser<br>\- Ô LẤY GIÁ TRỊ: ô Excel chứa kết quả, vd C6; nút slider để đặt riêng theo ItemName/ItemCode | images/23_ipqc_config_help_filename.jpg | Dòng có công thức → các ô Thư mục/Tên file/Ô lấy giá trị bị khoá |  |
| 12 | 4.3 | Ví dụ UV laser/VHX: #1 75 Top [x] .csv C6; #2 75 Bottom [x] .csv C7; #3 Tỷ lệ = #2/#1; #4 TH 238 [x]-TH .csv C6 | images/23_ipqc_config_laser.jpg | Ví dụ Laser: B1-Etching factor = 2*#3/(#2-#1) |  |
| 13 | 4.4 | Nhấn Edit → sửa → Lưu |  | Cảnh báo high-risk: sai cấu hình → đọc sai/phán định sai cho mọi request sau. Backup: Tải file mẫu trước khi sửa; tra "Lịch sử Logfile Config" để khôi phục |  |
| 14 | 5. Lịch sử |  |  |  |  |
| 15 | 5.1 | Dropdown Lịch sử tổng quát: "Lịch sử tổng quát (Template Layout)" và "Lịch sử Logfile Config" |  |  |  |

## IPQC Spec ItemName_draft

> Sheet có 49 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ TIÊU CHUẨN IPQC CHO ITEM NAME<br>GUIDELINES FOR USING THE IPQC SPEC FOR ITEM NAME MANAGEMENT FUNCTION <!-- A1 -->

VII, Hướng dẫn sử dụng chức năng IPQC > Quản lý Tiêu chuẩn IPQC cho Item Name <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Bộ lọc thêm Trạng thái (Tất cả/Set/Not Set); bảng có cột TRẠNG THÁI; Detail có "Mở rộng tất cả/Thu gọn tất cả", panel "Thông số mặt A/B (n chỉ tiêu)", cột HOẠT ĐỘNG. Ảnh: images/24_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình IPQC Spec for ItemName Management |  | Khai báo tiêu chuẩn đo cho các nội dung IPQC đã khai báo. Tại màn hình này người dùng khai báo theo Item Name và Sequence. |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Chọn Stage Name để hệ thống hiển thị các thông tin |  |  |  |
| 8 | 2.2 | Nhập thêm thông tin tìm kiếm (không bắt buộc):<br>\- Chọn Item Name (đã nhập tại màn quản lý Item) |  |  |  |
| 9 | 2.3 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 10 | 3. Thêm tiêu chuẩn IPQC mới cho ItemName/Insert IPQC Spec for ItemName |  |  |  |  |
| 11 | 3.1 | Nhấn Insert trên góc phải màn hình |  |  |  |
| 12 | 3.2 | Màn hình Insert hiển thị:<br>\+ Nếu tại màn hình quản lý người dùng chọn Stage Name > Hệ thống tự động chọn Stage |  |  |  |
| 13 |  | Có thể chọn:<br>Expand All: Hiển thị toàn bộ Side A, Side B của các content<br>Collapse All: Thu gọn hiển thị của Side A, Side B |  |  |  |
| 14 | 3.3 | Người dùng nhập các thông tin:<br>\- Chọn Item Name<br>\- Nhập Sequence<br>\- Nhập Unit<br>\- Nhập Leadtime: được tính bằng phút |  | Dữ liệu kết hợp: Stage name + ItemName + Sequence không được phép nhập trùng |  |
| 15 |  | Có thể lọc thông tin cho dễ theo dõi:<br>\- Chọn Location<br>\- Chọn Equipment Type | e |  |  |
| 16 | 3.4.1 | Nhấn Active tại nội dung có tiêu chuẩn theo Equipment Type<br>-> Cho phép nhập tiêu chuẩn<br>-> Có thể nhập riêng Side A/B hoặc cả 2 Side |  |  |  |
| 17 | 3.5.1 | 1. Nhập các giá trị theo điều kiện:<br>X Spec: LL<LCL<CENTER<UCL<UL<br>R Spec: UCL<UL<br>2. Khi nhập LL/UL > hiển thị LCL/UCL tương ứng<br>3. Chỉ cần nhập UL hoặc LL khi Active<br>4. Có thể không nhập R Spec |  |  |  |
| 18 |  | Nếu có tiêu chuẩn Side B, thực hiện tương tự |  |  |  |
| 19 | 3.6.1 | Sau khi nhập đủ thông tin (active ít nhất 1 tiêu chuẩn content của equipment type, side bất kì) > Nhấn Save để lưu |  |  |  |
| 20 | 3.7.1 | Hộp thoại xác nhận hiển thị Lưu và ghi đè tiêu chuẩn Sequence này cho toàn bộ Item Code |  |  |  |
| 21 | 3.8.1.1 | Xác nhận > Nhấn OK |  |  |  |
| 22 |  | Dữ liệu được lưu, hiển thị trong danh sách các tiêu chuẩn của công đoạn |  |  |  |
| 23 | 3.8.1.2 | Không lưu các khai báo này, cần chỉnh thêm > Nhấn Cancel |  |  |  |
| 24 |  | Quay lại màn hình nhập tiêu chuẩn |  |  |  |
| 25 | 3.4.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 26 | 4. Xem chi tiết tiêu chuẩn IPQC cho ItemName/Detail IPQC Spec for ItemName |  |  |  |  |
| 27 | 4.1 | Chọn Stage Name tại màn quản lý |  |  |  |
| 28 | 4.2 | Nhấn Detail tại dữ liệu tiêu chuẩn cần xem |  |  |  |
| 29 | 4.3 | Hệ thống hiển thị chi tiết và fill các thông tin cũ chính xác |  |  |  |
| 30 |  | Có thể lọc thông tin cho dễ theo dõi:<br>\- Chọn Location<br>\- Chọn Equipment Type |  |  |  |
| 31 |  | Có thể chọn:<br>Expand All: Hiển thị toàn bộ Side A, Side B của các content<br>Collapse All: Thu gọn hiển thị của Side A, Side B |  | Chú ý: Thông tin IPQC Spec for ItemName là duy nhất, yêu cầu không nhập trùng dữ liệu |  |
| 32 | 4.4 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 33 | 5. Cập nhật tiêu chuẩn IPQC cho ItemName/Updatel IPQC Spec for ItemName |  |  |  |  |
| 34 | 5.1 | Tại màn Detail, nhấn Edit để chỉnh sửa tiêu chuẩn |  |  |  |
| 35 | 5.2 | Màn hình Update fill các dữ liệu đã khai báo chính xác |  |  |  |
| 36 |  | Có thể chọn:<br>Expand All: Hiển thị toàn bộ Side A, Side B của các content<br>Collapse All: Thu gọn hiển thị của Side A, Side B |  |  |  |
| 37 |  | Có thể lọc thông tin cho dễ theo dõi:<br>\- Chọn Location<br>\- Chọn Equipment Type | e |  |  |
| 38 | 5.3.1 | Người dùng nhập các thông tin:<br>\- Nhập Sequence<br>\- Nhập Unit<br>\- Nhập Leadtime: được tính bằng phút |  |  |  |
| 39 |  | Dữ liệu kết hợp: Stage name + ItemName + Sequence<br>\+ Nếu thay đổi Sequence > Tạo thành tiêu chuẩn khác<br>\+ Nếu giữ nguyên Sequence > Chỉ cập nhật thay đổi tiêu chuẩn hiện tại |  |  |  |
| 40 | 5.4.1 | Nhấn Active tại nội dung có tiêu chuẩn theo Equipment Type<br>-> Cho phép nhập tiêu chuẩn<br>-> Có thể nhập riêng Side A/B hoặc cả 2 Side |  |  |  |
| 41 | 5.5.1 | 1. Nhập các giá trị theo điều kiện:<br>X Spec: LL<LCL<CENTER<UCL<UL<br>R Spec: UCL<UL<br>2. Khi nhập LL/UL > hiển thị LCL/UCL tương ứng<br>3. Chỉ cần nhập UL hoặc LL khi Active<br>4. Có thể không nhập R Spec |  |  |  |
| 42 |  | Nếu có tiêu chuẩn Side B, thực hiện tương tự |  |  |  |
| 43 | 5.6.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 44 | 5.7.1 | Sau khi nhập đủ thông tin (active ít nhất 1 tiêu chuẩn content của equipment type, side bất kì) > Nhấn Save để lưu |  |  |  |
| 45 | 5.8.1 | Hộp thoại xác nhận hiển thị Lưu và ghi đè tiêu chuẩn Sequence này cho toàn bộ Item Code |  |  |  |
| 46 | 5.9.1.1 | Xác nhận > Nhấn OK<br>Lưu ý: Khi update, sẽ update toàn bộ các ItemCode có tag Common, không update tag Individual |  |  |  |
| 47 | 5.9.2.1 | Không lưu các khai báo này, cần chỉnh thêm > Nhấn Cancel |  |  |  |
| 48 | 5.3.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 49 | 6. Xóa dữ liệu tiêu chuẩn IPQC cho ItemName/Delete IPQC Spec for ItemName |  |  |  |  |
| 50 | 6.1 | Chọn Stage Name tại màn hình quản lý |  |  |  |
| 51 | 6.2 | Nhấn Delete tại dòng có dữ liệu cần xóa |  |  |  |
| 52 | 6.3 | Hệ thống hiển thị hộp thoại xác nhận |  |  |  |
| 53 | 6.4.1 | Xác nhận > Nhấn OK<br>Lưu ý: Khi xóa, sẽ xóa toàn bộ các tiêu chuẩn ItemCode theo ItemName, không phân biệt tag |  |  |  |
| 54 | 6.4.2 | Hủy thao tác, đóng hộp thoại, giữ lại bản ghi > Nhấn Cancel |  |  |  |
| 55 | 7. Xem lịch sử chỉnh sửa của tiêu chuẩn IPQC cho ItemName/History Record |  |  |  |  |
| 56 | 7.1 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 57 | 7.2 | Màn hình History Summary hiển thị |  |  |  |
| 58 | 7.3 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý tiêu chuẩn IPQC cho ItemName |  |  |  |
| 59 | 7.4 | Nhấn Detail tại Lịch sử cần xem |  |  |  |
| 60 | 7.5 | Hộp thoại chi tiết lịch sử hiển thị |  |  |  |

## IPQC Spec ItemCode_draft

> Sheet có 30 ảnh chụp màn hình (bản cũ), không tách ra; ảnh mới của màn này nằm trong bộ KB.

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG QUẢN LÝ TIÊU CHUẨN IPQC CHO ITEM CODE<br>GUIDELINES FOR USING THE IPQC SPEC FOR ITEM CODE MANAGEMENT FUNCTION <!-- A1 -->

VII, Hướng dẫn sử dụng chức năng IPQC > Quản lý Tiêu chuẩn IPQC cho Item Code <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

Bảng có cột TRẠNG THÁI Common/Individual; Detail tương tự ItemName + Item Code. Ảnh: images/25_*.jpg <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R |
|---|---|---|---|---|---|
| 5 | 1 | Hiển thị màn hình IPQC Spec for ItemCode Management |  | Khai báo tiêu chuẩn đo cho các nội dung IPQC đã khai báo.<br>Khi tạo tiêu chuẩn tại màn Spec for ItemName, hệ thống tự động tạo các tiêu chuẩn cho các ItemCode thuộc ItemName.<br>Tag Common là các dữ liệu tạo bởi ItemName.<br>Tag Individual là các dữ liệu đã có chỉnh sửa. |  |
| 6 | 2. Tìm kiếm/Search |  |  |  |  |
| 7 | 2.1 | Chọn Stage Name để hệ thống hiển thị các thông tin |  |  |  |
| 8 | 2.2 | Nhập thêm thông tin tìm kiếm (không bắt buộc):<br>\- Chọn Item Name (đã nhập tại màn quản lý Item)<br>\- Chọn Item Code (khai báo theo Item Name) |  |  |  |
| 9 | 2.3 | Nhấn Clear > Hiển thị màn hình mặc định |  |  |  |
| 10 | 3. Xem chi tiết tiêu chuẩn IPQC cho ItemName/Detail IPQC Spec for ItemName |  |  |  |  |
| 11 | 3.1 | Chọn Stage Name tại màn quản lý |  |  |  |
| 12 | 3.2 | Nhấn Detail tại dữ liệu tiêu chuẩn cần xem |  |  |  |
| 13 | 3.3 | Hệ thống hiển thị chi tiết và fill các thông tin cũ chính xác |  |  |  |
| 14 |  | Có thể lọc thông tin cho dễ theo dõi:<br>\- Chọn Location<br>\- Chọn Equipment Type |  |  |  |
| 15 |  | Có thể chọn:<br>Expand All: Hiển thị toàn bộ Side A, Side B của các content<br>Collapse All: Thu gọn hiển thị của Side A, Side B |  |  |  |
| 16 | 3.4 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 17 | 4. Cập nhật tiêu chuẩn IPQC cho ItemName/Updatel IPQC Spec for ItemName |  |  |  |  |
| 18 | 4.1 | Tại màn Detail, nhấn Edit để chỉnh sửa tiêu chuẩn |  |  |  |
| 19 | 4.2 | Màn hình Update fill các dữ liệu đã khai báo chính xác |  |  |  |
| 20 |  | Có thể chọn:<br>Expand All: Hiển thị toàn bộ Side A, Side B của các content<br>Collapse All: Thu gọn hiển thị của Side A, Side B |  |  |  |
| 21 |  | Có thể lọc thông tin cho dễ theo dõi:<br>\- Chọn Location<br>\- Chọn Equipment Type | e |  |  |
| 22 | 4.3.1 | Người dùng nhập các thông tin:<br>\- Nhập Sequence<br>\- Nhập Unit<br>\- Nhập Leadtime: được tính bằng phút |  |  |  |
| 23 |  | Dữ liệu kết hợp: Stage name + ItemName + Sequence<br>\+ Nếu thay đổi Sequence > Tạo thành tiêu chuẩn khác<br>\+ Nếu giữ nguyên Sequence > Chỉ cập nhật thay đổi tiêu chuẩn hiện tại |  |  |  |
| 24 | 4.4.1 | Nhấn Active tại nội dung có tiêu chuẩn theo Equipment Type<br>-> Cho phép nhập tiêu chuẩn<br>-> Có thể nhập riêng Side A/B hoặc cả 2 Side |  |  |  |
| 25 | 4.5.1 | 1. Nhập các giá trị theo điều kiện:<br>X Spec: LL<LCL<CENTER<UCL<UL<br>R Spec: UCL<UL<br>2. Khi nhập LL/UL > hiển thị LCL/UCL tương ứng<br>3. Chỉ cần nhập UL hoặc LL khi Active<br>4. Có thể không nhập R Spec |  |  |  |
| 26 |  | Nếu có tiêu chuẩn Side B, thực hiện tương tự |  |  |  |
| 27 | 4.6.1 | Bắt buộc nhập Reason/Lý do thay đổi thông tin |  |  |  |
| 28 | 4.7.1 | Sau khi nhập đủ thông tin (active ít nhất 1 tiêu chuẩn content của equipment type, side bất kì) > Nhấn Save để lưu |  |  |  |
| 29 | 4.8.1 | Hộp thoại xác nhận hiển thị |  |  |  |
| 30 | 4.9.1.1 | Xác nhận > Nhấn OK |  |  |  |
| 31 |  | [Tại màn hình quản lý]<br>Cập nhật thành công, ItemCode được cập nhật tại màn hình này sẽ có tag Individual<br>Khi update tại ItemName sẽ không bị ghi đè dữ liệu |  |  |  |
| 32 | 4.9.2.1 | Không lưu các khai báo này, cần chỉnh thêm > Nhấn Cancel |  |  |  |
| 33 | 4.3.2 | Nhấn Back để quay lại màn quản lý |  |  |  |
| 34 | 5. Xem lịch sử chỉnh sửa của tiêu chuẩn IPQC cho ItemName/History Record |  |  |  |  |
| 35 | 5.1 | Nhấn History Summary trên góc phải màn hình |  |  |  |
| 36 | 5.2 | Màn hình History Summary hiển thị |  |  |  |
| 37 | 5.3 | Người dùng có thể thực hiện tìm kiếm tương tự màn Quản lý tiêu chuẩn IPQC cho ItemName |  |  |  |
| 38 | 5.4 | Nhấn Detail tại Lịch sử cần xem |  |  |  |
| 39 | 5.5 | Hộp thoại chi tiết lịch sử hiển thị |  |  |  |

## Service Monitor

HƯỚNG DẪN SỬ DỤNG CHỨC NĂNG ĐỌC FILE KẾT QUẢ ĐO<br>GUIDELINES FOR READING MEASUREMENT RESULT FILES <!-- A1 -->

VIII, Service đọc dữ liệu > Chức năng đọc file kết quả đo <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

CHƯA XÁC MINH LẠI trong Rev01 (ứng dụng desktop). Web hiện có chỉ báo Service Auto và Kiểu LogFile → cần rà soát trên máy đo. <!-- R4 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R | Ảnh |
|---|---|---|---|---|---|---|
| 5 | 1 | Khởi động Service được cài tại thiết bị, màn hình Service hiển thị |  |  |  | ![Service Monitor F5](assets/user-guide/service-monitor-01-F5.png) |
| 6 |  | Có thể truy cập các chức năng khác bằng cách nhấn vào các ô tương ứng trên thanh Menu bên trái |  |  |  | ![Service Monitor F6](assets/user-guide/service-monitor-02-F6.png) |
| 7 | 2. Các thông tin hiển thị trên màn hình |  |  |  |  |  |
| 8 | 2.1 | Khu vực thông tin và thực hiện thao tác chính, bao gồm:<br>1. Thông tin cài đặt của service, trạng thái kết nối<br>2. Các ô nhận thông tin (Mã yêu cầu, Mã nhân viên)<br>3. Các nút thao tác (được trình bày chi tiết trong các bước sau) |  |  |  | ![Service Monitor F8](assets/user-guide/service-monitor-03-F8.png) |
| 9 | 2.2 | Danh sách yêu cầu: Các yêu cầu đo tại Location + Equipment Type được hiển thị |  |  |  | ![Service Monitor F9](assets/user-guide/service-monitor-04-F9.png) |
| 10 | 2.3 | Nhật kí thực thi: Lưu lại các thay đổi/thao tác/lỗi trong quá trình đọc file |  |  |  | ![Service Monitor F10](assets/user-guide/service-monitor-05-F10.png) |
| 11 | 3. Thực hiện đọc file kết quả đo và phán định/Read file and Judgment |  |  |  |  |  |
| 12 | 3.1 | Scan Mã yêu cầu bằng mã QR Request No của yêu cầu cần đo<br>Lưu ý: chỉ nhận được các Request đã thực hiện nhận mẫu |  |  |  | ![Service Monitor F12](assets/user-guide/service-monitor-06-F12.png) |
| 13 | 3.2 | Scan Mã nhân viên bằng ID của người thực hiện đo<br>→ Hệ thống tự động tạo thư mục chứa các file |  |  |  | ![Service Monitor F13](assets/user-guide/service-monitor-07-F13.png) |
| 14 | 3.3 | Request được scan sẽ cập nhật trạng thái trên web<br>→ màn hình hiển thị mã yêu cầu đang đo |  |  |  | ![Service Monitor F14](assets/user-guide/service-monitor-08-F14.png) ![Service Monitor F14](assets/user-guide/service-monitor-09-F14.png) |
| 15 | 3.4 | Nhấn Thư mục để mở folder hệ thống |  |  |  | ![Service Monitor F15](assets/user-guide/service-monitor-10-F15.png) |
| 16 | 3.5 | Lưu file kết quả đo và các folder/file liên quan vào folder hiển thị trên màn hình |  |  |  | ![Service Monitor F16](assets/user-guide/service-monitor-11-F16.png) |
| 17 | 3.6 | Trong folder có file và các folder > Nút Đọc tệp hiển thị |  |  |  | ![Service Monitor F17](assets/user-guide/service-monitor-12-F17.png) |
| 18 | 3.7 | Nhấn Đọc tệp để hệ thống thực hiện đọc tệp + Copy các tệp có trong link Local sang link Server |  |  |  | ![Service Monitor F18](assets/user-guide/service-monitor-13-F18.png) |
| 19 | 3.8.1 | Khi đọc file thành công hệ thống hiển thị thông báo > Nhấn Đồng ý để xác nhận và đóng hộp thoại<br>1. Request được xóa khỏi danh sách đo<br>2. Trạng thái được cập nhật Hoàn thành/Completed<br>3. Copy các tệp có trong link Local sang link Server |  |  |  | ![Service Monitor F19](assets/user-guide/service-monitor-14-F19.png) ![Service Monitor F19](assets/user-guide/service-monitor-15-F19.png) |
| 20 | 3.8.2 | Trong quá trình đọc file thất bại<br>1. Hệ thống thông báo lỗi tại mục Nhật ký thực thi<br>2. Request vẫn ở trạng thái Đang đo/Measuring |  |  |  | ![Service Monitor F20](assets/user-guide/service-monitor-16-F20.png) |
| 21 | 4. Thực hiện đo lại và đọc file kết quả lần đo lại/Remeasure and Read file result |  |  |  |  |  |
| 22 | 4.1 | Scan Mã yêu cầu bằng mã QR Request No của yêu cầu cần đo lại<br>Lưu ý: chỉ nhận được các Request đã thực hiện nhận mẫu |  | Số lần được đo lại của các Request phụ thuộc vào số lần đã cấu hình tại màn Cài đặt |  | ![Service Monitor F22](assets/user-guide/service-monitor-17-F22.png) |
| 23 | 4.2 | Nếu Request đã được đo thành công trước đó > Hệ thống hiển thị hộp thoại xác nhận đo lại |  |  |  | ![Service Monitor F23](assets/user-guide/service-monitor-18-F23.png) |
| 24 | 4.3.1 | Xác nhận đo lại > Nhấn Đồng ý |  |  |  | ![Service Monitor F24](assets/user-guide/service-monitor-19-F24.png) |
| 25 | 4.4.1 | Service xác nhận đo lại, hiển thị ô Scan Mã nhân viên, người dùng scan ID người thực hiện tại đây |  |  |  | ![Service Monitor F25](assets/user-guide/service-monitor-20-F25.png) |
| 26 | 4.5.1 | Danh sách yêu cầu hiển thị lại thông tin của Request đo lại, số lần đã thực hiện đo và kết quả lần đo trước đó |  |  |  | ![Service Monitor F26](assets/user-guide/service-monitor-21-F26.png) |
| 27 | 4.3.2 | Đóng hộp thoại/Không đo lại Request > Nhấn Bỏ qua |  |  |  | ![Service Monitor F27](assets/user-guide/service-monitor-22-F27.png) |
| 28 | 5. Làm mới yêu cầu/Refresh Request |  |  |  |  |  |
| 29 | 5.1 | Khi đang thực hiện đo request > Nhấn Làm mới |  |  |  | ![Service Monitor F29](assets/user-guide/service-monitor-23-F29.png) |
| 30 | 5.2 | Hộp thoại xác nhận làm mới hiển thị |  |  |  | ![Service Monitor F30](assets/user-guide/service-monitor-24-F30.png) |
| 31 | 5.3.1 | Xác nhận > Nhấn Đồng ý |  |  |  | ![Service Monitor F31](assets/user-guide/service-monitor-25-F31.png) |
| 32 | 5.4.1 | Trạng thái của Request cập nhật thành Received |  |  |  | ![Service Monitor F32](assets/user-guide/service-monitor-26-F32.png) ![Service Monitor F32](assets/user-guide/service-monitor-27-F32.png) |
| 33 | 5.3.2 | Vẫn tiếp tục đo > Nhấn Bỏ qua |  |  |  | ![Service Monitor F33](assets/user-guide/service-monitor-28-F33.png) |

## Pending List

HƯỚNG DẪN XEM VÀ ĐO CÁC YÊU CẦU ĐANG CHỜ<br>GUIDELINES FOR VIEWING AND MEASURING PENDING REQUESTS <!-- A1 -->

VIII, Service đọc dữ liệu > Hướng dẫn xem các yêu cầu đang chờ <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R: CHƯA XÁC MINH LẠI trong Rev01. | Ảnh |
|---|---|---|---|---|---|---|
| 5 | 1 | Chọn menu Pending Request trong menu bên trái màn hình |  |  |  | ![Pending List F5](assets/user-guide/pending-list-01-F5.png) |
| 6 | 2 | Màn hình Danh sách yêu cầu chờ đo hiển thị |  |  |  | ![Pending List F6](assets/user-guide/pending-list-02-F6.png) |
| 7 | 3.1 | Để thực hiện đo các Request đang chờ đo, tìm Request No trong list |  |  |  | ![Pending List F7](assets/user-guide/pending-list-03-F7.png) |
| 8 | 4.1 | Nhấn đúp vào Request cần đọc lại |  |  |  | ![Pending List F8](assets/user-guide/pending-list-04-F8.png) |
| 9 | 5.1 | Service tự động fill Request No vào ô Mã yêu cầu<br>Thực hiện đo theo hướng dẫn tại Sheet Service Monitor |  | Hướng dẫn thực hiện đọc file đo |  | ![Pending List F9](assets/user-guide/pending-list-05-F9.png) |
| 10 | 3.2 | Không thực hiện đo yêu cầu nào/Không có yêu cầu nào > Nhấn Đóng hộp thoại |  |  |  | ![Pending List F10](assets/user-guide/pending-list-06-F10.png) |

## History Result

HƯỚNG DẪN TRUY CẬP VÀ XEM KẾT QUẢ CÁC LẦN ĐO<br>GUIDELINES FOR ACCESSING AND VIEWING MEASUREMENT RESULTS <!-- A1 -->

VIII, Service đọc dữ liệu > Chức năng lịch sử và xem kết quả đo <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R: CHƯA XÁC MINH LẠI trong Rev01. | Ảnh |
|---|---|---|---|---|---|---|
| 5 | 1 | Chọn menu Tóm tắt lịch sử trong menu bên trái màn hình |  |  |  | ![History Result F5](assets/user-guide/history-result-01-F5.png) |
| 6 | 2 | Màn hình Lịch sử hiển thị |  |  |  | ![History Result F6](assets/user-guide/history-result-02-F6.png) |
| 7 | 3. Tìm kiếm lịch sử |  |  |  |  |  |
| 8 | 3.1 | Có thể nhập các thông tin tìm kiếm:<br>\- Nhập Mã yêu cầu<br>\- Chọn Từ ngày - Đến Ngày: nếu không chọn mặc định là 7 ngày gần nhất<br>\- Chọn Kết quả đo: Tất cả/OK/NG |  |  |  | ![History Result F8](assets/user-guide/history-result-03-F8.png) |
| 9 | 3.2.1 | Nhấn Tìm kiếm > Hiển thị các dữ liệu trùng khớp |  |  |  | ![History Result F9](assets/user-guide/history-result-04-F9.png) |
| 10 | 3.2.2 | Nhấn Đặt lại > Hiển thị màn hình mặc định |  |  |  | ![History Result F10](assets/user-guide/history-result-05-F10.png) |
| 11 | 4. Xem kết quả đo của yêu cầu/View Result |  |  |  |  |  |
| 12 | 4.1 | Nhấn đúp vào yêu cầu cần xem lịch sử và kết quả đo |  |  |  | ![History Result F12](assets/user-guide/history-result-06-F12.png) |
| 13 | 4.2 | Kết quả đo hiển thị trên màn hình |  |  |  | ![History Result F13](assets/user-guide/history-result-07-F13.png) |
| 14 | 4.3.1 | Nhấn vào dòng hoặc cột Judgment của Side A/B để xem chi tiết dữ liệu |  |  |  | ![History Result F14](assets/user-guide/history-result-08-F14.png) |
| 15 | 4.4.1 | Có thể xem kết quả của các lần đo trước |  |  |  | ![History Result F15](assets/user-guide/history-result-09-F15.png) |
| 16 | 4.3.2 | Nhấn Đóng để đóng lịch sử |  |  |  | ![History Result F16](assets/user-guide/history-result-10-F16.png) |

## Service Configuration

HƯỚNG DẪN CÀI ĐẶT CẤU HÌNH SERVICE<br>GUIDELINES FOR CONFIGURING SERVICE SETTINGS <!-- A1 -->

VIII, Service đọc dữ liệu > Cấu hình Service <!-- A3 -->

CẬP NHẬT Rev01 (2026-10-28) <!-- R3 -->

| Row | A: Bước<br>Step | B: Hướng dẫn<br>Instruction | F: Hình ảnh thao tác<br>Picture | L: Chú ý<br>Notes | R: CHƯA XÁC MINH LẠI trong Rev01. | Ảnh |
|---|---|---|---|---|---|---|
| 5 | 1 | Chọn menu Cài đặt trong menu bên trái màn hình |  |  |  | ![Service Configuration F5](assets/user-guide/service-configuration-01-F5.png) |
| 6 | 2 | Màn hình Cài đặt hệ thống hiển thị |  |  |  | ![Service Configuration F6](assets/user-guide/service-configuration-02-F6.png) |
| 7 | 3 | Nhấn Location > Chọn Location trong danh sách |  |  |  | ![Service Configuration F7](assets/user-guide/service-configuration-03-F7.png) |
| 8 | 4 | Nhấn Equipment Type > Chọn Equipment Type trong danh sách<br>Lưu ý: Lọc theo Location đã chọn |  |  |  | ![Service Configuration F8](assets/user-guide/service-configuration-04-F8.png) |
| 9 | 5 | Nhấn Equipment > Chọn Equipment trong danh sách<br>Lưu ý: Lọc theo Equipment Type đã chọn |  |  |  | ![Service Configuration F9](assets/user-guide/service-configuration-05-F9.png) |
| 10 | 6 | Local Folder Path có thể chọn bằng 2 cách:<br>1. Người dùng copy path và paste trực tiếp vào ô nhập<br>2. Nhấn Browse > Tìm folder Local > OK |  |  |  | ![Service Configuration F10](assets/user-guide/service-configuration-06-F10.png) |
| 11 | 7 | Server Folder Path có thể chọn bằng 2 cách:<br>1. Người dùng copy path và paste trực tiếp vào ô nhập<br>2. Nhấn Browse > Tìm folder Server > OK |  |  |  | ![Service Configuration F11](assets/user-guide/service-configuration-07-F11.png) |
| 12 | 8 | Nhập Số lần đo lại tối đa |  |  |  | ![Service Configuration F12](assets/user-guide/service-configuration-08-F12.png) |
| 13 | 9 | Lưu lại các thay đổi đã nhập > Nhấn Lưu cài đặt |  |  |  | ![Service Configuration F13](assets/user-guide/service-configuration-09-F13.png) |
| 14 | 10 | Không lưu các thay đổi > Nhấn Hủy để đóng hộp thoại |  |  |  | ![Service Configuration F14](assets/user-guide/service-configuration-10-F14.png) |
