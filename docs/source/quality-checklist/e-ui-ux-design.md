# E. GIAO DIỆN, TRẢI NGHIỆM NGƯỜI DÙNG & THIẾT KẾ

_(UI, User Experience & Design Standards)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## E1. Liên kết & điều hướng (Navigation / Hyperlink)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A32:I32`, `4. Detailed Guidance!A32:J32`

### Nội dung yêu cầu

Liên kết dẫn trực tiếp và chính xác đến đúng đích cần đến.

### Tiêu chí đánh giá (Đạt)

1\. 100% liên kết được kiểm thử, không có broken link.\
2\. Số bước điều hướng tối ưu theo thiết kế UX.

### Giải thích (ngôn ngữ đơn giản)

Mọi liên kết, nút bấm điều hướng trong hệ thống phải dẫn chính xác đến đúng đích, không bị lỗi (broken link) và số bước điều hướng cần thiết phải tối ưu, không vòng vo.

### Cách kiểm tra (từng bước)

1\. Lập danh sách toàn bộ liên kết/menu điều hướng chính trong phạm vi đánh giá.\
2\. Click thử từng liên kết, xác nhận dẫn đúng đích, không lỗi 404/trang trắng.\
3\. Đếm số bước/số click cần thiết để hoàn tất các quy trình chính, so sánh với thiết kế UX đã phê duyệt (wireframe/user flow).

### Bằng chứng cần thu thập

Danh sách liên kết đã kiểm thử kèm kết quả (Pass/Fail); ảnh chụp lỗi broken link (nếu có); so sánh số bước thực tế với thiết kế UX.

### Điều kiện ĐẠT

1\. 100% liên kết dẫn đúng đích, không broken link.\
2\. Số bước điều hướng đúng theo thiết kế UX đã duyệt.

### Điều kiện KHÔNG ĐẠT

Có ≥1 liên kết lỗi/dẫn sai đích, hoặc số bước điều hướng thực tế nhiều hơn đáng kể so với thiết kế đã duyệt mà không có lý do chính đáng.

### Ví dụ lỗi thường gặp thực tế

Liên kết trong email thông báo hệ thống trỏ đến domain môi trường Test còn sót lại sau khi go-live Production, khiến người dùng click từ email nhận được nhưng vào nhầm môi trường.

## E2. Tính nhất quán giao diện (UI Consistency)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A33:I33`, `4. Detailed Guidance!A33:J33`

### Nội dung yêu cầu

Giao diện đồng nhất về màu sắc, font chữ, bố cục xuyên suốt hệ thống.

### Tiêu chí đánh giá (Đạt)

Tuân thủ 100% theo UI/UX style guide hoặc design system đã phê duyệt.

### Giải thích (ngôn ngữ đơn giản)

Màu sắc, font chữ, bố cục, khoảng cách phải đồng nhất xuyên suốt toàn hệ thống — người dùng không nên cảm thấy đang chuyển sang "một phần mềm khác" khi đổi module.

### Cách kiểm tra (từng bước)

1\. Lấy style guide/design system đã phê duyệt làm chuẩn đối chiếu.\
2\. Chụp màn hình đại diện của từng module chính, so sánh màu sắc (HEX), font, kích thước nút, khoảng cách với chuẩn.\
3\. Ghi nhận các điểm sai lệch (VD: module A dùng font khác module B).

### Bằng chứng cần thu thập

Ảnh chụp màn hình các module đối chiếu cạnh nhau với style guide; bảng liệt kê điểm không nhất quán (nếu có).

### Điều kiện ĐẠT

100% màn hình đối chiếu tuân thủ style guide/design system đã phê duyệt.

### Điều kiện KHÔNG ĐẠT

Phát hiện sai lệch rõ rệt về màu sắc/font/bố cục giữa các module không có lý do thiết kế đặc thù.

### Ví dụ lỗi thường gặp thực tế

Module được phát triển bởi đội ngũ/nhà thầu phụ khác nhau dùng bộ component UI khác nhau (khác thư viện, khác version), dẫn đến nút bấm, bảng biểu có style khác nhau rõ rệt dù cùng một hệ thống.

## E3. Khả năng học & sử dụng (Learnability)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A34:I34`, `4. Detailed Guidance!A34:J34`

### Nội dung yêu cầu

Người dùng mới có thể sử dụng hệ thống nhanh chóng với hướng dẫn tối thiểu.

### Tiêu chí đánh giá (Đạt)

Người dùng hoàn thành thao tác nghiệp vụ cơ bản trong thời gian đào tạo quy định (VD: ≤ 30 phút).

### Giải thích (ngôn ngữ đơn giản)

Người dùng mới (đặc biệt công nhân vận hành tại xưởng) phải có thể sử dụng được các thao tác nghiệp vụ cơ bản sau thời gian đào tạo ngắn, không cần hướng dẫn viên đứng cạnh liên tục.

### Cách kiểm tra (từng bước)

1\. Chọn người dùng đại diện chưa từng dùng hệ thống, cho đào tạo trong đúng thời lượng quy định.\
2\. Ngay sau đào tạo, yêu cầu thực hiện độc lập 1 bộ thao tác nghiệp vụ cơ bản, đo thời gian hoàn thành và số lần cần hỏi lại/hỗ trợ.\
3\. So sánh kết quả với mục tiêu đã đặt ra (VD: hoàn thành trong ≤ 30 phút).

### Bằng chứng cần thu thập

Kịch bản đào tạo và bài test thực hành; kết quả đo thời gian hoàn thành, số lần cần hỗ trợ của người dùng thử nghiệm.

### Điều kiện ĐẠT

Người dùng thử nghiệm hoàn thành thao tác nghiệp vụ cơ bản trong thời gian mục tiêu mà không cần hỗ trợ liên tục.

### Điều kiện KHÔNG ĐẠT

Người dùng thử nghiệm không hoàn thành được thao tác cơ bản trong thời gian mục tiêu, hoặc cần hỗ trợ liên tục ngoài dự kiến.

### Ví dụ lỗi thường gặp thực tế

Giao diện dùng nhiều thuật ngữ kỹ thuật/tiếng Anh chuyên ngành không quen thuộc với công nhân vận hành, khiến họ mất nhiều thời gian đoán ý nghĩa nút bấm dù đã qua đào tạo.

## E4. Khả năng truy cập (Accessibility)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A35:I35`, `4. Detailed Guidance!A35:J35`

### Nội dung yêu cầu

Hệ thống hỗ trợ người dùng khuyết tật/đa dạng thiết bị truy cập (nếu áp dụng).

### Tiêu chí đánh giá (Đạt)

Đáp ứng tiêu chuẩn WCAG 2.1 mức AA cho các hệ thống web hướng người dùng cuối (nếu trong phạm vi).

### Giải thích (ngôn ngữ đơn giản)

