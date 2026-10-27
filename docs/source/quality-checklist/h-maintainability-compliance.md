# H. BẢO TRÌ, QUẢN LÝ PHIÊN BẢN & TUÂN THỦ

_(Maintainability, Version Management & Compliance)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## H1. Chất lượng mã nguồn (Code Quality)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A71:I71`, `4. Detailed Guidance!A71:J71`

### Nội dung yêu cầu

Mã nguồn tuân thủ coding standard, có khả năng đọc hiểu và bảo trì tốt.

### Tiêu chí đánh giá (Đạt)

Đạt ngưỡng chất lượng theo công cụ phân tích tĩnh (SonarQube...): độ phức tạp, code smell, trùng lặp mã trong giới hạn quy định.

### Giải thích (ngôn ngữ đơn giản)

Mã nguồn phải tuân thủ coding standard, dễ đọc, dễ bảo trì — đánh giá qua công cụ phân tích tĩnh thay vì cảm tính, để đảm bảo hệ thống có thể duy trì lâu dài kể cả khi đổi đội ngũ phát triển.

### Cách kiểm tra (từng bước)

1\. Yêu cầu chạy công cụ phân tích tĩnh (VD: SonarQube) trên toàn bộ mã nguồn.\
2\. Rà soát các chỉ số: độ phức tạp cyclomatic, tỷ lệ trùng lặp mã (code duplication), số lượng code smell, lỗ hổng bảo mật phát hiện qua SAST.\
3\. So sánh với ngưỡng chất lượng đã quy định trong tiêu chuẩn nội bộ (Quality Gate).

### Bằng chứng cần thu thập

Báo cáo SonarQube (hoặc công cụ tương đương) kèm ngày chạy, phạm vi mã nguồn quét.

### Điều kiện ĐẠT

Đạt ngưỡng chất lượng theo công cụ phân tích tĩnh: độ phức tạp, code smell, trùng lặp mã trong giới hạn quy định (Quality Gate Pass).

### Điều kiện KHÔNG ĐẠT

Kết quả phân tích tĩnh không đạt Quality Gate, hoặc phát hiện nhiều code smell/bug nghiêm trọng chưa xử lý.

### Ví dụ lỗi thường gặp thực tế

Đội dự án chỉ chạy SonarQube một lần duy nhất lúc bàn giao rồi báo cáo kết quả đẹp, nhưng không tích hợp vào pipeline CI/CD nên các commit sau đó không được kiểm soát chất lượng liên tục, chất lượng mã nguồn suy giảm dần theo thời gian.

## H2. Tính module hóa (Modularity)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A72:I72`, `4. Detailed Guidance!A72:J72`

### Nội dung yêu cầu

Hệ thống được thiết kế theo module độc lập, giảm phụ thuộc chéo.

### Tiêu chí đánh giá (Đạt)

Thay đổi một module không gây ảnh hưởng ngoài dự kiến đến module khác (kiểm chứng qua regression test).

### Giải thích (ngôn ngữ đơn giản)

Hệ thống cần thiết kế theo các module độc lập, giảm phụ thuộc chéo — thay đổi 1 module không nên kéo theo lỗi ở các module không liên quan.

### Cách kiểm tra (từng bước)

1\. Chọn 1 module để thực hiện thay đổi nhỏ có kiểm soát (VD: sửa logic tính toán trong module A).\
2\. Chạy regression test toàn hệ thống, không chỉ module A.\
3\. Ghi nhận có lỗi phát sinh ở module khác không liên quan trực tiếp không.

### Bằng chứng cần thu thập

Kịch bản thay đổi thử nghiệm; kết quả regression test toàn hệ thống sau thay đổi.

### Điều kiện ĐẠT

Thay đổi một module không gây ảnh hưởng ngoài dự kiến đến module khác, xác nhận qua regression test.

### Điều kiện KHÔNG ĐẠT

Thay đổi 1 module gây lỗi lan sang module không liên quan, cho thấy mức độ phụ thuộc chéo cao (tight coupling).

### Ví dụ lỗi thường gặp thực tế

Sửa logic hiển thị báo cáo ở module Kho lại vô tình làm lỗi tính toán ở module Sản xuất do 2 module dùng chung 1 hàm tiện ích (shared utility) không được tách biệt rõ ràng theo domain.

## H3. Khả năng kiểm thử (Testability)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A73:I73`, `4. Detailed Guidance!A73:J73`

### Nội dung yêu cầu

