# F. ĐA NGÔN NGỮ & TRỢ GIÚP NGƯỜI DÙNG

_(Localization & Help/Support)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## F1. Hỗ trợ đa ngôn ngữ giao diện (Multi-language UI Support)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A54:I54`, `4. Detailed Guidance!A54:J54`

### Nội dung yêu cầu

Hệ thống hỗ trợ hiển thị giao diện theo nhiều ngôn ngữ (tối thiểu: Tiếng Việt, Tiếng Anh).

### Tiêu chí đánh giá (Đạt)

1\. 100% nhãn, thông báo, tài liệu hướng dẫn trong phạm vi được dịch đầy đủ cho từng ngôn ngữ hỗ trợ.\
2\. Không còn text hard-code ngôn ngữ gốc sót lại trên giao diện.

### Giải thích (ngôn ngữ đơn giản)

Toàn bộ nhãn, thông báo, tài liệu hướng dẫn phải được dịch đầy đủ cho từng ngôn ngữ hệ thống hỗ trợ (tối thiểu Việt/Anh), không sót text ngôn ngữ gốc chưa dịch.

### Cách kiểm tra (từng bước)

1\. Chuyển ngôn ngữ giao diện lần lượt qua từng ngôn ngữ được hỗ trợ.\
2\. Duyệt qua toàn bộ màn hình chính, ghi nhận các nhãn/thông báo còn sót ngôn ngữ gốc (chưa dịch) hoặc hiển thị key dịch (VD: "label.button.save" thay vì "Lưu").\
3\. Kiểm tra thông báo lỗi hệ thống (không chỉ nhãn tĩnh) cũng được dịch đầy đủ.

### Bằng chứng cần thu thập

Ảnh chụp màn hình theo từng ngôn ngữ; danh sách text chưa dịch/dịch sai phát hiện được.

### Điều kiện ĐẠT

1\. 100% nhãn, thông báo trong phạm vi được dịch đầy đủ cho mọi ngôn ngữ hỗ trợ.\
2\. Không còn text hard-code ngôn ngữ gốc.

### Điều kiện KHÔNG ĐẠT

Có ≥1 nhãn/thông báo chưa dịch hoặc hiển thị sai (lộ resource key) ở bất kỳ ngôn ngữ nào được công bố hỗ trợ.

### Ví dụ lỗi thường gặp thực tế

Thông báo lỗi validate (VD: "Trường này là bắt buộc") được hard-code cứng trong code thay vì lấy từ file resource ngôn ngữ, nên khi chuyển sang tiếng Anh, các nhãn tĩnh đã dịch nhưng riêng thông báo lỗi vẫn hiển thị tiếng Việt.

## F2. Khả năng mở rộng ngôn ngữ (Language Extensibility)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A55:I55`, `4. Detailed Guidance!A55:J55`

### Nội dung yêu cầu

Có thể bổ sung ngôn ngữ mới thông qua file resource/ngôn ngữ mà không cần chỉnh sửa mã nguồn.

### Tiêu chí đánh giá (Đạt)

1\. Thêm 1 ngôn ngữ mới thực hiện được qua cấu hình/resource file.\
2\. Không phát sinh lỗi hoặc cần build lại toàn hệ thống.

### Giải thích (ngôn ngữ đơn giản)

Kiến trúc hệ thống phải cho phép bổ sung một ngôn ngữ mới chỉ bằng cách thêm file resource/ngôn ngữ, không cần sửa mã nguồn hay build lại toàn hệ thống.

### Cách kiểm tra (từng bước)

1\. Yêu cầu đội kỹ thuật thử thêm 1 ngôn ngữ mới (VD: tiếng Nhật/Hàn nếu chưa hỗ trợ) chỉ qua thao tác cấu hình/resource file.\
2\. Quan sát có cần chỉnh sửa mã nguồn hoặc build/deploy lại toàn hệ thống không.\
3\. Kiểm tra ngôn ngữ mới hiển thị đúng, không gây lỗi ở các màn hình khác.

