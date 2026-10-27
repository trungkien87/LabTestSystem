# I. QUẢN LÝ LOG & GIÁM SÁT TẬP TRUNG

_(Log Management & Centralized Monitoring)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## I1. Đồng bộ log từ ứng dụng local lên hệ thống trung tâm (Local-to-Central Log Sync)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A87:I87`, `4. Detailed Guidance!A87:J87`

### Nội dung yêu cầu

Log phát sinh từ phần mềm chạy tại máy trạm/local phải được tự động gửi (đồng bộ) lên hệ thống quản lý log tập trung trên web.

### Tiêu chí đánh giá (Đạt)

1\. 100% sự kiện log quan trọng được đồng bộ lên hệ thống trung tâm trong thời gian quy định (VD: ≤ 5 phút hoặc real-time).\
2\. Có cơ chế xác nhận/đối soát đồng bộ thành công.

### Giải thích (ngôn ngữ đơn giản)

Log phát sinh tại các ứng dụng chạy trên máy trạm/local (thường phân tán khắp xưởng sản xuất) phải được tự động gửi lên hệ thống quản lý log tập trung, giúp đội vận hành giám sát toàn cảnh mà không cần đi kiểm tra từng máy.

### Cách kiểm tra (từng bước)

1\. Tạo một sự kiện log tại ứng dụng local (VD: thao tác đăng nhập, lỗi giả lập).\
2\. Đo thời gian từ lúc sự kiện phát sinh đến khi xuất hiện trên hệ thống trung tâm.\
3\. Kiểm tra cơ chế xác nhận/đối soát đồng bộ (VD: có báo cáo số lượng log đã gửi thành công/thất bại không).

### Bằng chứng cần thu thập

Log gốc tại máy trạm và log tương ứng trên dashboard trung tâm kèm mốc thời gian; báo cáo đối soát đồng bộ (nếu có).

### Điều kiện ĐẠT

1\. 100% sự kiện log quan trọng được đồng bộ lên hệ thống trung tâm trong thời gian quy định.\
2\. Có cơ chế xác nhận đồng bộ thành công.

### Điều kiện KHÔNG ĐẠT

Có sự kiện log quan trọng không được đồng bộ hoặc đồng bộ trễ quá ngưỡng quy định mà không có cảnh báo.

### Ví dụ lỗi thường gặp thực tế

Đồng bộ log hoạt động tốt ở điều kiện mạng ổn định lúc test, nhưng khi mạng xưởng sản xuất có độ trễ cao hơn thực tế (do nhiều thiết bị dùng chung băng thông), log bị dồn ứ và chậm hàng giờ mà không có cơ chế cảnh báo cho đội vận hành biết.

## I2. Xử lý khi mất kết nối mạng (Offline Buffering & Retry Sync)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A88:I88`, `4. Detailed Guidance!A88:J88`

### Nội dung yêu cầu

Khi mất kết nối mạng, log phải được lưu tạm tại local và tự động đồng bộ lại khi có kết nối trở lại, không bị thất lạc dữ liệu.

### Tiêu chí đánh giá (Đạt)

Test ngắt kết nối mạng: 100% log phát sinh trong thời gian offline được đồng bộ đầy đủ, đúng thứ tự, không trùng lặp sau khi kết nối được khôi phục.

### Giải thích (ngôn ngữ đơn giản)

Khi mất kết nối mạng tạm thời (thường xảy ra tại xưởng sản xuất), log phải được lưu tạm tại local và tự động đồng bộ lại đầy đủ khi có kết nối trở lại, không được thất lạc dữ liệu.

### Cách kiểm tra (từng bước)

1\. Ngắt kết nối mạng của ứng dụng local trong một khoảng thời gian (VD: 30 phút), trong lúc đó thực hiện các thao tác phát sinh log.\
2\. Khôi phục kết nối mạng, quan sát log offline có được tự động đồng bộ lại đầy đủ không.\
3\. Kiểm tra thứ tự log sau đồng bộ có đúng theo thời gian phát sinh gốc không, và không bị trùng lặp bản ghi.

### Bằng chứng cần thu thập

Danh sách log phát sinh trong thời gian offline; kết quả đối chiếu log sau khi đồng bộ lại (đầy đủ/đúng thứ tự/không trùng).

