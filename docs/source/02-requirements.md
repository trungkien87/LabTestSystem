# 02. Requirement — Danh sách chức năng

> Nguồn: sheet `02. Requirement` trong `LAB_Test_system_261013.xlsx`. Chuyển đổi tự động, giữ nguyên câu chữ gốc. Cột `Row` và tên cột (A, B, ...) là tọa độ ô trong Excel. Chữ đỏ trong Excel được đánh dấu 🔴**...**; ý nghĩa màu đỏ chưa được xác nhận.

Các cột gốc: A = Thứ tự, B = Chức năng, C = Đối tượng sử dụng, D = Requirement, E = Mục đích, F = Check point.

## 1. Cài đặt vài trò

- **Đối tượng sử dụng:** Smart Factory
- **Nguồn:** `02. Requirement!A2:F2`

### Requirement

1\. Thêm vai trò\
2\. Phân quyền cho từng vai tròn: View | Add | Edit | Delete

### Mục đích

1\. Quản lý quyền truy cập: Xác định người dùng được phép xem, thêm, sửa hoặc xóa dữ liệu.\
2\. Phân định trách nhiệm: Mỗi vai trò có quyền hạn phù hợp với nhiệm vụ được giao.\
3\. Đảm bảo tính toàn vẹn dữ liệu: Hạn chế việc chỉnh sửa hoặc xóa dữ liệu trái phép, tránh ảnh hưởng đến hoạt động của hệ thống.\
4\. Tăng cường bảo mật: Ngăn người dùng truy cập hoặc thao tác vào các chức năng không thuộc phạm vi công việc.\
5\. Dễ dàng quản lý: Khi có nhân sự mới hoặc thay đổi công việc, chỉ cần gán vai trò hoặc điều chỉnh quyền tương ứng.

## 2. Cài đặt thông tin người dùng

- **Đối tượng sử dụng:** Smart Factory
- **Nguồn:** `02. Requirement!A3:F3`

### Requirement

1\. Dữ liệu người dùng lấy từ hệ thống trainning\
2\. Thông tin: Mã nhân viên | Họ tên | Email | Phòng ban | Vai trò | Mật khẩu\
🔴**3. Cần cài đặt được role setting password, đặt được reset password, theo OPC-SF-0024 rule 6 tháng/ lần**\
🔴**2. Phân quyền tài khoản theo role**\
🔴**3. Phân quyền theo phòng ban**

### Mục đích

1\. Quản lý tập trung thông tin tài khoản người dùng.\
2\. Đảm bảo chính sách mật khẩu tuân thủ quy định OPC-SF-0024.\
3\. Kiểm soát chức năng mà từng nhóm người dùng được phép thực hiện.\
4\. Kiểm soát phạm vi dữ liệu mà người dùng được phép truy cập theo phòng ban.

## 3. Cài đặt máy chủ FPT

- **Đối tượng sử dụng:** Smart Factory
- **Nguồn:** `02. Requirement!A4:F4`

### Requirement

1\. IP Server\
2\. Port Server\
3\. User\
4\. Password\
5\. Remote Directory

### Mục đích

1\. Thiết lập máy chủ FTP để gửi logfile abnormal

## 4. Khai báo công đoạn

- **Đối tượng sử dụng:** Smart Factory
- **Nguồn:** `02. Requirement!A5:F5`

### Requirement

1\. Khai báo công đoạn (Stage):\
\- Stage code: tự sinh\
\- Stage name: tên công đoạn\
\- Sample type: Loại mẫu của công đoạn (sheet/ block/ pcs)\
\- Description: mô tả\
2\. Action: sửa, xóa, lịch sử

### Mục đích

1\. Quản lý tập trung danh sách công đoạn trên hệ thống.\
2\. Chuẩn hóa thông tin công đoạn và loại mẫu tương ứng.\
3\. Đảm bảo dữ liệu công đoạn nhất quán khi được sử dụng trong các chức năng khác.

## 5. Khai báo máy sản xuất

- **Đối tượng sử dụng:** Smart Factory
- **Nguồn:** `02. Requirement!A6:F6`

### Requirement

🔴**1. Dữ liệu được lấy từ Plus A**\
2\. Lọc: Factory, stage name\
3\. Khai báo machine\
\- Machine code: tự sinh\
\- Machine id: mã máy\
\- Machine name: tên máy\
\- Stage name: tên công đoạn\
\- Factory name: nhà máy\
\- Description: mổ tả\
4\. Action: xóa, lịch sử

### Mục đích

1\. Đồng bộ dữ liệu máy móc từ hệ thống Plus A\
2\. Quản lý thông tin máy móc theo từng nhà máy và công đoạn\
3\. Hỗ trợ tìm kiếm, tra cứu thông tin máy móc\
4\. Theo dõi lịch sử thay đổi dữ liệu nhằm đảm bảo khả năng truy xuất và quản lý dữ liệu

## 6. Khai báo Build name

- **Đối tượng sử dụng:** Smart Factory
- **Nguồn:** `02. Requirement!A7:F7`

### Requirement