### Bằng chứng cần thu thập

Biên bản/video thao tác thêm ngôn ngữ mới; ảnh chụp kết quả hiển thị.

### Điều kiện ĐẠT

Thêm ngôn ngữ mới thực hiện được qua cấu hình/resource file, không cần build lại toàn hệ thống, không phát sinh lỗi.

### Điều kiện KHÔNG ĐẠT

Việc thêm ngôn ngữ mới đòi hỏi sửa mã nguồn hoặc build/deploy lại toàn hệ thống, hoặc gây lỗi ở màn hình khác.

### Ví dụ lỗi thường gặp thực tế

Cấu trúc code hard-code danh sách ngôn ngữ hỗ trợ trong 1 mảng cố định (enum) ở nhiều nơi trong mã nguồn, nên thêm ngôn ngữ mới đòi hỏi sửa code ở nhiều module khác nhau thay vì chỉ thêm 1 file resource.

## F3. Định dạng theo vùng miền (Locale-specific Formatting)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A56:I56`, `4. Detailed Guidance!A56:J56`

### Nội dung yêu cầu

Định dạng ngày tháng, số, đơn vị tiền tệ hiển thị đúng theo ngôn ngữ/vùng miền đã chọn.

### Tiêu chí đánh giá (Đạt)

100% màn hình hiển thị đúng định dạng locale tương ứng khi đổi ngôn ngữ (VD: dd/mm/yyyy so với mm/dd/yyyy, dấu phân cách hàng nghìn/thập phân).

### Giải thích (ngôn ngữ đơn giản)

Định dạng ngày tháng, số, đơn vị tiền tệ phải thay đổi đúng theo ngôn ngữ/vùng miền được chọn (VD: dd/mm/yyyy khi chọn Việt Nam, mm/dd/yyyy khi chọn Mỹ).

### Cách kiểm tra (từng bước)

1\. Chuyển đổi qua từng ngôn ngữ/locale được hỗ trợ.\
2\. Kiểm tra định dạng ngày tháng, dấu phân cách hàng nghìn/thập phân trên các màn hình nhập liệu, báo cáo, biểu đồ.\
3\. Thử nhập ngày tháng theo định dạng của locale hiện tại, kiểm tra hệ thống hiểu đúng giá trị (không nhầm ngày/tháng).

### Bằng chứng cần thu thập

Ảnh chụp màn hình định dạng ngày/số theo từng locale; kết quả test nhập liệu ngày tháng.

### Điều kiện ĐẠT

100% màn hình hiển thị đúng định dạng locale tương ứng khi đổi ngôn ngữ.

### Điều kiện KHÔNG ĐẠT

Có ≥1 màn hình vẫn giữ định dạng cũ khi đã đổi locale, gây nguy cơ hiểu nhầm ngày/tháng (VD: 03/04 hiểu nhầm giữa 3-tháng-4 và tháng-3-ngày-4).

### Ví dụ lỗi thường gặp thực tế

Trường nhập ngày trên form nhập liệu vẫn cố định định dạng dd/mm/yyyy dù đã chuyển ngôn ngữ sang tiếng Anh (locale Mỹ thường dùng mm/dd/yyyy), khiến người dùng nước ngoài nhập nhầm ngày/tháng mà hệ thống vẫn chấp nhận vì cả 2 giá trị đều hợp lệ về mặt số học.

## F4. Chuyển đổi ngôn ngữ không mất dữ liệu (Seamless Language Switching)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A57:I57`, `4. Detailed Guidance!A57:J57`

### Nội dung yêu cầu

Người dùng có thể chuyển đổi ngôn ngữ giao diện trong khi sử dụng mà không bị mất phiên làm việc hoặc dữ liệu đang nhập.

### Tiêu chí đánh giá (Đạt)

