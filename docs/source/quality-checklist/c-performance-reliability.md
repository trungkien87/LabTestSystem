# C. HIỆU NĂNG & ĐỘ TIN CẬY

_(Performance Efficiency & Reliability)_

> Nguồn: `Software-Quality-Assessment-Checklist_EN_Rev04_20260803.xlsx` (Rev04, ban hành 2026-08-03), nhận ngày 2026-10-27. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Ô kết quả đánh giá trong file gốc đang để trống.

Mỗi tiêu chí gộp dữ liệu từ sheet `3. Assessment Checklist` (dòng ghi ở mục Nguồn) và sheet `4. Detailed Guidance` (cùng Mã).

## C1. Thời gian phản hồi (Response Time)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử hiệu năng/tải (load, stress, soak test)
- **Nguồn:** `3. Assessment Checklist!A15:I15`, `4. Detailed Guidance!A15:J15`

### Nội dung yêu cầu

Thời gian xử lý và phản hồi của hệ thống nằm trong ngưỡng chấp nhận.

### Tiêu chí đánh giá (Đạt)

1\. Response time trang/chức năng chính ≤ 3 giây (hoặc theo SLA).\
2\. ≤ hệ thống hiện hành nếu là nâng cấp.

### Giải thích (ngôn ngữ đơn giản)

Người dùng thao tác trên hệ thống (mở màn hình, submit form, chạy báo cáo) phải nhận được phản hồi trong thời gian chấp nhận được, không gây cảm giác "đứng máy" hay chờ đợi quá lâu làm gián đoạn dây chuyền sản xuất.

### Cách kiểm tra (từng bước)

1\. Xác định danh sách màn hình/chức năng chính (theo tần suất sử dụng cao) cần đo response time.\
2\. Dùng công cụ đo hiệu năng (VD: JMeter, Postman, browser dev tools) đo thời gian phản hồi thực tế ở điều kiện tải bình thường và tải cao điểm.\
3\. So sánh với ngưỡng SLA đã công bố (hoặc với hệ thống hiện hành nếu là dự án nâng cấp).\
4\. Lặp lại phép đo ở nhiều thời điểm trong ngày để loại trừ yếu tố ngẫu nhiên.

### Bằng chứng cần thu thập

Báo cáo đo response time (kèm công cụ, điều kiện tải, thời điểm đo); biểu đồ so sánh với ngưỡng SLA.

### Điều kiện ĐẠT

1\. Response time của các chức năng chính ≤ 3 giây (hoặc theo SLA đã thống nhất).\
2\. Không tệ hơn hệ thống hiện hành nếu là dự án nâng cấp.

### Điều kiện KHÔNG ĐẠT

Có ≥1 chức năng chính vượt ngưỡng SLA ở điều kiện tải bình thường, hoặc suy giảm đáng kể so với hệ thống cũ.

### Ví dụ lỗi thường gặp thực tế

Đo response time chỉ ở môi trường UAT với dữ liệu mẫu nhỏ, không phản ánh đúng thực tế khi database Production có hàng triệu bản ghi — dẫn đến câu truy vấn chậm hẳn khi go-live dù test trước đó đạt.

## C2. Khả năng chịu tải (Load & Stress Testing)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử hiệu năng/tải (load, stress, soak test)
- **Nguồn:** `3. Assessment Checklist!A16:I16`, `4. Detailed Guidance!A16:J16`

### Nội dung yêu cầu

Hệ thống hoạt động ổn định khi có nhiều người dùng/giao dịch truy cập đồng thời.

### Tiêu chí đánh giá (Đạt)

Đạt tải thiết kế (VD: X user đồng thời) với tỷ lệ lỗi < 1%, không giảm hiệu năng nghiêm trọng.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống phải hoạt động ổn định khi có nhiều người dùng/giao dịch truy cập đồng thời, đúng như tải thiết kế đã cam kết (VD: số ca sản xuất, số trạm truy cập cùng lúc).

### Cách kiểm tra (từng bước)