🔴**1. Build name được lấy tự hệ thống Plus A**\
🔴**2. Định nghĩa build MASS/ NPI**

### Mục đích

1\. Định nghĩa và phân loại Build theo hai loại: MASS và NPI\
2\. Build giúp xác định Item code là loại MASS hay NPI

## 7. Khai báo Build + Item

- **Đối tượng sử dụng:** Smart Factory
- **Nguồn:** `02. Requirement!A8:F8`

### Requirement

1\. Đồng bộ dữ liệu từ Plus A\
2\. Lọc: Item name | Item code | Build\
3\. Hiển thị: Item name | Item code | Build | Created date

### Mục đích

1\. Đồng bộ dữ liệu Item từ hệ thống Plus A.\
2\. Hỗ trợ tìm kiếm, lọc dữ liệu theo Item name, Item code và Build.\
3\. Hiển thị thông tin Item gồm: Item name, Item code, Build và Created date để thuận tiện tra cứu, theo dõi dữ liệu.

## 8. Khai báo vị trí (location)

- **Đối tượng sử dụng:** Smart Factory
- **Nguồn:** `02. Requirement!A9:F9`

### Requirement

1\. Lọc: Factory, department\
2\. Khai báo Location\
\- Factory: lựa chọn\
\- Department: nhập thủ công\
\- Location: Tự sinh ra = Factory + Department\
\- Description\
3\. Bảng hiển thị:\
\- Location code, Factory, Department, Location name, equipment type, description\
4\. Action: sửa, xóa, lịch sử

### Mục đích

1\. Khai báo vị trí (Vị trí sử đặt thiết bị đo)\
2\. Phục vụ việc khai báo layout template cho từng vị trí đo\
3\. Quản lí layout template riêng cho từng thư mục\
4\. Phân chia nhận request cho từng khu vực

## 9. Khai báo loại thiết bị đo (Equipment type)

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A10:F10`

### Requirement

🔴**1. Bắt buộc chọn: Location (Phân quyền locaiton được chọn theo user)**\
🔴**2. Hiển thị danh sách equipment type của location được chọn**\
3\. Khai báo:\
\- Equipment type code: *\
\- Equipment type: Nhập tên loại thiết bị\
\- Location: Tự động gắn với location đã chọn\
🔴**- Định dạng xử lí logfile: Lựa chọn định dạng**\
\- Description: mô tả\
4\. Action: Sửa, xóa, lịch sử

### Mục đích

1\. Cho phép khai báo và quản lý Equipment Type theo từng Location, đảm bảo mỗi loại thiết bị được gắn đúng vị trí quản lý.\
2\. Loại thiết bị đo tương ứng với phương pháp đo theo tài liệu 080-03022-Q\
3\. Định dạng xử lí logfile:\
\- VHX: Mỗi pcs một file\
\- Laser microscope: Nhiều pcs một file\
\- Nikon: Sử dụng định dạng template\
\- VHX 5500: Nhập trực tiếp lên web

## 10. Khai báo thiết bị đo (Equipment)

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A11:F11`

### Requirement

1\. Lọc: Location, Equipment type\
2\. Khai báo Equipment\
\- Equipment ID: Nhập Equipment ID\
\- Equipment Name: Nhập equipment name\
\- Equipment type: Lựa chọn equipment type\
\- Location: Lựa chọn dựa theo equipment type\
\- Description\
3\. Action: Sửa, xóa, lịch sử

### Mục đích

1\. Quản lý danh sách thiết bị theo từng Location và Equipment type.

## 11. Khai báo Rack

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A12:F12`

### Requirement

1\. Bắt buộc lựa chọn: Location (phân quyền lựa chọn theo user), cho phéo chọn all\
2\. Khai báo Rack\
\- Rack code (Tự sinh): FF-YYY-NNNN (F1-RCK-0001)\
\+ FF: Factory\
\+ YYY: RCK (Rack)\
\+ YYYY: Number\
\- Khai báo rack name: khai báo tên rack\
\- Khai báo location: Tự động khai báo theo location đã chọn\
\- Khai báo stage được sử dụng cho rack: cho phép lựa chọn nhiều location\
\- Description: mô tả\
3\. Bảng hiển thị:\
\- Rack code\
\- Location name\
\- Stage\
\- Description\
4\. Action: Sửa, xóa, history, diagram?\
🔴**5. Sử dụng ấn vào Rack sẽ link sang để cài đặt rack layer (Để giảm bước thao tác khi chọn)**

### Mục đích

1\. Quản lý danh sách Rack theo từng Factory, Location và Stage sử dụng.\
2\. Tự động sinh Rack code theo quy tắc thống nhất, đảm bảo tính duy nhất và thuận tiện cho việc quản lý, tra cứu.\
3\. Cho phép khai báo tên Rack, Location, các Stage sử dụng và thông tin mô tả.\
4\. Hỗ trợ lọc dữ liệu theo Location, bao gồm lựa chọn tất cả các Location trong phạm vi được phân quyền của user.\
5\. Hỗ trợ chỉnh sửa, xóa và theo dõi lịch sử thay đổi thông tin Rack.\
6\. Hỗ trợ xem sơ đồ Rack (Rack Diagram) và truy cập trực tiếp chức năng cài đặt Rack Layer khi chọn Rack, giúp giảm thao tác và nâng cao hiệu quả cấu hình.

## 12. Khai báo Layer

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A13:F13`

