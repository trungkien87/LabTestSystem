# J. ĐÀO TẠO & BÀN GIAO VẬN HÀNH

_(Training & Operational Handover)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## J1. Kế hoạch đào tạo người dùng cuối (End-user Training Plan)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Kế hoạch đào tạo, tài liệu/slide đào tạo, danh sách điểm danh có xác nhận
- **Nguồn:** `3. Assessment Checklist!A99:I99`, `4. Detailed Guidance!A99:J99`

### Nội dung yêu cầu

Có kế hoạch đào tạo đầy đủ cho từng nhóm người dùng (theo vai trò/quyền hạn) trước khi hệ thống go-live, bao gồm nội dung, đối tượng, thời lượng và người phụ trách.

### Tiêu chí đánh giá (Đạt)

1\. 100% nhóm người dùng chính (theo role) đã hoàn thành đào tạo trước go-live.\
2\. Có tài liệu/slide đào tạo và danh sách người tham dự có xác nhận (ký tên/điểm danh điện tử).

### Giải thích (ngôn ngữ đơn giản)

Trước khi hệ thống go-live, cần có kế hoạch đào tạo đầy đủ cho từng nhóm người dùng theo vai trò (vận hành, quản lý, IT hỗ trợ...), bao gồm nội dung, đối tượng, thời lượng và người phụ trách — không thể để người dùng tự mày mò khi hệ thống đã đi vào vận hành thật.

### Cách kiểm tra (từng bước)

1\. Rà soát kế hoạch đào tạo, xác nhận có đầy đủ các nhóm người dùng chính (theo role) trong phạm vi go-live.\
2\. Kiểm tra danh sách người tham dự có xác nhận (ký tên/điểm danh điện tử) cho từng buổi đào tạo.\
3\. Phỏng vấn ngẫu nhiên một vài người dùng đã qua đào tạo để xác nhận nội dung đào tạo có phù hợp, đủ để họ thao tác độc lập không.

### Bằng chứng cần thu thập

Kế hoạch đào tạo; tài liệu/slide đào tạo; danh sách điểm danh có xác nhận của từng nhóm người dùng.

### Điều kiện ĐẠT

1\. 100% nhóm người dùng chính đã hoàn thành đào tạo trước go-live.\
2\. Có tài liệu đào tạo và danh sách tham dự có xác nhận.

### Điều kiện KHÔNG ĐẠT

Có ≥1 nhóm người dùng chính chưa được đào tạo trước go-live, hoặc không có bằng chứng xác nhận tham dự.

### Ví dụ lỗi thường gặp thực tế

Đào tạo tập trung chủ yếu cho nhóm quản lý/super-user, trong khi công nhân vận hành trực tiếp tại dây chuyền (nhóm sử dụng hệ thống nhiều nhất) chỉ được hướng dẫn sơ qua bởi trưởng ca, dẫn đến nhiều lỗi thao tác nhỏ lặp lại sau go-live do chưa hiểu đúng quy trình.

## J2. Tài liệu bàn giao vận hành (Operation Handover Documentation)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Biên bản bàn giao có chữ ký, bộ tài liệu vận hành đính kèm
- **Nguồn:** `3. Assessment Checklist!A100:I100`, `4. Detailed Guidance!A100:J100`

### Nội dung yêu cầu

Đội xây dựng hệ thống bàn giao đầy đủ tài liệu vận hành (user manual, quy trình xử lý sự cố, thông tin liên hệ hỗ trợ) cho đội vận hành/Business Owner trước khi go-live.

### Tiêu chí đánh giá (Đạt)

100% tài liệu vận hành bắt buộc (User Manual, quy trình xử lý sự cố, danh sách liên hệ hỗ trợ) được bàn giao và có biên bản bàn giao ký xác nhận giữa các bên liên quan.

### Giải thích (ngôn ngữ đơn giản)

Đội xây dựng hệ thống phải bàn giao đầy đủ tài liệu vận hành (user manual, quy trình xử lý sự cố, thông tin liên hệ hỗ trợ) cho đội vận hành/Business Owner trước khi go-live, có biên bản ký xác nhận rõ ràng giữa các bên.

### Cách kiểm tra (từng bước)

1\. Lập danh sách tài liệu vận hành bắt buộc theo quy định nội bộ.\
2\. Kiểm tra biên bản bàn giao có chữ ký xác nhận của cả bên xây dựng hệ thống và bên nhận vận hành/Business Owner.\
3\. Đối chiếu từng tài liệu trong biên bản bàn giao có thực sự tồn tại, đầy đủ nội dung không (không chỉ có tên trong danh mục bàn giao).

### Bằng chứng cần thu thập

Biên bản bàn giao có chữ ký; bộ tài liệu vận hành đính kèm đối chiếu với danh mục trong biên bản.

### Điều kiện ĐẠT

100% tài liệu vận hành bắt buộc được bàn giao đầy đủ, có biên bản ký xác nhận giữa các bên liên quan.

### Điều kiện KHÔNG ĐẠT

Thiếu tài liệu vận hành bắt buộc, hoặc có biên bản bàn giao nhưng nội dung tài liệu đính kèm không đầy đủ như cam kết.

### Ví dụ lỗi thường gặp thực tế

Biên bản bàn giao liệt kê đầy đủ danh mục tài liệu và đã có chữ ký các bên, nhưng khi kiểm tra thực tế phát hiện tài liệu "Quy trình xử lý sự cố" chỉ là bản nháp sơ sài 1 trang, chưa đủ chi tiết để đội vận hành tự xử lý các tình huống sự cố phổ biến.