### Điều kiện ĐẠT

100% log phát sinh trong thời gian offline được đồng bộ đầy đủ, đúng thứ tự, không trùng lặp sau khi kết nối được khôi phục.

### Điều kiện KHÔNG ĐẠT

Có log bị mất, sai thứ tự, hoặc trùng lặp sau khi đồng bộ lại.

### Ví dụ lỗi thường gặp thực tế

Cơ chế buffer offline chỉ lưu được số lượng log giới hạn trong bộ nhớ (không ghi ra file tạm), nên nếu mất mạng kéo dài hơn dự kiến, các log phát sinh sau khi buffer đầy sẽ bị ghi đè và mất vĩnh viễn.

## I3. Chuẩn hóa định dạng log (Log Format Standardization)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A89:I89`, `4. Detailed Guidance!A89:J89`

### Nội dung yêu cầu

Log được ghi theo định dạng chuẩn, thống nhất giữa các module/ứng dụng.

### Tiêu chí đánh giá (Đạt)

100% bản ghi log tuân thủ định dạng chuẩn quy định: timestamp, mức độ, nguồn phát sinh (module/máy trạm), nội dung, mã sự kiện.

### Giải thích (ngôn ngữ đơn giản)

Log phải được ghi theo định dạng chuẩn, thống nhất giữa các module/ứng dụng (timestamp, mức độ, nguồn phát sinh, nội dung, mã sự kiện), giúp dễ dàng phân tích/tìm kiếm tự động thay vì mỗi module một kiểu.

### Cách kiểm tra (từng bước)

1\. Thu thập mẫu log từ nhiều module/ứng dụng khác nhau trong hệ thống.\
2\. Kiểm tra từng bản ghi log có đủ 5 thành phần chuẩn: timestamp, mức độ, nguồn phát sinh, nội dung, mã sự kiện.\
3\. So sánh định dạng giữa các module có nhất quán không (VD: cùng định dạng thời gian, cùng cấu trúc trường).

### Bằng chứng cần thu thập

Mẫu log trích xuất từ các module khác nhau đối chiếu định dạng.

### Điều kiện ĐẠT

100% bản ghi log tuân thủ định dạng chuẩn quy định với đầy đủ 5 thành phần.

### Điều kiện KHÔNG ĐẠT

Có module ghi log thiếu thành phần bắt buộc hoặc dùng định dạng khác biệt gây khó phân tích tập trung.

### Ví dụ lỗi thường gặp thực tế

Module tích hợp với hệ thống PLC ghi log theo định dạng riêng do nhà cung cấp thiết bị (không theo chuẩn nội bộ), khiến hệ thống log trung tâm không thể parse tự động và phải xử lý ngoại lệ riêng cho module này.

## I4. Phân loại mức độ log (Log Severity Classification)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A90:I90`, `4. Detailed Guidance!A90:J90`

### Nội dung yêu cầu

Log được phân loại theo mức độ: DEBUG/INFO/WARNING/ERROR/CRITICAL.

### Tiêu chí đánh giá (Đạt)

1\. 100% bản ghi log có gắn đúng mức độ.\
2\. Hệ thống trung tâm hỗ trợ lọc/tìm kiếm theo từng mức độ.

### Giải thích (ngôn ngữ đơn giản)

Log cần được phân loại theo mức độ nghiêm trọng (DEBUG/INFO/WARNING/ERROR/CRITICAL) để đội vận hành có thể lọc và ưu tiên xử lý đúng mức độ, tránh bị "chìm" trong hàng nghìn dòng log không quan trọng.

### Cách kiểm tra (từng bước)

1\. Rà soát mẫu log từ các module, kiểm tra mỗi bản ghi có gắn đúng mức độ tương ứng với bản chất sự kiện không (VD: lỗi nghiêm trọng không bị gắn nhầm INFO).\
2\. Thử dùng chức năng lọc/tìm kiếm trên hệ thống trung tâm theo từng mức độ, xác nhận lọc đúng.

### Bằng chứng cần thu thập

Mẫu log đối chiếu mức độ gắn với bản chất sự kiện; kết quả test lọc log theo mức độ trên hệ thống trung tâm.

### Điều kiện ĐẠT

