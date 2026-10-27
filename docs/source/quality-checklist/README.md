# Software Quality Assessment Checklist (Rev04)

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Checklist đánh giá chất lượng phần mềm trước go-live, gồm 98 tiêu chí chia 11 nhóm (A–K): 58 tiêu chí Bắt buộc, 40 tiêu chí Khuyến nghị.

## Tiêu chí theo nhóm

| Nhóm | File | Số tiêu chí | Bắt buộc | Khuyến nghị |
|---|---|---|---|---|
| A. CHỨC NĂNG<br>(Functional Suitability) | [a-functional.md](a-functional.md) | 5 | 5 | 0 |
| B. TÍNH TOÀN VẸN & BẢO VỆ DỮ LIỆU<br>(Data Integrity & Protection) | [b-data-integrity.md](b-data-integrity.md) | 5 | 5 | 0 |
| C. HIỆU NĂNG & ĐỘ TIN CẬY<br>(Performance Efficiency & Reliability) | [c-performance-reliability.md](c-performance-reliability.md) | 8 | 5 | 3 |
| D. BẢO MẬT<br>(Security) | [d-security.md](d-security.md) | 9 | 9 | 0 |
| E. GIAO DIỆN, TRẢI NGHIỆM NGƯỜI DÙNG & THIẾT KẾ<br>(UI, User Experience & Design Standards) | [e-ui-ux-design.md](e-ui-ux-design.md) | 22 | 8 | 14 |
| F. ĐA NGÔN NGỮ & TRỢ GIÚP NGƯỜI DÙNG<br>(Localization & Help/Support) | [f-localization-help.md](f-localization-help.md) | 10 | 2 | 8 |
| G. KHẢ NĂNG TƯƠNG THÍCH & TÍNH DI ĐỘNG<br>(Compatibility & Portability) | [g-compatibility-portability.md](g-compatibility-portability.md) | 7 | 3 | 4 |
| H. BẢO TRÌ, QUẢN LÝ PHIÊN BẢN & TUÂN THỦ<br>(Maintainability, Version Management & Compliance) | [h-maintainability-compliance.md](h-maintainability-compliance.md) | 16 | 11 | 5 |
| I. QUẢN LÝ LOG & GIÁM SÁT TẬP TRUNG<br>(Log Management & Centralized Monitoring) | [i-logging-monitoring.md](i-logging-monitoring.md) | 12 | 6 | 6 |
| J. ĐÀO TẠO & BÀN GIAO VẬN HÀNH<br>(Training & Operational Handover) | [j-training-handover.md](j-training-handover.md) | 2 | 2 | 0 |
| K. DI CHUYỂN DỮ LIỆU & XUẤT BÁO CÁO<br>(Data Migration & Reporting) | [k-data-migration-reporting.md](k-data-migration-reporting.md) | 2 | 2 | 0 |

## 1. User Guide

HƯỚNG DẪN SỬ DỤNG CHECKLIST ĐÁNH GIÁ CHẤT LƯỢNG PHẦN MỀM <!-- A1 -->

Checklist này dùng để đánh giá chất lượng phần mềm/hệ thống web trước khi go-live hoặc trong quá trình audit định kỳ, đứng trên góc độ người dùng cuối (end user), kết hợp với các yêu cầu kỹ thuật cơ bản về bảo mật, hiệu năng và giao diện. Bộ tiêu chí được xây dựng theo mô hình chất lượng ISO/IEC 25010, có tham chiếu bộ quy chuẩn thiết kế UI/UX & thương hiệu nội bộ đã được phê duyệt cho phần thiết kế giao diện. <!-- B4 -->

\• Sheet 1 - User Guide: tài liệu bạn đang đọc. <!-- B7 -->

\• Sheet 2 - Glossary: giải nghĩa các thuật ngữ/viết tắt kỹ thuật xuất hiện trong checklist, dùng khi cần tra cứu nhanh. <!-- B8 -->

\• Sheet 3 - Assessment Checklist: bảng checklist chính, dùng để chấm điểm Đạt/Không đạt cho từng tiêu chí. <!-- B9 -->

\• Sheet 4 - Detailed Guidance: hướng dẫn chi tiết cách kiểm tra, bằng chứng cần thu thập, điều kiện Đạt/Không đạt và lỗi thường gặp cho từng tiêu chí — dùng cho auditor và đội xây dựng hệ thống. <!-- B10 -->

Tại cột "Kết quả đánh giá" trong sheet Checklist danh gia, chọn 1 trong 3 giá trị từ danh sách thả xuống (dropdown): <!-- B13 -->