1\. Chuyển ngôn ngữ không làm mất dữ liệu đang thao tác, không yêu cầu đăng nhập lại.\
2\. Lựa chọn ngôn ngữ được lưu theo tài khoản người dùng.

### Giải thích (ngôn ngữ đơn giản)

Người dùng phải có thể đổi ngôn ngữ giao diện ngay trong lúc đang thao tác mà không bị mất dữ liệu đang nhập dở hoặc phải đăng nhập lại; lựa chọn ngôn ngữ nên được ghi nhớ theo tài khoản.

### Cách kiểm tra (từng bước)

1\. Đang nhập dở dữ liệu vào 1 form, thử đổi ngôn ngữ giao diện.\
2\. Kiểm tra dữ liệu đang nhập có bị mất không, có cần đăng nhập lại không.\
3\. Đăng xuất và đăng nhập lại (hoặc đăng nhập trên thiết bị khác cùng tài khoản), kiểm tra ngôn ngữ đã chọn trước đó có được ghi nhớ không.

### Bằng chứng cần thu thập

Kết quả test đổi ngôn ngữ giữa lúc nhập liệu; kết quả test ghi nhớ ngôn ngữ theo tài khoản qua các phiên đăng nhập.

### Điều kiện ĐẠT

1\. Đổi ngôn ngữ không làm mất dữ liệu đang thao tác, không yêu cầu đăng nhập lại.\
2\. Ngôn ngữ được lưu theo tài khoản người dùng.

### Điều kiện KHÔNG ĐẠT

Đổi ngôn ngữ làm mất dữ liệu đang nhập hoặc buộc đăng xuất, hoặc lựa chọn ngôn ngữ không được ghi nhớ ở lần đăng nhập sau.

### Ví dụ lỗi thường gặp thực tế

Thao tác đổi ngôn ngữ kích hoạt reload toàn trang (full page refresh) thay vì chỉ cập nhật nhãn hiển thị động, khiến dữ liệu đang nhập dở trên form bị mất trắng.

## F5. Tài liệu trợ giúp trực tuyến (Online Help / User Guide)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A58:I58`, `4. Detailed Guidance!A58:J58`

### Nội dung yêu cầu

Hệ thống cung cấp tài liệu/trợ giúp trực tuyến (help) hướng dẫn sử dụng cho từng chức năng chính.

### Tiêu chí đánh giá (Đạt)

1\. 100% chức năng chính có mục Help tương ứng, truy cập được từ giao diện (icon Help, tooltip, phím F1...).\
2\. Nội dung help đầy đủ, chính xác theo phiên bản hiện hành.

### Giải thích (ngôn ngữ đơn giản)

Mỗi chức năng chính phải có mục trợ giúp (help) truy cập được ngay trong hệ thống, hướng dẫn cách sử dụng, không bắt người dùng phải hỏi đồng nghiệp hoặc tìm tài liệu ở nơi khác.

### Cách kiểm tra (từng bước)

1\. Lập danh sách các chức năng chính trong phạm vi đánh giá.\
2\. Với mỗi chức năng, kiểm tra có mục Help truy cập được (icon Help, tooltip, phím tắt F1...) không.\
3\. Đọc nội dung help, đối chiếu có mô tả đúng, đầy đủ theo phiên bản phần mềm hiện hành không.

### Bằng chứng cần thu thập

Danh sách chức năng chính đối chiếu có/không có Help tương ứng; ảnh chụp nội dung help của một số chức năng mẫu.

### Điều kiện ĐẠT

100% chức năng chính có mục Help tương ứng, truy cập được từ giao diện, nội dung đầy đủ và chính xác theo phiên bản hiện hành.

### Điều kiện KHÔNG ĐẠT

Có ≥1 chức năng chính không có Help, hoặc nội dung Help lỗi thời không khớp phiên bản hiện hành.

