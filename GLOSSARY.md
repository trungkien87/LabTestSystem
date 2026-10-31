# Laboratory Test System

Hệ thống quản lý yêu cầu đo kiểm IPQC giữa Production (PR), Process Engineering (PE) và Laboratory: khai báo tiêu chuẩn, tạo và nhận yêu cầu đo, đọc kết quả từ thiết bị đo và đánh giá theo tiêu chuẩn.

## Language

### Sản phẩm

**Item name**:
Mã model sản phẩm, chỉ gồm chữ hoa và số, ví dụ `69DRCT`; một Item name có nhiều Item code.
_Avoid_: tên sản phẩm, model

**Item code**:
Mã hàng thuộc đúng một Item name và đúng một Build, chỉ gồm chữ hoa và số; dài 12 ký tự với hàng sản xuất, ví dụ `4M002401000B`, hoặc 7 ký tự với hàng test/prototype, ví dụ `26B0740`. Với hàng sản xuất, 6 ký tự cuối chỉ loại mã: `01000B` Front route, `02000B` Back route, `00000B` mã xuất hàng từ SEEV sang MI, `03000B` mã xuất hàng từ SEEV sang SECT.
_Avoid_: mã sản phẩm, Part No (khi muốn nói Item code)

**Build**:
Giai đoạn phát triển hoặc sản xuất mà một Item code thuộc về, xác định bằng Build Code và Build Phase và mang một Build Type, ví dụ Build Code `C8.0`, Build Phase `POC` (Proof Of Concept), Build Type NPI.
_Avoid_: Build Management

**Build Code**:
Mã của một Build, ví dụ `C8.0`, `C8.1`, `C1.0`, `RR/MP`.

**Build Phase**:
Tên viết tắt của giai đoạn trong Build, ví dụ `POC`, `EVT`, `PVT`; mỗi Build Phase có một Phase Name đầy đủ, ví dụ POC – Proof Of Concept, EVT – Engineering Validation Test.

**Build Type**:
Phân loại của một Build là NPI hoặc MP, do người dùng gán cho từng Build; quyết định Item code thuộc Build đó dùng số lượng mẫu NPI hay MP.
_Avoid_: MASS (dùng MP)

**Lot**:
Một lô sản xuất của một Item code, đánh số bằng 5 chữ số với hàng sản xuất, ví dụ `00094`, hoặc 3 chữ số với hàng test/prototype, ví dụ `001`.
_Avoid_: Lot No, lô, lot main, lot gốc (khi muốn nói Lot)

**Split lot**:
Một phần được cắt ra từ một Lot hoặc từ một Split lot khác, nên một Lot có thể cắt thành nhiều cấp: Lot cắt ra Split lot cấp 1, Split lot cấp 1 cắt ra Split lot cấp 2, và cứ thế. Mọi cấp đều đánh số bằng số Lot, dấu `-` và 2 chữ số thứ tự tiếp nối trong cùng Lot, ví dụ `00094-02` cấp 1 cắt ra `00094-05` và `00094-06` cấp 2, nên mã không cho biết Split lot cha.
_Avoid_: lot cắt, lot cut, sub-lot, child lot

**Indication number**:
Mã in trên Traveller ticket, có hai dạng. Hàng sản xuất: Item code 12 ký tự và Lot (hoặc Split lot) ghép liền, ví dụ `4M002401000B00094`. Hàng test/prototype: Item code 7 ký tự, Revision 1 chữ số, Part No 2 ký tự chữ hoa hoặc số, dấu `-`, rồi Lot (hoặc Split lot), ví dụ `26B07400V2-001-02` là Item code `26B0740`, Revision `0`, Part No `V2`, Split lot `001-02`.
_Avoid_: Indi Number, mã tem lô

**Revision**:
Số revision 1 chữ số ở vị trí thứ 8 trong Indication number của hàng test/prototype, ngay sau Item code, ví dụ `0`; không thuộc Item code.

**Part No**:
Mã 2 ký tự chữ hoa hoặc số ngay sau Revision trong Indication number của hàng test/prototype, ví dụ `V2`; hiện chỉ lưu để truy vết.

**Traveller ticket**:
Phiếu đi kèm một Lot qua các công đoạn sản xuất, in mã vạch Indication number và mã vạch Process Sequence của các Production Process trong Route.
_Avoid_: Indication sheet, travel ticket, tem lô