Hệ thống được thiết kế để dễ dàng viết và thực hiện kiểm thử tự động.

### Tiêu chí đánh giá (Đạt)

1\. Độ phủ unit test (code coverage) đạt mục tiêu quy định (VD: ≥ 70%).\
2\. Có khả năng chạy automation test.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống cần được thiết kế để dễ viết và chạy kiểm thử tự động (unit test, automation test), giúp phát hiện lỗi sớm và giảm chi phí kiểm thử thủ công lặp lại.

### Cách kiểm tra (từng bước)

1\. Yêu cầu báo cáo độ phủ unit test (code coverage) từ công cụ đo lường (VD: JaCoCo, Istanbul).\
2\. Kiểm tra có bộ automation test (UI/API) đang chạy được và tích hợp vào pipeline CI/CD không.\
3\. Thử chạy lại 1 phần bộ automation test để xác nhận thực sự chạy được, không chỉ là báo cáo trên giấy.

### Bằng chứng cần thu thập

Báo cáo code coverage; kết quả chạy thử bộ automation test.

### Điều kiện ĐẠT

1\. Độ phủ unit test đạt mục tiêu quy định (VD: ≥ 70%).\
2\. Có khả năng chạy automation test thành công thực tế.

### Điều kiện KHÔNG ĐẠT

Độ phủ unit test dưới mục tiêu, hoặc bộ automation test không chạy được/không được bảo trì cập nhật theo code mới.

### Ví dụ lỗi thường gặp thực tế

Báo cáo coverage đạt 75% nhưng phần lớn là unit test cho các hàm getter/setter đơn giản, trong khi logic nghiệp vụ phức tạp và rủi ro cao lại gần như không có test — coverage cao về số lượng nhưng thấp về chất lượng bảo vệ thực tế.

## H4. Tài liệu kỹ thuật (Technical Documentation)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A74:I74`, `4. Detailed Guidance!A74:J74`

### Nội dung yêu cầu

Có đầy đủ tài liệu thiết kế, API, hướng dẫn vận hành phục vụ bảo trì.

### Tiêu chí đánh giá (Đạt)

100% tài liệu kỹ thuật bắt buộc (SDS, API doc, Deployment guide...) đầy đủ, cập nhật theo phiên bản hiện hành.

### Giải thích (ngôn ngữ đơn giản)

Cần có đầy đủ tài liệu thiết kế hệ thống (SDS), tài liệu API, hướng dẫn vận hành để phục vụ bảo trì lâu dài, đặc biệt khi đổi đội ngũ phát triển hoặc chuyển giao cho đội vận hành khác.

### Cách kiểm tra (từng bước)

1\. Lập danh sách tài liệu kỹ thuật bắt buộc theo quy định nội bộ (SDS, API doc, deployment guide...).\
2\. Kiểm tra từng tài liệu có tồn tại, đầy đủ nội dung, và cập nhật theo phiên bản hiện hành.\
3\. Thử dùng tài liệu API để gọi thử một số API, xác nhận mô tả khớp với hành vi thực tế.

### Bằng chứng cần thu thập

Danh sách tài liệu kỹ thuật đối chiếu có/thiếu; kết quả test gọi API theo tài liệu.

### Điều kiện ĐẠT

100% tài liệu kỹ thuật bắt buộc đầy đủ, cập nhật theo phiên bản hiện hành, mô tả khớp hành vi thực tế.

### Điều kiện KHÔNG ĐẠT

Thiếu tài liệu kỹ thuật bắt buộc, hoặc tài liệu tồn tại nhưng lỗi thời không khớp phiên bản hiện hành.

### Ví dụ lỗi thường gặp thực tế

Tài liệu API doc (Swagger) không được tự động sinh từ code mà cập nhật thủ công riêng biệt, dẫn đến sau vài lần release, tài liệu không còn khớp với tham số/endpoint thực tế của API.

## H5. Quy tắc đặt tên phiên bản (Versioning Scheme)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A75:I75`, `4. Detailed Guidance!A75:J75`

### Nội dung yêu cầu

Áp dụng chuẩn Semantic Versioning (MAJOR.MINOR.PATCH) thống nhất.

### Tiêu chí đánh giá (Đạt)

1\. 100% phiên bản phát hành tuân thủ định dạng quy chuẩn.\
2\. Quy tắc tăng version đúng theo loại thay đổi.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống áp dụng chuẩn Semantic Versioning (MAJOR.MINOR.PATCH) thống nhất, giúp đội vận hành và người dùng hiểu ngay mức độ thay đổi của mỗi bản phát hành chỉ qua số phiên bản.

