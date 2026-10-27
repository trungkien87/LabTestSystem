# D. BẢO MẬT

_(Security)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## D1. Xác thực người dùng (Authentication)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A23:I23`, `4. Detailed Guidance!A23:J23`

### Nội dung yêu cầu

Hệ thống xác thực danh tính người dùng trước khi cho phép truy cập.

### Tiêu chí đánh giá (Đạt)

1\. Áp dụng chính sách mật khẩu mạnh, khóa tài khoản sau N lần đăng nhập sai.\
2\. Khuyến khích MFA cho tài khoản quan trọng.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống xác thực danh tính người dùng trước khi cho phép truy cập.

### Cách kiểm tra (từng bước)

1\. Thử đăng nhập sai mật khẩu liên tiếp N lần theo chính sách công bố — kiểm tra tài khoản có bị khóa đúng quy định không.\
2\. Kiểm tra cấu hình chính sách mật khẩu trên hệ thống thật (không chỉ theo tài liệu).\
3\. Nếu yêu cầu MFA cho tài khoản quan trọng, thử đăng nhập và xác nhận có bước xác thực thứ 2.

### Bằng chứng cần thu thập

Ảnh cấu hình chính sách mật khẩu; kết quả test khóa tài khoản; báo cáo Pentest phần authentication.

### Điều kiện ĐẠT

1\. Khóa tài khoản hoạt động đúng cấu hình công bố.\
2\. Chính sách mật khẩu mạnh bắt buộc.\
3\. MFA áp dụng cho tài khoản quan trọng (nếu trong phạm vi).

### Điều kiện KHÔNG ĐẠT

Tài khoản không bị khóa sau N lần sai (brute-force được), hoặc hệ thống chấp nhận mật khẩu yếu (VD: "123456", trùng username).

### Ví dụ lỗi thường gặp thực tế

Chính sách khóa tài khoản chỉ áp dụng cho giao diện web nhưng không áp dụng cho API đăng nhập (mobile app, tích hợp hệ thống khác) → vẫn brute-force được qua API.

## D2. Phân quyền truy cập (Authorization / RBAC)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A24:I24`, `4. Detailed Guidance!A24:J24`

### Nội dung yêu cầu

Phân quyền chức năng và dữ liệu theo vai trò/nhóm người dùng.

### Tiêu chí đánh giá (Đạt)

1\. 100% chức năng/dữ liệu nhạy cảm được kiểm soát theo role.\
2\. Test truy cập trái phép (privilege escalation) không thành công.

### Giải thích (ngôn ngữ đơn giản)

Phân quyền chức năng và dữ liệu theo vai trò/nhóm người dùng.

### Cách kiểm tra (từng bước)

1\. Lập ma trận quyền theo role, đối chiếu với thực tế hệ thống cho phép thao tác.\
2\. Đăng nhập bằng tài khoản quyền thấp, thử truy cập trực tiếp URL/API của chức năng quyền cao (kiểm tra cả UI lẫn API).\
3\. Thử đổi tham số ID trên URL/API (IDOR) để xem có truy cập được dữ liệu của user/role khác không.

### Bằng chứng cần thu thập

Ma trận phân quyền; báo cáo test truy cập trái phép (kèm log request/response); báo cáo Pentest phần authorization.

### Điều kiện ĐẠT

Không có trường hợp tài khoản quyền thấp truy cập được chức năng/dữ liệu ngoài phạm vi, kể cả qua thao tác trực tiếp URL/API.

### Điều kiện KHÔNG ĐẠT

Phát hiện dù chỉ 1 trường hợp truy cập trái phép thành công.

### Ví dụ lỗi thường gặp thực tế

Phân quyền chỉ kiểm soát ở giao diện (ẩn nút/menu) nhưng API backend không kiểm tra lại quyền, nên gọi trực tiếp API vẫn thao tác được dù không thấy nút trên UI.

## D3. Bảo vệ dữ liệu (Data Protection & Encryption)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A25:I25`, `4. Detailed Guidance!A25:J25`

### Nội dung yêu cầu

Dữ liệu nhạy cảm được mã hóa khi lưu trữ và truyền tải.

### Tiêu chí đánh giá (Đạt)

1\. Dữ liệu nhạy cảm (mật khẩu, thông tin cá nhân...) mã hóa at-rest & in-transit (HTTPS/TLS).\
2\. Không lưu plaintext.

### Giải thích (ngôn ngữ đơn giản)

Dữ liệu nhạy cảm được mã hóa khi lưu trữ và truyền tải.

### Cách kiểm tra (từng bước)