Với các hệ thống hướng đến người dùng cuối đa dạng (không chỉ vận hành nội bộ), giao diện cần hỗ trợ người khuyết tật (khiếm thị, hạn chế vận động) theo chuẩn quốc tế WCAG.

### Cách kiểm tra (từng bước)

1\. Xác định phạm vi áp dụng: hệ thống có hướng đến người dùng cuối công khai/đa dạng hay chỉ nội bộ vận hành xưởng (có thể miễn áp dụng nếu ngoài phạm vi).\
2\. Nếu trong phạm vi: dùng công cụ kiểm tra tự động (VD: axe, Lighthouse) quét các màn hình chính theo chuẩn WCAG 2.1 AA.\
3\. Kiểm tra thủ công một số tiêu chí không tự động hóa được: điều hướng bằng bàn phím, alt-text cho hình ảnh, hỗ trợ screen reader.

### Bằng chứng cần thu thập

Báo cáo quét tự động (axe/Lighthouse); kết quả kiểm tra thủ công điều hướng bàn phím/screen reader.

### Điều kiện ĐẠT

Đáp ứng WCAG 2.1 mức AA cho các màn hình trong phạm vi áp dụng.

### Điều kiện KHÔNG ĐẠT

Phát hiện lỗi WCAG mức AA chưa khắc phục ở các màn hình trong phạm vi, hoặc không thể điều hướng bằng bàn phím cho các thao tác chính.

### Ví dụ lỗi thường gặp thực tế

Hình ảnh/icon quan trọng không có thuộc tính alt-text, khiến screen reader không đọc được nội dung, người khiếm thị không biết chức năng của nút đó là gì.

## E5. Tương thích đa thiết bị (Responsive Design)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A36:I36`, `4. Detailed Guidance!A36:J36`

### Nội dung yêu cầu

Giao diện hiển thị đúng và sử dụng được trên nhiều kích thước màn hình/thiết bị.

### Tiêu chí đánh giá (Đạt)

Kiểm thử đạt trên tối thiểu các độ phân giải/thiết bị mục tiêu (desktop, tablet, mobile) theo phạm vi dự án.

### Giải thích (ngôn ngữ đơn giản)

Giao diện phải hiển thị đúng và sử dụng được trên nhiều kích thước màn hình (desktop, tablet, mobile) tùy theo phạm vi thiết bị mà dự án cam kết hỗ trợ.

### Cách kiểm tra (từng bước)

1\. Xác định danh sách thiết bị/độ phân giải mục tiêu theo phạm vi dự án.\
2\. Kiểm thử từng màn hình chính trên từng loại thiết bị/độ phân giải, chú ý các lỗi: chữ bị cắt, nút bấm chồng lấn, bảng dữ liệu tràn màn hình.\
3\. Với màn hình cảm ứng tại xưởng sản xuất (nếu có), kiểm tra thêm kích thước vùng chạm (tap target) đủ lớn để thao tác bằng găng tay.

### Bằng chứng cần thu thập

Ảnh chụp màn hình trên từng thiết bị/độ phân giải mục tiêu; danh sách lỗi hiển thị phát hiện (nếu có).

### Điều kiện ĐẠT

Kiểm thử đạt (không lỗi hiển thị nghiêm trọng) trên tối thiểu các thiết bị/độ phân giải mục tiêu theo phạm vi dự án.

### Điều kiện KHÔNG ĐẠT

Có ≥1 thiết bị/độ phân giải mục tiêu bị lỗi hiển thị nghiêm trọng (không thao tác được, mất dữ liệu hiển thị).

### Ví dụ lỗi thường gặp thực tế

Giao diện thiết kế tối ưu cho màn hình desktop nhưng khi hiển thị trên máy tính bảng gắn tại trạm sản xuất (thường có tỷ lệ màn hình khác), bảng dữ liệu bị tràn ngang phải cuộn liên tục, gây khó thao tác cho công nhân.

## E6. Kiểm tra dữ liệu đầu vào (Input Validation)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A37:I37`, `4. Detailed Guidance!A37:J37`

### Nội dung yêu cầu

Kiểm tra định dạng, kiểu dữ liệu, giá trị hợp lệ tại mọi trường nhập liệu.

### Tiêu chí đánh giá (Đạt)

1\. 100% trường nhập liệu có validate (client-side & server-side).\
2\. Từ chối/cảnh báo rõ ràng khi dữ liệu không hợp lệ.

### Giải thích (ngôn ngữ đơn giản)

Mọi trường nhập liệu phải kiểm tra định dạng, kiểu dữ liệu, giá trị hợp lệ — cả ở phía client (ngay khi gõ) lẫn phía server (không tin tưởng hoàn toàn dữ liệu từ client).

### Cách kiểm tra (từng bước)

1\. Liệt kê các trường nhập liệu quan trọng trong hệ thống.\
2\. Thử nhập dữ liệu sai định dạng/kiểu (chữ vào ô số, ngày tháng không hợp lệ, giá trị âm khi không cho phép).\
3\. Thử gửi request trực tiếp lên server (bỏ qua giao diện, VD qua Postman) với dữ liệu không hợp lệ để kiểm tra server có validate độc lập hay chỉ dựa vào client.

### Bằng chứng cần thu thập

Kết quả test từng trường nhập liệu (client-side); kết quả test gửi trực tiếp request server-side với dữ liệu sai.

### Điều kiện ĐẠT

1\. 100% trường nhập liệu có validate cả client-side và server-side.\
2\. Từ chối/cảnh báo rõ ràng khi dữ liệu không hợp lệ.

### Điều kiện KHÔNG ĐẠT

Có ≥1 trường chỉ validate ở client mà không validate ở server (có thể bị bypass), hoặc chấp nhận dữ liệu không hợp lệ.

### Ví dụ lỗi thường gặp thực tế

Form nhập liệu chặn ký tự đặc biệt ở giao diện web bằng JavaScript, nhưng khi gửi request trực tiếp qua API (bỏ qua UI), server vẫn chấp nhận và lưu dữ liệu chứa mã độc tiềm ẩn (thiếu server-side validation).

## E7. Xác nhận thao tác quan trọng (Confirmation Prompt)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A38:I38`, `4. Detailed Guidance!A38:J38`

### Nội dung yêu cầu

Yêu cầu xác nhận trước khi thực hiện thao tác không thể hoàn tác (xoá, ghi đè, duyệt...).

### Tiêu chí đánh giá (Đạt)

100% thao tác quan trọng (critical action) có bước xác nhận (confirm dialog) trước khi thực thi.

### Giải thích (ngôn ngữ đơn giản)

Các thao tác không thể hoàn tác hoặc có ảnh hưởng lớn (xóa dữ liệu, ghi đè, duyệt/phê duyệt) phải yêu cầu người dùng xác nhận trước khi thực thi, tránh thao tác nhầm gây hậu quả nghiêm trọng.