1\. Xác định tải thiết kế mục tiêu (số user đồng thời, số giao dịch/giây) theo yêu cầu dự án.\
2\. Chạy load test với tải bằng mức thiết kế, sau đó stress test tăng dần đến khi hệ thống có dấu hiệu quá tải.\
3\. Ghi nhận tỷ lệ lỗi (error rate), thời gian phản hồi tại mỗi mức tải, và hành vi hệ thống khi vượt ngưỡng (báo lỗi có kiểm soát hay crash).

### Bằng chứng cần thu thập

Báo cáo load/stress test đầy đủ (công cụ, kịch bản, số liệu error rate và response time theo từng mức tải).

### Điều kiện ĐẠT

1\. Đạt tải thiết kế với tỷ lệ lỗi < 1%, response time không suy giảm nghiêm trọng.\
2\. Khi vượt ngưỡng, hệ thống báo lỗi/giảm tải có kiểm soát thay vì crash toàn bộ.

### Điều kiện KHÔNG ĐẠT

Không đạt tải thiết kế (tỷ lệ lỗi ≥ 1% hoặc response time suy giảm nghiêm trọng), hoặc hệ thống crash khi đạt đúng tải thiết kế.

### Ví dụ lỗi thường gặp thực tế

Load test chỉ mô phỏng người dùng gọi cùng 1 API đơn giản lặp lại, không mô phỏng đúng kịch bản nghiệp vụ thực tế (nhiều loại giao dịch chạy song song), khiến kết quả test đẹp nhưng hệ thống vẫn nghẽn khi vận hành thật.

## C3. Sử dụng tài nguyên hệ thống (Resource Utilization)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Báo cáo kiểm thử hiệu năng/tải (load, stress, soak test)
- **Nguồn:** `3. Assessment Checklist!A17:I17`, `4. Detailed Guidance!A17:J17`

### Nội dung yêu cầu

Mức sử dụng CPU, RAM, băng thông, dung lượng DB trong ngưỡng an toàn khi vận hành.

### Tiêu chí đánh giá (Đạt)

1\. CPU/RAM trung bình ≤ 70–80% ở tải cao điểm.\
2\. Không phát sinh memory leak khi chạy dài hạn (soak test).

### Giải thích (ngôn ngữ đơn giản)

Mức tiêu thụ CPU, RAM, băng thông mạng, dung lượng database khi vận hành phải nằm trong ngưỡng an toàn, không sát giới hạn gây rủi ro khi tải tăng đột biến.

### Cách kiểm tra (từng bước)

1\. Giám sát CPU/RAM/network/disk trong suốt quá trình load test và soak test (chạy liên tục dài hạn, VD: 24–72 giờ).\
2\. So sánh mức sử dụng tài nguyên tại tải cao điểm với ngưỡng an toàn đã quy định.\
3\. Theo dõi xu hướng tăng dần của RAM theo thời gian để phát hiện rò rỉ bộ nhớ (memory leak).

### Bằng chứng cần thu thập

Biểu đồ giám sát tài nguyên (CPU/RAM/network) trong suốt thời gian test; kết luận về memory leak (nếu có).

### Điều kiện ĐẠT

1\. CPU/RAM trung bình ≤ 70–80% ở tải cao điểm.\
2\. Không có xu hướng tăng dần bất thường của RAM trong soak test (không memory leak).

### Điều kiện KHÔNG ĐẠT

Tài nguyên vượt ngưỡng an toàn ở tải cao điểm, hoặc phát hiện RAM tăng dần liên tục không giải phóng trong soak test.

### Ví dụ lỗi thường gặp thực tế

Chỉ chạy soak test trong 1–2 giờ nên không kịp phát hiện memory leak vốn chỉ lộ rõ sau 24–48 giờ vận hành liên tục — hệ thống chạy êm lúc nghiệm thu nhưng dần chậm và phải restart định kỳ khi go-live.

## C4. Khả năng mở rộng (Scalability)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Báo cáo kiểm thử hiệu năng/tải (load, stress, soak test)
- **Nguồn:** `3. Assessment Checklist!A18:I18`, `4. Detailed Guidance!A18:J18`

### Nội dung yêu cầu

