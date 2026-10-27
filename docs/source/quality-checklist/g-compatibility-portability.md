# G. KHẢ NĂNG TƯƠNG THÍCH & TÍNH DI ĐỘNG

_(Compatibility & Portability)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## G1. Tương thích trình duyệt/hệ điều hành

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ma trận kiểm thử tương thích (browser/OS/environment)
- **Nguồn:** `3. Assessment Checklist!A64:I64`, `4. Detailed Guidance!A64:J64`

### Nội dung yêu cầu

Hệ thống hoạt động đúng trên các trình duyệt/hệ điều hành trong phạm vi hỗ trợ.

### Tiêu chí đánh giá (Đạt)

Kiểm thử đạt trên 100% danh sách trình duyệt/OS được quy định trong phạm vi hỗ trợ chính thức.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống phải hoạt động đúng trên toàn bộ trình duyệt/hệ điều hành nằm trong phạm vi hỗ trợ chính thức đã công bố, không chỉ được kiểm thử trên 1 trình duyệt quen thuộc của đội phát triển.

### Cách kiểm tra (từng bước)

1\. Lấy danh sách trình duyệt/hệ điều hành trong phạm vi hỗ trợ chính thức (kèm phiên bản tối thiểu).\
2\. Kiểm thử các luồng nghiệp vụ chính trên từng trình duyệt/OS trong danh sách.\
3\. Ghi nhận các lỗi hiển thị/hoạt động khác biệt giữa các trình duyệt (rendering khác nhau, JavaScript không chạy...).

### Bằng chứng cần thu thập

Ma trận kiểm thử tương thích (browser × chức năng chính) kèm kết quả Pass/Fail; ảnh chụp lỗi phát hiện (nếu có).

### Điều kiện ĐẠT

Kiểm thử đạt trên 100% danh sách trình duyệt/OS được quy định trong phạm vi hỗ trợ chính thức.

### Điều kiện KHÔNG ĐẠT

Có ≥1 trình duyệt/OS trong phạm vi hỗ trợ chính thức nhưng phát hiện lỗi hoạt động/hiển thị nghiêm trọng.

### Ví dụ lỗi thường gặp thực tế

Đội phát triển chỉ test trên Chrome (trình duyệt họ dùng hàng ngày), nhưng nhà máy quy định dùng Edge làm trình duyệt tiêu chuẩn theo chính sách IT nội bộ — khi go-live phát hiện một số component JavaScript không tương thích với phiên bản Edge cũ đang triển khai.

## G2. Tích hợp hệ thống liên quan (System Integration / API)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ma trận kiểm thử tương thích (browser/OS/environment)
- **Nguồn:** `3. Assessment Checklist!A65:I65`, `4. Detailed Guidance!A65:J65`

### Nội dung yêu cầu

Trao đổi dữ liệu chính xác, ổn định với các hệ thống liên quan (ERP, PLC, SCADA, API bên thứ ba...).

### Tiêu chí đánh giá (Đạt)

1\. 100% interface/API được kiểm thử (positive/negative).\
2\. Tỷ lệ lỗi giao tiếp liên hệ thống = 0% trong test.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống phải trao đổi dữ liệu chính xác và ổn định với các hệ thống liên quan (ERP, PLC, SCADA, API bên thứ ba), vì MES thường không hoạt động độc lập mà là một mắt xích trong chuỗi hệ thống nhà máy.

### Cách kiểm tra (từng bước)

1\. Lập danh sách toàn bộ interface/API kết nối với hệ thống bên ngoài trong phạm vi dự án.\
2\. Kiểm thử từng interface với kịch bản positive (dữ liệu hợp lệ) và negative (dữ liệu lỗi, hệ thống đối tác không phản hồi, timeout).\
3\. Đo tỷ lệ lỗi giao tiếp trong quá trình test, đặc biệt với các luồng dữ liệu tần suất cao/liên tục.

### Bằng chứng cần thu thập

Danh sách interface/API kèm kết quả test positive/negative; log giao tiếp giữa các hệ thống trong quá trình test.

### Điều kiện ĐẠT

