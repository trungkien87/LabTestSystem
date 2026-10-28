# LAB Test system

Hệ thống quản lý yêu cầu đo kiểm IPQC giữa sản xuất (PR), kỹ thuật công đoạn (PE) và phòng LAB: khai báo tiêu chuẩn, tạo và nhận yêu cầu đo, đọc kết quả từ thiết bị đo và đánh giá theo tiêu chuẩn.

## Language

### Sản phẩm

**Item name**:
Mã model sản phẩm, chỉ gồm chữ hoa và số, ví dụ `69DRCT`; một Item name có nhiều Item code.
_Avoid_: tên sản phẩm, model

**Item code**:
Mã hàng thuộc đúng một Item name và đúng một Build, chỉ gồm chữ hoa và số, ví dụ `4M002401000B`. 6 ký tự cuối chỉ loại mã: `01000B` Upper/Front route, `02000B` Lower/Back route, `00000B` mã xuất hàng từ SEEV sang MI, `03000B` mã xuất hàng từ SEEV sang SECT.
_Avoid_: mã sản phẩm, part number

**Build**:
Giai đoạn phát triển hoặc sản xuất mà một Item code thuộc về, xác định bằng Build Code và Build Phase, ví dụ `C8.0 (POC)`, `RR/MP (RevA)`.
_Avoid_: Build Management

**Build Code**:
Mã của một Build, ví dụ `C8.0`, `C8.1`, `C1.0`, `RR/MP`.

**Build Phase**:
Tên viết tắt của giai đoạn trong Build, ví dụ `POC`, `EVT`, `PVT`; mỗi Build Phase có một Phase Name đầy đủ, ví dụ POC – Proof Of Concept, EVT – Engineering Validation Test.

**Lot**:
Một lô sản xuất của một Item code, đánh số bằng 5 chữ số, ví dụ `00094`.
_Avoid_: Lot No, lô

**Indication number**:
Mã in trên Traveller ticket, gồm Item code và Lot ghép liền, ví dụ `4M002401000B00094`.
_Avoid_: Indi Number, mã tem lô

**Traveller ticket**:
Phiếu đi kèm một Lot qua các công đoạn sản xuất, mang Indication number.
_Avoid_: travel ticket, tem lô

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
Số thứ tự 4 chữ số chỉ trình tự của một Production Process trong chuỗi Production Process mà sản phẩm đi qua; là số nguyên dương, tăng dần theo trình tự, ví dụ `0020`, `0030`. Viết tắt được chấp nhận: Process Seq, Process SEQ.
_Avoid_: Sequence, Seq, SEQ (đứng một mình), thứ tự công đoạn, bước, routing step

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

**Equipment**:
Một máy đo cụ thể, định danh bằng Equipment ID; thuộc đúng một Equipment model và đặt ở đúng một Laboratory Location.
_Avoid_: Machine, máy đo (đứng một mình), thiết bị

**Laboratory Location**:
Phòng vật lý nơi mẫu được chuyển tới để đo, có đặt thiết bị đo; mỗi phòng là một Laboratory Location dù do bộ phận nào sử dụng; đặt tên theo quy tắc `Nhà máy-Tầng-Phòng`, ví dụ `F1-Tầng 1-QALab`.
_Avoid_: Measurement Location, Location, vị trí, khu vực đo, "Công đoạn lấy kq"