### Ví dụ lỗi thường gặp thực tế

Chức năng mới thêm ở phiên bản gần nhất chưa được bổ sung nội dung Help tương ứng do quy trình phát triển không bắt buộc cập nhật tài liệu song song với code.

## F6. Trợ giúp theo ngữ cảnh (Context-sensitive Help)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A59:I59`, `4. Detailed Guidance!A59:J59`

### Nội dung yêu cầu

Người dùng có thể truy cập trợ giúp phù hợp với đúng màn hình/chức năng đang thao tác, không chỉ trang help chung chung.

### Tiêu chí đánh giá (Đạt)

Khi nhấn Help/F1 tại một màn hình bất kỳ, hệ thống hiển thị đúng nội dung trợ giúp tương ứng với màn hình/chức năng đó.

### Giải thích (ngôn ngữ đơn giản)

Khi người dùng nhấn Help/F1 ngay tại một màn hình cụ thể, hệ thống phải đưa họ đến đúng nội dung trợ giúp liên quan đến màn hình/chức năng đó, thay vì đưa về trang help chung chung phải tự tìm.

### Cách kiểm tra (từng bước)

1\. Chọn một số màn hình chức năng khác nhau, nhấn Help/F1 tại từng màn hình.\
2\. Kiểm tra nội dung help hiển thị có đúng khớp với màn hình/chức năng đang thao tác không.

### Bằng chứng cần thu thập

Ảnh chụp kết quả nhấn Help tại từng màn hình test, đối chiếu nội dung hiển thị.

### Điều kiện ĐẠT

Khi nhấn Help/F1 tại bất kỳ màn hình nào trong phạm vi test, hệ thống hiển thị đúng nội dung tương ứng với màn hình/chức năng đó.

### Điều kiện KHÔNG ĐẠT

Có ≥1 màn hình nhấn Help nhưng đưa về trang help chung chung hoặc sai chức năng.

### Ví dụ lỗi thường gặp thực tế

Nút Help trên tất cả màn hình đều trỏ về cùng 1 trang mục lục help tổng, người dùng phải tự tìm đúng phần liên quan thay vì được đưa thẳng vào đúng mục.

## F7. Câu hỏi thường gặp & xử lý lỗi (FAQ & Troubleshooting Guide)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A60:I60`, `4. Detailed Guidance!A60:J60`

### Nội dung yêu cầu

Có tài liệu FAQ và hướng dẫn xử lý các lỗi/thông báo thường gặp trong quá trình sử dụng.

### Tiêu chí đánh giá (Đạt)

Tài liệu FAQ/Troubleshooting bao phủ tối thiểu các lỗi, thông báo phổ biến được ghi nhận qua kênh hỗ trợ (help desk/ticket) của kỳ đánh giá gần nhất.

### Giải thích (ngôn ngữ đơn giản)

Cần có tài liệu FAQ/hướng dẫn xử lý lỗi bao phủ các vấn đề người dùng thực tế gặp phải, giúp họ tự xử lý các tình huống phổ biến mà không cần liên hệ hỗ trợ mỗi lần.

### Cách kiểm tra (từng bước)

1\. Lấy danh sách lỗi/thông báo phổ biến được ghi nhận qua kênh hỗ trợ (help desk/ticket) trong kỳ đánh giá gần nhất.\
2\. Đối chiếu với tài liệu FAQ/Troubleshooting hiện có, kiểm tra các vấn đề phổ biến này có được bao phủ không.\
3\. Đánh giá nội dung hướng dẫn xử lý có đủ chi tiết để người dùng tự làm theo được không.

### Bằng chứng cần thu thập

Danh sách lỗi/ticket phổ biến trong kỳ; tài liệu FAQ/Troubleshooting đối chiếu độ bao phủ.

### Điều kiện ĐẠT