1\. 100% interface/API được kiểm thử.\
2\. Tỷ lệ lỗi giao tiếp liên hệ thống = 0% trong test.

### Điều kiện KHÔNG ĐẠT

Có ≥1 interface phát sinh lỗi giao tiếp trong kịch bản test hợp lệ, hoặc không xử lý đúng khi hệ thống đối tác timeout/không phản hồi.

### Ví dụ lỗi thường gặp thực tế

Interface với PLC hoạt động ổn định khi test độc lập, nhưng khi PLC gửi dữ liệu dồn dập liên tục (burst) trong ca sản xuất cao điểm thực tế, hệ thống MES bị nghẽn hàng đợi xử lý (queue) do chưa test đúng tần suất dữ liệu thực tế.

## G3. Khả năng cùng tồn tại (Co-existence)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ma trận kiểm thử tương thích (browser/OS/environment)
- **Nguồn:** `3. Assessment Checklist!A66:I66`, `4. Detailed Guidance!A66:J66`

### Nội dung yêu cầu

Hệ thống không xung đột tài nguyên/tiến trình với phần mềm khác trên cùng môi trường.

### Tiêu chí đánh giá (Đạt)

Không phát sinh xung đột (cổng, tiến trình, tài nguyên) khi triển khai cùng ứng dụng khác theo môi trường thực tế.

### Giải thích (ngôn ngữ đơn giản)

Phần mềm không được xung đột tài nguyên (cổng mạng, tiến trình, bộ nhớ) với các phần mềm khác đang chạy trên cùng máy chủ/máy trạm, đặc biệt quan trọng khi triển khai trên máy trạm xưởng sản xuất vốn đã cài nhiều phần mềm khác (driver thiết bị, phần mềm giám sát...).

### Cách kiểm tra (từng bước)

1\. Xác định danh sách phần mềm khác cùng chạy trên môi trường triển khai thực tế (theo tài liệu môi trường/khảo sát hạ tầng).\
2\. Triển khai thử trên môi trường có đầy đủ các phần mềm đó, quan sát có xung đột cổng/tiến trình/tài nguyên không.\
3\. Kiểm tra hiệu năng của cả 2 phần mềm có bị ảnh hưởng lẫn nhau không khi chạy đồng thời.

### Bằng chứng cần thu thập

Danh sách phần mềm cùng môi trường; kết quả kiểm thử triển khai cùng môi trường thực tế.

### Điều kiện ĐẠT

Không phát sinh xung đột cổng/tiến trình/tài nguyên khi triển khai cùng ứng dụng khác theo môi trường thực tế.

### Điều kiện KHÔNG ĐẠT

Phát hiện xung đột (VD: trùng cổng, tranh chấp tài nguyên) khiến 1 trong 2 phần mềm hoạt động không ổn định.

### Ví dụ lỗi thường gặp thực tế

Ứng dụng local sử dụng cổng mặc định trùng với phần mềm giám sát thiết bị đã có sẵn trên máy trạm xưởng, gây lỗi "port already in use" khi khởi động, chỉ phát hiện khi triển khai thực tế vì môi trường test không có phần mềm giám sát đó.

## G4. Khả năng cài đặt (Installability)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ma trận kiểm thử tương thích (browser/OS/environment)
- **Nguồn:** `3. Assessment Checklist!A67:I67`, `4. Detailed Guidance!A67:J67`

### Nội dung yêu cầu

Hệ thống có thể cài đặt/triển khai dễ dàng, đúng hướng dẫn.

### Tiêu chí đánh giá (Đạt)

Cài đặt thành công theo tài liệu hướng dẫn (deployment guide) mà không cần can thiệp ngoài quy trình.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống phải cài đặt/triển khai được đúng theo tài liệu hướng dẫn (deployment guide), không cần các bước xử lý ngoài quy trình mà chỉ đội phát triển gốc mới biết.

### Cách kiểm tra (từng bước)