\- Đạt: hệ thống đáp ứng đầy đủ nội dung tại cột "Tiêu chí đánh giá (Đạt)", có bằng chứng kiểm chứng cụ thể (xem chi tiết tại sheet Huong dan chi tiet). <!-- B14 -->

\- Không đạt: hệ thống chưa đáp ứng đầy đủ điều kiện Đạt, cần ghi rõ lý do/lỗi phát hiện tại cột "Ghi chú". <!-- B15 -->

\- N/A (Không áp dụng): tiêu chí không áp dụng cho phạm vi hệ thống đang đánh giá (VD: hệ thống không có dữ liệu di chuyển từ hệ thống cũ). Cần nêu rõ lý do tại cột "Ghi chú". <!-- B16 -->

Ô sẽ tự động đổi màu theo kết quả chọn: xanh lá = Đạt, đỏ = Không đạt, xám = N/A. <!-- B17 -->

\• Bắt buộc: tiêu chí liên quan trực tiếp đến tính đúng đắn chức năng, an toàn dữ liệu, bảo mật hoặc tuân thủ pháp lý — hệ thống KHÔNG được go-live nếu còn tiêu chí Bắt buộc ở trạng thái Không đạt. <!-- B20 -->

\• Khuyến nghị: tiêu chí giúp nâng cao trải nghiệm/chất lượng tổng thể nhưng không chặn go-live nếu chưa đạt hoàn toàn; cần có kế hoạch khắc phục sau go-live và được Trưởng dự án phê duyệt ngoại lệ. <!-- B21 -->

Việc phân loại Bắt buộc/Khuyến nghị tại cột "Mức độ" là đề xuất mặc định — phòng Smart Factory có thể điều chỉnh lại theo đặc thù từng dự án trước khi ban hành chính thức. <!-- B22 -->

Ở cuối mỗi nhóm tiêu chí (Hạng mục lớn) và ở cuối bảng, hệ thống tự động tính % số tiêu chí Đạt trên tổng số tiêu chí đã đánh giá (loại trừ N/A) bằng công thức COUNTIFS. Điều kiện phê duyệt Go-live: 100% tiêu chí Bắt buộc = Đạt; tiêu chí Khuyến nghị được khuyến khích đạt tối thiểu 80%, phần còn lại phải có kế hoạch khắc phục kèm phê duyệt ngoại lệ. <!-- B25 -->

Bước 1: Đội xây dựng hệ thống/Auditor đọc kỹ mô tả từng tiêu chí và phần Detailed Guidance tương ứng trước khi kiểm tra. <!-- B28 -->

Bước 2: Thu thập bằng chứng theo đúng loại nêu tại cột "Loại bằng chứng" / sheet Detailed Guidance. <!-- B29 -->

Bước 3: Chấm Đạt/Không đạt/N/A tại sheet Assessment Checklist, ghi chú rõ lý do và đính kèm bằng chứng (link/file) tại cột Ghi chú. <!-- B30 -->

Bước 4: Tổng hợp kết quả, đối chiếu điều kiện go-live tại phần "TỔNG HỢP KẾT QUẢ THEO HẠNG MỤC" ở cuối sheet Assessment Checklist, rồi trình ký xác nhận (QA, PM, Business Owner). <!-- B31 -->

Phiên bản <!-- B34 -->

Rev 01 (2026-07-29): Ban hành checklist gốc (A-I, theo mô hình chất lượng ISO/IEC 25010). <!-- B35 -->

Rev 02 (2026-08-01): Bổ sung cột Mức độ/Loại bằng chứng, dropdown kết quả, công thức % đạt; bổ sung nhóm J (Đào tạo & Bàn giao) và K (Di chuyển dữ liệu & Xuất báo cáo); bổ sung sheet Huong dan su dung, Thuat ngu, Huong dan chi tiet. <!-- B36 -->

Rev 03: file trước đó được lưu hành với tên Rev03 nhưng không có dòng changelog tương ứng — ghi nhận lại tại đây để tránh mất dấu lịch sử phiên bản. <!-- B37 -->

Rev 04 (2026-08-03): Đổi toàn bộ tên sheet sang tiếng Anh (User Guide, Glossary, Assessment Checklist, Detailed Guidance); bỏ tham chiếu thương hiệu bên thứ ba (Synology Design Guide) khỏi phần giới thiệu, thay bằng quy chuẩn thiết kế nội bộ; tách các yêu cầu/tiêu chí đánh giá và điều kiện Đạt/Không đạt có nhiều điều kiện gộp chung thành các ý đánh số riêng (1. 2. 3.) để dễ đọc và dễ chấm điểm; sửa các nhãn/tham chiếu không nhất quán (N-A → N/A; "Mục 5" → tên phần thực tế); bổ sung ngày ban hành vào quy tắc đặt tên file. <!-- B38 -->