1\. Kiểm tra kết nối dùng HTTPS/TLS toàn bộ phiên làm việc (không chỉ trang login); kiểm tra chứng chỉ SSL hợp lệ.\
2\. Truy vấn trực tiếp DB (nếu được cấp quyền) hoặc bắt gói tin để kiểm tra dữ liệu nhạy cảm (mật khẩu, PII) có mã hóa/hash khi lưu và truyền không.\
3\. Kiểm tra mật khẩu lưu dạng hash một chiều (bcrypt/argon2), không phải plaintext hay mã hóa 2 chiều dễ đảo ngược.

### Bằng chứng cần thu thập

Kết quả rà soát chứng chỉ TLS; trích xuất DB (che phần nhạy cảm) chứng minh đã mã hóa; báo cáo SAST/DAST phần data protection.

### Điều kiện ĐẠT

1\. 100% dữ liệu nhạy cảm mã hóa at-rest & in-transit.\
2\. Mật khẩu hash một chiều với thuật toán mạnh.

### Điều kiện KHÔNG ĐẠT

Phát hiện dữ liệu nhạy cảm lưu plaintext, hoặc kết nối không HTTPS ở bất kỳ phần nào của luồng nghiệp vụ chính.

### Ví dụ lỗi thường gặp thực tế

HTTPS chỉ áp dụng cho domain chính nhưng API nội bộ/subdomain phụ vẫn chạy HTTP; hoặc mật khẩu hash bằng MD5 không salt.

## D4. Chống lỗ hổng bảo mật phổ biến (Vulnerability Protection)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A26:I26`, `4. Detailed Guidance!A26:J26`

### Nội dung yêu cầu

Hệ thống được kiểm tra và phòng chống các lỗ hổng phổ biến (SQL Injection, XSS, CSRF...).

### Tiêu chí đánh giá (Đạt)

Kết quả kiểm thử bảo mật (SAST/DAST/Pentest) không phát hiện lỗ hổng mức Critical/High theo OWASP Top 10.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống được kiểm tra và phòng chống các lỗ hổng phổ biến (SQL Injection, XSS, CSRF...).

### Cách kiểm tra (từng bước)

1\. Yêu cầu báo cáo SAST/DAST/Pentest gần nhất (không quá 6–12 tháng hoặc trước go-live).\
2\. Rà soát danh sách lỗ hổng theo mức độ (Critical/High/Medium/Low) và tình trạng khắc phục.\
3\. Với lỗ hổng Critical/High còn Open, yêu cầu giải trình phương án/thời hạn; có thể tái hiện thử 1–2 lỗ hổng điển hình.

### Bằng chứng cần thu thập

Báo cáo Pentest/SAST/DAST đầy đủ (ngày thực hiện, phạm vi, công cụ); bằng chứng khắc phục cho từng lỗ hổng đã đóng.

### Điều kiện ĐẠT

Không còn lỗ hổng mức Critical/High ở trạng thái Open tại thời điểm đánh giá.

### Điều kiện KHÔNG ĐẠT

Còn ≥ 1 lỗ hổng Critical/High chưa khắc phục hoặc chưa có phương án được phê duyệt.

### Ví dụ lỗi thường gặp thực tế

Báo cáo Pentest chỉ quét tự động (DAST tool) mà không kiểm thử thủ công logic nghiệp vụ, bỏ sót lỗ hổng logic (VD: bỏ qua bước thanh toán, thao túng giá qua tham số ẩn).

## D5. Nhật ký & giám sát bảo mật (Security Logging & Monitoring)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A27:I27`, `4. Detailed Guidance!A27:J27`

### Nội dung yêu cầu

Ghi nhận đầy đủ nhật ký cho các sự kiện bảo mật quan trọng.

### Tiêu chí đánh giá (Đạt)

1\. 100% sự kiện đăng nhập, phân quyền, truy cập dữ liệu nhạy cảm được log.\
2\. Log không thể chỉnh sửa/xoá bởi user thường.

### Giải thích (ngôn ngữ đơn giản)

Ghi nhận đầy đủ nhật ký cho các sự kiện bảo mật quan trọng.

### Cách kiểm tra (từng bước)

1\. Thực hiện thử: đăng nhập sai, đăng nhập đúng, thay đổi quyền, truy cập dữ liệu nhạy cảm.\
2\. Kiểm tra log có ghi nhận đầy đủ (thời gian, user, hành động, kết quả) các sự kiện trên.\
3\. Thử (với tài khoản user thường, nếu được phép trong phạm vi test) xóa/sửa 1 dòng log để kiểm tra tính bất biến.

### Bằng chứng cần thu thập

Trích xuất log tương ứng các hành động test; cấu hình phân quyền truy cập log.

### Điều kiện ĐẠT

