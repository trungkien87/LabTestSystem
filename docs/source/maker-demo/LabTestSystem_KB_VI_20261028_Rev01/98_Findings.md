---
doc: Phát hiện trong quá trình rà soát 2026-10-28 (read-only)
---

# Phát hiện & đề xuất kiểm tra

Phân loại: **Dữ kiện** = quan sát trực tiếp; **Suy luận** = giả thuyết cần xác nhận.

| ID | Mức | Màn hình | Dữ kiện | Suy luận / Rủi ro | Đề xuất |
|---|---|---|---|---|---|
| F-01 | Cao | Chi tiết nội dung yêu cầu | R261022_0007, "BVH: Tỷ lệ đường kính lỗ 75 Bottom/Top": hiển thị LL = **81**, giá trị TB 0.88, KẾT QUẢ OK. Spec hiện tại (ItemName & ItemCode 4M002401000B, Seq 0020) LL = **0.81** | Hoặc lỗi định dạng số khi hiển thị (mất "0."), hoặc spec được sửa sau khi tạo request (snapshot cũ). Người xem có thể hiểu sai phán định | Dev kiểm tra cách lưu/hiển thị spec trên request detail; kiểm tra lịch sử spec |
| F-02 | Trung bình | Cài đặt vai trò | Danh sách quyền không có dòng cho **Cấu hình IPQC** (/LogConfig); dòng "Cài d?t chung" lỗi encoding | Không phân quyền riêng được cho màn cấu hình đọc log (rủi ro sửa cấu hình ngoài ý muốn) | Bổ sung permission key; sửa encoding |
| F-03 | Thấp | Nhiều màn | Tiêu đề chưa Việt hoá khi chọn VI: Build Management, Location Management, Rack Management, Machine/Equipment Management - Insert, IPQC Content/Layout/Spec Management; nhãn Location dùng tiếng Anh (Factory, Department, Description) | Không nhất quán ngôn ngữ | Bổ sung resource VI |
| F-04 | Trung bình | Đổi mật khẩu | Không có ô "Mật khẩu hiện tại"; dropdown Tài khoản cho chọn tài khoản khác | Phụ thuộc hoàn toàn vào phân quyền Change Password; nếu cấp nhầm quyền Edit cho user thường có thể đổi mật khẩu người khác `[Suy luận – chưa thử]` | Xác nhận phân quyền; yêu cầu mật khẩu hiện tại khi tự đổi |
| F-05 | Trung bình | Thiết bị | Nhiều thiết bị có Loại thiết bị hiển thị "ET002" – mã không còn trong danh mục Loại thiết bị | Dữ liệu mồ côi; Service/Location có thể không lọc đúng thiết bị | Rà soát & gán lại loại thiết bị |
| F-06 | Thấp | Công đoạn, Thiết bị, Loại thiết bị | Dữ liệu test trong môi trường đang dùng: "Data gốc nhưng đổi Sample Type để test", "Đã thay đổi Type để test", TestFullF5, TestDF1, Stage Test 1609, Rack test F1/F5, TestRole | Lẫn dữ liệu test vào báo cáo | Dọn dữ liệu hoặc tách môi trường test |
| F-07 | Thấp | Tầng tủ | Label "Tên tầng (Tự động: Tầng 01, Tầng 02…)" nhưng dữ liệu sinh "Layer 01" | Không nhất quán | Thống nhất |
| F-08 | Thấp | Nội dung IPQC | Icon (?) cạnh SPC Rule 1–8 không hiển thị giải thích khi hover | Người dùng không biết rule | Bổ sung mô tả rule |
| F-09 | Thông tin | Yêu cầu | Bộ lọc "Mã máy" và "Item Code" có dấu `*` dù là bộ lọc | Gây hiểu nhầm bắt buộc | Bỏ `*` |
| F-10 | Thông tin | Yêu cầu / Tiếp nhận / Thống kê | Có nút ẩn "Save Selected" trong DOM; modal "Delete Row/Column" ẩn ở Vị trí theo tầng; trường Model/SN/Maker ẩn ở Thiết bị | Chức năng dở dang hoặc đã tắt | Xác nhận với dev |
| F-11 | Thông tin | Cài đặt chung | Thông tin FTP (host, user, mật khẩu) hiển thị cho người có quyền xem màn | Lộ thông tin kết nối | Giới hạn quyền View; che giá trị |

Tài liệu xlsx cũ cũng có lỗi đánh số bước (vd sheet Receive mục "3. Tìm kiếm" dùng số 2.x; IPQC Content bước 7.8.1) – đã chuẩn hoá trong bản Markdown.