Quy tắc đặt tên file: [DocumentName-in-English]_[Lang]_Rev[XX]_[YYYYMMDD].xlsx — ví dụ: Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx. Số Rev tăng dần theo từng lần ban hành chính thức, khớp với mục Phiên bản phía trên; ngày (YYYYMMDD) là ngày ban hành của đúng Rev đó. <!-- B39 -->

## 2. Glossary

| Thuật ngữ / Viết tắt | Giải nghĩa |
|---|---|
| URS/FS/BRD | User Requirement Specification / Functional Specification / Business Requirement Document — tài liệu đặc tả yêu cầu người dùng, yêu cầu chức năng và yêu cầu nghiệp vụ. |
| RTM | Requirement Traceability Matrix — ma trận truy vết thể hiện mối liên hệ giữa yêu cầu, thiết kế, test case và defect. |
| Test case (positive/negative/boundary) | Kịch bản kiểm thử với dữ liệu hợp lệ (positive), dữ liệu không hợp lệ (negative), và dữ liệu ở ngưỡng biên (boundary). |
| SLA | Service Level Agreement — cam kết mức độ dịch vụ (VD: thời gian phản hồi hỗ trợ). |
| RPO/RTO | Recovery Point Objective / Recovery Time Objective — điểm khôi phục dữ liệu tối đa chấp nhận mất và thời gian khôi phục hệ thống tối đa cho phép sau sự cố. |
| Soak test | Kiểm thử chạy hệ thống liên tục trong thời gian dài để phát hiện rò rỉ bộ nhớ (memory leak) hoặc suy giảm hiệu năng theo thời gian. |
| Graceful degradation | Suy giảm có kiểm soát — hệ thống vẫn hoạt động ở mức tối thiểu thay vì sập hoàn toàn khi một thành phần gặp lỗi. |
| DR (Disaster Recovery) | Khôi phục sau thảm họa — kế hoạch và diễn tập khôi phục hệ thống sau sự cố nghiêm trọng. |
| MFA | Multi-Factor Authentication — xác thực đa yếu tố, yêu cầu nhiều hơn 1 hình thức xác minh danh tính khi đăng nhập. |
| RBAC | Role-Based Access Control — phân quyền truy cập theo vai trò người dùng. |
| SAST/DAST | Static/Dynamic Application Security Testing — kiểm thử bảo mật tĩnh (phân tích mã nguồn) và động (chạy thử tấn công trên hệ thống đang hoạt động). |
| Pentest | Penetration Testing — kiểm thử xâm nhập, mô phỏng tấn công thực tế để tìm lỗ hổng bảo mật. |
| OWASP Top 10 | Danh sách 10 rủi ro bảo mật ứng dụng web phổ biến nhất do tổ chức OWASP công bố (SQL Injection, XSS, CSRF...). |
| At-rest / In-transit (encryption) | Mã hóa dữ liệu khi lưu trữ (at-rest) và khi truyền tải qua mạng (in-transit, VD: HTTPS/TLS). |
| WCAG 2.1 (mức AA) | Web Content Accessibility Guidelines — tiêu chuẩn quốc tế về khả năng truy cập nội dung web cho người khuyết tật; mức AA là mức tuân thủ phổ biến được yêu cầu. |
| Contrast ratio | Tỷ lệ tương phản giữa màu chữ và màu nền, ảnh hưởng đến khả năng đọc, đặc biệt với người khiếm thị. |
| Responsive design | Thiết kế giao diện tự động điều chỉnh hiển thị phù hợp với nhiều kích thước màn hình/thiết bị. |
| NTP | Network Time Protocol — giao thức đồng bộ thời gian giữa các máy chủ/máy trạm với một nguồn thời gian chuẩn. |
| Locale | Vùng/ngôn ngữ cụ thể quy định định dạng hiển thị ngày tháng, số, tiền tệ (VD: vi-VN, en-US). |
| VCS | Version Control System — hệ thống quản lý phiên bản mã nguồn (VD: Git, SVN). |
| Pull Request (PR) | Yêu cầu hợp nhất thay đổi mã nguồn, thường đi kèm bước review trước khi merge vào nhánh chính. |
| CCB | Change Control Board — hội đồng kiểm soát thay đổi, phê duyệt các thay đổi hệ thống chính thức. |
| UAT | User Acceptance Testing — kiểm thử nghiệm thu bởi người dùng/đại diện nghiệp vụ trước khi phát hành chính thức. |
| Semantic Versioning | Quy tắc đặt tên phiên bản theo định dạng MAJOR.MINOR.PATCH (VD: 2.4.1), thể hiện mức độ thay đổi. |
| Checksum/Hash (SHA-256) | Mã băm dùng để xác minh tính toàn vẹn của file/phần mềm, phát hiện nếu bị chỉnh sửa/giả mạo. |
| 21 CFR Part 11 / GxP | Các quy định của FDA (Mỹ) về hồ sơ điện tử/chữ ký điện tử và thực hành sản xuất tốt (GxP), thường áp dụng cho ngành dược/thực phẩm. |
| ISO 27001 | Tiêu chuẩn quốc tế về hệ thống quản lý an toàn thông tin. |
| PII | Personally Identifiable Information — thông tin định danh cá nhân (họ tên, CMND/CCCD, số điện thoại...). |
| SonarQube | Công cụ phân tích tĩnh mã nguồn, đo lường chất lượng code (code smell, độ phức tạp, trùng lặp mã...). |
| Code coverage | Tỷ lệ phần trăm mã nguồn được bao phủ bởi unit test tự động. |
| CI/CD | Continuous Integration/Continuous Deployment — tích hợp và triển khai liên tục, tự động hóa quy trình build/test/deploy. |
| Rollback | Khôi phục hệ thống về phiên bản/trạng thái trước đó khi phát hiện sự cố sau khi triển khai. |
| Data migration | Di chuyển dữ liệu từ hệ thống cũ sang hệ thống mới. |