1\. 100% sự kiện bảo mật quan trọng được log đầy đủ.\
2\. User thường không thể sửa/xóa log.

### Điều kiện KHÔNG ĐẠT

Thiếu log cho sự kiện quan trọng, hoặc log có thể bị chỉnh sửa/xóa bởi tài khoản không có thẩm quyền cao nhất.

### Ví dụ lỗi thường gặp thực tế

Chỉ log hành động thành công (login success) mà không log hành động thất bại (login failed) — không phát hiện được tấn công brute-force.

## D6. Quản lý phiên đăng nhập (Session Management)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A28:I28`, `4. Detailed Guidance!A28:J28`

### Nội dung yêu cầu

Kiểm soát an toàn vòng đời phiên làm việc của người dùng.

### Tiêu chí đánh giá (Đạt)

1\. Tự động hết hạn phiên sau thời gian không hoạt động quy định.\
2\. Session token không lộ trên URL.\
3\. Đăng xuất hủy session hoàn toàn.

### Giải thích (ngôn ngữ đơn giản)

Kiểm soát an toàn vòng đời phiên làm việc của người dùng.

### Cách kiểm tra (từng bước)

1\. Đăng nhập rồi để hệ thống không thao tác lâu hơn ngưỡng quy định, kiểm tra phiên có tự hết hạn không.\
2\. Kiểm tra session token có xuất hiện trên URL không (dễ lộ qua lịch sử trình duyệt, log server).\
3\. Đăng xuất rồi thử dùng lại token/cookie cũ (qua dev tools hoặc gửi lại request) để xem session có thực sự bị hủy không.

### Bằng chứng cần thu thập

Kết quả test timeout phiên; ảnh cấu hình session; kết quả test tái sử dụng token sau logout.

### Điều kiện ĐẠT

1\. Phiên tự hết hạn đúng thời gian quy định.\
2\. Token không lộ trên URL.\
3\. Token vô hiệu hoàn toàn ngay sau khi đăng xuất.

### Điều kiện KHÔNG ĐẠT

Phiên không hết hạn hoặc token cũ vẫn dùng được sau khi logout.

### Ví dụ lỗi thường gặp thực tế

Đăng xuất chỉ xóa token phía client mà server không thu hồi token, nên nếu kẻ tấn công đã lấy được token trước đó vẫn dùng được sau khi user logout.

## D7. Độ phức tạp mật khẩu (Password Complexity Policy)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A29:I29`, `4. Detailed Guidance!A29:J29`

### Nội dung yêu cầu

Hệ thống bắt buộc áp dụng chính sách độ phức tạp mật khẩu khi tạo/đổi mật khẩu.

### Tiêu chí đánh giá (Đạt)

1\. Mật khẩu tối thiểu 8–12 ký tự, kết hợp chữ hoa, chữ thường, số và ký tự đặc biệt.\
2\. Hệ thống từ chối mật khẩu không đạt chuẩn.\
3\. Có chính sách hết hạn/đổi định kỳ và không cho phép tái sử dụng N mật khẩu gần nhất (nếu áp dụng).

### Giải thích (ngôn ngữ đơn giản)

Hệ thống bắt buộc áp dụng chính sách độ phức tạp mật khẩu khi tạo/đổi mật khẩu.

### Cách kiểm tra (từng bước)

1\. Thử tạo/đổi mật khẩu không đạt chuẩn (VD: "12345678", toàn chữ thường) — hệ thống phải từ chối.\
2\. Kiểm tra cấu hình chính sách hết hạn/đổi định kỳ và không tái sử dụng N mật khẩu gần nhất (nếu áp dụng).

### Bằng chứng cần thu thập

Kết quả test tạo/đổi mật khẩu không hợp lệ; cấu hình chính sách mật khẩu trên admin console.

### Điều kiện ĐẠT

1\. Hệ thống từ chối 100% mật khẩu không đạt chuẩn đã quy định.\
2\. Chính sách hết hạn/không tái sử dụng hoạt động đúng (nếu áp dụng).

### Điều kiện KHÔNG ĐẠT

Hệ thống chấp nhận mật khẩu yếu hơn chuẩn đã công bố.

### Ví dụ lỗi thường gặp thực tế

Quy định độ phức tạp chỉ áp dụng khi user tự đổi mật khẩu, nhưng admin tạo tài khoản mới qua chức năng import hàng loạt lại không bị kiểm tra ràng buộc này.

## D8. Quản lý mật khẩu mặc định (Default Password Management)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A30:I30`, `4. Detailed Guidance!A30:J30`

### Nội dung yêu cầu

Hệ thống cho phép quản trị viên thiết lập mật khẩu mặc định khi tạo tài khoản mới hoặc reset mật khẩu, đồng thời đảm bảo an toàn.

