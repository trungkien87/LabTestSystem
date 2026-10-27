# A. CHỨC NĂNG

_(Functional Suitability)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## A1. Đầy đủ chức năng (Functional Completeness)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo test case (positive/negative/boundary) + ma trận truy vết RTM
- **Nguồn:** `3. Assessment Checklist!A5:I5`, `4. Detailed Guidance!A5:J5`

### Nội dung yêu cầu

Tất cả chức năng trong tài liệu đặc tả (URS/FS/BRD) được xây dựng đầy đủ, không thiếu sót.

### Tiêu chí đánh giá (Đạt)

1\. Đối chiếu 100% hạng mục trong Requirement Traceability Matrix (RTM).\
2\. Không có yêu cầu nào chưa được hiện thực hóa.

### Giải thích (ngôn ngữ đơn giản)

Tất cả chức năng trong tài liệu đặc tả (URS/FS/BRD) được xây dựng đầy đủ, không thiếu sót.

### Cách kiểm tra (từng bước)

1\. Lấy tài liệu URS/FS/BRD bản mới nhất đã phê duyệt và RTM.\
2\. Đối chiếu từng dòng yêu cầu với RTM — mỗi yêu cầu phải có ít nhất 1 test case tương ứng.\
3\. Yêu cầu đội dự án demo trực tiếp các chức năng khó kiểm chứng qua tài liệu.\
4\. Ghi nhận danh sách yêu cầu (nếu có) chưa được hiện thực hóa, kèm mã yêu cầu.

### Bằng chứng cần thu thập

RTM bản mới nhất; báo cáo test case đã Pass; ảnh/video demo chức năng.

### Điều kiện ĐẠT

1\. 100% dòng yêu cầu trong RTM ở trạng thái "Đã xây dựng & test Pass".\
2\. Không có yêu cầu "Chưa triển khai" hoặc "Thiếu test case".

### Điều kiện KHÔNG ĐẠT

Phát hiện ≥ 1 yêu cầu trong URS/FS/BRD không có trong RTM, hoặc có trong RTM nhưng chưa xây dựng/chưa test.

### Ví dụ lỗi thường gặp thực tế

RTM lập từ đầu dự án nhưng không cập nhật khi có yêu cầu thay đổi (change request) giữa chừng → yêu cầu phát sinh sau này bị bỏ sót khi audit; hoặc RTM chỉ liệt kê module chính, thiếu yêu cầu phụ trợ (báo cáo, export, thông báo email...).

## A2. Tính đúng đắn chức năng (Functional Correctness)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo test case (positive/negative/boundary) + ma trận truy vết RTM
- **Nguồn:** `3. Assessment Checklist!A6:I6`, `4. Detailed Guidance!A6:J6`

### Nội dung yêu cầu

Kết quả xử lý của hệ thống chính xác theo nghiệp vụ và công thức tính toán quy định.

### Tiêu chí đánh giá (Đạt)

100% test case chức năng (positive/negative/boundary) đạt kết quả đúng như kỳ vọng (expected result).

### Giải thích (ngôn ngữ đơn giản)

Kết quả xử lý của hệ thống chính xác theo nghiệp vụ và công thức tính toán quy định.

### Cách kiểm tra (từng bước)

1\. Lấy bộ test case chức năng (positive/negative/boundary) đã build từ RTM.\
2\. Chọn ngẫu nhiên tối thiểu 20–30% test case (ưu tiên nghiệp vụ tính toán phức tạp), chạy lại độc lập, không dựa vào kết quả đội dự án tự báo cáo.\
3\. Với công thức tính toán (VD: OEE, giá thành, tồn kho...), đối chiếu công thức trên hệ thống với công thức nghiệp vụ đã được Business Owner phê duyệt.

### Bằng chứng cần thu thập

Báo cáo test case đầy đủ (kèm ảnh kết quả); biên bản đối chiếu công thức tính toán có chữ ký Business Owner.

### Điều kiện ĐẠT

1\. 100% test case có kết quả thực tế = expected result.\
2\. Không lệch số liệu khi audit chạy lại mẫu ngẫu nhiên.

### Điều kiện KHÔNG ĐẠT

Có ≥ 1 test case fail, hoặc kết quả tính toán sai lệch so với công thức đã duyệt.

### Ví dụ lỗi thường gặp thực tế

Làm tròn số sai quy tắc (làm tròn xuống thay vì theo chuẩn kế toán) gây lệch nhỏ nhưng tích lũy sai lớn qua nhiều bản ghi; hoặc công thức đúng ở Test nhưng bị cấu hình khác ở Production do thông số hệ thống chưa đồng bộ.

## A3. Tính phù hợp chức năng (Functional Appropriateness)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo test case (positive/negative/boundary) + ma trận truy vết RTM
- **Nguồn:** `3. Assessment Checklist!A7:I7`, `4. Detailed Guidance!A7:J7`

### Nội dung yêu cầu

Chức năng được thiết kế phù hợp, hỗ trợ đúng mục tiêu và quy trình nghiệp vụ của người dùng.

### Tiêu chí đánh giá (Đạt)

Không phát sinh thao tác thừa hoặc thao tác vòng vo (workaround) khi thực hiện quy trình nghiệp vụ chính.

### Giải thích (ngôn ngữ đơn giản)