## 3. Assessment Checklist — phần tổng hợp và ký xác nhận

TỔNG HỢP KẾT QUẢ THEO HẠNG MỤC <!-- dòng 104 -->

Hạng mục · Số tiêu chí · Đạt · Không đạt · N/A · % Đạt (loại trừ N/A) <!-- dòng 105 -->

A. CHỨC NĂNG · 5 · 0 · 0 · 0 <!-- dòng 106 -->

B. TÍNH TOÀN VẸN & BẢO VỆ DỮ LIỆU · 5 · 0 · 0 · 0 <!-- dòng 107 -->

C. HIỆU NĂNG & ĐỘ TIN CẬY · 8 · 0 · 0 · 0 <!-- dòng 108 -->

D. BẢO MẬT · 9 · 0 · 0 · 0 <!-- dòng 109 -->

E. GIAO DIỆN, TRẢI NGHIỆM NGƯỜI DÙNG & THIẾT KẾ · 22 · 0 · 0 · 0 <!-- dòng 110 -->

F. ĐA NGÔN NGỮ & TRỢ GIÚP NGƯỜI DÙNG · 10 · 0 · 0 · 0 <!-- dòng 111 -->

G. KHẢ NĂNG TƯƠNG THÍCH & TÍNH DI ĐỘNG · 7 · 0 · 0 · 0 <!-- dòng 112 -->

H. BẢO TRÌ, QUẢN LÝ PHIÊN BẢN & TUÂN THỦ · 16 · 0 · 0 · 0 <!-- dòng 113 -->

I. QUẢN LÝ LOG & GIÁM SÁT TẬP TRUNG · 12 · 0 · 0 · 0 <!-- dòng 114 -->

J. ĐÀO TẠO & BÀN GIAO VẬN HÀNH · 2 · 0 · 0 · 0 <!-- dòng 115 -->

K. DI CHUYỂN DỮ LIỆU & XUẤT BÁO CÁO · 2 · 0 · 0 · 0 <!-- dòng 116 -->

TỔNG THỂ · 98 · 0 · 0 · 0 <!-- dòng 117 -->

Ghi chú: Hệ thống chỉ được phê duyệt Go-live/phát hành chính thức khi 100% tiêu chí "Bắt buộc" đạt kết quả "Đạt". Tiêu chí "Khuyến nghị" chưa đạt cần có kế hoạch khắc phục và được Trưởng dự án phê duyệt ngoại lệ. <!-- dòng 119 -->

Xác nhận: <!-- dòng 121 -->

Người đánh giá / QA · Trưởng dự án (PM) · Đại diện người dùng (Business Owner) <!-- dòng 122 -->

(Ký, ghi rõ họ tên) · (Ký, ghi rõ họ tên) · (Ký, ghi rõ họ tên) <!-- dòng 126 -->