### Cách kiểm tra (từng bước)

1\. Lập danh sách các thao tác được xem là "quan trọng/không thể hoàn tác" trong hệ thống (xóa, duyệt, đóng lô, ghi đè cấu hình...).\
2\. Thực hiện từng thao tác, quan sát có hộp thoại xác nhận (confirm dialog) hiện ra trước khi thực thi hay không.\
3\. Kiểm tra nội dung dialog có mô tả rõ hậu quả (VD: "Hành động này không thể hoàn tác") để người dùng hiểu đúng mức độ nghiêm trọng.

### Bằng chứng cần thu thập

Danh sách thao tác quan trọng đã rà soát; ảnh chụp dialog xác nhận tương ứng từng thao tác.

### Điều kiện ĐẠT

100% thao tác quan trọng có bước xác nhận rõ ràng trước khi thực thi.

### Điều kiện KHÔNG ĐẠT

Có ≥1 thao tác quan trọng thực thi ngay không cần xác nhận.

### Ví dụ lỗi thường gặp thực tế

Chức năng xóa hàng loạt (bulk delete) có xác nhận khi xóa từng dòng riêng lẻ, nhưng khi chọn nhiều dòng và xóa cùng lúc lại bỏ qua bước xác nhận do lỗi logic chỉ áp dụng cho thao tác đơn lẻ.

## E8. Ngăn chặn thao tác trùng lặp (Duplicate / Double-submit Prevention)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A39:I39`, `4. Detailed Guidance!A39:J39`

### Nội dung yêu cầu

Ngăn xử lý trùng lặp khi người dùng click nhiều lần hoặc gửi lại yêu cầu.

### Tiêu chí đánh giá (Đạt)

Test double-click/double-submit không tạo bản ghi trùng lặp hoặc giao dịch lặp.

### Giải thích (ngôn ngữ đơn giản)

Khi người dùng click nút submit nhiều lần liên tiếp (do mạng chậm, do sốt ruột) hoặc bấm F5/back rồi gửi lại, hệ thống không được tạo ra bản ghi/giao dịch trùng lặp.

### Cách kiểm tra (từng bước)

1\. Thử double-click liên tiếp nhanh vào nút submit của các form tạo giao dịch quan trọng.\
2\. Thử submit form, sau đó bấm nút back trình duyệt và submit lại.\
3\. Kiểm tra dữ liệu sau các thao tác trên có phát sinh bản ghi trùng lặp không.

### Bằng chứng cần thu thập

Kết quả test double-click/double-submit; dữ liệu trước/sau thao tác đối chiếu số lượng bản ghi tạo ra.

### Điều kiện ĐẠT

Test double-click/double-submit không tạo bản ghi trùng lặp hoặc giao dịch lặp trong mọi trường hợp thử.

### Điều kiện KHÔNG ĐẠT

Có ≥1 trường hợp double-click/double-submit tạo ra bản ghi hoặc giao dịch trùng lặp.

### Ví dụ lỗi thường gặp thực tế

Nút "Xác nhận nhập kho" không bị vô hiệu hóa (disable) ngay sau click đầu tiên trong khi chờ phản hồi server, khiến người dùng click thêm lần nữa do tưởng chưa nhận thao tác, dẫn đến ghi nhận nhập kho 2 lần cho cùng 1 lô hàng.

## E9. Thông báo lỗi rõ ràng (Clear Error Messaging)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A40:I40`, `4. Detailed Guidance!A40:J40`

### Nội dung yêu cầu

Thông báo lỗi hiển thị rõ ràng, dễ hiểu, hướng dẫn cách khắc phục.

### Tiêu chí đánh giá (Đạt)

100% thông báo lỗi mô tả đúng nguyên nhân, không hiển thị lỗi kỹ thuật (stack trace) cho người dùng cuối.

### Giải thích (ngôn ngữ đơn giản)

Khi có lỗi xảy ra, thông báo hiển thị cho người dùng cuối phải dễ hiểu, mô tả đúng nguyên nhân và hướng xử lý — không hiển thị lỗi kỹ thuật thô (stack trace, mã lỗi hệ thống) gây hoang mang và có thể lộ thông tin nhạy cảm về kiến trúc hệ thống.

### Cách kiểm tra (từng bước)

1\. Chủ động tạo ra các tình huống lỗi phổ biến (nhập sai dữ liệu, mất kết nối, timeout, không đủ quyền).\
2\. Quan sát nội dung thông báo lỗi hiển thị cho người dùng.\
3\. Đánh giá thông báo có mô tả đúng nguyên nhân bằng ngôn ngữ thông thường và có gợi ý hướng xử lý không.

### Bằng chứng cần thu thập

Ảnh chụp các thông báo lỗi tương ứng từng tình huống test.

### Điều kiện ĐẠT

100% thông báo lỗi mô tả đúng nguyên nhân bằng ngôn ngữ dễ hiểu, không hiển thị lỗi kỹ thuật (stack trace, SQL error) cho người dùng cuối.

### Điều kiện KHÔNG ĐẠT

Có ≥1 tình huống hiển thị lỗi kỹ thuật thô cho người dùng cuối, hoặc thông báo lỗi chung chung không giúp người dùng biết cách xử lý.

### Ví dụ lỗi thường gặp thực tế

Khi mất kết nối đến hệ thống liên quan (VD: PLC/SCADA), giao diện hiển thị nguyên văn exception "Connection timeout at 10.0.x.x:502" thay vì thông báo thân thiện như "Không thể kết nối thiết bị, vui lòng kiểm tra đường truyền hoặc liên hệ IT".

## E10. Cấu hình mã lỗi (Configurable Error Code)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A41:I41`, `4. Detailed Guidance!A41:J41`

### Nội dung yêu cầu

Hệ thống cho phép quản trị viên cấu hình, quản lý danh mục mã lỗi (error code) gồm mã, mô tả, mức độ, hướng xử lý mà không cần can thiệp mã nguồn.

### Tiêu chí đánh giá (Đạt)

1\. 100% mã lỗi phát sinh trên hệ thống nằm trong danh mục có thể cấu hình qua giao diện quản trị.\
2\. Thêm/sửa/vô hiệu hóa mã lỗi thực hiện được mà không cần build/deploy lại ứng dụng.\
3\. Không tồn tại mã lỗi hard-code nằm ngoài danh mục quản lý.

### Giải thích (ngôn ngữ đơn giản)

Quản trị viên phải có thể thêm/sửa/vô hiệu hóa mã lỗi (error code) — bao gồm nội dung mô tả, mức độ, hướng xử lý — thông qua giao diện quản trị, không cần lập trình viên can thiệp mã nguồn mỗi khi cần điều chỉnh.

### Cách kiểm tra (từng bước)