Hệ thống có khả năng mở rộng để đáp ứng tăng trưởng dữ liệu/người dùng trong tương lai.

### Tiêu chí đánh giá (Đạt)

1\. Kiến trúc hỗ trợ scale-up/scale-out.\
2\. Kiểm chứng qua test tăng tải theo lộ trình dự kiến (VD: +50% user).

### Giải thích (ngôn ngữ đơn giản)

Kiến trúc hệ thống phải có khả năng mở rộng (thêm server, thêm tài nguyên) để đáp ứng tăng trưởng số người dùng/dữ liệu trong tương lai mà không cần thiết kế lại từ đầu.

### Cách kiểm tra (từng bước)

1\. Rà soát tài liệu kiến trúc, xác nhận có hỗ trợ scale-up (tăng cấu hình máy) và/hoặc scale-out (thêm node/instance).\
2\. Thực hiện test tăng tải theo lộ trình tăng trưởng dự kiến (VD: +50% số user) và quan sát hệ thống có đáp ứng được khi tăng thêm tài nguyên tương ứng không.\
3\. Kiểm tra các điểm nghẽn tiềm ẩn (single point of bottleneck) như database không thể scale-out, license giới hạn số connection...

### Bằng chứng cần thu thập

Tài liệu kiến trúc mô tả khả năng mở rộng; báo cáo test tăng tải theo kịch bản tăng trưởng.

### Điều kiện ĐẠT

Kiến trúc hỗ trợ scale-up/scale-out được kiểm chứng qua test thực tế đạt mức tăng tải dự kiến mà không cần thiết kế lại.

### Điều kiện KHÔNG ĐẠT

Không kiểm chứng được khả năng mở rộng, hoặc phát hiện điểm nghẽn kiến trúc (VD: database đơn instance không thể scale) cản trở tăng trưởng theo lộ trình đã cam kết.

### Ví dụ lỗi thường gặp thực tế

Ứng dụng có thể scale-out nhiều instance nhưng toàn bộ session lưu tại local memory (không dùng session store tập trung), nên khi thêm server mới, người dùng bị đăng xuất ngẫu nhiên do load balancer định tuyến sang instance khác.

## C5. Độ ổn định vận hành (Stability / Uptime)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử hiệu năng/tải (load, stress, soak test)
- **Nguồn:** `3. Assessment Checklist!A19:I19`, `4. Detailed Guidance!A19:J19`

### Nội dung yêu cầu

Hệ thống vận hành liên tục, ổn định, hạn chế downtime ngoài kế hoạch.

### Tiêu chí đánh giá (Đạt)

1\. Uptime ≥ mức cam kết (VD: 99.5%).\
2\. Số lần downtime ngoài kế hoạch ≤ ngưỡng cho phép/tháng.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống phải vận hành liên tục, ổn định trong thời gian dài, hạn chế tối đa các lần gián đoạn (downtime) ngoài kế hoạch ảnh hưởng đến sản xuất.

### Cách kiểm tra (từng bước)

1\. Thu thập số liệu uptime/downtime thực tế trong kỳ đánh giá (từ hệ thống giám sát/monitoring tool).\
2\. Phân loại downtime: có kế hoạch (bảo trì đã thông báo) và ngoài kế hoạch (sự cố).\
3\. Đối chiếu tỷ lệ uptime thực tế với mức cam kết trong SLA.

### Bằng chứng cần thu thập

Báo cáo uptime/downtime từ công cụ giám sát trong kỳ đánh giá; danh sách sự cố downtime ngoài kế hoạch kèm nguyên nhân.

### Điều kiện ĐẠT

1\. Uptime thực tế ≥ mức cam kết (VD: 99.5%).\
2\. Số lần downtime ngoài kế hoạch không vượt ngưỡng cho phép/tháng.

### Điều kiện KHÔNG ĐẠT

Uptime thực tế dưới mức cam kết, hoặc downtime ngoài kế hoạch xảy ra thường xuyên hơn ngưỡng cho phép.

### Ví dụ lỗi thường gặp thực tế