### Requirement

1\. Hiển thị Rack vừa lựa chọn\
2\. Bắt buộc lựa chọn rack\
3\. Thêm\
🔴**- Layer name: Nhập layer name (Layer name tự sinh nếu không nhập)**\
\- Row count: Nhập số hàng\
\- Column count: Nhập số cột\
\- Description: Mô tả\
\- Active: Sử dụng hay không sử dụng\
4\. Bảng hiển thị:\
\- Layer code: "Rack code"-MM (F1-RCK-0001-01)\
\+ MM: Tầng số\
\- Layer name: Tên layer\
\- Row count: số hàng\
\- Column count: số cột\
🔴**- Qty position: ?**\
\- Description\
\- Status: Anctve/ Inactive\
5\. Xóa: Khi ấn nút xóa sẽ nhập lí do và xóa tầng lớn nhất

## 13. Khai báo position

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A14:F14`

### Requirement

🔴**1. Ấn vào Layer Name sẽ để setup position.**\
2\. Bảng hiển thị:\
\- Position code: "Layer code"-row.column (F1-RCK-0002-01-01.01)\
2\. Mặc định cài max Qty = 10, sample type = sheet\
3\. Description\
4\. Action: Sửa, history

## 14. Khai báo nội dung IPQC cho từng công đoạn

- **Đối tượng sử dụng:** PE Engineer
- **Nguồn:** `02. Requirement!A15:F15`

### Requirement

1\. Lựa chọn stage name *\
\- Giới hạn stage name theo phần quyền user\
2\. Lọc:\
\- Equipment type: Dựa theo IPQC content đã khai báo\
\- Location: Dựa theo Equipment type\
3\. Insert:\
\- IPQC Content: Nhập nội dung IPQC\
\- Equipment & location: Lựa chọn equipment type, lựa chọn location (Cho phép multiple equipment type & location)\
\- Nhập số lượng NPI & MASS (Số lượng yêu cầu đối với hàng NPI và hàng MASS)\
\- Order: Sắp xếp hiển thị nội dung (Set logic tự count cho order)\
\- SPC Rule: Tích chọn rule quản lí cho nội dung IPQC Content\
\- Description\
4\. Action: Sửa, xóa, history

### Mục đích

1\. Quản lý và khai báo nội dung kiểm tra IPQC theo từng công đoạn (Stage), phù hợp với quyền hạn của từng user.\
2\. Thiết lập loại thiết bị (Equipment Type) và khu vực đo (Location) tương ứng với từng nội dung IPQC.\
3\. Quy định số lượng mẫu kiểm tra đối với hàng NPI và MASS, đảm bảo đáp ứng yêu cầu kiểm soát chất lượng.\
4\. Sắp xếp thứ tự hiển thị nội dung IPQC, giúp chuẩn hóa trình tự kiểm tra.\
5\. Thiết lập quy tắc SPC để theo dõi, phân tích và kiểm soát chất lượng quá trình sản xuất.\
6\. Cho phép chỉnh sửa, xóa và tra cứu lịch sử thay đổi nhằm đảm bảo tính chính xác và khả năng truy xuất dữ liệu.

## 15. Khai báo layout

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A16:F16`

### Requirement

🔴**1. Lựa chọn Location: Bắt buộc lựa chọn location**\
2\. Công đoạn: Bắt buộc lựa chọn công đoạn\
3\. Loại thiết bị: Bắt buộc lựa chọn loại thiết bị\
3\. Hiển thị Layout logfile/ template cho từng loại thiết bị\
4\. Nếu muốn thêm/ sửa layout cần sử dụng nút edit

### Mục đích

1\. Quản lý layout logfile/template theo từng Location, công đoạn (Stage) và loại thiết bị (Equipment Type).\
2\. Đảm bảo người dùng lựa chọn đúng thông tin trước khi xem layout tương ứng.\
3\. Chuẩn hóa cấu trúc dữ liệu logfile/template theo từng loại thiết bị, phục vụ việc đọc và xử lý dữ liệu đo.\
4\. Cho phép thêm mới hoặc chỉnh sửa layout thông qua chức năng Edit, đảm bảo việc thay đổi được thực hiện có kiểm soát.\
5\. Hạn chế sai sót do sử dụng nhầm layout, đảm bảo tính chính xác và thống nhất của dữ liệu đo IPQC

## 16. Khai báo spec

- **Đối tượng sử dụng:** PE Engineer
- **Nguồn:** `02. Requirement!A17:F17`

### Requirement