1\. 100% bản ghi log có gắn đúng mức độ.\
2\. Hệ thống trung tâm hỗ trợ lọc/tìm kiếm theo từng mức độ chính xác.

### Điều kiện KHÔNG ĐẠT

Có log gắn sai mức độ (VD: lỗi nghiêm trọng gắn INFO) hoặc chức năng lọc theo mức độ không hoạt động đúng.

### Ví dụ lỗi thường gặp thực tế

Lỗi mất kết nối đến hệ thống ERP (ảnh hưởng nghiêm trọng đến đồng bộ dữ liệu) chỉ được gắn mức WARNING thay vì ERROR/CRITICAL, khiến đội vận hành lọc theo mức Critical để xử lý ưu tiên lại bỏ sót sự cố này.

## I5. Tìm kiếm & tra cứu log tập trung (Centralized Log Search & Query)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A91:I91`, `4. Detailed Guidance!A91:J91`

### Nội dung yêu cầu

Người quản trị có thể tìm kiếm, tra cứu, lọc log của tất cả máy trạm/ứng dụng local từ giao diện web tập trung.

### Tiêu chí đánh giá (Đạt)

1\. Tìm kiếm được theo thời gian, mức độ, nguồn phát sinh, từ khóa.\
2\. Thời gian phản hồi tìm kiếm ≤ 5 giây với dữ liệu trong 30 ngày gần nhất.

### Giải thích (ngôn ngữ đơn giản)

Quản trị viên phải tìm kiếm, lọc log của tất cả máy trạm/ứng dụng local từ một giao diện web tập trung, với tốc độ phản hồi đủ nhanh để phục vụ xử lý sự cố kịp thời.

### Cách kiểm tra (từng bước)

1\. Thực hiện tìm kiếm log theo các tiêu chí: khoảng thời gian, mức độ, nguồn phát sinh, từ khóa nội dung.\
2\. Đo thời gian phản hồi của truy vấn tìm kiếm với dữ liệu trong 30 ngày gần nhất.\
3\. Kiểm tra kết quả tìm kiếm có chính xác, đầy đủ so với dữ liệu gốc không.

### Bằng chứng cần thu thập

Kết quả test tìm kiếm theo từng tiêu chí kèm thời gian phản hồi đo được.

### Điều kiện ĐẠT

1\. Tìm kiếm được theo thời gian, mức độ, nguồn phát sinh, từ khóa.\
2\. Thời gian phản hồi ≤ 5 giây với dữ liệu trong 30 ngày gần nhất.

### Điều kiện KHÔNG ĐẠT

Thiếu khả năng lọc theo một trong các tiêu chí trên, hoặc thời gian phản hồi vượt ngưỡng quy định.

### Ví dụ lỗi thường gặp thực tế

Tìm kiếm log nhanh khi dữ liệu còn ít lúc mới go-live, nhưng sau vài tháng tích lũy hàng chục triệu bản ghi, do thiếu đánh index đúng cho các trường tìm kiếm phổ biến, thời gian phản hồi tăng lên hàng chục giây, ảnh hưởng đến tốc độ xử lý sự cố thực tế.

## I6. Lưu trữ & thời gian giữ log (Log Retention Policy)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A92:I92`, `4. Detailed Guidance!A92:J92`

### Nội dung yêu cầu

Log được lưu trữ trong thời gian quy định trước khi lưu trữ nguội (archive) hoặc xóa.

### Tiêu chí đánh giá (Đạt)

1\. Thời gian lưu trữ log tuân thủ chính sách đã quy định (VD: tối thiểu 6–12 tháng hoặc theo quy định ngành áp dụng).\
2\. Có cơ chế archive/xóa tự động sau thời hạn.

### Giải thích (ngôn ngữ đơn giản)

Log phải được lưu trữ trong thời gian quy định (theo yêu cầu ngành/nội bộ) trước khi được lưu trữ nguội (archive) hoặc xóa, đảm bảo đủ dữ liệu phục vụ truy vết/audit khi cần mà không lưu vô thời hạn gây tốn tài nguyên.

### Cách kiểm tra (từng bước)