### Sản xuất

**Factory**:
Nhà máy, tên đầy đủ Factory 1 … Factory 5, viết tắt F1 … F5.
_Avoid_: xưởng, plant

**Production Process**:
Một công đoạn sản xuất, ví dụ `UV Laser`, `R/R Copper`; mỗi Production Process có đúng một Sample Form.
_Avoid_: Stage, công đoạn (đứng một mình), process (đứng một mình)

**Sample Form**:
Hình thức của mẫu lấy từ một Production Process: sheet, block, panel hoặc piece.
_Avoid_: Sample type, loại mẫu

**Production Machine**:
Máy sản xuất, định danh bằng Machine ID, ví dụ `CPRR009`; đặt ở đúng một Factory và chạy một hoặc nhiều Production Process.
_Avoid_: Machine (đứng một mình), máy; không dùng cho thiết bị đo (xem Equipment)

**Process Sequence**:
Số thứ tự 4 chữ số chỉ trình tự của một Production Process trong một Route; từ `0000` đến `9999`, tăng dần theo trình tự, ví dụ `0020`, `0030`. Chỉ duy nhất trong một Route: các Route khác nhau của cùng Item name có thể trùng số. Với hàng test/prototype không chia Route, Process Sequence đánh liên tục cho cả chuỗi và duy nhất trong Item code. Viết tắt được chấp nhận: Process Seq, Process SEQ.
_Avoid_: Sequence, Seq, SEQ (đứng một mình), thứ tự công đoạn, bước, routing step

**Route**:
Chuỗi Production Process có thứ tự mà một Item code hàng sản xuất đi qua. Mỗi Item code hàng sản xuất thuộc đúng một Route, xác định theo 6 ký tự cuối: Front route (`01000B`), Back route (`02000B`), MI route (`00000B`, xuất SEEV sang MI), SECT route (`03000B`, xuất SEEV sang SECT). Item code hàng test/prototype không chia Route.
_Avoid_: Upper route, Lower route, Front process, Back process, Shipping route, process (đứng một mình), routing

### Đo kiểm

**Request**:
Yêu cầu đo IPQC cho một Indication number tại một Process Sequence, gồm các Measurement Step theo Measurement Order; định danh bằng Request No dạng `RYYMMDD_NNNN`, ví dụ `R260710_0001`.
_Avoid_: Order, Order No, yêu cầu đo (đứng một mình)

**Overdue**:
Cờ của một Request đã qua Deadline mà chưa Completed; không phải một trạng thái, Request vẫn giữ trạng thái tiến độ của nó.
_Avoid_: Delayed, Quá hạn, Trễ hạn (khi dùng như một trạng thái)

**Equipment type**:
Nhóm phân loại thiết bị đo, ví dụ OMM (Optical Measurement Machine).
_Avoid_: loại máy đo, Machine type

**Equipment brand**:
Hãng sản xuất thiết bị đo, ví dụ Keyence, Nikon, Mitutoyo.
_Avoid_: maker (từ này dành cho bên phát triển hệ thống), nhà cung cấp

**Equipment model**:
Dòng máy đo của một Equipment brand, ví dụ `VHX-7000`, `NEXIV`, `QV`; thuộc đúng một Equipment brand và một Equipment type.
_Avoid_: model (đứng một mình), loại máy

**LogFile type**:
Định dạng file kết quả mà một Equipment model xuất ra: Template, VHX, Laser hoặc Manual Input; mọi Equipment cùng model dùng cùng một LogFile type.
_Avoid_: Kiểu LogFile, định dạng log

**Equipment**:
Một máy đo cụ thể, định danh bằng Equipment ID; thuộc đúng một Equipment model và đặt ở đúng một Laboratory Location.
_Avoid_: Machine, máy đo (đứng một mình), thiết bị

**Laboratory Location**:
Phòng vật lý có đặt Equipment, nơi mẫu được đo; có thể là phòng thí nghiệm hoặc một khu vực trong xưởng sản xuất; mỗi phòng là một Laboratory Location dù do bộ phận nào sử dụng. Không có tầng quản lý nào phía trên: mỗi phòng thí nghiệm đúng là một Laboratory Location. Đặt tên theo quy tắc `Factory – Floor – Room`, ví dụ `F1 – 1st Floor – QA Lab`, `F5 – 1st Floor – Etching`.
_Avoid_: Measurement Location, Location, vị trí, khu vực đo, "Công đoạn lấy kq", In line, Laboratory (khi muốn nói một phòng đo cụ thể), LAB test, LAB, Laboratary