### Cách kiểm tra (từng bước)

1\. Rà soát lịch sử các phiên bản phát hành gần đây.\
2\. Kiểm tra định dạng số phiên bản có tuân thủ MAJOR.MINOR.PATCH không.\
3\. Đối chiếu loại thay đổi thực tế (breaking change, tính năng mới, sửa lỗi) với cách tăng version tương ứng có đúng quy tắc semver không.

### Bằng chứng cần thu thập

Lịch sử phiên bản phát hành; đối chiếu loại thay đổi với cách tăng số phiên bản.

### Điều kiện ĐẠT

1\. 100% phiên bản phát hành tuân thủ định dạng quy chuẩn.\
2\. Quy tắc tăng version đúng theo loại thay đổi.

### Điều kiện KHÔNG ĐẠT

Phát hiện phiên bản đặt tên không theo quy chuẩn, hoặc tăng version sai loại (VD: thay đổi breaking change nhưng chỉ tăng PATCH).

### Ví dụ lỗi thường gặp thực tế

Một thay đổi cấu trúc dữ liệu API (breaking change, ảnh hưởng hệ thống tích hợp) chỉ được tăng version dạng PATCH (VD: 2.3.1 → 2.3.2) thay vì MAJOR, khiến đội tích hợp bên thứ ba không nhận biết được cần điều chỉnh code phía họ.

## H6. Quản lý mã nguồn (Source Code Control)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A76:I76`, `4. Detailed Guidance!A76:J76`

### Nội dung yêu cầu

Mã nguồn được quản lý qua hệ thống kiểm soát phiên bản với chiến lược nhánh rõ ràng.

### Tiêu chí đánh giá (Đạt)

1\. 100% mã nguồn lưu trên VCS (Git/SVN).\
2\. Có branching strategy.\
3\. 100% thay đổi qua Pull Request có review trước khi merge.

### Giải thích (ngôn ngữ đơn giản)

Mã nguồn phải được quản lý qua hệ thống kiểm soát phiên bản (Git/SVN) với chiến lược nhánh (branching strategy) rõ ràng, và mọi thay đổi phải qua review trước khi merge.

### Cách kiểm tra (từng bước)

1\. Kiểm tra mã nguồn có được lưu trữ đầy đủ trên VCS không (không có phần code chỉ tồn tại cục bộ trên máy lập trình viên).\
2\. Rà soát chiến lược nhánh đang áp dụng (VD: GitFlow, trunk-based).\
3\. Kiểm tra lịch sử Pull Request/Merge Request gần đây có bắt buộc review (ít nhất 1 người khác phê duyệt) trước khi merge không.

### Bằng chứng cần thu thập

Cấu trúc branching trên VCS; lịch sử Pull Request kèm người review và trạng thái phê duyệt.

### Điều kiện ĐẠT

1\. 100% mã nguồn lưu trên VCS.\
2\. Có branching strategy rõ ràng.\
3\. 100% thay đổi qua Pull Request có review trước khi merge.

### Điều kiện KHÔNG ĐẠT

Phát hiện mã nguồn không đầy đủ trên VCS, hoặc có merge trực tiếp vào nhánh chính không qua review.

### Ví dụ lỗi thường gặp thực tế

Một số bản sửa lỗi khẩn cấp (hotfix) được merge thẳng vào nhánh production mà bỏ qua bước review do áp lực thời gian, tạo tiền lệ và dần trở thành thói quen bỏ qua quy trình kiểm soát chất lượng.

## H7. Kiểm soát thay đổi (Change Control)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A77:I77`, `4. Detailed Guidance!A77:J77`

### Nội dung yêu cầu

Mọi thay đổi hệ thống được kiểm soát và phê duyệt chính thức qua CCB.

### Tiêu chí đánh giá (Đạt)

100% thay đổi có Change Request, đánh giá tác động và phê duyệt trước khi triển khai.

### Giải thích (ngôn ngữ đơn giản)

Mọi thay đổi hệ thống (tính năng mới, sửa lỗi, cấu hình) phải được kiểm soát và phê duyệt chính thức qua hội đồng kiểm soát thay đổi (CCB - Change Control Board) trước khi triển khai, tránh thay đổi tùy tiện không đánh giá tác động.

### Cách kiểm tra (từng bước)