1\. Rà soát chính sách retention log đã quy định (thời gian lưu trữ tối thiểu, quy định ngành áp dụng nếu có).\
2\. Kiểm tra log cũ nhất còn truy xuất được có đúng khớp với thời gian retention đã cấu hình không.\
3\. Kiểm tra cơ chế archive/xóa tự động sau thời hạn có hoạt động đúng không (không xóa sớm hơn hoặc giữ lại vượt quá thời hạn không cần thiết).

### Bằng chứng cần thu thập

Chính sách retention log; kết quả kiểm tra log cũ nhất còn truy xuất được; cấu hình cơ chế archive/xóa tự động.

### Điều kiện ĐẠT

1\. Thời gian lưu trữ log tuân thủ chính sách đã quy định.\
2\. Có cơ chế archive/xóa tự động sau thời hạn.

### Điều kiện KHÔNG ĐẠT

Log bị xóa sớm hơn thời gian retention quy định (mất dữ liệu cần cho audit), hoặc không có cơ chế archive/xóa tự động khiến dữ liệu log phình to không kiểm soát.

### Ví dụ lỗi thường gặp thực tế

Chính sách quy định giữ log tối thiểu 12 tháng để phục vụ audit ngành, nhưng do dung lượng lưu trữ giới hạn, hệ thống tự động xóa log cũ hơn 3 tháng để tiết kiệm dung lượng mà không ai cập nhật lại cấu hình theo đúng chính sách mới ban hành.

## I7. Bảo mật & toàn vẹn log (Log Integrity & Access Control)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A93:I93`, `4. Detailed Guidance!A93:J93`

### Nội dung yêu cầu

Log không thể bị chỉnh sửa/xóa bởi người dùng không có thẩm quyền, đảm bảo tính toàn vẹn phục vụ audit.

### Tiêu chí đánh giá (Đạt)

1\. 100% log ở chế độ chỉ đọc (read-only) đối với user thường.\
2\. Có cơ chế phát hiện chỉnh sửa trái phép (checksum/hash).\
3\. Hành động xóa log (nếu có) chỉ dành cho quản trị cấp cao nhất và được ghi log riêng.

### Giải thích (ngôn ngữ đơn giản)

Log phải được bảo vệ khỏi việc chỉnh sửa/xóa trái phép — nếu ai cũng có thể sửa log thì log không còn giá trị làm bằng chứng phục vụ audit hay điều tra sự cố.

### Cách kiểm tra (từng bước)

1\. Đăng nhập bằng tài khoản user thường, thử sửa/xóa 1 dòng log — xác nhận bị từ chối (read-only).\
2\. Kiểm tra cơ chế phát hiện chỉnh sửa trái phép (checksum/hash) có được áp dụng cho log lưu trữ không.\
3\. Nếu hệ thống cho phép xóa log (VD: hết hạn retention), kiểm tra hành động này chỉ dành cho quản trị cấp cao nhất và bản thân hành động xóa cũng được ghi log riêng.

### Bằng chứng cần thu thập

Kết quả thử sửa/xóa log bằng tài khoản thường; cấu hình phân quyền truy cập log; log ghi nhận hành động xóa log (nếu có).

### Điều kiện ĐẠT

1\. 100% log ở chế độ chỉ đọc với user thường.\
2\. Có cơ chế phát hiện chỉnh sửa trái phép.\
3\. Hành động xóa log chỉ dành cho quản trị cấp cao nhất và được ghi log riêng.

### Điều kiện KHÔNG ĐẠT

User thường có thể sửa/xóa log, hoặc không có cơ chế phát hiện chỉnh sửa trái phép, hoặc hành động xóa log không được ghi nhận.

### Ví dụ lỗi thường gặp thực tế

Tài khoản quản trị hệ thống (system admin, có quyền truy cập DB trực tiếp) có thể xóa trực tiếp bản ghi log qua truy vấn SQL mà không đi qua ứng dụng, nên hành động này không được ghi log lại — tạo lỗ hổng truy vết dù giao diện ứng dụng đã kiểm soát tốt.

## I8. Cảnh báo từ log bất thường (Log-based Alerting)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A94:I94`, `4. Detailed Guidance!A94:J94`

### Nội dung yêu cầu

Hệ thống trung tâm phân tích log để phát hiện và cảnh báo các sự kiện bất thường/lỗi nghiêm trọng từ các ứng dụng local.