1\. Truy cập màn hình quản trị danh mục mã lỗi, thử thêm mới/sửa/vô hiệu hóa một mã lỗi.\
2\. Kiểm tra thay đổi có hiệu lực ngay mà không cần build/deploy lại ứng dụng.\
3\. Rà soát mã nguồn/log lỗi thực tế phát sinh, đối chiếu xem có mã lỗi nào hard-code, không nằm trong danh mục quản lý được không.

### Bằng chứng cần thu thập

Ảnh/video thao tác thêm sửa mã lỗi qua giao diện quản trị; danh sách mã lỗi hard-code phát hiện (nếu có).

### Điều kiện ĐẠT

1\. 100% mã lỗi phát sinh nằm trong danh mục có thể cấu hình qua giao diện quản trị.\
2\. Thay đổi có hiệu lực không cần build/deploy lại.

### Điều kiện KHÔNG ĐẠT

Tồn tại mã lỗi hard-code ngoài danh mục quản lý, hoặc thay đổi mã lỗi yêu cầu deploy lại ứng dụng.

### Ví dụ lỗi thường gặp thực tế

Danh mục mã lỗi quản lý được qua giao diện chỉ áp dụng cho lỗi nghiệp vụ, còn lỗi hệ thống/tích hợp (VD: lỗi kết nối API bên thứ ba) vẫn hard-code trong mã nguồn, mỗi lần cần đổi nội dung thông báo phải chờ release mới.

## E11. Logo & nhận diện thương hiệu (Logo & Brand Identity Usage)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A42:I42`, `4. Detailed Guidance!A42:J42`

### Nội dung yêu cầu

Logo công ty/sản phẩm hiển thị trong phần mềm (màn hình đăng nhập, header, splash screen, tài liệu xuất ra...) phải tuân thủ quy chuẩn về màu sắc, kích thước tối thiểu, khoảng cách an toàn và vị trí đặt.

### Tiêu chí đánh giá (Đạt)

1\. Logo không bị kéo giãn, nén, xoay, đổi màu sai quy định, không thêm khung/đổ bóng/viền.\
2\. Kích thước tối thiểu ≥ 80px trên màn hình.\
3\. Có khoảng cách an toàn (clear space) xung quanh logo tối thiểu bằng chiều cao ký tự đầu của logo.\
4\. Logo đặt đúng vị trí quy định (góc hoặc giữa) theo thiết kế đã phê duyệt.

### Giải thích (ngôn ngữ đơn giản)

Logo hiển thị trong phần mềm (màn hình đăng nhập, header, tài liệu xuất ra) phải tuân thủ đúng quy chuẩn về màu sắc, kích thước, khoảng cách an toàn và vị trí, đảm bảo tính chuyên nghiệp và nhất quán thương hiệu.

### Cách kiểm tra (từng bước)

1\. Lấy tài liệu brand guideline làm chuẩn đối chiếu (kích thước tối thiểu, khoảng cách an toàn, màu sắc cho phép).\
2\. Chụp màn hình các vị trí có logo (login, header, splash screen, báo cáo xuất ra) và đo đạc thực tế (kích thước pixel, khoảng cách xung quanh).\
3\. Kiểm tra logo có bị kéo giãn/nén sai tỷ lệ, đổi màu, thêm hiệu ứng (khung/đổ bóng) không đúng quy định không.

### Bằng chứng cần thu thập

Ảnh chụp các vị trí hiển thị logo kèm số đo kích thước/khoảng cách; đối chiếu với brand guideline.

### Điều kiện ĐẠT

1\. Logo không bị kéo giãn/nén/xoay/đổi màu sai quy định.\
2\. Kích thước tối thiểu ≥ 80px.\
3\. Khoảng cách an toàn đạt chuẩn.\
4\. Vị trí đặt đúng thiết kế đã phê duyệt.

### Điều kiện KHÔNG ĐẠT

Phát hiện ≥1 vị trí logo vi phạm quy chuẩn (sai tỷ lệ, sai màu, thiếu khoảng cách an toàn, sai vị trí).

### Ví dụ lỗi thường gặp thực tế

Logo trên báo cáo PDF xuất ra bị co giãn không đúng tỷ lệ gốc (stretch) do khung chứa ảnh trong template báo cáo không giữ tỷ lệ khung hình (aspect ratio), khiến logo bị méo khi in.

## E12. Bảng màu thương hiệu & tỷ lệ sử dụng (Color Palette & Usage Proportion)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A43:I43`, `4. Detailed Guidance!A43:J43`

### Nội dung yêu cầu

Giao diện phần mềm sử dụng bảng màu thương hiệu thống nhất (màu chính, màu nhấn, màu cảnh báo/lỗi) theo đúng tỷ lệ quy định, không phối màu tùy tiện.

### Tiêu chí đánh giá (Đạt)

1\. 100% màn hình sử dụng đúng mã màu (HEX) trong bảng màu thương hiệu đã phê duyệt.\
2\. Màu chính (đen/trắng/xám) chiếm tỷ lệ lớn nhất trong bố cục.\
3\. Màu nhấn thương hiệu dùng có chủ đích cho phần tử tương tác (nút bấm, liên kết).\
4\. Màu cảnh báo/lỗi chỉ dùng cho warning/error và không vượt quá 5% tổng diện tích giao diện.

### Giải thích (ngôn ngữ đơn giản)

Toàn hệ thống phải dùng chung một bảng màu thương hiệu (màu chính, màu nhấn, màu cảnh báo) theo đúng tỷ lệ diện tích quy định, tránh phối màu tùy tiện gây rối mắt hoặc mất tính chuyên nghiệp.

### Cách kiểm tra (từng bước)

1\. Lấy bảng màu thương hiệu (brand color palette) đã phê duyệt kèm mã HEX cụ thể.\
2\. Dùng công cụ soi màu (color picker) trên các màn hình chính, đối chiếu mã HEX thực tế với bảng màu chuẩn.\
3\. Ước lượng tỷ lệ diện tích của từng nhóm màu (màu nền/chính, màu nhấn, màu cảnh báo) trên bố cục tổng thể của màn hình.

### Bằng chứng cần thu thập

Ảnh chụp màn hình kèm mã HEX đo được; bảng đối chiếu tỷ lệ diện tích màu thực tế so với quy định.

### Điều kiện ĐẠT

1\. 100% màn hình dùng đúng mã HEX trong bảng màu đã duyệt.\
2\. Màu chính chiếm tỷ lệ lớn nhất.\
3\. Màu nhấn dùng có chủ đích cho phần tử tương tác.\
4\. Màu cảnh báo/lỗi không vượt quá 5% diện tích.

### Điều kiện KHÔNG ĐẠT

Phát hiện màu sai mã HEX so với bảng chuẩn, hoặc màu cảnh báo/lỗi lạm dụng vượt quá tỷ lệ quy định làm giao diện trông "báo động" liên tục.

### Ví dụ lỗi thường gặp thực tế

