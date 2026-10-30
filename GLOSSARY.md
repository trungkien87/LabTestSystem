# Laboratory Test System

Hệ thống quản lý yêu cầu đo kiểm IPQC giữa Production (PR), Process Engineering (PE) và Laboratory: khai báo tiêu chuẩn, tạo và nhận yêu cầu đo, đọc kết quả từ thiết bị đo và đánh giá theo tiêu chuẩn.

## Language

### Sản phẩm

**Item name**:
Mã model sản phẩm, chỉ gồm chữ hoa và số, ví dụ `69DRCT`; một Item name có nhiều Item code.
_Avoid_: tên sản phẩm, model

**Item code**:
Mã hàng thuộc đúng một Item name và đúng một Build, chỉ gồm chữ hoa và số; dài 12 ký tự với hàng sản xuất, ví dụ `4M002401000B`, hoặc 7 ký tự với hàng test/prototype, ví dụ `26B0740`. Với hàng sản xuất, 6 ký tự cuối chỉ loại mã: `01000B` Front route, `02000B` Back route, `00000B` mã xuất hàng từ SEEV sang MI, `03000B` mã xuất hàng từ SEEV sang SECT.
_Avoid_: mã sản phẩm, part number, Part No (khi muốn nói Item code)

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
_Avoid_: Lot No, lô

**Split lot**:
Một phần được cắt ra từ một Lot, đánh số bằng số Lot gốc, dấu `-` và 2 chữ số thứ tự, ví dụ `00094-02`, `001-02`.
_Avoid_: lot cắt, sub-lot, child lot

**Indication number**:
Mã in trên Traveller ticket, có hai dạng. Hàng sản xuất: Item code 12 ký tự và Lot (hoặc Split lot) ghép liền, ví dụ `4M002401000B00094`. Hàng test/prototype: Item code 7 ký tự, Revision 1 chữ số, Part No 2 ký tự chữ hoa hoặc số, dấu `-`, rồi Lot (hoặc Split lot), ví dụ `26B07400V2-001-02` là Item code `26B0740`, Revision `0`, Part No `V2`, Split lot `001-02`.
_Avoid_: Indi Number, mã tem lô

**Revision**:
Số revision 1 chữ số ở vị trí thứ 8 trong Indication number của hàng test/prototype, ngay sau Item code, ví dụ `0`; không thuộc Item code.

**Part No**:
Mã 2 ký tự chữ hoa hoặc số ngay sau Revision trong Indication number của hàng test/prototype, ví dụ `V2`; hiện chỉ lưu để truy vết.

**Traveller ticket**:
Phiếu đi kèm một Lot qua các công đoạn sản xuất, mang Indication number.
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
Máy sản xuất, định danh bằng Machine ID, ví dụ `CPRR009`; thuộc đúng một Production Process và một Factory.
_Avoid_: Machine (đứng một mình), máy; không dùng cho thiết bị đo (xem Equipment)

**Process Sequence**:
Số thứ tự 4 chữ số chỉ trình tự của một Production Process trong một Route; là số nguyên dương, tăng dần theo trình tự, ví dụ `0020`, `0030`. Chỉ duy nhất trong một Route: Front route và Back route của cùng Item name có thể trùng số. Viết tắt được chấp nhận: Process Seq, Process SEQ.
_Avoid_: Sequence, Seq, SEQ (đứng một mình), thứ tự công đoạn, bước, routing step

**Route**:
Chuỗi Production Process có thứ tự mà một Item code đi qua, gồm Front route (mã `…01000B`) và Back route (mã `…02000B`); mỗi Item code sản xuất thuộc đúng một Route.
_Avoid_: Upper route, Lower route, Front process, Back process, process (đứng một mình), routing

### Đo kiểm

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
Phòng vật lý có đặt Equipment, nơi mẫu được đo; có thể là phòng của Laboratory hoặc một khu vực trong xưởng sản xuất; mỗi phòng là một Laboratory Location dù do bộ phận nào sử dụng. Đặt tên theo quy tắc `Factory – Floor – Room`, ví dụ `F1 – 1st Floor – QA Lab`, `F5 – 1st Floor – Etching`.
_Avoid_: Measurement Location, Location, vị trí, khu vực đo, "Công đoạn lấy kq", In line

### Tiêu chuẩn và đánh giá

**IPQC Content**:
In-Process Quality Control Content: một nội dung kiểm soát chất lượng trong quá trình sản xuất, tức là chỉ tiêu cần đo, ví dụ "BVH Top".
_Avoid_: hạng mục đo, chỉ tiêu (đứng một mình), Nội dung IPQC

**Specification Limit**:
Giới hạn chấp nhận do kỹ thuật hoặc khách hàng đặt, gồm LL (Lower Limit) và UL (Upper Limit); dùng để đánh giá OK/NG.
_Avoid_: Spec (khi muốn nói giới hạn), tiêu chuẩn, X Spec

**Control Limit**:
Giới hạn thống kê của quá trình, gồm LCL, Center line và UCL; dùng cho SPC rule, cảnh báo sớm trước khi ra NG.
_Avoid_: giới hạn cảnh báo, R Spec

**Result File Mapping**:
Thiết lập cách đọc dữ liệu từ file kết quả (logfile hoặc template) của một Equipment model: vị trí ô, hàng, cột và chiều lấy dữ liệu.
_Avoid_: Layout, Bố cục IPQC, Cấu hình IPQC

### Tổ chức

**Department**:
Phòng ban của người dùng, là một trong bốn: Process Engineering – Phòng Kỹ thuật công đoạn (PE), Production – Phòng Sản xuất (PR), Quality Assurance – Phòng Quản lý chất lượng (QA), Smart Factory – Phòng nhà máy thông minh (SF).
_Avoid_: bộ phận, nhóm

**Job Level**:
Cấp bậc của người dùng trong Department: Manager, Engineer, Leader hoặc Operator.
_Avoid_: Position (dành cho vị trí trên Rack), Role, OP, công nhân

**Laboratory**:
Phòng thí nghiệm dùng để đo đạc, kiểm thử, thuộc quản lý của Department PR hoặc QA.
_Avoid_: QA Lab, LAB test, LAB, Laboratary