1\. Chọn mẫu một số thay đổi đã triển khai gần đây (tính năng mới, hotfix, thay đổi cấu hình).\
2\. Đối chiếu từng thay đổi có Change Request tương ứng không, có đánh giá tác động (impact assessment) không, có phê duyệt trước khi triển khai không.\
3\. Kiểm tra đặc biệt các thay đổi khẩn cấp (hotfix) có tuân thủ quy trình rút gọn nhưng vẫn có ghi nhận/phê duyệt sau đó (retrospective approval) không.

### Bằng chứng cần thu thập

Danh sách Change Request đối chiếu với các thay đổi thực tế đã triển khai; biên bản phê duyệt CCB.

### Điều kiện ĐẠT

100% thay đổi có Change Request, đánh giá tác động và phê duyệt trước khi triển khai (hoặc phê duyệt hồi tố có kiểm soát với trường hợp khẩn cấp).

### Điều kiện KHÔNG ĐẠT

Có ≥1 thay đổi được triển khai mà không có Change Request/phê duyệt tương ứng.

### Ví dụ lỗi thường gặp thực tế

Thay đổi cấu hình hệ thống (VD: điều chỉnh ngưỡng cảnh báo) được thực hiện trực tiếp bởi IT vận hành mà không qua quy trình Change Request vì "chỉ là cấu hình nhỏ", nhưng thực tế lại ảnh hưởng đến logic cảnh báo chất lượng của toàn bộ dây chuyền.

## H8. Quản lý môi trường (Environment Management)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A78:I78`, `4. Detailed Guidance!A78:J78`

### Nội dung yêu cầu

Tách biệt môi trường Dev / Test (UAT) / Production.

### Tiêu chí đánh giá (Đạt)

1\. Tồn tại tối thiểu 3 môi trường độc lập.\
2\. Không kiểm thử/thay đổi trực tiếp trên Production.

### Giải thích (ngôn ngữ đơn giản)

Cần tách biệt rõ ràng giữa môi trường Dev (phát triển) / Test-UAT (kiểm thử/nghiệm thu) / Production (vận hành thật), tránh thử nghiệm hoặc thay đổi trực tiếp trên môi trường Production gây rủi ro cho dữ liệu/vận hành thật.

### Cách kiểm tra (từng bước)

1\. Xác nhận tồn tại tối thiểu 3 môi trường độc lập (Dev/Test-UAT/Production) với hạ tầng/database tách biệt.\
2\. Rà soát lịch sử thao tác gần đây trên Production, kiểm tra có dấu hiệu test/debug trực tiếp trên môi trường này không.\
3\. Kiểm tra quy trình promote code/thay đổi giữa các môi trường có tuân thủ thứ tự Dev → Test/UAT → Production không.

### Bằng chứng cần thu thập

Sơ đồ/tài liệu mô tả các môi trường; log truy cập/thao tác trên Production; quy trình promote giữa các môi trường.

### Điều kiện ĐẠT

1\. Tồn tại tối thiểu 3 môi trường độc lập.\
2\. Không có bằng chứng kiểm thử/thay đổi trực tiếp trên Production.

### Điều kiện KHÔNG ĐẠT

Thiếu môi trường tách biệt (VD: Dev và Production dùng chung database), hoặc phát hiện thao tác test/debug trực tiếp trên Production.

### Ví dụ lỗi thường gặp thực tế

Môi trường UAT và Production dùng chung 1 database vì thiếu hạ tầng, khiến dữ liệu test bị lẫn vào dữ liệu thật hoặc ngược lại — vi phạm nghiêm trọng nguyên tắc tách biệt môi trường.

## H9. Ghi chú phát hành & nhật ký thay đổi (Release Notes & Changelog)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A79:I79`, `4. Detailed Guidance!A79:J79`

### Nội dung yêu cầu

Mỗi phiên bản có tài liệu mô tả đầy đủ nội dung thay đổi.

### Tiêu chí đánh giá (Đạt)

1\. 100% phiên bản có Release Note (tính năng mới, lỗi đã sửa, known issues).\
2\. Changelog cập nhật liên tục.

### Giải thích (ngôn ngữ đơn giản)

Mỗi phiên bản phát hành cần có tài liệu mô tả đầy đủ nội dung thay đổi (tính năng mới, lỗi đã sửa, vấn đề còn tồn tại), giúp người dùng và đội vận hành nắm được thay đổi mà không cần dò tìm thủ công.

### Cách kiểm tra (từng bước)