Đội phát triển tự chọn màu gần đúng bằng mắt thay vì lấy đúng mã HEX từ design system, dẫn đến nhiều màn hình có cùng ý nghĩa nhưng sắc độ hơi khác nhau, khó nhận ra khi nhìn lướt nhưng gây thiếu nhất quán khi soi kỹ.

## E13. Màu sắc cảnh báo (Warning/Alert Color Standard)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A44:I44`, `4. Detailed Guidance!A44:J44`

### Nội dung yêu cầu

Màu sắc thể hiện trạng thái/mức độ cảnh báo (bình thường, cảnh báo, lỗi/nguy hiểm) trên bảng thống kê, dashboard, biểu đồ phải được quy định thống nhất và áp dụng nhất quán toàn hệ thống.

### Tiêu chí đánh giá (Đạt)

1\. 100% màn hình sử dụng đúng bộ mã màu (HEX) quy chuẩn cho từng mức trạng thái (VD: xanh lá = bình thường, vàng/cam = cảnh báo, đỏ = lỗi/nguy hiểm).\
2\. Không dùng màu tùy tiện sai ý nghĩa.\
3\. Màu sắc cảnh báo đảm bảo độ tương phản đọc được theo chuẩn tại mục P3.

### Giải thích (ngôn ngữ đơn giản)

Màu thể hiện trạng thái (bình thường/cảnh báo/lỗi) trên dashboard, bảng thống kê, biểu đồ phải theo quy ước thống nhất toàn hệ thống (VD: xanh = bình thường, vàng/cam = cảnh báo, đỏ = lỗi/nguy hiểm) để người vận hành nhận diện tức thời mà không cần đọc chữ.

### Cách kiểm tra (từng bước)

1\. Lấy bộ quy ước màu trạng thái đã quy định làm chuẩn.\
2\. Rà soát các màn hình dashboard/bảng thống kê/biểu đồ có hiển thị trạng thái, đối chiếu màu sắc thực tế với quy ước.\
3\. Kiểm tra tại các module khác nhau (do có thể do đội phát triển khác nhau xây dựng) có dùng nhất quán cùng 1 bộ màu không.

### Bằng chứng cần thu thập

Ảnh chụp các màn hình có hiển thị trạng thái màu sắc; đối chiếu với bộ quy ước màu chuẩn.

### Điều kiện ĐẠT

1\. 100% màn hình dùng đúng bộ mã màu quy chuẩn cho từng mức trạng thái.\
2\. Đảm bảo độ tương phản đọc được theo chuẩn E14.

### Điều kiện KHÔNG ĐẠT

Phát hiện màn hình dùng màu sai ý nghĩa quy ước (VD: đỏ dùng cho trạng thái bình thường ở 1 module khác với chuẩn chung), gây hiểu nhầm mức độ nghiêm trọng.

### Ví dụ lỗi thường gặp thực tế

Module cảnh báo chất lượng dùng đỏ = "cần chú ý" (mức nhẹ) trong khi module giám sát máy dùng đỏ = "dừng khẩn cấp" (mức nghiêm trọng nhất) — người vận hành quen với 1 module dễ phản ứng sai mức độ khi chuyển sang module khác.

## E14. Độ tương phản màu sắc (Color Contrast Ratio – WCAG)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A45:I45`, `4. Detailed Guidance!A45:J45`

### Nội dung yêu cầu

Tỷ lệ tương phản giữa văn bản/thành phần giao diện và nền phải đảm bảo khả năng đọc, đặc biệt cho người khiếm thị.

### Tiêu chí đánh giá (Đạt)

1\. Đạt tối thiểu mức AA theo tiêu chuẩn WCAG: tỷ lệ tương phản ≥ 4.5:1 giữa chữ và nền cho cỡ chữ dưới 18pt (≥ 3:1 cho chữ lớn/đậm).\
2\. 100% màn hình chính được kiểm tra bằng công cụ đo tương phản trước khi phát hành.

### Giải thích (ngôn ngữ đơn giản)

Chữ và các thành phần giao diện quan trọng phải có độ tương phản đủ lớn so với nền để đọc được rõ ràng, đặc biệt quan trọng với người khiếm thị hoặc khi màn hình đặt trong môi trường ánh sáng mạnh tại xưởng sản xuất.

### Cách kiểm tra (từng bước)

1\. Dùng công cụ đo tương phản màu (VD: WebAIM Contrast Checker, trình duyệt dev tools) trên các cặp màu chữ/nền tại màn hình chính.\
2\. Ghi nhận tỷ lệ tương phản đo được, so với ngưỡng WCAG AA (4.5:1 cho chữ thường, 3:1 cho chữ lớn/đậm).\
3\. Ưu tiên kiểm tra các màn hình dùng nhiều tại hiện trường sản xuất (dashboard, cảnh báo) vì môi trường ánh sáng khắc nghiệt hơn văn phòng.

### Bằng chứng cần thu thập

Kết quả đo tương phản từng cặp màu kiểm tra kèm công cụ sử dụng.

### Điều kiện ĐẠT

Đạt tối thiểu mức AA: tương phản ≥ 4.5:1 (chữ thường) hoặc ≥ 3:1 (chữ lớn/đậm) cho 100% màn hình chính được kiểm tra.

### Điều kiện KHÔNG ĐẠT

Có ≥1 màn hình chính có cặp màu chữ/nền dưới ngưỡng AA.

### Ví dụ lỗi thường gặp thực tế

Chữ màu xám nhạt trên nền trắng dùng cho nhãn phụ (label) trông "tinh tế" trên máy tính văn phòng nhưng gần như không đọc được trên màn hình cảm ứng ngoài xưởng dưới ánh sáng mạnh do độ tương phản quá thấp.

## E15. Kiểu chữ & khoảng cách văn bản (Typography Standards)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A46:I46`, `4. Detailed Guidance!A46:J46`

### Nội dung yêu cầu

Hệ thống sử dụng bộ font chữ chuẩn, nhất quán, có quy tắc rõ ràng về giãn dòng, độ rộng dòng và căn lề cho từng loại nội dung.

### Tiêu chí đánh giá (Đạt)

1\. 100% giao diện dùng bộ font chữ đã quy định thống nhất (kèm phông chữ riêng cho từng ngôn ngữ Á Đông nếu hỗ trợ đa ngôn ngữ).\
2\. Giãn dòng tiêu đề khoảng 1.15–1.25 lần cỡ chữ, phụ đề 1.25–1.5 lần, nội dung 1.5–1.6 lần.\
3\. Độ rộng dòng văn bản dài khoảng 40–70 ký tự/dòng.\
4\. Căn lề trái cho văn bản dài, căn giữa chỉ dùng cho tiêu đề/nội dung ngắn.

### Giải thích (ngôn ngữ đơn giản)