**Measurement Step**:
Một phép đo trong chuỗi đo tuần tự mà cùng một mẫu lần lượt đi qua; ứng với đúng một IPQC Content. Thứ tự các Measurement Step do Measurement Order quy định.
_Avoid_: Sequence, Seq (dành cho Process Sequence), route (dành cho Route), bước (đứng một mình), measurement route

**Step No**:
Số thứ tự của một Measurement Step trong chuỗi đo, bắt đầu từ 1, ví dụ 1, 2, 3.
_Avoid_: Sequence No, Seq No, thứ tự bước

**Measurement Attempt**:
Một lần đo của một Measurement Step, sinh ra khi file kết quả được đọc hợp lệ; đánh số 1, 2, 3… trong Measurement Step. Khi Measurement Step đo xong, Judgement của nó là Judgement của Measurement Attempt cuối cùng; các lần trước vẫn được giữ.
_Avoid_: lần đo (đứng một mình), Retry, Re-measure count

**Measurement Order**:
Thứ tự đo các IPQC Content của một IPQC Spec, gán Step No cho từng Measurement Step; mỗi IPQC Spec có đúng một Measurement Order, khai riêng với IPQC Spec và chỉ sắp xếp các IPQC Content đã có trong IPQC Spec đó.
_Avoid_: Measurement Sequence, measurement route, measurement flow, thứ tự đo (đứng một mình)

### Tiêu chuẩn và đánh giá

**IPQC Content**:
In-Process Quality Control Content: một nội dung kiểm soát chất lượng trong quá trình sản xuất, tức là chỉ tiêu cần đo, ví dụ "BVH Top"; chỉ định đúng một Equipment type để đo, không chỉ định Equipment cụ thể.
_Avoid_: hạng mục đo, chỉ tiêu (đứng một mình), Nội dung IPQC

**IPQC Spec**:
Bộ khai báo đo của một sản phẩm tại một Process Sequence: Unit, các IPQC Content cần đo, và với mỗi IPQC Content là Side, Piece quantity, Measurement points per piece, Specification Limit và Control Limit. Có hai biến thể: Common dùng chung cho các Item code cùng Item name và cùng Route, Individual chỉ cho một Item code.
_Avoid_: Spec (đứng một mình), Standard, bộ tiêu chuẩn

**Unit**:
Số mẫu PR mang lên cho một Request, đếm theo Sample Form của Production Process, ví dụ 1 panel; khai trong IPQC Spec.
_Avoid_: số lượng mẫu (đứng một mình), Qty

**Piece quantity**:
Số piece đo cho một IPQC Content, có hai giá trị NPI và MP; Build Type của Item code quyết định dùng giá trị nào. Viết tắt được chấp nhận: pcs.
_Avoid_: Sample size, số mẫu, Qty

**Measurement points per piece**:
Số điểm hoặc lỗ đo trên một piece cho một IPQC Content, tính cho mỗi Side.
_Avoid_: số điểm (đứng một mình), point, số lỗ

**Side**:
Mặt của mẫu được đo, Side A hoặc Side B; bật hoặc tắt riêng cho từng IPQC Content trong IPQC Spec. Mỗi Side là một tập dữ liệu riêng, có Specification Limit, Control Limit, X̄ và R riêng.
_Avoid_: mặt (đứng một mình), Face

**Specification Limit**:
Giới hạn chấp nhận do kỹ thuật hoặc khách hàng đặt, gồm LL (Lower Limit), UL (Upper Limit) hoặc cả hai, tức có thể một phía hoặc hai phía; khai riêng cho Side A và Side B nếu IPQC Content đo cả hai mặt; dùng để đánh giá OK/NG.
_Avoid_: Spec (khi muốn nói giới hạn), tiêu chuẩn, X Spec

**Control Limit**:
Giới hạn thống kê của quá trình, gồm LCL, Center line và UCL; khai cho biểu đồ X, biểu đồ R hoặc cả hai; X là trung bình (X̄) mọi giá trị đo của một Request cho một IPQC Content, R là max − min của các giá trị đó, tính riêng cho Side A và Side B nếu IPQC Content đo cả hai mặt; khai riêng cho từng Side; Center line là giá trị trung tâm thống kê, không phải giá trị mục tiêu; dùng cho SPC rule, cảnh báo sớm trước khi ra NG.
_Avoid_: giới hạn cảnh báo, R Spec