1\. Spec theo Item name:\
\- Lựa chọn stage * (Giới hạn phân quyền)\
2\. Sau khi lựa chọn Stage:\
\- Cho phép hiển thị tất cả các Item name\
\- Gắn trạng thái Not set (Item name chưa được cài spec), Set (Item name đã được cài spec)\
3\. Thêm spec cho Item name\
\- Chọn spec dựa theo lọc\
\- Chọn Item name\
\- Nhập sequence\
\- Nhập Unit : số lượng sheet/ block/ pcs cần đem đi phòng LAB\
\- Nhập leadtime\
\- Tích chọn IPQC áp dụng cho Item name, nhập spec\
\- Khi nhập spec cho phép lọc IPQC Content, Equipment type\
🔴**4. Chuyển trạng thái "Set" Item name sau khi được set spec**\
🔴**5. Gắn link vào Item name, chọn vào Item name sẽ hiển thị list Item code**\
🔴**6. Action: Edit, delete, detail**\
\- Edit Item name thì dữ liệu edit sẽ chỉ áp dụng cho các Item "Common"

### Mục đích

1\. Quản lý và khai báo tiêu chuẩn kiểm tra (Spec) theo từng Item name và công đoạn (Stage), đảm bảo dữ liệu được quản lý đúng phạm vi phân quyền.\
2\. Theo dõi trạng thái thiết lập Spec của từng Item name (Not set / Set), giúp nhận biết các mã hàng chưa được khai báo hoặc đã hoàn thành thiết lập.\
3\. Khai báo các thông tin phục vụ kiểm tra tại phòng LAB, bao gồm Sequence, số lượng mẫu cần đo (Unit) và thời gian xử lý dự kiến (Lead time).\
4\. Thiết lập Spec cho từng nội dung IPQC, cho phép lọc theo IPQC Content và Equipment Type để xác định đúng tiêu chuẩn kiểm tra áp dụng.\
5\. Liên kết Item name với danh sách Item code tương ứng, hỗ trợ tra cứu và quản lý Spec theo từng mã hàng cụ thể.\
6\. Cho phép chỉnh sửa, xóa và xem chi tiết Spec, đảm bảo tính chính xác, nhất quán và khả năng truy xuất thông tin tiêu chuẩn kiểm tra.

## 17. Theo dõi trạng thái

- **Đối tượng sử dụng:** PR Leader
- **Nguồn:** `02. Requirement!A18:F18`

### Requirement

1\. Thanh hiển thị trạng thái:\
\- Requested: Đã request\
\- Processing: Đang xử lí\
\- Completed: Hoàn thành\
\- Delayed: Trễ hạn\
\- Cancelled: Hủy\
2\. Lọc: Request no | Stage name | Machine ID | Indication number | Item name | Item code | status | From | To\
\- Stage name: Giới hạn lựa chọn theo phân quyền user\
\- Lọc nhanh thời gian tạo request: 1 ngày, 1 tuần, 1 tháng\
3\. Bảng hiển thị\
\- Status | Judgement | Request | Judgment | Request no | Stage name | Machine ID | Indication number | Item name | Item code | Lot no | Created date | Deadline | Action (Detail)\
\- Detail: Hiển thị OP ID request | Location | Equipment type | Equipment ID | Operator ID, | Status | Error log | Judgment | Detail ( xem kết quả, đánh giá của từng nội dung)

### Mục đích

1\. Theo dõi và quản lý toàn bộ yêu cầu đo kiểm IPQC theo các trạng thái: Requested, Processing, Completed, Delayed và Cancelled.\
2\. Hỗ trợ tìm kiếm, lọc yêu cầu theo Request No, công đoạn, máy, Indication Number, Item name, Item code, trạng thái và thời gian tạo request.\
3\. Giới hạn phạm vi dữ liệu theo quyền truy cập công đoạn của từng user, đảm bảo phân quyền trong quá trình quản lý.\
4\. Theo dõi tiến độ xử lý, thời hạn hoàn thành (Deadline) và nhận diện các yêu cầu bị trễ hạn để kịp thời xử lý.\
5\. Hiển thị thông tin tổng quan về yêu cầu, kết quả và phán định chất lượng (Judgement), giúp người dùng nhanh chóng nắm bắt tình trạng kiểm tra.\
6\. Cho phép xem chi tiết từng request, bao gồm thông tin máy móc, vị trí đo, thiết bị, người thao tác, trạng thái, lỗi phát sinh và kết quả đánh giá của từng nội dung kiểm tra.\
7\. Hỗ trợ truy xuất lịch sử và kết quả đo kiểm, nâng cao khả năng kiểm soát chất lượng, theo dõi tiến độ và phối hợp giữa bộ phận sản xuất (PR) và phòng LAB.

## 18. Tạo yêu cầu đo IPQC

- **Đối tượng sử dụng:** PR Operator
- **Nguồn:** `02. Requirement!A19:F19`

### Requirement

1\. Scan/ lựa chọn mã máy (machine ID)\
2\. Tự động hiển thị machine name, stage name

### Mục đích

1\. Cho phép người dùng quét mã hoặc lựa chọn Machine ID để xác định máy cần thực hiện request đo kiểm IPQC.\
2\. Tự động hiển thị Machine Name và Stage Name tương ứng với Machine ID đã chọn, giúp giảm thao tác nhập liệu thủ công.\
3\. Đảm bảo thông tin máy móc và công đoạn được xác định chính xác, hạn chế nhầm lẫn khi tạo yêu cầu đo kiểm