Tài liệu FAQ/Troubleshooting bao phủ tối thiểu các lỗi/thông báo phổ biến được ghi nhận qua kênh hỗ trợ của kỳ đánh giá gần nhất.

### Điều kiện KHÔNG ĐẠT

Các vấn đề lặp lại nhiều lần qua kênh hỗ trợ nhưng không được đưa vào tài liệu FAQ, khiến người dùng và bộ phận hỗ trợ phải xử lý lại từ đầu mỗi lần.

### Ví dụ lỗi thường gặp thực tế

Lỗi "không đăng nhập được sau khi đổi mật khẩu" là ticket phổ biến nhất trong 3 tháng liên tiếp nhưng chưa từng được cập nhật vào FAQ, đội hỗ trợ vẫn phải trả lời thủ công lặp lại cùng 1 câu trả lời cho từng người dùng.

## F8. Kênh hỗ trợ & liên hệ (Support Contact Channel)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A61:I61`, `4. Detailed Guidance!A61:J61`

### Nội dung yêu cầu

Hệ thống cung cấp thông tin kênh liên hệ hỗ trợ (email, hotline, ticket...) khi người dùng cần trợ giúp thêm ngoài tài liệu help.

### Tiêu chí đánh giá (Đạt)

1\. Thông tin liên hệ hỗ trợ hiển thị rõ ràng trong hệ thống và/hoặc tài liệu đi kèm.\
2\. Có SLA thời gian phản hồi hỗ trợ được công bố và tuân thủ.

### Giải thích (ngôn ngữ đơn giản)

Người dùng cần biết cách liên hệ hỗ trợ (email, hotline, ticket) khi tài liệu help không đủ giải quyết vấn đề của họ, kèm cam kết thời gian phản hồi rõ ràng.

### Cách kiểm tra (từng bước)

1\. Kiểm tra thông tin kênh liên hệ hỗ trợ có hiển thị rõ ràng trong hệ thống/tài liệu đi kèm không.\
2\. Rà soát SLA thời gian phản hồi hỗ trợ đã công bố.\
3\. Kiểm tra thực tế lịch sử phản hồi các yêu cầu hỗ trợ gần nhất có tuân thủ SLA đã công bố không.

### Bằng chứng cần thu thập

Ảnh chụp thông tin kênh liên hệ; tài liệu SLA hỗ trợ; số liệu thời gian phản hồi thực tế của các ticket gần nhất.

### Điều kiện ĐẠT

1\. Thông tin liên hệ hỗ trợ hiển thị rõ ràng.\
2\. Có SLA thời gian phản hồi được công bố và tuân thủ trong thực tế.

### Điều kiện KHÔNG ĐẠT

Không có thông tin liên hệ hỗ trợ rõ ràng trong hệ thống, hoặc SLA phản hồi không được tuân thủ trong thực tế.

### Ví dụ lỗi thường gặp thực tế

Thông tin liên hệ hỗ trợ chỉ có trong tài liệu bàn giao dự án ban đầu (không cập nhật khi đổi nhân sự phụ trách), người dùng liên hệ theo thông tin cũ nhưng không ai phản hồi.

## F9. Đa ngôn ngữ cho tài liệu trợ giúp (Help Localization)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A62:I62`, `4. Detailed Guidance!A62:J62`

### Nội dung yêu cầu

Nội dung trợ giúp (help) được cung cấp theo đúng ngôn ngữ đang được chọn trên giao diện.

### Tiêu chí đánh giá (Đạt)

100% ngôn ngữ được hệ thống hỗ trợ (theo Mục M) có tài liệu Help tương ứng đầy đủ, không thiếu hoặc lệch ngôn ngữ so với giao diện.

### Giải thích (ngôn ngữ đơn giản)

Nội dung trợ giúp (help) phải có đầy đủ cho mọi ngôn ngữ mà hệ thống hỗ trợ, khớp với ngôn ngữ đang chọn trên giao diện, không chỉ có bản tiếng Việt hoặc tiếng Anh riêng lẻ.