### Tiêu chí đánh giá (Đạt)

1\. Mật khẩu mặc định không được đặt cố định/dễ đoán (VD: không dùng "123456", trùng username).\
2\. Bắt buộc người dùng đổi mật khẩu ngay lần đăng nhập đầu tiên.\
3\. Mật khẩu mặc định được gửi qua kênh an toàn (không gửi plaintext qua email/chat không mã hóa).

### Giải thích (ngôn ngữ đơn giản)

Hệ thống cho phép admin thiết lập mật khẩu mặc định khi tạo tài khoản mới/reset mật khẩu, đồng thời đảm bảo an toàn.

### Cách kiểm tra (từng bước)

1\. Tạo thử 1 tài khoản mới/reset mật khẩu 1 tài khoản, kiểm tra mật khẩu mặc định có ngẫu nhiên/đủ mạnh không.\
2\. Đăng nhập lần đầu bằng mật khẩu mặc định, kiểm tra hệ thống có bắt buộc đổi ngay không.\
3\. Kiểm tra kênh gửi mật khẩu mặc định (email/SMS) có an toàn không, có gửi kèm username trong cùng kênh không.

### Bằng chứng cần thu thập

Kết quả test tạo tài khoản/reset mật khẩu; ảnh nội dung email/SMS gửi mật khẩu mặc định.

### Điều kiện ĐẠT

Mật khẩu mặc định ngẫu nhiên/đủ mạnh, bắt buộc đổi ở lần đăng nhập đầu, gửi qua kênh an toàn.

### Điều kiện KHÔNG ĐẠT

Mật khẩu mặc định cố định/dễ đoán, hoặc không bắt buộc đổi ngay, hoặc gửi plaintext qua kênh không mã hóa.

### Ví dụ lỗi thường gặp thực tế

Mật khẩu mặc định được set cố định là "Abc@123" cho mọi tài khoản mới để tiện IT hỗ trợ, không đổi theo từng user.

## D9. Mã hóa dữ liệu cấu hình/thiết lập (Configuration & Settings Encryption)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử bảo mật (SAST/DAST/Pentest) + cấu hình hệ thống liên quan
- **Nguồn:** `3. Assessment Checklist!A31:I31`, `4. Detailed Guidance!A31:J31`

### Nội dung yêu cầu

Các trường nhập liệu (input) chứa thông tin cấu hình nhạy cảm trong màn hình Settings (connection string, API key, mật khẩu kết nối, thông số tích hợp...) không được lưu trữ dưới dạng văn bản thuần (plain text).

### Tiêu chí đánh giá (Đạt)

1\. 100% giá trị cấu hình nhạy cảm được mã hóa trước khi lưu (database/config file).\
2\. Không thể đọc được giá trị gốc khi truy cập trực tiếp file cấu hình/DB.\
3\. Có cơ chế giải mã an toàn tại thời điểm hệ thống sử dụng.\
4\. Giao diện chỉ hiển thị dạng che (mask) khi xem lại.

### Giải thích (ngôn ngữ đơn giản)

Các trường cấu hình nhạy cảm trong Settings (connection string, API key...) không được lưu dạng plaintext.

### Cách kiểm tra (từng bước)

1\. Vào màn hình Settings, nhập thử connection string/API key/mật khẩu kết nối — kiểm tra giao diện có che (mask) giá trị khi xem lại không.\
2\. Nếu được cấp quyền, mở trực tiếp file cấu hình/bảng cấu hình trong DB để kiểm tra giá trị có lưu plaintext không.\
3\. Kiểm tra cơ chế giải mã có diễn ra an toàn (chỉ trong bộ nhớ runtime, không log ra file/log) khi hệ thống sử dụng giá trị này.

### Bằng chứng cần thu thập

Ảnh giao diện Settings (giá trị bị mask); trích xuất file cấu hình/DB (che phần nhạy cảm) chứng minh đã mã hóa.

### Điều kiện ĐẠT

1\. 100% giá trị cấu hình nhạy cảm mã hóa khi lưu trữ.\
2\. Không đọc được giá trị gốc khi truy cập trực tiếp DB/file.\
3\. Giao diện chỉ hiển thị dạng che.

### Điều kiện KHÔNG ĐẠT

Phát hiện bất kỳ giá trị cấu hình nhạy cảm nào lưu plaintext hoặc hiển thị đầy đủ (không mask) trên giao diện.

### Ví dụ lỗi thường gặp thực tế

Connection string DB được lưu mã hóa trong file config chính, nhưng tồn tại file backup/config cũ (VD: appsettings.old.json) trên server còn lưu plaintext, bị bỏ sót khi audit.