Toàn hệ thống dùng chung bộ font chữ với quy tắc rõ ràng về giãn dòng, độ rộng dòng, căn lề — đảm bảo văn bản dễ đọc và nhất quán về mặt hình ảnh.

### Cách kiểm tra (từng bước)

1\. Lấy bộ font chữ chuẩn và bảng quy tắc typography đã phê duyệt.\
2\. Kiểm tra font thực tế áp dụng trên các màn hình (bao gồm font riêng cho ngôn ngữ Á Đông nếu có hỗ trợ đa ngôn ngữ).\
3\. Đo giãn dòng, độ rộng dòng văn bản dài, cách căn lề trên các màn hình có nội dung văn bản nhiều (VD: mô tả, ghi chú).

### Bằng chứng cần thu thập

Ảnh chụp màn hình kèm thông số đo (giãn dòng, độ rộng dòng) đối chiếu với quy định.

### Điều kiện ĐẠT

1\. 100% giao diện dùng đúng bộ font quy định.\
2\. Giãn dòng, độ rộng dòng, căn lề đúng theo quy tắc đã duyệt.

### Điều kiện KHÔNG ĐẠT

Phát hiện màn hình dùng font khác quy định, hoặc giãn dòng/độ rộng dòng sai lệch đáng kể gây khó đọc.

### Ví dụ lỗi thường gặp thực tế

Font chữ tiếng Việt có dấu hiển thị bằng font hệ thống mặc định (fallback font) do font thương hiệu không hỗ trợ đầy đủ ký tự có dấu, khiến một số màn hình hiển thị font khác hẳn phần còn lại mà không ai để ý vì dấu vẫn đọc được.

## E16. Hệ thống Icon (Iconography System)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A47:I47`, `4. Detailed Guidance!A47:J47`

### Nội dung yêu cầu

Icon trong giao diện được thiết kế và sử dụng nhất quán theo một bộ nguyên tắc chung về kiểu dáng, độ dày nét, góc bo và lưới thiết kế.

### Tiêu chí đánh giá (Đạt)

1\. 100% icon trong cùng hệ thống dùng chung phong cách (outline, bo góc, độ dày nét thống nhất, lưới kích thước chuẩn).\
2\. Không dùng quá 2 màu trên 1 icon và không dùng gradient.\
3\. Mỗi khái niệm/chức năng chỉ có 1 icon đại diện duy nhất, không tồn tại icon trùng lặp ý nghĩa khác kiểu dáng.

### Giải thích (ngôn ngữ đơn giản)

Icon trong giao diện phải theo cùng một phong cách (outline/filled, độ dày nét, góc bo, lưới kích thước) và mỗi chức năng chỉ nên có 1 icon đại diện duy nhất, tránh gây nhầm lẫn.

### Cách kiểm tra (từng bước)

1\. Thu thập toàn bộ icon đang sử dụng trong hệ thống (chụp màn hình hoặc export từ design system).\
2\. So sánh phong cách (outline vs filled, độ dày nét, bo góc) giữa các icon.\
3\. Kiểm tra có tồn tại 2 icon khác kiểu dáng nhưng cùng đại diện 1 chức năng/khái niệm không (VD: 2 icon "xóa" khác nhau ở 2 module).

### Bằng chứng cần thu thập

Bảng tổng hợp icon đã thu thập theo từng khái niệm/chức năng, đánh dấu các trường hợp không nhất quán.

### Điều kiện ĐẠT

1\. 100% icon dùng chung phong cách thống nhất.\
2\. Không dùng quá 2 màu/1 icon, không gradient.\
3\. Mỗi khái niệm chỉ có 1 icon đại diện duy nhất.

### Điều kiện KHÔNG ĐẠT

Phát hiện icon khác phong cách trộn lẫn, hoặc cùng 1 khái niệm có nhiều icon khác kiểu dáng.

### Ví dụ lỗi thường gặp thực tế

Icon lấy từ nhiều bộ thư viện icon miễn phí khác nhau (do các lập trình viên tự chọn) khiến độ dày nét và góc bo không đồng nhất — nhìn tổng thể màn hình có vẻ "lộn xộn" dù từng icon riêng lẻ đều đẹp.

## E17. Hình minh họa & trạng thái trống (Illustration & Empty-state Consistency)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A48:I48`, `4. Detailed Guidance!A48:J48`

### Nội dung yêu cầu

Hình minh họa dùng cho màn hình trạng thái trống (empty state), onboarding, thông báo lỗi... tuân thủ phong cách và bảng màu thống nhất.

### Tiêu chí đánh giá (Đạt)

1\. 100% hình minh họa trong hệ thống dùng chung một phong cách thiết kế (không pha trộn nhiều style khác nhau).\
2\. Ưu tiên tông màu chủ đạo theo bảng màu thương hiệu (VD: xám làm nền, màu nhấn để làm điểm nhấn), hạn chế màu sắc thừa gây mất tập trung.

### Giải thích (ngôn ngữ đơn giản)

Các hình minh họa dùng cho màn hình chưa có dữ liệu (empty state), onboarding, hoặc trang lỗi phải theo cùng một phong cách và tông màu, tránh pha trộn nhiều phong cách gây rối mắt.

### Cách kiểm tra (từng bước)

1\. Thu thập toàn bộ hình minh họa xuất hiện tại các màn hình empty-state/onboarding/lỗi trong hệ thống.\
2\. So sánh phong cách vẽ (flat, 3D, line-art...) và tông màu chủ đạo giữa các hình.\
3\. Đối chiếu với bảng màu thương hiệu để xác định hình minh họa có ưu tiên tông màu chủ đạo đúng quy định không.

### Bằng chứng cần thu thập

Ảnh chụp các màn hình có hình minh họa; nhận xét về mức độ nhất quán phong cách.

### Điều kiện ĐẠT

100% hình minh họa dùng chung một phong cách thiết kế, ưu tiên tông màu chủ đạo theo bảng màu thương hiệu.

### Điều kiện KHÔNG ĐẠT

Phát hiện hình minh họa pha trộn nhiều phong cách khác nhau rõ rệt (VD: 1 hình vẽ tay, 1 hình 3D render) trong cùng hệ thống.

### Ví dụ lỗi thường gặp thực tế

Hình minh họa trang "không có dữ liệu" được tải miễn phí từ nhiều nguồn khác nhau trên internet (mỗi lập trình viên tự tìm), dẫn đến mỗi module có phong cách hình minh họa khác hẳn nhau.

## E18. Sơ đồ/biểu đồ kỹ thuật (Diagram & Topology Standards)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A49:I49`, `4. Detailed Guidance!A49:J49`

### Nội dung yêu cầu

Sơ đồ mạng, sơ đồ quy trình sản xuất, sơ đồ kết nối thiết bị hiển thị trong phần mềm tuân thủ chuẩn thống nhất về ký hiệu, màu sắc và độ dày nét.