Downtime do lỗi định kỳ (VD: job dọn dẹp dữ liệu chạy giờ hành chính gây treo hệ thống) tái diễn nhiều lần nhưng không được xếp vào nhóm "sự cố cần khắc phục gốc rễ" mà chỉ xử lý tạm bằng cách restart thủ công mỗi lần xảy ra.

## C6. Khả năng chịu lỗi (Fault Tolerance)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử hiệu năng/tải (load, stress, soak test)
- **Nguồn:** `3. Assessment Checklist!A20:I20`, `4. Detailed Guidance!A20:J20`

### Nội dung yêu cầu

Hệ thống tiếp tục hoạt động hoặc suy giảm có kiểm soát (graceful degradation) khi một thành phần gặp lỗi.

### Tiêu chí đánh giá (Đạt)

Test giả lập lỗi (kill service, ngắt kết nối DB...): hệ thống không mất dữ liệu, tự phục hồi hoặc chuyển dự phòng.

### Giải thích (ngôn ngữ đơn giản)

Khi một thành phần của hệ thống gặp sự cố (service con bị crash, mất kết nối DB, mất 1 node trong cluster), toàn hệ thống không được sụp đổ hoàn toàn mà nên tiếp tục hoạt động ở mức suy giảm có kiểm soát (graceful degradation) hoặc tự động chuyển sang thành phần dự phòng.

### Cách kiểm tra (từng bước)

1\. Lập danh sách kịch bản giả lập lỗi: kill 1 service/tiến trình, ngắt kết nối DB, ngắt 1 node trong cluster (nếu có).\
2\. Thực hiện từng kịch bản trên môi trường test/staging (không thực hiện trực tiếp trên Production trừ khi có kế hoạch DR diễn tập).\
3\. Quan sát: hệ thống có mất dữ liệu không, có tự phục hồi/chuyển dự phòng (failover) không, thời gian gián đoạn là bao lâu.

### Bằng chứng cần thu thập

Kịch bản test giả lập lỗi; kết quả quan sát (video/log) từng kịch bản kèm thời gian gián đoạn thực tế.

### Điều kiện ĐẠT

Với mọi kịch bản test, hệ thống không mất dữ liệu và tự phục hồi hoặc chuyển dự phòng trong thời gian chấp nhận được.

### Điều kiện KHÔNG ĐẠT

Có ≥1 kịch bản gây mất dữ liệu, hoặc hệ thống không thể tự phục hồi/chuyển dự phòng mà cần can thiệp thủ công kéo dài ngoài ngưỡng chấp nhận.

### Ví dụ lỗi thường gặp thực tế

Hệ thống có cấu hình cluster 2 node tưởng là dự phòng, nhưng khi test thực tế ngắt 1 node thì node còn lại không tự động nhận traffic (do thiếu cấu hình health-check/failover đúng), toàn hệ thống vẫn downtime dù có "dự phòng" trên giấy tờ.

## C7. Khả năng khôi phục sau sự cố (Recoverability)

- **Mức độ:** Bắt buộc
- **Loại bằng chứng:** Báo cáo kiểm thử hiệu năng/tải (load, stress, soak test)
- **Nguồn:** `3. Assessment Checklist!A21:I21`, `4. Detailed Guidance!A21:J21`

### Nội dung yêu cầu

Hệ thống có khả năng khôi phục nhanh chóng sau sự cố nghiêm trọng.

### Tiêu chí đánh giá (Đạt)

1\. Thời gian khôi phục thực tế (RTO) ≤ mục tiêu.\
2\. Diễn tập DR (Disaster Recovery) tối thiểu 1–2 lần/năm.

### Giải thích (ngôn ngữ đơn giản)

Sau một sự cố nghiêm trọng (mất server, lỗi hệ thống diện rộng), hệ thống phải có khả năng khôi phục hoạt động trong thời gian mục tiêu đã cam kết (RTO), thông qua kế hoạch và diễn tập cụ thể (không chỉ backup dữ liệu như B5, mà là khôi phục toàn bộ hệ thống/dịch vụ).

### Cách kiểm tra (từng bước)

