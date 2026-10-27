# B. TÍNH TOÀN VẸN & BẢO VỆ DỮ LIỆU

_(Data Integrity & Protection)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## B1. Đồng bộ dữ liệu đa tầng

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo đối chiếu dữ liệu (data reconciliation) / trích xuất audit trail
- **Nguồn:** `3. Assessment Checklist!A10:I10`, `4. Detailed Guidance!A10:J10`

### Nội dung yêu cầu

Dữ liệu nhất quán giữa data log, database và giao diện hiển thị cho người dùng cuối.

### Tiêu chí đánh giá (Đạt)

1\. Đối chiếu ngẫu nhiên tối thiểu 30 bản ghi/đợt kiểm tra.\
2\. Sai lệch = 0%.

### Giải thích (ngôn ngữ đơn giản)

Cùng một bản ghi nghiệp vụ phải cho ra giá trị giống nhau dù xem ở đâu — log hệ thống ghi lại lúc phát sinh, database lưu trữ chính thức, và màn hình hiển thị cho người dùng. Nếu 3 tầng này lệch nhau, người dùng ra quyết định sai mà không biết.

### Cách kiểm tra (từng bước)

1\. Chọn ngẫu nhiên tối thiểu 30 bản ghi thuộc các nghiệp vụ trọng yếu khác nhau (không chỉ 1 module).\
2\. Với mỗi bản ghi, truy xuất giá trị ở 3 nguồn: log gốc (event log/audit trail), truy vấn trực tiếp DB, và giá trị hiển thị trên UI/report.\
3\. Đối chiếu từng trường dữ liệu quan trọng (số lượng, trạng thái, thời gian) giữa 3 nguồn.\
4\. Lặp lại ở ít nhất 2 thời điểm khác nhau (giờ cao điểm và thấp điểm) để phát hiện lỗi do độ trễ đồng bộ (sync lag).

### Bằng chứng cần thu thập

Bảng đối chiếu 3 cột (log – DB – UI) cho từng bản ghi mẫu; ảnh chụp màn hình tại thời điểm truy vấn; trích xuất truy vấn DB.

### Điều kiện ĐẠT

1\. 100% mẫu đối chiếu (≥30 bản ghi) khớp tuyệt đối giữa log, DB và UI.\
2\. Nếu có độ trễ đồng bộ thì nằm trong ngưỡng đã công bố và không gây hiển thị sai cho người dùng.

### Điều kiện KHÔNG ĐẠT

Có ≥1 bản ghi lệch giá trị giữa các tầng mà không giải thích được bằng độ trễ đồng bộ đã công bố.

### Ví dụ lỗi thường gặp thực tế

UI dùng cache/session cũ nên hiển thị số liệu trễ hơn DB thực tế vài phút mà không có cơ chế làm mới (refresh) tự động, khiến người vận hành ra quyết định dựa trên số liệu đã lỗi thời tưởng là real-time.

## B2. Khớp dữ liệu hệ thống & file đính kèm

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo đối chiếu dữ liệu (data reconciliation) / trích xuất audit trail
- **Nguồn:** `3. Assessment Checklist!A11:I11`, `4. Detailed Guidance!A11:J11`

### Nội dung yêu cầu

Dữ liệu nhập trong hệ thống (MES) và nội dung file đính kèm (attachment) phải khớp nhau.

### Tiêu chí đánh giá (Đạt)

1\. 100% bản ghi có đính kèm được kiểm tra khớp dữ liệu.\
2\. Không có sai lệch.

### Giải thích (ngôn ngữ đơn giản)

Khi người dùng đính kèm file (chứng từ, ảnh kiểm tra, báo cáo scan...) vào một bản ghi, thông tin nhập tay trên hệ thống (số lô, kết quả, số lượng) phải khớp với nội dung thực tế trong file đó.

### Cách kiểm tra (từng bước)

1\. Lọc danh sách bản ghi có đính kèm file trong kỳ đánh giá.\
2\. Chọn mẫu (ưu tiên bản ghi có giá trị/rủi ro cao) và mở từng file đính kèm để đối chiếu thủ công với dữ liệu đã nhập trên hệ thống.\
3\. Kiểm tra hệ thống có cơ chế cảnh báo/validate khi dữ liệu nhập và file có dấu hiệu không khớp (VD: OCR đối chiếu số liệu) hay hoàn toàn phụ thuộc vào thao tác thủ công của người nhập.