### Tiêu chí đánh giá (Đạt)

100% sự kiện log mức Critical/Error được cảnh báo tự động đến người quản trị trong thời gian quy định (≤ X phút), đúng kênh/đúng người nhận.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống trung tâm cần tự động phân tích log để phát hiện và cảnh báo các sự kiện bất thường/lỗi nghiêm trọng từ các ứng dụng local, giúp đội vận hành phản ứng sớm thay vì chỉ phát hiện khi có người dùng phản ánh.

### Cách kiểm tra (từng bước)

1\. Giả lập một sự kiện log mức Critical/Error tại ứng dụng local (VD: lỗi kết nối liên tục).\
2\. Đo thời gian từ lúc log phát sinh đến khi cảnh báo được gửi đến người quản trị.\
3\. Kiểm tra cảnh báo gửi đúng kênh (email/SMS/dashboard) và đúng người phụ trách theo phân công.

### Bằng chứng cần thu thập

Kết quả test giả lập sự kiện log bất thường kèm thời gian nhận cảnh báo thực tế; cấu hình alerting.

### Điều kiện ĐẠT

100% sự kiện log mức Critical/Error test đều được cảnh báo tự động trong thời gian quy định, đúng kênh, đúng người nhận.

### Điều kiện KHÔNG ĐẠT

Có sự kiện log mức Critical/Error không được cảnh báo, hoặc cảnh báo trễ quá ngưỡng, hoặc gửi sai người/kênh.

### Ví dụ lỗi thường gặp thực tế

Cảnh báo được cấu hình dựa trên số lượng lỗi vượt ngưỡng trong 1 khoảng thời gian (threshold-based), nên nếu lỗi nghiêm trọng chỉ xảy ra 1 lần duy nhất (chưa đạt ngưỡng để trigger cảnh báo), sự cố sẽ không được phát hiện kịp thời dù mức độ nghiêm trọng cao.

## I9. Giám sát trạng thái ứng dụng local (Local Application Health Monitoring)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A95:I95`, `4. Detailed Guidance!A95:J95`

### Nội dung yêu cầu

Hệ thống trung tâm giám sát được trạng thái hoạt động (online/offline, phiên bản) của từng ứng dụng local.

### Tiêu chí đánh giá (Đạt)

Dashboard trung tâm hiển thị chính xác trạng thái, phiên bản, thời gian đồng bộ log gần nhất của 100% ứng dụng local đang được quản lý.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống trung tâm cần giám sát được trạng thái hoạt động (online/offline, phiên bản đang chạy) của từng ứng dụng local, giúp đội vận hành biết ngay khi có máy trạm nào gặp sự cố hoặc chạy phiên bản lỗi thời.

### Cách kiểm tra (từng bước)

1\. Kiểm tra dashboard trung tâm có hiển thị trạng thái (online/offline), phiên bản, thời gian đồng bộ log gần nhất của từng ứng dụng local không.\
2\. Thử tắt 1 ứng dụng local, quan sát dashboard có cập nhật trạng thái offline kịp thời không.\
3\. Đối chiếu số lượng ứng dụng local hiển thị trên dashboard với số lượng thực tế đang triển khai.

### Bằng chứng cần thu thập

Ảnh chụp dashboard giám sát trạng thái; kết quả test tắt ứng dụng local và quan sát cập nhật trạng thái.

### Điều kiện ĐẠT

Dashboard trung tâm hiển thị chính xác trạng thái, phiên bản, thời gian đồng bộ log gần nhất của 100% ứng dụng local đang được quản lý.

### Điều kiện KHÔNG ĐẠT

Dashboard thiếu ứng dụng local đang triển khai thực tế, hoặc trạng thái hiển thị không chính xác/cập nhật trễ.

### Ví dụ lỗi thường gặp thực tế

Dashboard hiển thị trạng thái "online" dựa trên lần đồng bộ log cuối cùng cách đó nhiều giờ (do không có heartbeat/ping riêng), khiến một máy trạm đã ngừng hoạt động từ lâu vẫn hiển thị "online" gây hiểu nhầm cho đội vận hành.

## I10. Chuẩn hóa vị trí lưu trữ log (Standardized Log Storage Location)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A96:I96`, `4. Detailed Guidance!A96:J96`