Chức năng được thiết kế phù hợp, hỗ trợ đúng mục tiêu và quy trình nghiệp vụ của người dùng.

### Cách kiểm tra (từng bước)

1\. Yêu cầu super user từng bộ phận thực hiện quy trình nghiệp vụ chính từ đầu đến cuối trên hệ thống thật/UAT.\
2\. Đếm số bước/màn hình thực tế, so sánh với SOP đã thống nhất.\
3\. Ghi nhận thao tác thừa, phải nhập lại dữ liệu đã có, hoặc phải dùng công cụ ngoài hệ thống (Excel, giấy).

### Bằng chứng cần thu thập

Video/ảnh thao tác thực tế đối chiếu SOP; phản hồi bằng văn bản từ super user.

### Điều kiện ĐẠT

Không phát sinh bước thừa/workaround khi thực hiện quy trình chính so với SOP.

### Điều kiện KHÔNG ĐẠT

Có ≥ 1 quy trình chính phải qua thao tác vòng vo/công cụ ngoài hệ thống mới hoàn tất.

### Ví dụ lỗi thường gặp thực tế

Hệ thống thiếu liên kết dữ liệu giữa các module (phải nhập lại thông tin đơn hàng ở module khác dù đã nhập ở module trước) → người dùng phải dùng Excel trung gian.

## A4. Xử lý ngoại lệ & trường hợp biên (Exception & Boundary Handling)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo test case (positive/negative/boundary) + ma trận truy vết RTM
- **Nguồn:** `3. Assessment Checklist!A8:I8`, `4. Detailed Guidance!A8:J8`

### Nội dung yêu cầu

Hệ thống xử lý đúng các trường hợp ngoại lệ, dữ liệu biên, dữ liệu rỗng/âm/vượt ngưỡng.

### Tiêu chí đánh giá (Đạt)

100% test case ngoại lệ/biên (edge case) được thực hiện, không gây lỗi hệ thống (crash, treo, sai dữ liệu).

### Giải thích (ngôn ngữ đơn giản)

Hệ thống xử lý đúng các trường hợp ngoại lệ, dữ liệu biên, dữ liệu rỗng/âm/vượt ngưỡng.

### Cách kiểm tra (từng bước)

1\. Rà soát danh sách test case biên đã build (dữ liệu rỗng, âm, vượt ngưỡng, ký tự đặc biệt, file quá dung lượng...).\
2\. Chạy lại ngẫu nhiên 10–15 case biên rủi ro cao nhất (auditor tự chọn thêm, không chỉ theo danh sách có sẵn).\
3\. Quan sát hệ thống có crash, treo, hiển thị lỗi kỹ thuật (stack trace), hoặc lưu sai dữ liệu không.

### Bằng chứng cần thu thập

Báo cáo test case biên; ảnh/video khi audit tự chạy thêm case biên.

### Điều kiện ĐẠT

1\. 100% test case biên/ngoại lệ Pass.\
2\. Hệ thống không crash/treo/lưu sai dữ liệu.\
3\. Thông báo lỗi rõ ràng.

### Điều kiện KHÔNG ĐẠT

Có ≥ 1 trường hợp biên gây crash, treo, mất dữ liệu, hoặc lưu sai dữ liệu mà không cảnh báo.

### Ví dụ lỗi thường gặp thực tế

Chỉ test giá trị biên "đẹp" (0, số âm nhỏ) mà bỏ sót các trường hợp thực tế như dán dữ liệu chứa ký tự ẩn/emoji, hoặc nhập số cực lớn gây tràn kiểu dữ liệu (integer overflow).

## A5. Khả năng truy vết yêu cầu (Requirements Traceability)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo test case (positive/negative/boundary) + ma trận truy vết RTM
- **Nguồn:** `3. Assessment Checklist!A9:I9`, `4. Detailed Guidance!A9:J9`

### Nội dung yêu cầu

Mỗi chức năng phải truy vết được về yêu cầu gốc và test case tương ứng.

### Tiêu chí đánh giá (Đạt)

100% chức năng có liên kết Requirement ↔ Design ↔ Test case ↔ Defect (nếu có).

### Giải thích (ngôn ngữ đơn giản)

Mỗi chức năng phải truy vết được về yêu cầu gốc và test case tương ứng.

### Cách kiểm tra (từng bước)

1\. Chọn ngẫu nhiên 5–10 chức năng, truy vết ngược: chức năng → test case → yêu cầu gốc trong RTM.\
2\. Với chức năng có defect đã ghi nhận, kiểm tra defect có liên kết ngược về test case/yêu cầu không.\
3\. Kiểm tra công cụ quản lý (RTM/Jira/ALM...) có hỗ trợ tra cứu 2 chiều không.

### Bằng chứng cần thu thập

RTM/công cụ quản lý test có liên kết đầy đủ; ảnh minh họa truy vết 2 chiều.

### Điều kiện ĐẠT

100% mẫu kiểm tra truy vết đầy đủ chuỗi Requirement–Design–Test case–Defect.

### Điều kiện KHÔNG ĐẠT

Có chức năng không xác định được yêu cầu gốc, hoặc test case không gắn với yêu cầu nào trong RTM.

### Ví dụ lỗi thường gặp thực tế

RTM lập bằng Excel tách rời công cụ quản lý defect (Jira...) và không đồng bộ, dẫn đến mất liên kết khi có thay đổi.