### Bằng chứng cần thu thập

Bảng đối chiếu dữ liệu nhập vs. nội dung file đính kèm; danh sách bản ghi được kiểm tra kèm kết luận khớp/không khớp.

### Điều kiện ĐẠT

1\. 100% bản ghi được kiểm tra có dữ liệu khớp giữa hệ thống và file đính kèm.\
2\. Nếu phát hiện sai lệch phải có quy trình xử lý/điều chỉnh đã ghi nhận.

### Điều kiện KHÔNG ĐẠT

Có ≥1 bản ghi dữ liệu hệ thống không khớp nội dung file đính kèm mà không được phát hiện/xử lý.

### Ví dụ lỗi thường gặp thực tế

Người vận hành đính kèm nhầm file của lô hàng khác (do đặt tên file không chuẩn hóa) nhưng hệ thống không có cơ chế kiểm tra chéo, dẫn đến hồ sơ có dữ liệu và bằng chứng không tương ứng — rủi ro lớn khi audit truy xuất nguồn gốc (traceability).

## B3. Kiểm soát phiên bản file đính kèm

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo đối chiếu dữ liệu (data reconciliation) / trích xuất audit trail
- **Nguồn:** `3. Assessment Checklist!A12:I12`, `4. Detailed Guidance!A12:J12`

### Nội dung yêu cầu

Hệ thống ngăn chặn upload file sai, trùng lặp hoặc file phiên bản cũ.

### Tiêu chí đánh giá (Đạt)

Hệ thống tự động từ chối/cảnh báo 100% trường hợp file sai định dạng, trùng tên, hoặc version thấp hơn bản hiện hành.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống phải ngăn người dùng vô tình tải lên nhầm file (sai định dạng, trùng tên đè lên bản mới hơn, hoặc phiên bản cũ đã lỗi thời).

### Cách kiểm tra (từng bước)

1\. Thử upload file sai định dạng so với quy định (VD: yêu cầu PDF nhưng tải file .docx).\
2\. Thử upload file trùng tên với file đã tồn tại, quan sát hệ thống có cảnh báo/từ chối hay ghi đè âm thầm.\
3\. Thử upload file có số phiên bản thấp hơn phiên bản hiện hành (nếu tên file có quy ước version) để kiểm tra cơ chế chặn.

### Bằng chứng cần thu thập

Ảnh/video các phép thử upload sai định dạng, trùng tên, version cũ; thông báo lỗi hệ thống hiển thị tương ứng.

### Điều kiện ĐẠT

Hệ thống từ chối hoặc cảnh báo rõ ràng cho 100% các trường hợp thử nghiệm (sai định dạng, trùng tên, version thấp hơn).

### Điều kiện KHÔNG ĐẠT

Có ≥1 trường hợp hệ thống cho phép upload/ghi đè mà không cảnh báo, có nguy cơ mất dữ liệu phiên bản cũ.

### Ví dụ lỗi thường gặp thực tế

Tải file trùng tên sẽ tự động ghi đè file cũ trong storage mà không lưu lịch sử phiên bản (versioning), khiến không thể khôi phục lại file gốc nếu người dùng tải nhầm.

## B4. Nhật ký truy vết dữ liệu (Audit Trail)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo đối chiếu dữ liệu (data reconciliation) / trích xuất audit trail
- **Nguồn:** `3. Assessment Checklist!A13:I13`, `4. Detailed Guidance!A13:J13`

### Nội dung yêu cầu

Mọi thay đổi dữ liệu quan trọng được ghi nhận đầy đủ: ai, khi nào, thay đổi gì, giá trị trước/sau.

### Tiêu chí đánh giá (Đạt)

1\. 100% thao tác tạo/sửa/xoá dữ liệu trọng yếu có audit trail.\
2\. Log không thể chỉnh sửa hoặc xoá.

### Giải thích (ngôn ngữ đơn giản)

Mọi hành động tạo/sửa/xóa dữ liệu quan trọng phải được ghi lại: ai thực hiện, lúc nào, thay đổi cái gì, giá trị trước và sau — phục vụ truy vết trách nhiệm và tuân thủ (đặc biệt với hệ thống áp dụng ALCOA+).