1\. Rà soát lịch sử phát hành các phiên bản gần đây, kiểm tra từng phiên bản có Release Note tương ứng không.\
2\. Đối chiếu nội dung Release Note với các thay đổi thực tế đã triển khai (qua Change Request/commit log).\
3\. Kiểm tra Release Note có mục "known issues" (vấn đề đã biết còn tồn tại) không.

### Bằng chứng cần thu thập

Danh sách Release Note theo từng phiên bản; đối chiếu với Change Request/commit log tương ứng.

### Điều kiện ĐẠT

1\. 100% phiên bản có Release Note đầy đủ (tính năng mới, lỗi đã sửa, known issues).\
2\. Changelog cập nhật liên tục.

### Điều kiện KHÔNG ĐẠT

Có ≥1 phiên bản phát hành không có Release Note, hoặc nội dung Release Note không khớp với thay đổi thực tế đã triển khai.

### Ví dụ lỗi thường gặp thực tế

Release Note chỉ liệt kê tính năng mới nổi bật nhưng bỏ sót các bản sửa lỗi nhỏ (minor bugfix) đã triển khai cùng đợt, khiến người dùng không biết vấn đề họ từng báo cáo đã được xử lý hay chưa.

## H10. Kiểm thử trước phát hành (Pre-release Testing)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A80:I80`, `4. Detailed Guidance!A80:J80`

### Nội dung yêu cầu

Mọi phiên bản được kiểm thử đầy đủ trước khi triển khai chính thức.

### Tiêu chí đánh giá (Đạt)

1\. 100% regression test liên quan pass.\
2\. UAT ký duyệt.\
3\. Không còn lỗi mở mức Critical/High.

### Giải thích (ngôn ngữ đơn giản)

Mọi phiên bản phải được kiểm thử đầy đủ (bao gồm regression test và UAT) trước khi triển khai chính thức, đảm bảo không phát hành phiên bản còn lỗi nghiêm trọng.

### Cách kiểm tra (từng bước)

1\. Rà soát bộ regression test liên quan đến các thay đổi của phiên bản gần nhất, kiểm tra kết quả Pass/Fail.\
2\. Kiểm tra biên bản UAT (User Acceptance Test) có chữ ký xác nhận của Business Owner/đại diện người dùng.\
3\. Rà soát danh sách lỗi (defect) còn mở tại thời điểm phát hành, xác nhận không còn lỗi mức Critical/High.

### Bằng chứng cần thu thập

Báo cáo regression test; biên bản UAT có chữ ký; danh sách defect còn mở phân loại theo mức độ.

### Điều kiện ĐẠT

1\. 100% regression test liên quan pass.\
2\. UAT đã ký duyệt.\
3\. Không còn lỗi mở mức Critical/High tại thời điểm phát hành.

### Điều kiện KHÔNG ĐẠT

Có regression test fail chưa xử lý, hoặc phát hành khi chưa có UAT ký duyệt, hoặc còn lỗi Critical/High chưa khắc phục.

### Ví dụ lỗi thường gặp thực tế

Do áp lực deadline go-live, phiên bản được phát hành khi UAT chưa hoàn tất ký duyệt chính thức (chỉ có xác nhận miệng/email không chính thức), khiến trách nhiệm chấp nhận rủi ro không rõ ràng khi có sự cố sau phát hành.

## H11. Kế hoạch khôi phục (Rollback & Backup Plan)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A81:I81`, `4. Detailed Guidance!A81:J81`

### Nội dung yêu cầu

Có phương án khôi phục hệ thống về trạng thái trước đó khi phát sinh sự cố.

### Tiêu chí đánh giá (Đạt)

1\. 100% đợt triển khai có kế hoạch rollback và backup trước khi update.\
2\. RTO đáp ứng khi diễn tập/thực tế.

### Giải thích (ngôn ngữ đơn giản)

Trước mỗi đợt triển khai (deploy), cần có phương án rollback rõ ràng để đưa hệ thống về trạng thái trước đó nếu phiên bản mới gặp sự cố nghiêm trọng sau khi go-live.

### Cách kiểm tra (từng bước)

1\. Rà soát kế hoạch triển khai gần nhất, kiểm tra có mục rollback plan và backup trước khi update không.\
2\. Kiểm tra backup trước triển khai có thực sự được tạo và xác minh (không chỉ có kế hoạch trên giấy).\
3\. Nếu có sự cố rollback thực tế đã xảy ra trong quá khứ, đối chiếu thời gian thực hiện rollback với RTO mục tiêu.