**Judgement**:
Kết luận OK hoặc NG so với Specification Limit; NG khi có ít nhất một giá trị đo, ở bất kỳ Side nào, nằm ngoài Specification Limit của Side đó. Có ở ba cấp: Measurement Attempt, Measurement Step khi đã đo xong, và Request (NG ngay khi có một Measurement Step NG, OK chỉ khi mọi Measurement Step OK). Không phải trạng thái tiến độ; lần đọc file kết quả bị lỗi không tạo ra Judgement.
_Avoid_: Judgment, phán định (đứng một mình), Status NG, Error (khi muốn nói Judgement)

**Result File Mapping**:
Thiết lập cách đọc dữ liệu từ file kết quả (logfile hoặc template) để lấy giá trị của một IPQC Content trên một Equipment model: vị trí ô, hàng, cột và chiều lấy dữ liệu. Mỗi cặp Equipment model × IPQC Content có đúng một Result File Mapping, dùng chung cho mọi Equipment cùng model ở mọi Laboratory Location.
_Avoid_: Layout, Bố cục IPQC, Cấu hình IPQC

**SPC Violation**:
Ghi nhận một SPC rule bị vi phạm bởi một Measurement Step đã đo xong, cho một Side, ví dụ X̄ vượt UCL; luôn được ghi khi IPQC Content có Control Limit, dù có sinh Abnormal hay không.
_Avoid_: SPC NG, NG SPC, cảnh báo SPC, Out of control (khi muốn nói Judgement NG)

### Abnormal

**Abnormal**:
Một cảnh báo chất lượng phát sinh từ một Measurement Step đã đo xong có Judgement NG hoặc có SPC Violation được bật theo dõi; mỗi Measurement Step có tối đa một Abnormal, được leader xác nhận rồi gửi sang hệ thống Abnormal Report của Plus A để xử lý hàng.
_Avoid_: Abnormal report (khi muốn nói bản ghi; Abnormal report là file CSV gửi đi), bất thường, cảnh báo NG

**Abnormal reason**:
Lý do phát sinh của một Abnormal: Spec NG (vượt Specification Limit), một hoặc nhiều SPC rule, hoặc cả hai.
_Avoid_: Abnormal type, loại Abnormal

**Abnormal Setting**:
Tập dòng quy tắc quyết định Spec NG, SPC Violation hoặc Measurement Attempt NG nào được bật hay tắt cảnh báo, theo phạm vi Item name, Item code, IPQC Content và Production Machine; mỗi dòng có hiệu lực chỉ sau khi được người thứ hai phê duyệt.
_Avoid_: Abnormal config, cài đặt cảnh báo, bật tắt Abnormal

**Project Year**:
Năm của dự án mà một Item name thuộc về, ví dụ 2026; lấy từ hệ thống sản xuất bên ngoài, không phải ngày tạo Item name.
_Avoid_: Item name Year, Created date (khi muốn nói năm dự án), năm sản phẩm

### Tổ chức

**Department**:
Phòng ban của người dùng, là một trong bốn: Process Engineering – Phòng Kỹ thuật công đoạn (PE), Production – Phòng Sản xuất (PR), Quality Assurance – Phòng Quản lý chất lượng (QA), Smart Factory – Phòng nhà máy thông minh (SF). Chỉ ghi nhận người dùng đến từ phòng nào; không quyết định quyền thao tác, quyền do Role quyết định.
_Avoid_: bộ phận, nhóm

**Job Level**:
Cấp bậc của người dùng trong Department: Manager, Engineer, Leader hoặc Operator. Chỉ là thông tin như Department, không quyết định quyền thao tác.
_Avoid_: Position (dành cho vị trí trên Rack), Role (dành cho tập quyền), OP, công nhân

**Role**:
Tập quyền thao tác trong hệ thống, do quản trị viên tạo và tuỳ biến, rồi gán cho người dùng; quyền của người dùng chỉ do Role quyết định.
_Avoid_: quyền, nhóm quyền, permission group, Job Level (khi muốn nói Role)