### Cách kiểm tra (từng bước)

1\. Thực hiện lần lượt: tạo mới, sửa, và xóa (nếu được phép) một bản ghi trọng yếu.\
2\. Kiểm tra audit trail có ghi đủ 5 yếu tố: user, timestamp, hành động, giá trị trước, giá trị sau.\
3\. Thử dùng tài khoản user thường để sửa/xóa dòng log vừa tạo, xác nhận log không thể chỉnh sửa.\
4\. Kiểm tra audit trail có áp dụng cho cả thao tác thực hiện qua API/import hàng loạt, không chỉ qua UI.

### Bằng chứng cần thu thập

Trích xuất audit trail tương ứng từng thao tác test; kết quả thử sửa/xóa log bằng tài khoản không có thẩm quyền.

### Điều kiện ĐẠT

1\. 100% thao tác tạo/sửa/xóa dữ liệu trọng yếu (kể cả qua API/import) có audit trail đầy đủ 5 yếu tố.\
2\. Log không thể bị chỉnh sửa/xóa bởi user thường.

### Điều kiện KHÔNG ĐẠT

Thiếu audit trail cho ≥1 loại thao tác trọng yếu, hoặc log có thể bị sửa/xóa bởi tài khoản không có thẩm quyền cao nhất.

### Ví dụ lỗi thường gặp thực tế

Audit trail chỉ ghi nhận thao tác qua giao diện web, nhưng dữ liệu sửa qua công cụ import Excel hàng loạt hoặc qua truy vấn DB trực tiếp của IT lại không được ghi log — tạo lỗ hổng truy vết khi có sai lệch dữ liệu diện rộng.

## B5. Sao lưu & khôi phục dữ liệu

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo đối chiếu dữ liệu (data reconciliation) / trích xuất audit trail
- **Nguồn:** `3. Assessment Checklist!A14:I14`, `4. Detailed Guidance!A14:J14`

### Nội dung yêu cầu

Dữ liệu được sao lưu định kỳ và có khả năng khôi phục khi cần.

### Tiêu chí đánh giá (Đạt)

1\. Backup tự động theo lịch quy định.\
2\. Khôi phục thử nghiệm thành công, đạt mục tiêu RPO/RTO.

### Giải thích (ngôn ngữ đơn giản)

Dữ liệu phải được sao lưu định kỳ và đã được kiểm chứng có thể khôi phục thành công khi cần, không chỉ "có backup" trên lý thuyết.

### Cách kiểm tra (từng bước)

1\. Kiểm tra lịch backup tự động đã cấu hình (tần suất, phạm vi dữ liệu, nơi lưu trữ — bao gồm lưu ngoài site/offsite nếu yêu cầu).\
2\. Rà soát log backup gần nhất, xác nhận backup chạy đúng lịch, không lỗi.\
3\. Yêu cầu đội vận hành thực hiện khôi phục thử nghiệm (restore drill) trên môi trường tách biệt, đo thời gian thực tế so với mục tiêu RTO/RPO đã cam kết.\
4\. Kiểm tra dữ liệu sau khôi phục có đầy đủ, đúng, không thiếu bản ghi so với thời điểm backup.

### Bằng chứng cần thu thập

Cấu hình lịch backup; log backup 3 lần gần nhất; biên bản/video khôi phục thử nghiệm kèm thời gian thực tế đạt được.

### Điều kiện ĐẠT

1\. Backup chạy tự động đúng lịch quy định.\
2\. Khôi phục thử nghiệm thành công, đạt mục tiêu RPO/RTO đã cam kết.\
3\. Dữ liệu sau khôi phục toàn vẹn.

### Điều kiện KHÔNG ĐẠT

Backup không chạy đúng lịch/bị lỗi mà không phát hiện kịp thời, hoặc khôi phục thử nghiệm thất bại/không đạt RTO-RPO, hoặc chưa từng thực hiện restore drill.

### Ví dụ lỗi thường gặp thực tế

Có lịch backup tự động nhưng chưa từng thử khôi phục thực tế — đến khi sự cố thật xảy ra mới phát hiện file backup bị lỗi định dạng hoặc thiếu quyền truy cập, không khôi phục được.