### Bằng chứng cần thu thập

Kế hoạch rollback/backup của các đợt triển khai gần nhất; bằng chứng backup đã thực hiện; log rollback thực tế (nếu có).

### Điều kiện ĐẠT

1\. 100% đợt triển khai có kế hoạch rollback và backup trước khi update.\
2\. RTO đáp ứng khi diễn tập/thực tế.

### Điều kiện KHÔNG ĐẠT

Có đợt triển khai không có kế hoạch rollback/backup trước đó, hoặc rollback thực tế không đạt RTO mục tiêu.

### Ví dụ lỗi thường gặp thực tế

Kế hoạch rollback chỉ đề cập khôi phục lại mã nguồn (code) về phiên bản cũ, nhưng không tính đến trường hợp phiên bản mới đã thay đổi cấu trúc database (migration) — khi cần rollback thực tế phát hiện không thể chỉ revert code mà còn phải xử lý dữ liệu đã thay đổi cấu trúc, kéo dài thời gian downtime ngoài dự kiến.

## H12. Quản lý tài liệu theo phiên bản (Documentation Control)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A82:I82`, `4. Detailed Guidance!A82:J82`

### Nội dung yêu cầu

Tài liệu hệ thống cập nhật đồng bộ theo từng phiên bản phần mềm.

### Tiêu chí đánh giá (Đạt)

100% tài liệu (SRS, SDS, User Manual...) có số phiên bản khớp với phiên bản phần mềm.

### Giải thích (ngôn ngữ đơn giản)

Toàn bộ tài liệu hệ thống (SRS, SDS, User Manual...) phải cập nhật đồng bộ theo từng phiên bản phần mềm, tránh tình trạng tài liệu và phần mềm thực tế "lệch pha" theo thời gian.

### Cách kiểm tra (từng bước)

1\. Lập danh sách các tài liệu hệ thống bắt buộc phải đồng bộ theo phiên bản.\
2\. Kiểm tra số phiên bản ghi trên từng tài liệu có khớp với phiên bản phần mềm hiện hành không.\
3\. Chọn mẫu một số nội dung trong tài liệu, đối chiếu với hành vi thực tế của phần mềm phiên bản hiện hành.

### Bằng chứng cần thu thập

Danh sách tài liệu kèm số phiên bản; đối chiếu nội dung mẫu với phần mềm thực tế.

### Điều kiện ĐẠT

100% tài liệu (SRS, SDS, User Manual...) có số phiên bản khớp với phiên bản phần mềm.

### Điều kiện KHÔNG ĐẠT

Có ≥1 tài liệu có số phiên bản không khớp hoặc nội dung không còn phản ánh đúng phần mềm hiện hành.

### Ví dụ lỗi thường gặp thực tế

User Manual được cập nhật lần cuối ở phiên bản 3 tháng trước, trong khi phần mềm đã qua 2 lần release thay đổi giao diện — tài liệu vẫn còn ảnh chụp màn hình giao diện cũ không còn khớp thực tế.

## H13. Kiểm tra tính toàn vẹn phần mềm qua mã băm (Software Integrity Verification – Hashcode)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A83:I83`, `4. Detailed Guidance!A83:J83`

### Nội dung yêu cầu

Mỗi phiên bản phần mềm phát hành phải có mã băm (checksum/hash, VD: SHA-256) để xác minh phần mềm không bị chỉnh sửa, giả mạo trong quá trình phân phối, triển khai và vận hành.

### Tiêu chí đánh giá (Đạt)

1\. 100% phiên bản phát hành được công bố kèm mã băm (hash) chính thức, lưu trữ/quản lý tập trung và gắn đúng với số phiên bản tương ứng.\
2\. Hệ thống/quy trình triển khai xác minh khớp hash trước khi cài đặt.\
3\. Có cơ chế kiểm tra định kỳ hash trong quá trình vận hành và cảnh báo ngay khi phát hiện sai lệch (dấu hiệu phần mềm bị chỉnh sửa/giả mạo).

### Giải thích (ngôn ngữ đơn giản)

Mỗi phiên bản phần mềm phát hành cần có mã băm (checksum/hash, VD: SHA-256) để xác minh phần mềm không bị chỉnh sửa/giả mạo trong quá trình phân phối, triển khai và vận hành — đặc biệt quan trọng với phần mềm cài đặt tại nhiều máy trạm phân tán.

