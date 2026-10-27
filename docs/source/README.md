# Tài liệu nguồn: LAB Test system (bản chuyển từ Excel)

Thư mục này là **bản chụp nguyên trạng (snapshot)** của file concept/specification `LAB_Test_system_261013.xlsx` (31 sheet), chuyển sang Markdown để agent và team đọc, tìm kiếm và theo dõi lịch sử bằng git.

- **File gốc:** `LAB_Test_system_261013.xlsx` (25 561 204 byte), nhận ngày 2026-10-27.
- **Ngày chuyển đổi:** 2026-10-27.
- **Quy ước sử dụng:** không sửa nội dung trong thư mục này. Quyết định, thuật ngữ và spec mới ghi vào `GLOSSARY.md`, `docs/adr/` và spec/issue trên GitHub, rồi trỏ ngược về đây làm nguồn. Nếu file Excel ra bản mới, chuyển đổi lại thành một commit riêng để `git diff` thấy được thay đổi.

## Mục lục

Sheet `00. Content` của file gốc chỉ liệt kê 11 mục đầu (cột "Checkpoint" ghi lại ở bảng dưới). Các sheet còn lại không có trong mục lục gốc nhưng vẫn được chuyển đổi đầy đủ.

| Sheet gốc | File | Checkpoint (từ `00. Content`) | Ghi chú |
|---|---|---|---|
| 01. Concept | [01-concept.md](01-concept.md) | | Có sơ đồ: chữ chép lại từ hình |
| 02. Requirement | [02-requirements.md](02-requirements.md) | | 37 chức năng; giữ đánh dấu chữ đỏ |
| 03. IPQC Contents | [03-ipqc-contents.md](03-ipqc-contents.md) | | Mục lục gốc gọi là "IPQC Content Masterlist" |
| 04. Meeting Minutes | [04-meeting-minutes.md](04-meeting-minutes.md) | | |
| Ref.01. UV Laser | [ref/ref-01-uv-laser.md](ref/ref-01-uv-laser.md) | 2026-10-19 | |
| Ref.02. De-smear (Plasma) | [ref/ref-02-de-smear-plasma.md](ref/ref-02-de-smear-plasma.md) | 2026-10-19 | |
| Ref.03. DFR Development | [ref/ref-03-dfr-development.md](ref/ref-03-dfr-development.md) | 2026-10-19 | |
| Ref.04. RR SS Etching | [ref/ref-04-rr-ss-etching.md](ref/ref-04-rr-ss-etching.md) | 2026-10-19 | |
| Ref.05. Copper Plating | [ref/ref-05-copper-plating.md](ref/ref-05-copper-plating.md) | | Chỉ có ảnh và dòng mục lục của sheet |
| Ref.06. Guide hole | [ref/ref-06-guide-hole.md](ref/ref-06-guide-hole.md) | | |
| Ref.07. Printing | [ref/ref-07-printing.md](ref/ref-07-printing.md) | | Chỉ có ảnh và dòng mục lục của sheet |
| Ref.08. SR Development | [ref/ref-08-sr-development.md](ref/ref-08-sr-development.md) | _(không có trong mục lục)_ | |
| Ref.09. CVL full lamination | [ref/ref-09-cvl-full-lamination.md](ref/ref-09-cvl-full-lamination.md) | _(không có trong mục lục)_ | Chỉ có ảnh và dòng mục lục của sheet |
| Ref.10. ENIG | [ref/ref-10-enig.md](ref/ref-10-enig.md) | _(không có trong mục lục)_ | Chỉ có ảnh và dòng mục lục của sheet |
| Ref.11. SUS Pre-tack | [ref/ref-11-sus-pre-tack.md](ref/ref-11-sus-pre-tack.md) | _(không có trong mục lục)_ | Chỉ có ảnh và dòng mục lục của sheet |
| Ref.12. InkJet | [ref/ref-12-inkjet.md](ref/ref-12-inkjet.md) | _(không có trong mục lục)_ | Ô A1 ghi nhầm "Ref.11. SUS Pre-tack" |
| 50. 2DID Laser marking | [process-control/50-2did-laser-marking.md](process-control/50-2did-laser-marking.md) | _(không có trong mục lục)_ | Bảng FAI/IPQC theo NPI/MP |
| 51. 2DID Cognex reading | [process-control/51-2did-cognex-reading.md](process-control/51-2did-cognex-reading.md) | _(không có trong mục lục)_ | |
| 52. Punching | [process-control/52-punching.md](process-control/52-punching.md) | _(không có trong mục lục)_ | Chưa có dữ liệu |
| 53. E-check | [process-control/53-e-check.md](process-control/53-e-check.md) | _(không có trong mục lục)_ | |
| 54. Plasma Cleaning | [process-control/54-plasma-cleaning.md](process-control/54-plasma-cleaning.md) | _(không có trong mục lục)_ | |
| 55. DI Water | [process-control/55-di-water.md](process-control/55-di-water.md) | _(không có trong mục lục)_ | |
| 56. FPC N2 Baking | [process-control/56-fpc-n2-baking.md](process-control/56-fpc-n2-baking.md) | _(không có trong mục lục)_ | |
| 56. FPC N2 Baking (2) | [process-control/56-fpc-n2-baking-2.md](process-control/56-fpc-n2-baking-2.md) | _(không có trong mục lục)_ | Trùng số 56 với sheet trên |
| 57. QC Gate | [process-control/57-qc-gate.md](process-control/57-qc-gate.md) | _(không có trong mục lục)_ | |
| 58. AVI | [process-control/58-avi.md](process-control/58-avi.md) | _(không có trong mục lục)_ | Chưa có dữ liệu |
| 59. Visual Inspection | [process-control/59-visual-inspection.md](process-control/59-visual-inspection.md) | _(không có trong mục lục)_ | Chưa có dữ liệu |
| Group 1 | [fai/fai-group-1.md](fai/fai-group-1.md) | _(không có trong mục lục)_ | Quy tắc FAI + flowchart |
| Group 2 | [fai/fai-group-2.md](fai/fai-group-2.md) | _(không có trong mục lục)_ | Quy tắc FAI + flowchart |
| Customer rule | [customer-rule.md](customer-rule.md) | _(không có trong mục lục)_ | Chỉ có 2 ảnh, không có chữ |