1\. Lấy tài liệu deployment guide hiện có.\
2\. Yêu cầu một người không tham gia phát triển (VD: nhân sự IT vận hành) thực hiện cài đặt hoàn toàn theo tài liệu, trên môi trường sạch (clean environment).\
3\. Ghi nhận các bước gặp khó khăn, cần hỗ trợ ngoài tài liệu, hoặc lỗi phát sinh trong quá trình cài đặt.

### Bằng chứng cần thu thập

Tài liệu deployment guide; biên bản/video quá trình cài đặt thử nghiệm độc lập.

### Điều kiện ĐẠT

Cài đặt thành công theo đúng tài liệu hướng dẫn mà không cần can thiệp ngoài quy trình.

### Điều kiện KHÔNG ĐẠT

Cài đặt thất bại hoặc cần các bước xử lý không có trong tài liệu (phải hỏi trực tiếp đội phát triển).

### Ví dụ lỗi thường gặp thực tế

Deployment guide thiếu bước cấu hình 1 biến môi trường quan trọng (do lập trình viên nhớ làm theo thói quen mà quên ghi vào tài liệu), khiến người triển khai độc lập bị lỗi ứng dụng không khởi động được mà không rõ nguyên nhân.

## G5. Khả năng thích ứng môi trường (Adaptability)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ma trận kiểm thử tương thích (browser/OS/environment)
- **Nguồn:** `3. Assessment Checklist!A68:I68`, `4. Detailed Guidance!A68:J68`

### Nội dung yêu cầu

Hệ thống có thể vận hành trên nhiều môi trường hạ tầng khác nhau (on-premise/cloud).

### Tiêu chí đánh giá (Đạt)

Kiểm chứng triển khai thành công trên tối thiểu môi trường mục tiêu đã cam kết (VD: on-prem và cloud nếu áp dụng).

### Giải thích (ngôn ngữ đơn giản)

Hệ thống cần vận hành được trên các môi trường hạ tầng khác nhau (on-premise và/hoặc cloud) tùy theo cam kết của dự án, tạo linh hoạt khi doanh nghiệp thay đổi chiến lược hạ tầng.

### Cách kiểm tra (từng bước)

1\. Xác định các môi trường hạ tầng mục tiêu đã cam kết trong hợp đồng/tài liệu dự án.\
2\. Triển khai thử nghiệm (hoặc xác nhận đã triển khai) trên từng môi trường mục tiêu.\
3\. Kiểm tra tính năng hoạt động tương đương giữa các môi trường (không có tính năng chỉ chạy được ở 1 môi trường).

### Bằng chứng cần thu thập

Tài liệu cam kết môi trường mục tiêu; bằng chứng triển khai thành công trên từng môi trường.

### Điều kiện ĐẠT

Kiểm chứng triển khai thành công trên tối thiểu các môi trường mục tiêu đã cam kết.

### Điều kiện KHÔNG ĐẠT

Không triển khai được hoặc phát sinh lỗi nghiêm trọng trên 1 trong các môi trường mục tiêu đã cam kết.

### Ví dụ lỗi thường gặp thực tế

Ứng dụng dùng đường dẫn file cứng theo cấu trúc ổ đĩa Windows (VD: C:\data\...) khiến không triển khai được trên môi trường cloud dùng container Linux dù cam kết ban đầu hỗ trợ cả 2 môi trường.

## G6. Khả năng thay thế thành phần (Replaceability)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ma trận kiểm thử tương thích (browser/OS/environment)
- **Nguồn:** `3. Assessment Checklist!A69:I69`, `4. Detailed Guidance!A69:J69`

### Nội dung yêu cầu

Có thể thay thế một thành phần/phiên bản mà không ảnh hưởng lớn đến toàn hệ thống.

### Tiêu chí đánh giá (Đạt)

Thay thế thử nghiệm một thành phần (VD: nâng cấp thư viện, đổi DB engine con) không phát sinh lỗi nghiêm trọng.

### Giải thích (ngôn ngữ đơn giản)

Cần có khả năng thay thế một thành phần/phiên bản (thư viện, DB engine con, module con) mà không gây ảnh hưởng lớn đến toàn hệ thống, giúp nâng cấp/bảo trì lâu dài dễ dàng hơn.

### Cách kiểm tra (từng bước)

