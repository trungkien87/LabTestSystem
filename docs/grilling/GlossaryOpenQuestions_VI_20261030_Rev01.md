# Câu hỏi còn mở – Ticket #2 Thuật ngữ lõi

Version: 20261030 Rev.01
Ticket: [#2 Chốt thuật ngữ lõi và quan hệ giữa các khái niệm](https://github.com/trungkien87/LabTestSystem/issues/2)
Thuật ngữ đã chốt: [`GLOSSARY.md`](../../GLOSSARY.md)

## Cách trả lời

- Mỗi câu có một đề xuất ➡️. Trả lời **yes** nghĩa là đồng ý với đề xuất.
- Nếu không đồng ý, ghi câu trả lời vào dòng **Trả lời** của câu đó.
- **[khác demo]** đánh dấu chỗ quyết định khác với demo của maker.
- Tên tạm: **IPQC Spec** là bộ khai báo đo của một sản phẩm, và chờ chốt ở Q32.

## Tổng hợp

| Nhóm | Câu |
|---|---|
| A. Sản phẩm | Q15a, Q15b, Q15c, Q17, Q18, Q30, Q31 |
| B. Số lượng mẫu và IPQC Spec | Q7, Q9, Q10, Q32 |
| C. Thiết bị và tiêu chuẩn | Q22, Q33, Q34, Q35 |
| D. Location và tổ chức | Q12, Q27, Q28, Q29 |

Tổng cộng 19 câu.

---

## A. Sản phẩm

### Q15a – Mã trên Indication sheet test có dạng thế nào?

Đã chốt: Item code không phải lúc nào cũng dài 12 ký tự, vì Indication sheet test có định dạng khác. Do đó hệ thống không thể tách Indication number thành Item code và Lot theo độ dài.

Cần bạn cung cấp:
- 2–3 mã thật của Indication sheet test, kèm ý nghĩa của từng phần.
- "Test" là loại lot gì, ví dụ lot thử nghiệm của PE hay lot chạy thử máy.
- Item code của lot test có được khai trong master data như Item code thường không.
- Item code của lot test có đuôi `01000B` hoặc `02000B` để suy ra Route không. Câu này liên quan Q10.

**Trả lời:**

### Q15b – Đuôi Lot có luôn đúng một trong hai dạng không?

Hai dạng là `5 số` (Lot, ví dụ `00094`) và `5 số-2 số` (Split lot, ví dụ `00094-02`). Câu hỏi áp dụng cho cả lot test.

➡️ Đề xuất cách tách Indication number:
1. Tìm Lot hoặc Split lot ở **cuối chuỗi**, theo đúng một trong hai dạng trên.
2. Phần còn lại phía trước là Item code, và Item code đó phải có trong master data.
3. Nếu không tìm được Lot ở cuối chuỗi, hoặc Item code chưa có trong master data, hệ thống từ chối và cho nhập tay.
4. Chữ thường tự đổi thành chữ hoa.

Điều kiện để cách này đúng: lot test cũng dùng một trong hai dạng đuôi Lot trên. Nếu không, cần thêm một quy tắc riêng cho lot test, xây từ các ví dụ ở Q15a.

**Trả lời:**

### Q15c – "Indication sheet" và "Traveller ticket" có phải là một?

`GLOSSARY.md` hiện ghi Indication number được in trên **Traveller ticket**.

➡️ Đề xuất: nếu hai tên chỉ cùng một phiếu, giữ tên Traveller ticket và đưa "Indication sheet" vào danh sách _Avoid_. Nếu là hai phiếu khác nhau, bạn cho biết chúng khác nhau thế nào.

**Trả lời:**

### Q17 – Mã xuất hàng có được dùng để tạo Request không?

Mã xuất hàng gồm `…00000B` (SEEV sang MI) và `…03000B` (SEEV sang SECT).

➡️ Đề xuất: không. Hai loại mã này không đi qua Production Process nào, nên hệ thống từ chối tạo Request với chúng.

**Trả lời:**

### Q18 – Ký tự cuối `B` là gì, và Build của một Item code có đổi theo thời gian không?

➡️ Đề xuất:
- `B` là revision. Đổi sang `C` nghĩa là có một Item code mới; IPQC Spec Individual của mã cũ không tự chuyển sang mã mới.
- Build của một Item code không đổi. Nếu thực tế Build có đổi, mỗi Request phải lưu Build tại thời điểm tạo.

**Trả lời:**

### Q30 – Indication number của Split lot có dạng thế nào?

➡️ Đề xuất:
- Indication number của Split lot có dạng Item code + Lot + `-` + 2 chữ số, ví dụ `4M002401000B00094-02`.
- Hệ thống tách theo quy tắc ở Q15b. Không giới hạn độ dài cố định.
- Nếu Traveller ticket của Split lot in theo dạng khác, bạn gửi một ví dụ thật.

**Trả lời:**

### Q31 – Split lot có được xử lý như một Lot độc lập không?

Tình huống: Lot `00094` được cắt thành `00094-01` và `00094-02`, chạy trên hai Production Machine khác nhau. `00094-01` đã đo UV Laser với kết quả OK. Vậy `00094-02` có cần Request đo riêng không?

➡️ Đề xuất:
- Có. Mỗi Split lot có Request và kết quả riêng. Kết quả của Split lot này không thay cho Split lot khác.
- Hệ thống vẫn giữ liên kết với Lot gốc `00094`, để tra cứu và báo cáo được theo Lot gốc.

**Trả lời:**

---

## B. Số lượng mẫu và IPQC Spec

### Q7 – Bốn thuật ngữ số lượng

Ví dụ: PR mang lên **1 panel**. Laboratory cắt ra **5 piece** để đo. Mỗi piece đo **3 lỗ**, ở cả **Side A và Side B**. Kết quả là 5 × 3 × 2 = 30 giá trị đo.

➡️ Đề xuất:
- **Unit**: số mẫu mang lên cho một Request, đếm theo Sample Form, khai trong IPQC Spec.
- **Piece quantity**: số piece đo cho một IPQC Content, có giá trị NPI và giá trị MP. Viết tắt "pcs".
- **Measurement points per piece**: số điểm hoặc lỗ đo trên một piece.
- **Side A / Side B**: bật hoặc tắt cho từng IPQC Content trong từng IPQC Spec.

**Trả lời:**

### Q9 – Khoá của IPQC Spec

Đã chốt ở Q16: Front route và Back route có thể trùng Process Sequence.

➡️ Đề xuất:
- **Common**: khai theo Item name × Route × Process Sequence.
- **Individual**: khai theo Item code × Process Sequence. Route không cần trong khoá, vì Item code đã xác định Route.
- Mỗi bộ (Item name, Route, Process Sequence) ứng với đúng một Production Process. Một Production Process có thể lặp lại ở nhiều Process Sequence, ví dụ R/R Copper ở `0040` và `0090`.
- **Điều kiện:** mọi Item code cùng Item name và cùng Route đi qua cùng một trình tự Production Process. Nếu điều kiện này sai, Common không dùng chung được và mọi IPQC Spec phải là Individual.
- **[khác demo]** Khoá của demo là Stage + Item name + Sequence, không có Route.

**Trả lời:**

### Q10 – Khi tạo Request, Process Sequence do hệ thống tự xác định hay PR chọn?

Requirement 20 ghi "Scan/Lựa chọn sequence".

➡️ Đề xuất:
1. Từ Indication number, hệ thống lấy Item code, rồi từ Item code lấy Route.
2. Từ Machine ID vừa quét, hệ thống lấy Production Process.
3. Hệ thống tìm các Process Sequence trong Route đó có Production Process này. Có 1 kết quả thì tự chọn. Có nhiều kết quả thì PR chọn trong danh sách.
4. PR không được gõ tay Process Sequence.

**Rủi ro:** nếu Item code của lot test không có đuôi `01000B`/`02000B` (Q15a), bước 1 phải lấy Route từ master data của Item code, không suy ra từ chuỗi ký tự.

**Trả lời:**

### Q32 – Bộ khai báo đo của một sản phẩm gọi là gì?

Bộ này gồm Unit, Lead time, danh sách IPQC Content được chọn, và với mỗi IPQC Content có Side A/B, Specification Limit, Control Limit. Bộ được khai theo khoá ở Q9 và có hai biến thể Common và Individual.

➡️ Đề xuất:
- Gọi là **IPQC Spec**. Tên này khớp với màn hình "IPQC Spec ItemName / ItemCode" của demo.
- "Spec" đứng một mình đưa vào danh sách _Avoid_, vì dễ nhầm với Specification Limit.

**Trả lời:**

---

## C. Thiết bị và tiêu chuẩn

### Q22 – IPQC Content chỉ định Equipment type hay Equipment model?

➡️ Đề xuất:
- Chỉ định **Equipment type**, ví dụ "đo bằng OMM". Laboratory chọn máy cụ thể khi đo.
- Nếu một chỉ tiêu chỉ đo được trên một số model, IPQC Content có thêm danh sách Equipment model được phép. Danh sách này không bắt buộc.

**Trả lời:**

### Q33 – Specification Limit có được khai một phía không, và Control Limit áp dụng cho cả X và R?

➡️ Đề xuất:
- Specification Limit được khai một phía, tức chỉ có LL hoặc chỉ có UL. Ví dụ: độ dày mạ chỉ có giới hạn dưới.
- Control Limit áp dụng cho cả biểu đồ trung bình (X) và biểu đồ biên độ (R). Biểu đồ R chỉ có Center line và UCL.
- Center line là giá trị trung tâm thống kê, không phải giá trị mục tiêu do kỹ thuật đặt.

**Trả lời:**

### Q34 – Result File Mapping khai theo khoá nào?

Một file VHX có thể chứa giá trị của nhiều IPQC Content, nên hệ thống cần biết ô nào ứng với IPQC Content nào.

➡️ Đề xuất:
- Khoá là **Equipment model × IPQC Content**. Không có Laboratory Location trong khoá. Không có Production Process trong khoá, vì IPQC Content đã thuộc một Production Process.
- Hai máy cùng model đặt ở hai phòng dùng chung một mapping.
- **[khác demo]** Demo tạo layout riêng theo Vị trí và Loại thiết bị.
- **Rủi ro:** nếu hai phòng dùng hai template Excel khác nhau cho cùng một model, phải đưa Laboratory Location trở lại khoá.

**Trả lời:**

### Q35 – Một phép đo trong chuỗi đo tuần tự gọi là gì?

Yêu cầu đã ghi ở [#8](https://github.com/trungkien87/LabTestSystem/issues/8#issuecomment-6472640297): cùng một mẫu phải lần lượt qua các phép đo đã cấu hình theo IPQC Content.

➡️ Đề xuất:
- Gọi là **Measurement Step**, đánh số bằng **Step No** (1, 2, 3…).
- Không dùng "Sequence", vì từ này đã dành cho Process Sequence.
- Không dùng "route", vì từ này đã dành cho Route.
- Không dùng "bước" đứng một mình.

**Trả lời:**

---

## D. Location và tổ chức

### Q12 – Department chỉ dùng để phân quyền?

➡️ Đề xuất:
- Department (PE/PR/QA/SF) chỉ là phòng ban của user. Department không nằm trong tên Laboratory Location và không gắn với IPQC Content.
- User được thao tác ở Location nào và Production Process nào là do phân quyền quyết định ([#10](https://github.com/trungkien87/LabTestSystem/issues/10)).
- **[khác demo]** Demo dùng "Department" theo 3 nghĩa.

**Trả lời:**

### Q27 – Tên Laboratory Location có được dịch theo ngôn ngữ giao diện không?

➡️ Đề xuất: không. Tên Location là dữ liệu và chỉ viết bằng tiếng Anh theo dạng `Factory – Floor – Room`. Yêu cầu đa ngôn ngữ F1 chỉ áp dụng cho nhãn và thông báo trên giao diện.

**Trả lời:**

### Q28 – Một Laboratory gồm một hay nhiều Laboratory Location?

Hai tình huống cần phân biệt:
- **(a)** Lab đo của QA ở F1 có hai phòng: `F1 – 1st Floor – QA Lab` và `F1 – 3rd Floor – Reliability`. Đây là 1 Laboratory có 2 Location, hay 2 Laboratory?
- **(b)** Khu đo `F5 – 1st Floor – Etching` nằm trong xưởng. Khu này thuộc một Laboratory của PR, hay không thuộc Laboratory nào?

➡️ Đề xuất:
- **Laboratory** là đơn vị quản lý: có tên, thuộc một Department (PR hoặc QA), có Leader và Operator. Mỗi Laboratory có **một hoặc nhiều** Laboratory Location.
- **Laboratory Location** là phòng vật lý. Mỗi Laboratory Location thuộc **đúng một** Laboratory.
- Theo đề xuất này, (a) là 1 Laboratory có 2 Location, và (b) thuộc một Laboratory của PR.
- Nếu ở xưởng mỗi Laboratory luôn chỉ có một phòng, nên gộp hai khái niệm làm một để bớt một tầng master data.

**Trả lời:**

### Q29 – "Laboratory Leader" là ai?

Câu này phụ thuộc Q28. Nếu Q28 chọn gộp hai khái niệm, đọc "gán vào Laboratory" thành "gán vào Laboratory Location".

➡️ Đề xuất:
- Laboratory Leader là một user có Job Level **Leader**, được gán vào một Laboratory. Đây không phải Job Level thứ năm.
- Mỗi user được gán vào tối đa một Laboratory.
- Leader được nhận mẫu mặc định tại các Location của Laboratory mình. Operator chỉ nhận mẫu khi được phân quyền ([#10](https://github.com/trungkien87/LabTestSystem/issues/10)).

**Trả lời:**