## 19. Tạo yêu cầu đo IPQC

- **Đối tượng sử dụng:** PR Operator
- **Nguồn:** `02. Requirement!A20:F20`

### Requirement

1\.  Scan/ nhập Indi number\
2\. Tự động hiển thị Item name, Item code, Lot no, Build

### Mục đích

1\. Cho phép người dùng quét hoặc nhập Indication Number để xác định thông tin sản phẩm cần thực hiện đo kiểm IPQC.\
2\. Tự động hiển thị các thông tin liên quan gồm Item Name, Item Code, Lot No và Loại hàng MASS/ NPI dựa trên Indication Number đã nhập.

## 20. Lựa chọn sequence

- **Đối tượng sử dụng:** PR Operator
- **Nguồn:** `02. Requirement!A21:F21`

### Requirement

1\. Scan/ Lựa chọn sequence dựa trên dữ liệu đã khai báo\
2\. Dealine: Tự động hiển thị\
3\. Commnent: Nhập thủ công\
4\. View detai:\
\-  Side A (B), hiển thị side A B trên dưới\
\- #\
\- Equipment type\
\- IPQC Content\
\-  Spec\
\- Quantity\
\- Location\
5\. Ấn Lưu để tạo mã request

### Mục đích

1\. Cho phép người dùng quét hoặc lựa chọn Sequence từ dữ liệu đã được khai báo Spec, đảm bảo lựa chọn đúng nội dung cần đo kiểm.\
2\. Tự động hiển thị Deadline dựa trên thời gian xử lý đã thiết lập, hỗ trợ theo dõi và kiểm soát thời hạn hoàn thành request.\
3\. Cho phép nhập Comment để bổ sung thông tin hoặc yêu cầu đặc biệt liên quan đến việc đo kiểm.\
4\. Hiển thị chi tiết các nội dung cần đo kiểm theo từng Side A/B, bao gồm Equipment Type, IPQC Content, Spec, Quantity và Location, giúp người dùng xác nhận đầy đủ thông tin trước khi gửi yêu cầu.\
5\. Cho phép lưu thông tin để tạo Request No, làm cơ sở theo dõi trạng thái xử lý, kết quả đo kiểm và đánh giá chất lượng sản phẩm.

## 21. Hiển thị dữ liệu sau khi tạo request

- **Đối tượng sử dụng:** PR Operator
- **Nguồn:** `02. Requirement!A22:F22`

### Requirement

1\. Tự động tạo mã request no dựa theo định dạng "RYYMMDD_NNNN"\
\- R: Viết tắt của Request\
\- YY: Năm (26)\
\- MM: Tháng (07)\
\- DD: Ngày (10)\
\- NNNN: Số request tự động tăng (0001)\
\- Ví dụ: R260710_0001\
2\. Trạng thái sau khi tạo yêu cầu là: Requested ( Đã yêu cầu )

### Mục đích

1\. Tự động tạo mã Request No theo định dạng RYYMMDD_NNNN, đảm bảo mỗi yêu cầu đo kiểm có mã định danh riêng biệt, thống nhất và dễ tra cứu.\
2\. Tự động tăng số thứ tự request trong ngày, giúp quản lý số lượng yêu cầu và hạn chế trùng lặp mã.\
3\. Tự động thiết lập trạng thái Requested (Đã yêu cầu) sau khi tạo request thành công, giúp xác định yêu cầu đã được gửi và đang chờ xử lý.\
4\. Hỗ trợ theo dõi tiến độ, tra cứu và truy xuất thông tin yêu cầu đo kiểm trong toàn bộ quy trình IPQC/LAB.

## 22. In mã yêu cầu

- **Đối tượng sử dụng:** PR Operator
- **Nguồn:** `02. Requirement!A23:F23`

### Requirement

1\. Cho phép in nhiều request cùng lúc\
2\. In QR code:\
\- Định dạng khổ giấy A5\
3\. Hiển thị thông tin:\
\- Request No\
\- Stage\
\- Item code\
\- Lot no\
\- Created date\
\- Operator ID

## 23. Mang mẫu đo tới LAB Test

- **Đối tượng sử dụng:** PR Operator
- **Nguồn:** `02. Requirement!A24:F24`

### Requirement

1\. Dán mã request vào mẫu đo\
2\. Đem mẫu đến nơi chỉ định