### Cách kiểm tra (từng bước)

1\. Kiểm tra mỗi bản phát hành có được công bố kèm mã hash chính thức không, lưu trữ ở đâu.\
2\. Thử tính lại hash của file cài đặt thực tế đang sử dụng, so sánh với hash công bố.\
3\. Kiểm tra quy trình triển khai có bước xác minh hash trước khi cài đặt không, và có cơ chế kiểm tra định kỳ trong vận hành không.

### Bằng chứng cần thu thập

Bảng mã hash công bố theo từng phiên bản; kết quả tính lại hash thực tế đối chiếu; quy trình triển khai có bước xác minh hash.

### Điều kiện ĐẠT

1\. 100% phiên bản phát hành có mã hash chính thức, lưu trữ tập trung, gắn đúng với phiên bản.\
2\. Quy trình triển khai xác minh hash trước khi cài đặt.\
3\. Có kiểm tra định kỳ và cảnh báo khi lệch.

### Điều kiện KHÔNG ĐẠT

Có phiên bản phát hành không kèm mã hash chính thức, hoặc quy trình triển khai không xác minh hash trước khi cài đặt.

### Ví dụ lỗi thường gặp thực tế

Mã hash được công bố trong email nội bộ (dễ thất lạc/không tra cứu lại được) thay vì lưu trữ tập trung trong hệ thống quản lý phát hành chính thức, khiến sau vài tháng không ai còn tra cứu được hash gốc để đối chiếu khi nghi ngờ phần mềm bị chỉnh sửa.

## H14. Tuân thủ chuẩn ngành/pháp lý

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A84:I84`, `4. Detailed Guidance!A84:J84`

### Nội dung yêu cầu

Đáp ứng các chuẩn/quy định ngành áp dụng (21 CFR Part 11, GxP, ISO 27001...).

### Tiêu chí đánh giá (Đạt)

1\. 100% yêu cầu bắt buộc có bằng chứng (evidence) đáp ứng.\
2\. Không có phát hiện (finding) nghiêm trọng khi audit.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống phải đáp ứng các chuẩn/quy định ngành áp dụng (VD: 21 CFR Part 11, GxP, ISO 27001 tùy lĩnh vực sản xuất), với bằng chứng cụ thể chứ không chỉ tuyên bố tuân thủ.

### Cách kiểm tra (từng bước)

1\. Xác định danh sách chuẩn/quy định áp dụng cho hệ thống theo lĩnh vực sản xuất/ngành nghề của doanh nghiệp.\
2\. Với mỗi yêu cầu bắt buộc trong chuẩn, yêu cầu cung cấp bằng chứng (evidence) cụ thể đáp ứng.\
3\. Rà soát kết quả audit gần nhất (nội bộ hoặc bên ngoài) liên quan đến các chuẩn này, xem có phát hiện (finding) nghiêm trọng chưa khắc phục không.

### Bằng chứng cần thu thập

Ma trận đối chiếu yêu cầu chuẩn ngành với bằng chứng đáp ứng; báo cáo audit gần nhất.

### Điều kiện ĐẠT

1\. 100% yêu cầu bắt buộc có bằng chứng đáp ứng.\
2\. Không có phát hiện nghiêm trọng chưa khắc phục khi audit.

### Điều kiện KHÔNG ĐẠT

Có yêu cầu bắt buộc không có bằng chứng đáp ứng, hoặc còn phát hiện nghiêm trọng từ audit gần nhất chưa khắc phục.

### Ví dụ lỗi thường gặp thực tế

Hệ thống tuyên bố tuân thủ 21 CFR Part 11 về chữ ký điện tử, nhưng khi kiểm tra thực tế phát hiện chữ ký điện tử không gắn kèm đầy đủ ý nghĩa (meaning), thời gian, danh tính người ký theo đúng yêu cầu chi tiết của chuẩn — chỉ đáp ứng về mặt hình thức, chưa đủ về nội dung.

## H15. Bảo vệ dữ liệu cá nhân

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A85:I85`, `4. Detailed Guidance!A85:J85`

### Nội dung yêu cầu

Tuân thủ quy định về bảo vệ dữ liệu cá nhân (nếu hệ thống xử lý PII).

### Tiêu chí đánh giá (Đạt)

1\. Dữ liệu cá nhân được thu thập, lưu trữ, xử lý đúng phạm vi cho phép.\
2\. Có cơ chế đồng ý/thu hồi đồng ý nếu áp dụng.