### Nội dung yêu cầu

Log file (tại máy trạm/local và tại hệ thống trung tâm) phải được lưu trữ tại vị trí/đường dẫn và cấu trúc thư mục đã được chuẩn hóa, thống nhất giữa các ứng dụng/máy trạm.

### Tiêu chí đánh giá (Đạt)

1\. 100% ứng dụng ghi log đúng theo đường dẫn/thư mục chuẩn đã quy định (VD: cấu trúc theo năm/tháng/ngày, theo module).\
2\. Có tài liệu quy định rõ cấu trúc thư mục lưu log.\
3\. Không lưu log tại vị trí ngẫu nhiên, phân tán tùy tiện.

### Giải thích (ngôn ngữ đơn giản)

Log file (tại máy trạm/local và tại hệ thống trung tâm) phải được lưu tại vị trí/cấu trúc thư mục đã chuẩn hóa, thống nhất giữa các ứng dụng/máy trạm, giúp đội IT dễ quản lý, backup, và tra cứu thủ công khi cần.

### Cách kiểm tra (từng bước)

1\. Rà soát tài liệu quy định cấu trúc thư mục lưu log chuẩn.\
2\. Kiểm tra thực tế đường dẫn lưu log trên một số máy trạm/ứng dụng đại diện.\
3\. Đối chiếu cấu trúc thư mục thực tế (theo năm/tháng/ngày, theo module) có đúng quy định không.

### Bằng chứng cần thu thập

Tài liệu quy định cấu trúc thư mục log; ảnh chụp đường dẫn lưu log thực tế trên các máy trạm mẫu.

### Điều kiện ĐẠT

100% ứng dụng ghi log đúng theo đường dẫn/cấu trúc thư mục chuẩn đã quy định.

### Điều kiện KHÔNG ĐẠT

Có ứng dụng ghi log tại vị trí không theo chuẩn, phân tán tùy tiện.

### Ví dụ lỗi thường gặp thực tế

Một module tích hợp của nhà cung cấp thứ ba ghi log mặc định vào thư mục cài đặt của chính nó thay vì thư mục log chuẩn chung, khiến đội IT không phát hiện ra nguồn log này khi thực hiện backup/dọn dẹp định kỳ theo quy trình chuẩn.

## I11. Quản lý dung lượng file log/event (Log/Event File Size Management)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A97:I97`, `4. Detailed Guidance!A97:J97`

### Nội dung yêu cầu

Dung lượng từng file log/event và tổng dung lượng thư mục log phải được kiểm soát, không để phình to quá mức gây ảnh hưởng hiệu năng ghi/đọc và vận hành lâu dài.

### Tiêu chí đánh giá (Đạt)

1\. File log/event tự động xoay vòng (rotate/split) khi đạt ngưỡng dung lượng quy định (VD: ≤ 100MB/file).\
2\. Có cơ chế nén (compress) hoặc archive file log cũ.\
3\. Tổng dung lượng thư mục log được giám sát, cảnh báo khi vượt ngưỡng (VD: ≥ 80% dung lượng phân bổ).\
4\. Test ghi log liên tục dài hạn (soak test) không làm giảm hiệu năng ghi/đọc do file quá lớn.

### Giải thích (ngôn ngữ đơn giản)

Dung lượng từng file log và tổng dung lượng thư mục log phải được kiểm soát (rotate, nén, archive) để không phình to quá mức gây ảnh hưởng hiệu năng ghi/đọc khi vận hành lâu dài.

### Cách kiểm tra (từng bước)

1\. Kiểm tra cấu hình rotate log (ngưỡng dung lượng/file trước khi xoay vòng).\
2\. Chạy test ghi log liên tục dài hạn (soak test), quan sát file log có tự động rotate/nén đúng cấu hình không.\
3\. Theo dõi tổng dung lượng thư mục log theo thời gian, xác nhận có cảnh báo khi vượt ngưỡng phân bổ không.

### Bằng chứng cần thu thập

Cấu hình rotate/nén log; kết quả soak test ghi log dài hạn; biểu đồ theo dõi dung lượng thư mục log.

### Điều kiện ĐẠT