## 24. Theo dõi trạng thái các request đo tại LAB Test

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A25:F25`

### Requirement

1\. Trạng thái tổng hợp (Tổng hợp all): Requested | Recived | Measuring | Completed | NG |\
2\. Lọc: Request no | Stage name | Machine ID | Item name | Item code | From | To\
3\.  Lựa chọn Uncompled, Completed\
4\.  Bảng hiển thị: # | Status | Judgment | Request no | Stage name | Machine ID | Item name | Item code | Lot no | Rack | Position | Deadline | Action: Detail\
5\. Hiển thị detail: Equipment type | Equipment ID | Operator ID | Status | Judgment | Action\
6\. Detail: IPQC Content | LL | LCL | AVG | UCL | UL | Judgment | Qty\
7\. Pcs value: No | Value

### Mục đích

1\. Tổng hợp và theo dõi trạng thái xử lý request đo kiểm IPQC/LAB, bao gồm Requested, Received, Measuring, Completed và NG, giúp nắm bắt tiến độ thực hiện và kết quả đánh giá chất lượng.\
2\. Hỗ trợ tìm kiếm, lọc request theo Request No, Stage Name, Machine ID, Item Name, Item Code và khoảng thời gian, giúp tra cứu thông tin nhanh chóng.\
3\. Cho phép phân loại yêu cầu chưa hoàn thành (Uncompleted) và đã hoàn thành (Completed), hỗ trợ quản lý công việc tồn đọng và tiến độ xử lý.\
4\. Hiển thị thông tin tổng quan của request, bao gồm trạng thái, kết quả đánh giá (Judgment), thông tin sản phẩm, Lot No, Rack, Position và Deadline, giúp kiểm soát tiến độ và vị trí lưu trữ mẫu.\
5\. Cho phép xem chi tiết thông tin đo kiểm theo thiết bị, người thao tác, trạng thái xử lý và kết quả đánh giá của từng nội dung IPQC.\
6\. Hiển thị dữ liệu thống kê đo kiểm gồm LL, LCL, AVG, UCL, UL, Judgment và Quantity, hỗ trợ đánh giá kết quả so với tiêu chuẩn kỹ thuật.\
7\. Quản lý giá trị đo của từng sản phẩm (PCS Value) theo số thứ tự và giá trị tương ứng, đảm bảo khả năng truy xuất dữ liệu, kiểm tra tính tuân thủ Spec và phân tích chất lượng sản phẩm.

## 25. Vị trí nhận mã request

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A26:F26`

### Requirement

1\. Lựa chọn location:\
\- Phân quyền theo user\
\- Mặc định khi user đăng nhập sẽ lựa chọn theo location đã được phân quyền\
\- Nếu user được phân nhiều location thì sẽ hiển thị danh sách all

### Mục đích

1\. Đảm bảo người dùng lựa chọn Location trước khi quét mã Request, giúp xác định đúng khu vực tiếp nhận và thực hiện đo kiểm IPQC/LAB\
2\. Phân quyền Location theo từng user, đảm bảo người dùng chỉ được truy cập và xử lý dữ liệu thuộc phạm vi được cấp quyền.\
3\. Tự động thiết lập Location mặc định khi đăng nhập đối với user chỉ được phân quyền một Location, giảm thao tác lựa chọn thủ công\
4\. Hiển thị danh sách tất cả Location được phân quyền đối với user có nhiều Location, cho phép lựa chọn khu vực phù hợp trước khi thực hiện công việc.\
5 Hạn chế nhầm lẫn giữa các khu vực đo kiểm, đảm bảo tính chính xác trong quá trình tiếp nhận request, quản lý thiết bị và truy xuất kết quả đo

## 26. Quét mã request

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A27:F27`

### Requirement

1\. Scan Request No\
\- Quét mã để nhận request no.\
2\. Xác nhận nhận request\
3\. Chuyển trạng thái Recived sau khi quét mã request

### Mục đích

1\. Cho phép nhân viên LAB quét QR Code để tự động nhận diện và truy xuất thông tin Request No cần tiếp nhận\
2\. Xác nhận tiếp nhận request sau khi quét mã, cập nhật trạng thái từ Requested (Đã yêu cầu) sang Received (Đã tiếp nhận)\
3\. Đảm bảo ghi nhận chính xác thời điểm và quá trình bàn giao yêu cầu từ bộ phận sản xuất (PR) đến phòng LAB\
4\. Hạn chế nhầm lẫn, bỏ sót request và hỗ trợ theo dõi tiến độ xử lý yêu cầu đo kiểm

## 27. Phân bổ request tới rack

- **Đối tượng sử dụng:** _(trống trong nguồn)_
- **Nguồn:** `02. Requirement!A28:F28`

### Requirement

1\. Hệ thống tự động xác định Rack phù hợp dựa trên Location và loại mẫu đo.\
2\. Tự động lựa chọn Position\
3\. Hiển thị thông tin Rack name: Rack No 2\
4\. Hiện thị vị trí: F5-RCK-0002-01-01.01\
5\. Nếu không tìm thấy vị trí phù hợp, thông báo không thể phân bổ và yêu cầu người dùng xử lí

### Mục đích

1\. Tự động xác định Rack phù hợp dựa trên Location và loại mẫu đo (Sheet / Block / PCS), đảm bảo mẫu được phân bổ đúng khu vực lưu trữ.\
2\. Tự động lựa chọn Position còn trống và đáp ứng điều kiện lưu trữ, giảm thao tác thủ công và hạn chế nhầm lẫn.\
3\. Hiển thị Rack Name và vị trí lưu trữ cụ thể sau khi phân bổ, giúp nhân viên LAB dễ dàng xác định và lấy mẫu khi cần.\
4\. Thông báo khi không tìm thấy Rack/Position phù hợp, yêu cầu người dùng xử lý để đảm bảo mẫu được lưu trữ đúng quy định và không bị thất lạc.

## 28. Đem mẫu tới thiết bị đo & mở phần mềm service

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A29:F29`