### Giải thích (ngôn ngữ đơn giản)

Nếu hệ thống xử lý thông tin cá nhân (PII) của nhân viên/người dùng, cần tuân thủ quy định bảo vệ dữ liệu cá nhân về phạm vi thu thập, lưu trữ, xử lý và quyền của chủ thể dữ liệu (đồng ý/thu hồi đồng ý nếu áp dụng).

### Cách kiểm tra (từng bước)

1\. Xác định các trường dữ liệu cá nhân (PII) mà hệ thống đang thu thập/lưu trữ (họ tên, CMND/CCCD, số điện thoại, dữ liệu sinh trắc học...).\
2\. Đối chiếu phạm vi thu thập/xử lý thực tế với mục đích sử dụng đã công bố/quy định pháp lý áp dụng.\
3\. Kiểm tra cơ chế đồng ý (consent)/thu hồi đồng ý nếu hệ thống yêu cầu (đặc biệt với dữ liệu sinh trắc học như vân tay chấm công).

### Bằng chứng cần thu thập

Danh sách trường dữ liệu cá nhân đang xử lý; tài liệu chính sách bảo vệ dữ liệu cá nhân; cơ chế đồng ý/thu hồi đồng ý (nếu có).

### Điều kiện ĐẠT

1\. Dữ liệu cá nhân được thu thập, lưu trữ, xử lý đúng phạm vi cho phép.\
2\. Có cơ chế đồng ý/thu hồi đồng ý nếu áp dụng.

### Điều kiện KHÔNG ĐẠT

Phát hiện thu thập/xử lý dữ liệu cá nhân vượt phạm vi cho phép, hoặc thiếu cơ chế đồng ý khi pháp luật/chính sách yêu cầu.

### Ví dụ lỗi thường gặp thực tế

Hệ thống chấm công thu thập dữ liệu vân tay của nhân viên nhưng không có văn bản thông báo/xin sự đồng ý rõ ràng về mục đích sử dụng và thời gian lưu trữ, tiềm ẩn rủi ro vi phạm quy định bảo vệ dữ liệu sinh trắc học.

## H16. Sẵn sàng cho kiểm toán nội bộ

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo công cụ phân tích mã nguồn, lịch sử VCS, phiếu Change Request/Release Note
- **Nguồn:** `3. Assessment Checklist!A86:I86`, `4. Detailed Guidance!A86:J86`

### Nội dung yêu cầu

Hệ thống cung cấp đầy đủ bằng chứng, báo cáo phục vụ kiểm toán nội bộ/bên ngoài.

### Tiêu chí đánh giá (Đạt)

Có thể trích xuất báo cáo/log phục vụ audit trong thời gian quy định (VD: ≤ 1 ngày làm việc).

### Giải thích (ngôn ngữ đơn giản)

Hệ thống phải có khả năng trích xuất đầy đủ báo cáo, log, bằng chứng phục vụ hoạt động kiểm toán nội bộ/bên ngoài trong thời gian hợp lý, không mất nhiều ngày dò tìm thủ công.

### Cách kiểm tra (từng bước)

1\. Đặt ra một yêu cầu trích xuất báo cáo/log điển hình mà kiểm toán viên thường yêu cầu (VD: toàn bộ audit trail của 1 lô sản xuất trong 1 tháng).\
2\. Yêu cầu đội vận hành thực hiện trích xuất, đo thời gian thực tế hoàn thành.\
3\. Kiểm tra dữ liệu trích xuất có đầy đủ, đúng định dạng dễ đọc cho kiểm toán viên không.

### Bằng chứng cần thu thập

Yêu cầu trích xuất mẫu; thời gian thực tế hoàn thành; dữ liệu trích xuất kết quả.

### Điều kiện ĐẠT

Có thể trích xuất báo cáo/log phục vụ audit trong thời gian quy định (VD: ≤ 1 ngày làm việc).

### Điều kiện KHÔNG ĐẠT

Thời gian trích xuất vượt quá ngưỡng quy định, hoặc dữ liệu trích xuất không đầy đủ/khó sử dụng cho mục đích audit.

### Ví dụ lỗi thường gặp thực tế

Dữ liệu audit trail được lưu ở nhiều bảng/nhiều hệ thống con khác nhau, không có công cụ/báo cáo tổng hợp sẵn có, mỗi lần kiểm toán viên yêu cầu phải nhờ đội IT viết truy vấn thủ công mất nhiều ngày mới trích xuất xong.