### Tiêu chí đánh giá (Đạt)

1\. 100% sơ đồ trong hệ thống dùng chung bộ ký hiệu/quy ước màu (VD: một màu cho thiết bị/hệ thống chính, một màu khác cho thiết bị phụ trợ).\
2\. Đường nối thể hiện đúng chiều quan hệ bằng mũi tên.\
3\. Độ dày nét, kiểu nét đứt/liền nhất quán giữa các sơ đồ trong toàn hệ thống.

### Giải thích (ngôn ngữ đơn giản)

Các sơ đồ mạng, sơ đồ quy trình sản xuất, sơ đồ kết nối thiết bị hiển thị trong phần mềm phải dùng chung một bộ ký hiệu, màu sắc và độ dày nét, giúp người đọc (kỹ sư, vận hành) hiểu đúng và nhanh dù xem sơ đồ ở module nào.

### Cách kiểm tra (từng bước)

1\. Thu thập các sơ đồ kỹ thuật hiển thị trong hệ thống (sơ đồ mạng, sơ đồ dây chuyền, sơ đồ kết nối).\
2\. Kiểm tra bộ ký hiệu/quy ước màu có nhất quán giữa các sơ đồ (VD: cùng 1 màu cho "thiết bị chính" ở mọi sơ đồ).\
3\. Kiểm tra chiều mũi tên, kiểu nét (đứt/liền), độ dày nét có đồng nhất không.

### Bằng chứng cần thu thập

Ảnh chụp các sơ đồ kỹ thuật từ nhiều module; nhận xét đối chiếu tính nhất quán ký hiệu/màu sắc.

### Điều kiện ĐẠT

1\. 100% sơ đồ dùng chung bộ ký hiệu/quy ước màu.\
2\. Mũi tên thể hiện đúng chiều quan hệ.\
3\. Độ dày/kiểu nét nhất quán.

### Điều kiện KHÔNG ĐẠT

Phát hiện sơ đồ dùng ký hiệu/màu khác quy ước chung, gây hiểu nhầm khi đọc chéo giữa các module.

### Ví dụ lỗi thường gặp thực tế

Sơ đồ topology mạng dùng màu xanh cho "thiết bị online" ở module giám sát mạng, nhưng ở module giám sát máy sản xuất lại dùng màu xanh cho "máy đang dừng" — kỹ sư quen đọc module này dễ hiểu nhầm khi chuyển sang module khác.

## E19. Quản trị hệ thống thiết kế (Design System Governance)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A50:I50`, `4. Detailed Guidance!A50:J50`

### Nội dung yêu cầu

Có tài liệu/bộ quy chuẩn thiết kế (design guideline/design system) chính thức được phê duyệt, làm nguồn tham chiếu duy nhất cho toàn bộ đội ngũ phát triển.

### Tiêu chí đánh giá (Đạt)

1\. Tồn tại tài liệu Design Guideline/Design System được phê duyệt, có số phiên bản và được cập nhật khi có thay đổi.\
2\. 100% thành viên thiết kế/phát triển UI đối chiếu tuân thủ design system trước khi release.\
3\. Mọi ngoại lệ so với chuẩn thiết kế phải được phê duyệt chính thức và ghi nhận lý do.

### Giải thích (ngôn ngữ đơn giản)

Cần có một tài liệu/bộ quy chuẩn thiết kế chính thức, được phê duyệt và cập nhật, làm nguồn tham chiếu duy nhất (single source of truth) cho toàn bộ đội ngũ phát triển — tránh tình trạng mỗi người làm theo gu thẩm mỹ riêng.

### Cách kiểm tra (từng bước)

1\. Yêu cầu cung cấp tài liệu Design Guideline/Design System chính thức, kiểm tra có số phiên bản, ngày phê duyệt.\
2\. Phỏng vấn nhanh 2–3 thành viên đội thiết kế/phát triển UI để xác nhận họ có biết và tham chiếu tài liệu này không.\
3\. Kiểm tra có quy trình phê duyệt cho các trường hợp ngoại lệ (thiết kế khác chuẩn) không, và các ngoại lệ đã áp dụng có được ghi nhận lý do không.

### Bằng chứng cần thu thập

Tài liệu Design System kèm lịch sử phiên bản; bằng chứng phê duyệt các trường hợp ngoại lệ (nếu có).

### Điều kiện ĐẠT

1\. Tồn tại Design System được phê duyệt chính thức, có versioning.\
2\. Đội ngũ phát triển xác nhận có tham chiếu.\
3\. Mọi ngoại lệ được phê duyệt và ghi nhận lý do.

### Điều kiện KHÔNG ĐẠT

Không có tài liệu Design System chính thức, hoặc có nhưng không được đội ngũ phát triển sử dụng thực tế, hoặc có ngoại lệ thiết kế không qua phê duyệt.

### Ví dụ lỗi thường gặp thực tế

Design System tồn tại dưới dạng file Figma nhưng chỉ đội thiết kế truy cập được, lập trình viên frontend không có quyền xem hoặc không biết file tồn tại, nên tự ước lượng theo ảnh chụp màn hình cũ đã lỗi thời.

## E20. Hiển thị số lượng trên bảng thống kê (Statistic Table Count Display)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A51:I51`, `4. Detailed Guidance!A51:J51`

### Nội dung yêu cầu

Bảng thống kê (statistic/dashboard) hiển thị đầy đủ, chính xác tổng số bản ghi và số lượng theo từng nhóm/trạng thái tương ứng với dữ liệu thực tế trong hệ thống.

### Tiêu chí đánh giá (Đạt)

1\. 100% số liệu hiển thị trên bảng thống kê khớp với dữ liệu gốc (đối chiếu ngẫu nhiên tối thiểu 30 lượt, sai lệch = 0%).\
2\. Số liệu cập nhật đúng theo tần suất quy định (real-time hoặc định kỳ).\
3\. Định dạng số tuân thủ dấu phân cách hàng nghìn theo locale đang chọn.

### Giải thích (ngôn ngữ đơn giản)

Các con số trên bảng thống kê/dashboard (tổng số, số theo nhóm/trạng thái) phải khớp chính xác với dữ liệu thực tế trong hệ thống, cập nhật đúng tần suất, và định dạng số đúng theo locale.

### Cách kiểm tra (từng bước)

1\. Chọn ngẫu nhiên tối thiểu 30 lượt đối chiếu số liệu trên bảng thống kê với số liệu truy vấn trực tiếp từ dữ liệu gốc.\
2\. Kiểm tra tần suất cập nhật số liệu (real-time hay theo chu kỳ) có đúng như thiết kế không.\
3\. Kiểm tra định dạng số (dấu phân cách hàng nghìn) có đúng theo locale/ngôn ngữ đang chọn không.

### Bằng chứng cần thu thập