## Quy ước chuyển đổi

- **Giữ nguyên câu chữ gốc**, kể cả lỗi chính tả (ví dụ "vài trò", "Recive", "Equpment", "máy chủ FPT") và số thứ tự bị lặp. Đầu dòng dạng `1.`, `-`, `+` được escape (`1\.`) để Markdown không tự đánh lại số.
- **Truy vết về Excel:** mỗi bảng có cột `Row` (số dòng Excel) và tên cột dạng `A`, `B: Tên cột`. Đoạn văn một ô có chú thích ẩn `<!-- A1 -->`; ảnh có `<!-- ảnh neo tại ô ... -->`.
- **Chữ đỏ** trong Excel (chỉ có ở `02. Requirement`) được đánh dấu `🔴**...**`. Ý nghĩa của màu đỏ (mới thêm? cần xác nhận?) **chưa được xác nhận** với chủ tài liệu.
- **Ô gộp (merged cell) theo chiều dọc** được lặp lại xuống các dòng nó phủ, chỉ ở cột đầu của vùng gộp. Ô gộp theo chiều ngang giữ ở ô trái nhất; tiêu đề bảng nhiều tầng được ghép bằng ` / `.
- **Số:** ghi theo 15 chữ số có nghĩa, bằng độ chính xác Excel lưu trữ, để bỏ nhiễu dấu phẩy động (ví dụ `2.0500000000000003` thành `2.05`). Giá trị là kết quả công thức đã tính sẵn trong file. Lỗi công thức (`#REF!`, `#DIV/0!`, `#VALUE!`) giữ nguyên như nguồn.
- **Ngày:** `YYYY-MM-DD`, kèm `HH:MM:SS` nếu ô có giờ.
- **Bảng rộng hơn 30 cột** (dữ liệu đo mẫu trong các sheet Ref) được xuất nguyên vẹn ra `ref/data/*.csv` (UTF-8 có BOM để Excel mở đúng tiếng Việt); file `.md` chỉ trích 6 dòng đầu, cột A..L.
- **Ảnh nhúng** được tách vào `assets/<tên-file>/`, đặt theo thứ tự ô neo. Ảnh rộng hơn 1600 px được thu nhỏ còn 1600 px chiều ngang.
- **Sơ đồ vẽ bằng shape** (Concept, Group 1, Group 2) được render bằng LibreOffice 24.2. Bản render có thể khác Excel ở font hoặc phần chữ bị che. Phần chữ trong `.md` lấy từ XML của shape, cấu trúc luồng chép lại từ hình và ghi rõ là bản chép lại. Các hộp chú thích vẽ đè lên ảnh trong sheet Ref được liệt kê ở cuối từng file.

## Vấn đề có sẵn trong file gốc

Đây là những gì quan sát được trong lúc chuyển đổi. Chưa sửa gì; cần chủ tài liệu xác nhận.

1. **Hyperlink hỏng (19 link):** cột B của `03. IPQC Contents` trỏ tới các sheet không tồn tại (`'1. UV Laser'`, `'2.De-smear (Plasma)'`, `'9. Development'`, ...). Ô A2 của 11 sheet `50`–`59` trỏ tới sheet `Summary`, cũng không tồn tại.
2. **Lỗi công thức:** `Ref.03` có 16 ô `#REF!`; `Ref.04` có 1 284 ô `#DIV/0!` và 24 ô `#VALUE!`.
3. **Mục lục `00. Content`** chỉ có 11 mục, thiếu 19 sheet (Ref.08–12, 50–59, Group 1/2, Customer rule).
4. **`01. Concept`** có hai mục cùng đánh số "IV". Hộp "Yêu cầu" có dòng `3)` bị che khi xem trong Excel. Sheet này còn chứa một ảnh chụp bảng requirement, chưa đối chiếu với sheet `02`.
5. **`Ref.12. InkJet`** có ô A1 ghi "Ref.11. SUS Pre-tack".
6. **Hai sheet cùng số 56** (`56. FPC N2 Baking` và `56. FPC N2 Baking (2)`).