### Requirement

1\. Hiển thị trạng thái kết nối cơ sở dữ liệu, logfile\
\- Trạng thái kết nối phần biệt dễ dàng qua màu sắc: Xanh: Connected, Đỏ: Disconnected\
2\. Cảnh báo nếu kết nối không thành công\
3\. Hiển thị danh sách Request đang Pending theo Equipment Type được khai báo cho thiết bị.\
4\. Chỉ hiển thị các Request chưa hoàn thành đo và phù hợp với loại thiết bị\
\- Request No | Machine ID | Stage | Indication number | Item name | Deadline | Lần đo | Trạng thái\
5\. Tự động cập nhật danh sách khi có Request mới hoặc trạng thái Request thay đổi.

### Mục đích

1\. Giám sát tình trạng kết nối Database và Logfile, đảm bảo hệ thống có thể truy xuất và ghi nhận dữ liệu đo kiểm.\
2\. Phát hiện sớm sự cố kết nối, giúp người dùng kịp thời xử lý và hạn chế gián đoạn quy trình đo kiểm IPQC/LAB.\
3\. Hiển thị danh sách Request đang chờ xử lý theo Equipment Type được khai báo cho thiết bị, đảm bảo chỉ hiển thị các yêu cầu phù hợp và chưa hoàn thành đo kiểm.\
4\. Cung cấp thông tin tổng quan về số lượng request đang chờ

## 29. Quét mã request & mã nhân viên

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A30:F30`

### Requirement

1\. Thao tác:\
\- Mã yêu cầu: scan mã yêu cầu\
\- Mã nhân viên: sau khi scan mã yêu cầu\
\- Làm mới (popup xác nhận khi làm mới mà trạng thái chưa hoàn thành)\
\- Đọc tệp (Đợi có file thì đọc tệp mới sáng)

### Mục đích

1\. Cho phép scan Request No để xác định yêu cầu đo kiểm cần thực hiện, đảm bảo xử lý đúng request.\
2\. Cho phép nhập hoặc scan Operator ID sau khi scan Request No thành công, nhằm ghi nhận nhân viên chịu trách nhiệm thực hiện đo kiểm.

## 30. Tạo folder request đo tại local

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A31:F31`

### Requirement

1\. Tự động tạo folder "Temp" sau khi quét Request No tại thiết bị đo.\
vd: C:\Users\mt01450\Desktop\TEMP\
2\. Tự động tạo đường dẫn để lưu logfile (nếu có):\
cd: C:\Users\mt01450\Desktop\TEMP\BHV NBS\DK\
2\. Tải file template (nếu có)\
3\. Thông báo nếu không có quyền truy cập và tạo folder

### Mục đích

1\. Tự động chuẩn bị thư mục lưu trữ dữ liệu đo theo từng Request No, đảm bảo dữ liệu được tổ chức rõ ràng và dễ truy xuất.\
2\. Giúp nhân viên khi lưu trữ logfile không cần phải xác định vị trí của folder, cố định vị trí lưu trữ.

## 31. Tiến hành đo, xử lí dữ liệu và file báo cáo

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A32:F32`

### Requirement

1\. Tiến hành đo mẫu theo nội dung IPQC của request\
2\. Import dữ liệu vào file báo cáo:\
\- Theo đúng cấu trúc cột, hàng đã khai báo\
3\. Lưu trữ log file đúng với dữ liệu đã khải báo, folder, tên logfile

## 32. Đọc tệp

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A33:F33`

### Requirement

1\. Nút đọc tệp trên phần mềm sẽ sáng khi nhận đủ file