1\. Rà soát tài liệu kế hoạch khôi phục thảm họa (Disaster Recovery Plan) — quy trình, vai trò trách nhiệm, RTO/RPO mục tiêu.\
2\. Kiểm tra lịch sử diễn tập DR (drill) đã thực hiện trong 12 tháng gần nhất.\
3\. Nếu có thể, tham gia/quan sát 1 đợt diễn tập DR thực tế và đo thời gian khôi phục thực tế so với mục tiêu.

### Bằng chứng cần thu thập

Tài liệu DR Plan; biên bản diễn tập DR gần nhất (thời gian bắt đầu sự cố giả lập → thời gian khôi phục hoàn tất).

### Điều kiện ĐẠT

1\. Có DR Plan chính thức.\
2\. Đã diễn tập tối thiểu 1–2 lần/năm.\
3\. Thời gian khôi phục thực tế trong diễn tập ≤ RTO mục tiêu.

### Điều kiện KHÔNG ĐẠT

Không có DR Plan, hoặc chưa từng diễn tập, hoặc thời gian khôi phục thực tế vượt RTO mục tiêu.

### Ví dụ lỗi thường gặp thực tế

DR Plan được viết đầy đủ trên giấy nhưng chưa từng diễn tập thực tế — đến khi có sự cố thật, quy trình lý thuyết không khớp với thực tế hạ tầng đã thay đổi theo thời gian, khiến thời gian khôi phục thực tế gấp nhiều lần RTO cam kết.

## C8. Giám sát & cảnh báo hệ thống (Monitoring & Alarm)

- **Mức độ:** Khuyến nghị
- **Loại bằng chứng:** Báo cáo kiểm thử hiệu năng/tải (load, stress, soak test)
- **Nguồn:** `3. Assessment Checklist!A22:I22`, `4. Detailed Guidance!A22:J22`

### Nội dung yêu cầu

Hệ thống tự động giám sát và cảnh báo khi phát hiện bất thường (lỗi, quá tải, gián đoạn).

### Tiêu chí đánh giá (Đạt)

100% sự kiện bất thường được phát hiện và cảnh báo trong ≤ X phút, đúng kênh/đúng người nhận, có phân loại mức độ.

### Giải thích (ngôn ngữ đơn giản)

Hệ thống cần tự động phát hiện các dấu hiệu bất thường (lỗi, quá tải, gián đoạn dịch vụ) và gửi cảnh báo kịp thời đến đúng người, thay vì chờ người dùng cuối phản ánh mới biết có sự cố.

### Cách kiểm tra (từng bước)

1\. Rà soát danh sách sự kiện được cấu hình giám sát/cảnh báo (CPU cao, service down, disk đầy, response time chậm...).\
2\. Giả lập một số sự kiện bất thường trên môi trường test (VD: dừng 1 service, làm đầy ổ đĩa test) và đo thời gian từ lúc xảy ra đến lúc cảnh báo được gửi.\
3\. Kiểm tra cảnh báo có phân loại đúng mức độ (Warning/Critical) và gửi đúng kênh/đúng người phụ trách.

### Bằng chứng cần thu thập

Cấu hình hệ thống giám sát/alerting; kết quả test giả lập sự cố kèm thời gian nhận cảnh báo thực tế; ảnh/log tin nhắn cảnh báo nhận được.

### Điều kiện ĐẠT

100% sự kiện bất thường test đều được phát hiện và cảnh báo trong thời gian quy định, đúng kênh, đúng người nhận, đúng phân loại mức độ.

### Điều kiện KHÔNG ĐẠT

Có ≥1 sự kiện bất thường không được cảnh báo, cảnh báo trễ quá ngưỡng, hoặc gửi sai kênh/sai người nhận.

### Ví dụ lỗi thường gặp thực tế

Cảnh báo được cấu hình gửi qua email nhưng địa chỉ nhận là của nhân sự đã nghỉ việc/đổi vai trò từ lâu, không ai theo dõi hộp thư đó — hệ thống "có cảnh báo" trên cấu hình nhưng thực tế không ai nhận được khi sự cố xảy ra.