1\. File log tự động rotate khi đạt ngưỡng dung lượng quy định.\
2\. Có cơ chế nén/archive log cũ.\
3\. Cảnh báo khi tổng dung lượng vượt ngưỡng.\
4\. Hiệu năng ghi/đọc không suy giảm trong soak test.

### Điều kiện KHÔNG ĐẠT

File log không rotate/phình to không kiểm soát, hoặc hiệu năng ghi/đọc suy giảm rõ rệt khi file log quá lớn trong soak test.

### Ví dụ lỗi thường gặp thực tế

Cấu hình rotate log theo thời gian (VD: mỗi ngày 1 file) nhưng không giới hạn theo dung lượng, nên vào những ngày có sự cố phát sinh log dồn dập (log storm), 1 file log có thể phình lên hàng GB trong 1 ngày, làm chậm hẳn thao tác đọc/ghi log của ứng dụng.

## I12. Cấu trúc & số lượng file trong thư mục log (Log Folder Structure & File Count Control)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Mẫu log trích xuất + ảnh chụp dashboard giám sát tập trung
- **Nguồn:** `3. Assessment Checklist!A98:I98`, `4. Detailed Guidance!A98:J98`

### Nội dung yêu cầu

Cấu trúc thư mục lưu log được tổ chức khoa học (phân theo ngày/tháng/module) và giới hạn số lượng file/thư mục con trong một folder để tránh suy giảm hiệu năng truy xuất khi vận hành lâu dài.

### Tiêu chí đánh giá (Đạt)

1\. Số lượng file trong 1 thư mục không vượt ngưỡng khuyến nghị của hệ điều hành/file system (VD: ≤ 10.000 file/folder), vượt ngưỡng phải tự động tạo thư mục con mới.\
2\. Test với khối lượng file tích lũy lớn theo thời gian (VD: hàng trăm nghìn file sau nhiều tháng vận hành), thao tác liệt kê/tìm kiếm/ghi file vẫn ổn định, thời gian phản hồi không suy giảm đáng kể so với ban đầu.

### Giải thích (ngôn ngữ đơn giản)

Cấu trúc thư mục lưu log cần tổ chức khoa học (phân theo ngày/tháng/module) và giới hạn số lượng file/thư mục con trong 1 folder, tránh suy giảm hiệu năng truy xuất file system khi tích lũy hàng trăm nghìn file theo thời gian vận hành.

### Cách kiểm tra (từng bước)

1\. Kiểm tra cấu trúc phân cấp thư mục log thực tế (có phân theo ngày/tháng/module hay dồn hết vào 1 thư mục phẳng).\
2\. Nếu có dữ liệu log tích lũy lâu dài, thử thao tác liệt kê/tìm kiếm file trong thư mục có nhiều file nhất, đo thời gian phản hồi.\
3\. Nếu chưa đủ dữ liệu thực tế, có thể tạo môi trường test mô phỏng khối lượng file lớn tương đương nhiều tháng vận hành để kiểm tra hiệu năng.

### Bằng chứng cần thu thập

Cấu trúc thư mục log thực tế; kết quả đo thời gian liệt kê/tìm kiếm file với khối lượng lớn.

### Điều kiện ĐẠT

1\. Số lượng file trong 1 thư mục không vượt ngưỡng khuyến nghị (VD: ≤ 10.000 file/folder).\
2\. Vượt ngưỡng tự động tạo thư mục con mới.\
3\. Thao tác liệt kê/tìm kiếm/ghi file vẫn ổn định với khối lượng file tích lũy lớn.

### Điều kiện KHÔNG ĐẠT

Thư mục log dồn hết file vào 1 cấp phẳng không phân chia, số file vượt ngưỡng khuyến nghị của file system, hoặc hiệu năng truy xuất suy giảm rõ rệt khi test với khối lượng file lớn.

### Ví dụ lỗi thường gặp thực tế

Toàn bộ log của mỗi ngày được ghi phẳng vào 1 thư mục theo tên file gắn timestamp mà không phân theo giờ/module, sau 6 tháng vận hành thư mục chứa hàng trăm nghìn file khiến thao tác liệt kê thư mục (`ls`/`dir`) trên máy trạm cũ mất hàng chục giây, ảnh hưởng đến các tác vụ dọn dẹp/backup tự động.