### Cách kiểm tra (từng bước)

1\. Chuyển ngôn ngữ giao diện lần lượt qua từng ngôn ngữ được hỗ trợ (theo mục F1).\
2\. Với mỗi ngôn ngữ, mở tài liệu Help tương ứng, kiểm tra có đầy đủ nội dung không.\
3\. Đối chiếu nội dung help giữa các ngôn ngữ có tương đương về mức độ chi tiết không (không có ngôn ngữ nào bị rút gọn/lược bớt).

### Bằng chứng cần thu thập

Ảnh chụp nội dung Help theo từng ngôn ngữ; bảng đối chiếu mức độ đầy đủ giữa các ngôn ngữ.

### Điều kiện ĐẠT

100% ngôn ngữ được hệ thống hỗ trợ có tài liệu Help tương ứng đầy đủ, không thiếu/lệch so với giao diện.

### Điều kiện KHÔNG ĐẠT

Có ≥1 ngôn ngữ hỗ trợ trên giao diện nhưng tài liệu Help chưa dịch đầy đủ hoặc thiếu hẳn.

### Ví dụ lỗi thường gặp thực tế

Giao diện hỗ trợ đầy đủ tiếng Anh, nhưng toàn bộ tài liệu Help chỉ có bản tiếng Việt — người dùng nước ngoài chọn giao diện tiếng Anh vẫn phải đọc help bằng tiếng Việt.

## F10. Cập nhật tài liệu trợ giúp theo phiên bản (Help Version Synchronization)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Ảnh chụp giao diện đa ngôn ngữ + file resource ngôn ngữ
- **Nguồn:** `3. Assessment Checklist!A63:I63`, `4. Detailed Guidance!A63:J63`

### Nội dung yêu cầu

Nội dung Help được cập nhật đồng bộ khi phần mềm thay đổi chức năng theo phiên bản mới.

### Tiêu chí đánh giá (Đạt)

1\. 100% thay đổi chức năng ảnh hưởng đến người dùng được phản ánh trong tài liệu Help trước hoặc ngay khi phát hành phiên bản tương ứng.\
2\. Số phiên bản tài liệu Help khớp với phiên bản phần mềm.

### Giải thích (ngôn ngữ đơn giản)

Khi phần mềm thay đổi chức năng ở phiên bản mới, tài liệu Help phải được cập nhật đồng bộ trước hoặc ngay khi phát hành, tránh tình trạng hướng dẫn không còn khớp với giao diện thực tế.

### Cách kiểm tra (từng bước)

1\. Rà soát changelog/release note của các phiên bản gần nhất, xác định các thay đổi chức năng ảnh hưởng đến người dùng.\
2\. Đối chiếu nội dung Help hiện tại có phản ánh đúng các thay đổi đó không.\
3\. Kiểm tra số phiên bản ghi trên tài liệu Help có khớp với phiên bản phần mềm hiện hành không.

### Bằng chứng cần thu thập

Changelog/release note đối chiếu với nội dung Help; số phiên bản tài liệu Help vs. phần mềm.

### Điều kiện ĐẠT

1\. 100% thay đổi chức năng ảnh hưởng người dùng được phản ánh trong Help trước hoặc ngay khi phát hành.\
2\. Số phiên bản Help khớp phần mềm.

### Điều kiện KHÔNG ĐẠT

Có thay đổi chức năng đã phát hành nhưng Help chưa cập nhật, hoặc số phiên bản Help không khớp phần mềm hiện hành.

### Ví dụ lỗi thường gặp thực tế

Chức năng phê duyệt được đổi từ 1 bước thành 2 bước (thêm bước duyệt cấp 2) ở phiên bản mới, nhưng tài liệu Help vẫn mô tả quy trình 1 bước cũ, khiến người dùng bối rối khi làm theo hướng dẫn không còn đúng.