## 33. Đánh giá giữ liệu sau khi đọc tệp

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A34:F34`

### Requirement

1\. Đọc và kiểm tra dữ liệu đo từ logfile sau khi người dùng nhấn Đọc tệp.\
2\. Đối chiếu dữ liệu đo với Spec/IPQC criteria đã khai báo cho Request.\
3\. Tự động đánh giá kết quả đo theo giới hạn tiêu chuẩn:\
\- OK: Tất cả dữ liệu nằm trong giới hạn cho phép.\
\- NG: Có ít nhất một dữ liệu nằm ngoài giới hạn cho phép.\
\- Error: Không thể đọc dữ liệu, thiếu dữ liệu hoặc dữ liệu không đúng định dạng.\
4\. Kiểm tra tính đầy đủ của dữ liệu theo số lượng mẫu và các hạng mục đo được khai báo.\
5\. Hiển thị kết quả đánh giá và chi tiết các hạng mục NG để người dùng dễ dàng kiểm tra.\
6\. Lưu kết quả đánh giá cùng dữ liệu đo, Request No, thời gian đo và Operator ID để phục vụ truy xuất lịch sử.\
7\. Chỉ cho phép hoàn tất Request khi dữ liệu đã được đọc và đánh giá hợp lệ; trường hợp lỗi cần thông báo nguyên nhân để người dùng xử lý.\
8\. Xử lí kết quả NG và đo lại:\
\- Cho phép người dùng thực hiện đo lại khi kết quả đánh giá là NG.\
\- Khi đo lại, hệ thống ghi nhận số lần đo, thời gian đo, Operator ID và kết quả của từng lần đo.\
\- Dữ liệu và kết quả đánh giá của các lần đo trước được lưu lại để phục vụ truy xuất lịch sử.\
\- Sau khi đo lại, hệ thống tự động đọc dữ liệu và đánh giá lại theo Spec/IPQC criteria đã khai báo.\
\- Chỉ cập nhật kết quả hiện tại theo lần đo mới nhất sau khi dữ liệu được đọc và đánh giá hợp lệ; không ghi đè hoặc làm mất lịch sử các lần đo trước.

### Mục đích

1\. Tự động đánh giá dữ liệu đo sau khi đọc tệp, dựa trên Spec/IPQC criteria đã khai báo.\
2\. Đảm bảo dữ liệu đo đầy đủ, đúng định dạng và đáp ứng yêu cầu kiểm tra chất lượng.\
3\. Phát hiện kịp thời các hạng mục NG hoặc dữ liệu bất thường, giảm sai sót do đánh giá thủ công.\
4\. Lưu trữ kết quả đánh giá gắn với từng Request, phục vụ truy xuất lịch sử và theo dõi chất lượng sản phẩm.

## 34. Copy dữ liệu lên server

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A35:F35`

### Requirement

1\. Di chuyển logfile, template sau khi ấn đọc tệp\
vd:\
\- Local: ...\YYYY\YYYY-MM\YYYY-MM-DD\Request No\
vd: D:\Saomai\Local\2026\2026-Sep\2026-Sep-14\R260914_0001\
\- Server: ...\YYYY\YYYY-MM\Stage name\Item name\Item code\Item code_lot_Machine ID_Operator ID (OP Request)\Equipment Type\Datetime_Operator ID (OP Measurement)\
vd: \\10.212.5.215\ok2ship\00.Lab F1\2026\2026-Jul\RTR Copper Plating\69DRCT(25Y)\4M002301000B\4M002301000B_00068_CPRR009_00000\Crosscut & VHX\20260714_095103_01450

### Mục đích

1\. Tự động di chuyển logfile và template từ thư mục tạm sang thư mục lưu trữ Local và Server sau khi người dùng nhấn Đọc tệp.\
2\. Sắp xếp dữ liệu theo đúng cấu trúc thư mục đã quy định, dựa trên ngày đo, Request No, công đoạn, Item name, Item code, Lot No, Machine ID, Operator ID và Equipment Type.\
3\. Đảm bảo logfile và template được lưu đúng vị trí, đúng tên và liên kết với thông tin của từng Request, phục vụ truy xuất lịch sử đo và đối chiếu dữ liệu.\
4\. Đồng bộ dữ liệu giữa Local và Server, hỗ trợ quản lý tập trung, sao lưu và hạn chế thất lạc dữ liệu đo.

## 35. Lịch sử dữ liệu đo tại máy

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A36:F36`

### Requirement

1\. Lưu trữ và hiển thị lịch sử dữ liệu đo tại máy theo từng request, bao gồm các lần đo lại:\
\- Lọc theo from, to\
\- Tóm tắt lịch sử: (Lịch sử cần ghi lại tất cả các lần đo tại equipment no\
\+ Stt | Mã yêu cầu | Tên công đoạn | Mã máy | Indication number | Item name | Trạng thái (Ấn vào để view detail ) | Ngày hoàn thành | Người thực hiện | Đường dẫn file (local) | Event log\
2\. Cho phép người dùng tra cứu dữ liệu đo, kết quả đánh giá OK/NG, thời gian đo và Operator ID của từng lần đo.

### Mục đích

1\. Đảm bảo khả năng truy xuất dữ liệu và lịch sử đo, phục vụ kiểm tra chất lượng và điều tra nguyên nhân khi có bất thường

## 36. Gửi Abnormal nếu kết quả đo NG

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A37:F37`

### Requirement

Phương án 1: NG lần nào gửi Abnormal lần đó\
\- Chỉ cần một lần đo NG là gửi cảnh báo -> cảnh báo nhiều, dễ bị trùng khi đo lại, chưa xác định được kết quả NG thật hay do OP thao tác sai.\
Phương án 2: NG sau số lần đo quy định\
\- Ví dụ, sau 3 lần đo vẫn NG thì gửi Abnormal -> Dễ quản lí, nhưng có thể trì hoãn cảnh báo\
Phương án 3: NG ở lần đo cuối -> Chỉ gửi Abnormal khi người dùng không đo lại nữa -> Khó xác định lúc nào người dùng đã đo xong

## 37. SPC Control chart

- **Đối tượng sử dụng:** LAB test
- **Nguồn:** `02. Requirement!A38:F38`

### Requirement

1\. Bắc buộc lựa chọn: Stage và Item name\
\- Stage * | Machine ID | Item name* | Item code