Bảng đối chiếu số liệu thống kê vs. dữ liệu gốc (≥30 lượt); ảnh chụp định dạng số theo từng locale.

### Điều kiện ĐẠT

1\. 100% số liệu đối chiếu khớp với dữ liệu gốc (sai lệch = 0%).\
2\. Cập nhật đúng tần suất.\
3\. Định dạng số đúng locale.

### Điều kiện KHÔNG ĐẠT

Có ≥1 số liệu thống kê sai lệch so với dữ liệu gốc, hoặc cập nhật trễ hơn tần suất quy định, hoặc sai định dạng số theo locale.

### Ví dụ lỗi thường gặp thực tế

Bảng thống kê đếm số bản ghi theo bộ lọc ngày nhưng dùng sai múi giờ (UTC thay vì local time) khiến số liệu "hôm nay" bị lệch vài giờ, không khớp với số liệu người vận hành tự đếm thủ công.

## E21. Tính chính xác về thời gian (Time/Timestamp Accuracy)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A52:I52`, `4. Detailed Guidance!A52:J52`

### Nội dung yêu cầu

Thời gian hiển thị và ghi nhận trên toàn hệ thống (timestamp log, đồng hồ giao diện, dấu thời gian bản ghi) phải chính xác và đồng bộ theo một nguồn thời gian chuẩn.

### Tiêu chí đánh giá (Đạt)

1\. Chênh lệch thời gian giữa các máy trạm/server với nguồn thời gian chuẩn (NTP) ≤ 1 giây (hoặc theo ngưỡng quy định).\
2\. Toàn hệ thống thống nhất một múi giờ (timezone) đã cấu hình, hiển thị nhất quán giữa các module.\
3\. Có cơ chế đồng bộ NTP tự động định kỳ và cảnh báo khi lệch vượt ngưỡng.

### Giải thích (ngôn ngữ đơn giản)

Thời gian hiển thị và ghi nhận trên toàn hệ thống (đồng hồ giao diện, timestamp log, dấu thời gian bản ghi) phải chính xác và đồng bộ theo một nguồn thời gian chuẩn (NTP), vì sai lệch thời gian có thể làm sai thứ tự sự kiện khi truy vết sự cố hoặc tính toán thời gian sản xuất.

### Cách kiểm tra (từng bước)

1\. So sánh đồng hồ hiển thị trên các máy trạm/server với nguồn thời gian chuẩn (NTP server nội bộ hoặc chuẩn quốc gia).\
2\. Kiểm tra cấu hình múi giờ (timezone) có thống nhất giữa các module/máy chủ không.\
3\. Kiểm tra hệ thống có cơ chế đồng bộ NTP tự động định kỳ và cảnh báo khi lệch vượt ngưỡng không.

### Bằng chứng cần thu thập

Kết quả đo chênh lệch thời gian giữa các máy trạm/server với nguồn chuẩn; cấu hình đồng bộ NTP.

### Điều kiện ĐẠT

1\. Chênh lệch thời gian ≤ 1 giây (hoặc theo ngưỡng quy định) giữa các máy trạm/server với nguồn chuẩn.\
2\. Múi giờ thống nhất toàn hệ thống.\
3\. Có cơ chế đồng bộ NTP tự động và cảnh báo khi lệch.

### Điều kiện KHÔNG ĐẠT

Phát hiện máy trạm/server lệch thời gian vượt ngưỡng, hoặc múi giờ không thống nhất giữa các module, hoặc không có cơ chế đồng bộ tự động.

### Ví dụ lỗi thường gặp thực tế

Server đặt tại data center dùng UTC nhưng ứng dụng hiển thị theo giờ địa phương không qua chuyển đổi đúng cách, khiến timestamp log server và thời gian thực tế người vận hành thấy trên máy trạm lệch nhau đúng số giờ chênh múi giờ — gây khó khăn khi đối chiếu sự cố.

## E22. Hiển thị đơn vị tính (Unit of Measurement Display)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp màn hình đối chiếu style guide/design system + báo cáo kiểm thử UI
- **Nguồn:** `3. Assessment Checklist!A53:I53`, `4. Detailed Guidance!A53:J53`

### Nội dung yêu cầu

Mọi trường dữ liệu có đơn vị đo (nhiệt độ, áp suất, thời gian, dung lượng, tốc độ...) phải hiển thị rõ đơn vị tính kèm theo giá trị trên giao diện, báo cáo và biểu đồ.

### Tiêu chí đánh giá (Đạt)

1\. 100% trường dữ liệu có đơn vị được hiển thị đơn vị đi kèm giá trị (bảng, biểu đồ, form nhập liệu, báo cáo xuất ra).\
2\. Đơn vị hiển thị nhất quán, đúng chuẩn quy định trên toàn hệ thống (VD: °C, kg, ms, MB).\
3\. Với trường cho phép đổi đơn vị, giá trị được tự động quy đổi chính xác khi chuyển đổi.

### Giải thích (ngôn ngữ đơn giản)

Mọi giá trị có đơn vị đo (nhiệt độ, áp suất, thời gian, dung lượng, tốc độ...) phải luôn hiển thị kèm đơn vị trên giao diện, báo cáo, biểu đồ — tránh người vận hành hiểu nhầm đơn vị dẫn đến sai sót nghiêm trọng trong vận hành thiết bị.

### Cách kiểm tra (từng bước)

1\. Rà soát các trường/biểu đồ/báo cáo có giá trị đo lường, kiểm tra có hiển thị đơn vị kèm theo không.\
2\. Kiểm tra đơn vị hiển thị có nhất quán, đúng chuẩn quy định trên toàn hệ thống không (VD: luôn là °C, không lẫn °F ở nơi khác).\
3\. Với trường cho phép đổi đơn vị (VD: kg ↔ lb), thử chuyển đổi và kiểm tra giá trị quy đổi có chính xác không.

### Bằng chứng cần thu thập

Ảnh chụp các màn hình/báo cáo có giá trị đo lường kèm đơn vị; kết quả test chuyển đổi đơn vị (nếu áp dụng).

### Điều kiện ĐẠT

1\. 100% trường dữ liệu có đơn vị được hiển thị đơn vị đi kèm.\
2\. Đơn vị nhất quán, đúng chuẩn.\
3\. Giá trị quy đổi chính xác khi chuyển đổi.

### Điều kiện KHÔNG ĐẠT

Có ≥1 trường dữ liệu có đơn vị nhưng không hiển thị đơn vị, hoặc đơn vị không nhất quán giữa các màn hình, hoặc quy đổi sai giá trị.

### Ví dụ lỗi thường gặp thực tế

Biểu đồ nhiệt độ hiển thị chỉ số nhưng không ghi đơn vị trên trục, người vận hành ở ca sau tưởng nhầm đơn vị °F sang °C (do một số thiết bị đo gốc dùng °F) dẫn đến đánh giá sai tình trạng thiết bị.
