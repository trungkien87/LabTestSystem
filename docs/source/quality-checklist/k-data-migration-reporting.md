# K. DI CHUYỂN DỮ LIỆU & XUẤT BÁO CÁO

_(Data Migration & Reporting)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## K1. Di chuyển dữ liệu khi go-live (Data Migration Verification)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo đối chiếu dữ liệu trước/sau di chuyển, kế hoạch migration
- **Nguồn:** `3. Assessment Checklist!A101:I101`, `4. Detailed Guidance!A101:J101`

### Nội dung yêu cầu

Dữ liệu từ hệ thống cũ (nếu có) được di chuyển đầy đủ, chính xác sang hệ thống mới, không phát sinh sai lệch hoặc mất dữ liệu trong quá trình chuyển đổi.

### Tiêu chí đánh giá (Đạt)

1\. Đối chiếu tối thiểu 100% bản ghi trọng yếu (hoặc mẫu đại diện theo kế hoạch kiểm thử) giữa hệ thống cũ và hệ thống mới.\
2\. Sai lệch = 0%.\
3\. Có báo cáo migration kèm phương án xử lý bản ghi lỗi (nếu có).

### Giải thích (ngôn ngữ đơn giản)

Khi chuyển đổi từ hệ thống cũ sang hệ thống mới, toàn bộ dữ liệu quan trọng phải được di chuyển đầy đủ, chính xác, không phát sinh sai lệch hoặc mất dữ liệu trong quá trình chuyển đổi — đây là bước rủi ro cao nhất trong dự án go-live vì lỗi thường chỉ phát hiện sau khi hệ thống cũ đã ngừng sử dụng.

### Cách kiểm tra (từng bước)

1\. Lấy kế hoạch migration (phạm vi dữ liệu, phương pháp, thời gian thực hiện).\
2\. Đối chiếu dữ liệu trọng yếu giữa hệ thống cũ và hệ thống mới — 100% bản ghi trọng yếu hoặc mẫu đại diện theo kế hoạch kiểm thử đã thống nhất.\
3\. Kiểm tra báo cáo migration có ghi nhận các bản ghi lỗi (nếu có) và phương án xử lý (bỏ qua có lý do, sửa tay, di chuyển lại) không.\
4\. Xác nhận dữ liệu migration đã được rà soát trước khi hệ thống cũ chính thức ngừng sử dụng (không còn đường lùi để đối chiếu lại).

### Bằng chứng cần thu thập

Kế hoạch migration; báo cáo đối chiếu dữ liệu trước/sau di chuyển; phương án xử lý bản ghi lỗi (nếu có).

### Điều kiện ĐẠT

1\. Đối chiếu đạt 100% bản ghi trọng yếu (hoặc mẫu đại diện theo kế hoạch) giữa hệ thống cũ và mới với sai lệch = 0%.\
2\. Có báo cáo migration đầy đủ.

### Điều kiện KHÔNG ĐẠT

Phát hiện sai lệch dữ liệu giữa hệ thống cũ và mới chưa được xử lý/giải trình, hoặc không có báo cáo đối chiếu migration.

### Ví dụ lỗi thường gặp thực tế

Dữ liệu số liệu (VD: số lượng tồn kho) migration đúng, nhưng các trường liên kết quan hệ (VD: mã lô sản xuất liên kết với mã khách hàng) bị lệch do khác biệt cấu trúc khóa chính giữa 2 hệ thống, chỉ phát hiện sau vài tuần khi người dùng truy vết ngược một lô hàng cụ thể và thấy sai thông tin liên kết.

## K2. Độ chính xác xuất/in báo cáo (Report Export & Print Accuracy)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** File báo cáo xuất mẫu (PDF/Excel) đối chiếu với dữ liệu gốc trên giao diện
- **Nguồn:** `3. Assessment Checklist!A102:I102`, `4. Detailed Guidance!A102:J102`

### Nội dung yêu cầu

Báo cáo/dữ liệu xuất ra dưới các định dạng (PDF, Excel, bản in) phải khớp chính xác với dữ liệu hiển thị trên hệ thống, đúng định dạng, không bị cắt xén hoặc lỗi hiển thị.

### Tiêu chí đánh giá (Đạt)

1\. 100% báo cáo xuất/in được kiểm tra khớp số liệu với dữ liệu gốc trên hệ thống.\
2\. Không lỗi định dạng (font, xuống dòng, cắt bảng).\
3\. Tên file/tiêu đề báo cáo đúng quy định.

### Giải thích (ngôn ngữ đơn giản)

Báo cáo/dữ liệu khi xuất ra các định dạng (PDF, Excel, bản in) phải khớp chính xác với dữ liệu hiển thị trên hệ thống, đúng định dạng, không bị cắt xén hay lỗi hiển thị — vì báo cáo xuất ra thường được dùng làm hồ sơ chính thức, gửi khách hàng hoặc phục vụ audit.

### Cách kiểm tra (từng bước)

1\. Chọn mẫu các loại báo cáo chính trong hệ thống, xuất ra từng định dạng (PDF/Excel/in trực tiếp).\
2\. Đối chiếu số liệu trên file xuất ra với dữ liệu gốc hiển thị trên giao diện hệ thống.\
3\. Kiểm tra lỗi định dạng: font chữ, ký tự đặc biệt/tiếng Việt có dấu, xuống dòng, bảng bị cắt khi tràn trang, tên file/tiêu đề báo cáo.

### Bằng chứng cần thu thập

File báo cáo xuất mẫu (PDF/Excel) đối chiếu với dữ liệu gốc trên giao diện; danh sách lỗi định dạng phát hiện (nếu có).

### Điều kiện ĐẠT

1\. 100% báo cáo xuất/in được kiểm tra khớp số liệu với dữ liệu gốc.\
2\. Không lỗi định dạng.\
3\. Tên file/tiêu đề đúng quy định.

### Điều kiện KHÔNG ĐẠT

Có ≥1 báo cáo xuất ra sai lệch số liệu so với dữ liệu gốc, hoặc lỗi định dạng nghiêm trọng (cắt bảng, sai font tiếng Việt) ảnh hưởng đến khả năng sử dụng báo cáo.

### Ví dụ lỗi thường gặp thực tế

Báo cáo Excel xuất ra đúng số liệu nhưng bảng dữ liệu có nhiều cột bị tràn khổ giấy khi in trực tiếp (không tự động fit-to-page), khiến các cột cuối bị cắt mất khi in, người dùng phải tự điều chỉnh thủ công mỗi lần in.