1\. Chọn 1 thành phần có khả năng cần thay thế trong tương lai (VD: nâng cấp phiên bản thư viện, đổi engine DB con).\
2\. Thực hiện thay thế thử nghiệm trên môi trường test.\
3\. Chạy regression test để xác nhận không phát sinh lỗi nghiêm trọng do việc thay thế.

### Bằng chứng cần thu thập

Kịch bản thay thế thành phần thử nghiệm; kết quả regression test sau khi thay thế.

### Điều kiện ĐẠT

Thay thế thử nghiệm một thành phần không phát sinh lỗi nghiêm trọng, các chức năng liên quan vẫn hoạt động đúng.

### Điều kiện KHÔNG ĐẠT

Thay thế thành phần gây lỗi lan rộng ra các module không liên quan trực tiếp, cho thấy mức độ phụ thuộc chéo (coupling) cao.

### Ví dụ lỗi thường gặp thực tế

Nâng cấp phiên bản thư viện xử lý ngày tháng gây lỗi ở nhiều module không liên quan vì toàn hệ thống phụ thuộc trực tiếp vào 1 phiên bản cụ thể của thư viện đó mà không qua lớp trừu tượng (abstraction layer), khiến việc thay thế trở nên rủi ro cao.

## G7. Chuẩn hóa vị trí cài đặt phần mềm (Standardized Installation Path)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ma trận kiểm thử tương thích (browser/OS/environment)
- **Nguồn:** `3. Assessment Checklist!A70:I70`, `4. Detailed Guidance!A70:J70`

### Nội dung yêu cầu

Phần mềm phải được cài đặt tại vị trí/đường dẫn thư mục đã được quy định chuẩn, thống nhất giữa các máy trạm/môi trường.

### Tiêu chí đánh giá (Đạt)

1\. 100% máy trạm/môi trường cài đặt đúng theo đường dẫn chuẩn đã quy định (VD: thư mục cài đặt riêng theo chuẩn nội bộ, không cài tại thư mục hệ thống/thư mục người dùng tùy ý).\
2\. Có tài liệu quy định rõ đường dẫn tiêu chuẩn.\
3\. Mọi thay đổi đường dẫn cài đặt phải được phê duyệt qua Change Request.

### Giải thích (ngôn ngữ đơn giản)

Phần mềm phải được cài đặt tại đường dẫn thư mục quy định thống nhất giữa các máy trạm/môi trường, giúp đội IT dễ quản lý, bảo trì, và tránh xung đột quyền truy cập khi cài tại thư mục hệ thống/thư mục người dùng tùy ý.

### Cách kiểm tra (từng bước)

1\. Rà soát tài liệu quy định đường dẫn cài đặt chuẩn của tổ chức.\
2\. Kiểm tra thực tế đường dẫn cài đặt trên một số máy trạm/môi trường đại diện.\
3\. Kiểm tra các lần thay đổi đường dẫn cài đặt (nếu có) có qua phê duyệt Change Request không.

### Bằng chứng cần thu thập

Tài liệu quy định đường dẫn chuẩn; ảnh chụp đường dẫn cài đặt thực tế trên các máy trạm mẫu; Change Request liên quan (nếu có thay đổi).

### Điều kiện ĐẠT

1\. 100% máy trạm/môi trường cài đặt đúng theo đường dẫn chuẩn đã quy định.\
2\. Mọi thay đổi đường dẫn được phê duyệt qua Change Request.

### Điều kiện KHÔNG ĐẠT

Có ≥1 máy trạm/môi trường cài đặt sai vị trí quy định (VD: cài trong thư mục người dùng cá nhân, thư mục hệ thống), hoặc thay đổi đường dẫn không qua phê duyệt.

### Ví dụ lỗi thường gặp thực tế

Một số máy trạm được cài đặt vội trong đợt triển khai gấp rút tại thư mục Desktop/Downloads của tài khoản người dùng cá nhân thay vì thư mục chuẩn theo quy định nội bộ, gây khó khăn khi đội IT cần đồng loạt cập nhật hoặc backup cấu hình sau này.
