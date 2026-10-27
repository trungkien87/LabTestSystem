# Định dạng logfile/template theo Equipment type

> Research cho issue #3 "Tổng hợp định dạng logfile/template theo Equipment type".
> Nguồn duy nhất: snapshot `docs/source/` (chuyển từ `LAB_Test_system_261013.xlsx`). Không dùng nguồn ngoài.
> Tài liệu này **chỉ ghi sự thật đầu vào**, không quyết định kiến trúc hay data model.
>
> Quy ước: **[Sự thật]** là điều đọc thấy trực tiếp trong file/ảnh/ô được trích. **[Suy luận]** là điều tác giả rút ra từ việc đối chiếu các nguồn, chưa ai xác nhận. Đường dẫn ảnh là tương đối từ `docs/research/`.

## Tóm tắt

- Requirement 9 chỉ định nghĩa 4 kiểu "Định dạng xử lí logfile": **VHX: mỗi pcs một file; Laser microscope: nhiều pcs một file; Nikon: dùng định dạng template; VHX 5500: nhập trực tiếp lên web** ([02-requirements.md](../source/02-requirements.md), mục 9, dòng "Mục đích" 3). Nguồn mẫu thực tế cho thấy **nhiều hơn 4 kiểu** (xem bảng).
- Có **mẫu logfile thô** (ảnh chụp nội dung file) cho: **VHX** (CSV "Plane measurement results data", 1 pcs/file), **Laser microscope** (CSV nhiều pcs/file, cột A = `điểm đo-pcs`), **Mitutoyo/OMM** (CSV dạng `FeatureLabel A1[i,j]`, nhiều pcs/file), **T-King** (`LOGFILE TKING.xlsx`, mỗi lần đo một hàng ngang).
- Có **template/file báo cáo** (không phải logfile thô) cho: Impedance và VHX QA Lab (cùng mẫu "CPK Data Sheet - Rev 06"), Zygo (ACF Roughness), báo cáo cross-cut BVH, báo cáo SR sau crosscut, các file tổng hợp nhiều lot (Etching, DFR/SR Development).
- **Không có mẫu nào** cho **Nikon** và **XRF**, dù cả hai được nêu tên trong nguồn. Impedance chỉ có template kết quả, chưa có logfile thô (biên bản họp 2026-10-21 ghi "Khảo sát logfile: Mitutoyo, Impedance" là việc còn mở).
- Tên folder/tên file đang **mã hóa thông tin khác nhau theo từng công đoạn** (Item-Lot-loại hàng-máy; Item-Lot_ID đo+công đoạn; điểm đo; số pcs; mặt A/B...). Không có một quy tắc đặt tên chung.
- Đích nhập WCS hầu như luôn là **5 cột kết quả + X + R**, trong khi logfile có 3, 5, 6, 32 hoặc 36 pcs. Đây là special case chung.

## Bảng tổng hợp

Ký hiệu cột "Định dạng": **1 pcs/file**, **nhiều pcs/file**, **template** (file báo cáo/Excel có cấu trúc cố định), **nhập tay** (đọc giá trị trên máy rồi gõ vào file hoặc web).

| Equipment type | Công đoạn / Ref | Định dạng | Tên file/thư mục mã hóa gì | Vị trí dữ liệu | IPQC Content đo | Nguồn |
|---|---|---|---|---|---|---|
| **VHX** (logfile CSV) | UV Laser / Ref.01 | 1 pcs/file (CSV). Lỗ TH tách file riêng `n-TH.csv` | Folder `Item-Lot-Loại hàng-Máy` (vd `4M0024-00110-R-70`); file `n.csv` = PCS No | CSV mục `[Main]`: cột C (Result), hàng 6 = No.1 Diameter, hàng 7 = No.2 Diameter | BVH Top, BVH Bottom, Taper Bottom/Top (≥80%), TH hole size | Ref.01 ảnh 01-A9, 02-D9, CSV rows32-37, shape |
| **VHX** (logfile CSV + ảnh) | Copper Plating (cross-cut) / Ref.05; Etch back De-smear / Ref.02 | 1 pcs/file: `n.csv` + `n.jpg` + `nS.jpg`; kèm 1 file báo cáo `.xlsx` | Folder `Item-Lot_<số>+<mã>` (vd `4M0024-00234_520704+RR14_76281`) → loại lỗ (`BVH BS`, `BVH NBS`, `PTH`) → nội dung (`DODAY`); báo cáo `…-OK.xlsx` (hậu tố = Judgement) | Nội dung CSV **không có ảnh**. Báo cáo: mỗi hàng = Sample No, mỗi cột = một IPQC content | Via size Top/Bottom, Taper, độ dày đồng thành lỗ (trái/phải/PI/chất dính), tổng Cu, đáy lỗ, base Cu, etching back, etch down, lồi/lõm | Ref.05 ảnh 01-G7, 02-P7, 03-A8; Ref.02 rows 25-38 |
| **VHX** (logfile CSV + ảnh) | SR Printing (Cross cut SR) / Ref.07 | 1 pcs/file `n.csv` + `n.jpg` + `nS.jpg` | Folder `Item-Lot_<số> <chữ>` (vd `4M0024-00166_507356 SAY`) → folder **điểm đo** (`HA`, `I1AB`, `I1B`, `I2AB`); báo cáo `4M0024-00166+00204.xlsx` | CSV `[Main]`: cột C hàng 6-9 = `Parallel` No.1..4 → khớp 4 content của vị trí HA | SRCP, SR UNDER CUT, SR/CU, CU DUOI SR, SR/MA, SR/MB, TONG CAO/THAP… | Ref.07 ảnh 01-Q1, 02-J6, 03-V6, 04-A9, shape |
| **VHX** (QA Lab, template) | RR SS Etching cross-cut / Ref.04 | Template "CPK Data Sheet - Rev 06", nhiều pcs/file | Header: Item, Lot No, Date, Công đoạn `CROSSCUT`, ID | Hàng 72 = Dim (TOP/BOTTOM/CIRCUIT HIGHT) theo cột B1,C1,B2,C2…; hàng 92-123 = pcs 1..32 | Độ rộng mạch Top/Bottom, độ dày đồng (circuit height), khoảng cách C | Ref.04 rows 56-123 |
| **VHX nhập tay** (VHX, VHX 5500, VHX970, "VHX không xuất logfile") | DFR Development / Ref.03; SR Development / Ref.08; SR Heat cure; ENIG finger/pad; 2DID Laser marking | Nhập tay vào file tổng hợp nhiều lot (Ref.03, 08) hoặc web (Req.9: VHX 5500) | Không có logfile | Ref.03: hàng = lot; khối B1..B4, mỗi khối Center + 1..32. Ref.08: khối B1..B3 (Aside), B4..B6 (Bside), mỗi khối Center/Min/Max/…/cpk + 1..5 | Hole and button misalignment (Ref.03); SR opening size (Ref.08); Golden finger width, SMD/NSMD pad (ENIG) | Ref.03 shape + CSV rows9-16; Ref.08 shape + CSV rows8-16; 03-ipqc rows 9, 26-28, 42-44; Req.9 |
| **Laser microscope** | RR SS Etching (Đo mạch) / Ref.04 | Nhiều pcs/file; mỗi file = một loại nội dung đo | Folder `CR_1_69DRCT_4M0023_02060_1.94_#5_511000_W05`; file `B_Plane(Point height).csv`, `B_Profile.csv` | Cột A = `điểm đo-pcs` (vd `B1-1`); Plane: cột D,E,F (header hàng 1-3); Profile: cột C (`Perp.1`), từ hàng 4/5 | Độ rộng mạch Top/Bottom, khoảng cách, độ dày đồng, etching factor (B1..B7, C1..C6) | Ref.04 ảnh 01-A9, 02-J9, 03-V9, 04-A169, shape |
| **Mitutoyo** (OMM) | CVL full lamination (CL shift) / Ref.09 | Nhiều pcs/file; mỗi file CSV có kèm `.txt` cùng tên; kèm báo cáo CPK `.xlsx` | Folder `Item-Lot_ID đo+Công đoạn` (vd `4M0024-00041_510841+CL`); file theo nhóm điểm: `C`, `MA`, `MB`, `XN FAI A3 PT1+7+19+23` | CSV bảng: Feature Type, FeatureLabel (`A1[i,j]`), FeatureID, Output Item, Actual, Nominal, Deviation, Upper/LowerTol, PassFail | CL shift A-1/A-2/A-3, FAI 11, FAI 14, Alignment mark C (C1, C2) | Ref.09 ảnh 01-A7, 02-E7, 03-K7, 04-A29; 03-ipqc row 37 (Link `21. Mitutoyo`) |
| **T-King** | Guide hole / Ref.06 | 1 file Excel `LOGFILE TKING.xlsx`, **mỗi lần đo = 1 hàng ngang** | Tên file cố định, không mã hóa lot | Hàng dữ liệu: cột A = ngày giờ, cột C..R = 16 giá trị "Distance from the two round", cột S = OK; phía trên là khối thống kê | Đường kính lỗ đục (Dimension) | Ref.06 ảnh 01-M19, 02-A60, shape; 03-ipqc row 24 |
| **Impedance** | RR SS Etching / Ref.04 (QA Lab); SUS Pre-tack / Ref.11 | Template "CPK Data Sheet - Rev 06", nhiều pcs/file. **Chưa có logfile thô** | Header: Part Number, Item, Lot No, Date, Công đoạn `CROSSCUT`, ID | Cột BP = `CHAN 1`, BQ = `CHAN 2` (Nominal 44, ±8.8); hàng 162-167 = pcs 1..6 | Điện trở impedance sau Etching / sau SUS Press; Impedance single (Ref.11) | Ref.04 rows 126-168 + CSV rows133-157; ảnh 04-A169; Ref.11 ảnh 01-A35 |
| **Zygo** | ENIG (độ nhám) / Ref.10 | Template "ACF ROUGHNESS RESULT", nhiều pcs/file; nhiều sheet theo số điểm và số pcs | Tên sheet: `Form 1 đ -6pcs`, `Form 2đ -6pcs`, `Form 4 đ -6pcs`, `Form 6 đ-6 pcs`, `Form 1 đ -32pcs (2)`, `Form 4 đ-32 pcs`, `Form 6 đ-32 pcs` | Bảng trái: Sample 1..6 × điểm A1,A2,B1,B2 × Sa,Sq,Sz,Sdr. Bảng phải: Pt No 1..6 × A1-Sa, A1-Sq, A2-Sdr, B1-Sa, B1-Sq, B2-Sdr + thống kê | Sa, Sq, Sdr | Ref.10 ảnh 01-A11, 02-A44; 03-ipqc row 47 |
| **Nikon** | _(không rõ)_ | Req.9: "Sử dụng định dạng template" | **Không có mẫu** | **Không có mẫu** | **Không rõ** | Req.9; biên bản họp 2026-10-09 |
| **XRF** | ENIG (độ dày mạ Ni/Pd/Au) / Ref.10 | **Không có mẫu** | Chỉ có link folder `…\00000.Do day xray\NAM 2026\THANG 9\18-9-2026` | **Không có mẫu** | Plating thickness Ni, Pd, Au; 4 điểm/pcs × 5 pcs/sheet/lot | 03-ipqc row 40; Ref.10 ảnh 02-A44 |

## Chi tiết theo Equipment type

### 1. VHX: logfile CSV, mỗi pcs một file

**Định nghĩa trong requirement.** [Sự thật] "VHX: Mỗi pcs một file" ([02-requirements.md](../source/02-requirements.md) mục 9, Mục đích 3).

#### 1a. UV Laser (Ref.01)

- **Thư mục và tên file.** [Sự thật] Ảnh [01-A9](../source/assets/ref-01-uv-laser/01-A9.png): đường dẫn `anh-aom-f5 > VHX data > THANG 9 > 1-9 > 4M0024-00110-R-70`; trong đó có `1.csv`, `1-TH.csv`, `2.csv`, `2-TH.csv`, `3.csv`, `3-TH.csv` (mỗi file 1 KB). Shape chép trong [ref-01-uv-laser.md](../source/ref/ref-01-uv-laser.md): "Tên file tương ứng với pcs no", "Tên file tương ưng với PCS No".
- [Sự thật] Bảng tổng hợp [ref-01-uv-laser-rows32-37.csv](../source/ref/data/ref-01-uv-laser-rows32-37.csv) có cột `SourceFile` (cột BE) với giá trị `4M0024-00400-R-31`, trùng với các cột Item (`4M0024`), Lot (`00400`), Loại hàng (`R`), Máy (`31`) của cùng hàng.
- [Suy luận] Tên folder = `Item-Lot-Loại hàng-Máy`. Hậu tố `-TH` = lỗ TH (cột H "Kiểu lỗ (BVH/TH)" của bảng tổng hợp có hai giá trị BVH và TH). Ngày `1-9` là ngày đo. Có 3 pcs vì MP lấy "3 pcs/panel/laser head/lot" (ảnh [05-E39](../source/assets/ref-01-uv-laser/05-E39.png)).
- **Nội dung file.** [Sự thật] Ảnh [02-D9](../source/assets/ref-01-uv-laser/02-D9.png): CSV có tiêu đề `Title: Plane measurement results data`, `Date saved`, `Comment`, rồi các mục `[ Main ]`, `[ XY Measure ]`, `[ Area ]`. Trong `[ Main ]`: hàng 6 `1 | Diameter | 78.22 | µm`, hàng 7 `2 | Diameter | 68.96 | µm`, hàng 8 `Count | 0 | pcs`. Shape: "Nội dung IPQC tương ứng của PCS No", "ô gái trị tương ứng với nội dung".
- [Suy luận] No.1 = Top, No.2 = Bottom. Căn cứ: trong bảng tổng hợp, hàng 35 (Bot/Top) = 0.880025… = 68.95 / 78.35 (hàng 34 / hàng 33). Taper được **tính**, không đo.
- **Màn hình cấu hình (prototype).** [Sự thật] Ảnh [03-G10](../source/assets/ref-01-uv-laser/03-G10.png): màn "LAB TEST SYSTEM" chọn Vị trí / Tên công đoạn / Loại thiết bị = VHX; cấu hình riêng **Side A** và **Side B**, mỗi IPQC content có: Đường dẫn thư mục (vd `BVH NBS\DK`), Tên file (`[x]`), Định dạng file (`.csv`), Công thức (vd `#1/#2*100`, các hàm AVG/SUM/MAX/MIN/ABS/ROUND/SQRT), Ô lấy giá trị (`C5`, `C6`, `C7`, hoặc `Theo Item (2)`).
- **Template báo cáo.** [Sự thật] Ảnh [04-A39](../source/assets/ref-01-uv-laser/04-A39.png) "BÁO CÁO ĐO ĐƯỜNG KÍNH LỖ SAU UV LASER": mỗi STT 3 hàng (Top, Bottom, Bottom/Top >80%), cột Lỗ 1/Lỗ 2/Lỗ 3; ghi rõ 3 sơ đồ vị trí: 32 lỗ/sheet senko test (NPI), 3 lỗ/WS (mass), 3 lỗ/coupon cuối roll.
- **Đích WCS.** [Sự thật] Ảnh [06-J39](../source/assets/ref-01-uv-laser/06-J39.png): TH Kích thước 1/2 × 3 lỗ; BVH Kích thước 1/2 × 3 lỗ × Top/Bottom/Tỷ lệ, kèm X, R.
- **IPQC Content.** [Sự thật] [03-ipqc-contents.md](../source/03-ipqc-contents.md) Excel row 3-5: BVH Top, BVH Bottom, PTH Hole size (top); Method actual `Cross cut + VHX`; Công đoạn lấy kq `In line`; Phương pháp `Tổng hợp logfile theo ngày`.

#### 1b. Copper Plating cross-cut (Ref.05) và Etch back De-smear (Ref.02)

- **Thư mục.** [Sự thật] Ảnh [03-A8](../source/assets/ref-05-copper-plating/03-A8.png): `…00.Lab F1 > 2026 > 9. THÁNG 9 > 2. Cross cut sau Copper > …` chứa 3 folder `BVH BS`, `BVH NBS`, `PTH` và file `4M0024-00234_520704+RR14_76281-OK.xlsx`. Ảnh [01-G7](../source/assets/ref-05-copper-plating/01-G7.png): `2026 > 9. THÁNG 9 > 2. Cross cut sau Copper > 11-09 > 4M0024-00234_520704+RR14_76281 > BVH NBS > DODAY` chứa `1.csv, 1.jpg, 1S.jpg` … `6.csv, 6.jpg, 6S.jpg`.
- [Suy luận] Phân cấp: ngày đo → `Item-Lot_<số>+<mã>` → loại lỗ/mặt (BS/NBS = có/không bonding sheet, theo tiêu đề báo cáo "MẶT KHÔNG CÓ BONDING SHEET") → loại nội dung (`DODAY` = độ dày; ví dụ `BHV NBS\DK` trong requirement 30 và `BVH NBS\DK` trong ảnh 03-G10 gợi ý `DK` = đường kính). `520704` và `RR14_76281` chưa rõ nghĩa. `.jpg` / `S.jpg` là ảnh chụp mặt cắt (S có thể là ảnh có số đo); chưa xác nhận.
- **Nội dung CSV:** **không có ảnh chụp nội dung** CSV cho Ref.05. (Gap.)
- **Báo cáo.** [Sự thật] Ảnh [02-P7](../source/assets/ref-05-copper-plating/02-P7.png) và bảng [ref-02-de-smear-plasma.md](../source/ref/ref-02-de-smear-plasma.md) rows 25-38: "KẾT QUẢ CROSS CUT LỖ BVH - MẶT KHÔNG CÓ BONDING SHEET"; header Item name, Item code (`4M0024-00234_520704+RR14_76281` ở Ref.05, `4M0024-00235_520704+RR14_76281` ở Ref.02), Loại mẫu, ngày, Judgement, Approve; mỗi hàng = Sample No 1..n; cột D..S = Taper, Via size Top/Bottom, các độ dày đồng, etching back, etching downbase, lồi/lõm. Ref.02 hàng 29 đánh số cột 1..15, hàng 30 ghi `-, -, 1, 2, 3, -, 4, 5, -, -, 6, 7, 8, 9, 10`.
- [Suy luận] Hàng 30 của Ref.02 là bảng ánh xạ "số thứ tự phép đo trong CSV → cột báo cáo" (độ dày lấy từ CSV theo thứ tự 1..10; Via size Top/Bottom có `-` vì lấy từ nguồn khác, ví dụ folder đường kính; Taper là cột tính).
- **IPQC Content / tần suất.** [Sự thật] Ảnh [04-A27](../source/assets/ref-05-copper-plating/04-A27.png): BVH hole 10 nội dung, PTH hole 8 nội dung; "1 hole (B1)/pc x 6 pcs (pcs 1; 5; 7; 12; 18; 21)/panel x 1 panel No.6/sheet x 1 sheet/lot". [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 19-23: `Cross cut + VHX`, QA lab, `VBA tổng hợp logfile theo lot`.
- **Đích WCS.** [Sự thật] Ảnh [06-S27](../source/assets/ref-05-copper-plating/06-S27.png), [07-Z27](../source/assets/ref-05-copper-plating/07-Z27.png): TH/BVH × Pcs 1..5 + X + R.
- **De-smear Etching rate.** [Sự thật] Ref.02 rows 40-61: bảng "Test etching rate máy R/R plasma No.6", 9 điểm × Before/After/Diff/Etc amount/Etc rate theo vật liệu MB/PK; Method `weighting loss` ([03-ipqc-contents.md](../source/03-ipqc-contents.md) row 7-8). Thiết bị là cân, nhập tay, **không phải VHX**.

#### 1c. SR Printing cross-cut (Ref.07)

- **Thư mục.** [Sự thật] Ảnh [02-J6](../source/assets/ref-07-printing/02-J6.png): `ok2ship > 00.Lab F1 > 2026 > 9. THÁNG 9 > 3. Cross cut SR > 14-09 > 4M0024-00166_507356 SAY > HA`, chứa `1.csv/1.jpg/1S.jpg` … `5.csv/5.jpg/5S.jpg`. Ảnh [04-A9](../source/assets/ref-07-printing/04-A9.png): cùng cấp có folder `HA`, `I1AB`, `I1B`, `I2AB` và `4M0024-00166+00204.xlsx`. Shape: "Tạo folder với các điểm đo".
- **Nội dung CSV.** [Sự thật] Ảnh [01-Q1](../source/assets/ref-07-printing/01-Q1.png): cùng format "Plane measurement results data", nhưng `[ Main ]` có 4 dòng `Parallel`: 35.1, 2, 16.1, 10.9 µm (Date saved 9/15/2026 2:07 AM).
- [Sự thật] Báo cáo ảnh [03-V6](../source/assets/ref-07-printing/03-V6.png) "KẾT QUẢ ĐO SR SAU CROSSCUT": vị trí HA, pcs 1 = SRCP 35.1, SR UNDER CUT 2.0, SR/CU 16.1, CU DUOI SR 10.9; khớp đúng 4 giá trị của CSV. Cột kết quả 1..10, nhưng chỉ 1..5 có dữ liệu.
- [Suy luận] Mỗi folder vị trí có số dòng `Parallel` khác nhau (HA: 4; I1AB: 6; I1B: 4; I2AB: ≥2, theo số nội dung trong báo cáo). Thứ tự dòng `Parallel` = thứ tự nội dung trong báo cáo.
- [Sự thật] Đích WCS ảnh [07-Q23](../source/assets/ref-07-printing/07-Q23.png): chỉ "Độ dày SR (Cross cut)" Mặt A / Mặt B × 5 pcs + X + R. Tần suất ảnh [05-A23](../source/assets/ref-07-printing/05-A23.png): khoét 5 pcs/sheet x 1 sheet/lot; Cross section & OMM.

#### 1d. VHX QA Lab cho Etching (Ref.04)

- [Sự thật] [ref-04-rr-ss-etching.md](../source/ref/ref-04-rr-ss-etching.md) rows 56-123 ("VHX - QA Lab"): "CPK Data Sheet - Rev 06", mã `OPA-QA-0225-01-rev 03`; header Item `7S4683`, Lot No, Date, Công đoạn `CROSSCUT`, ID (2 người), Judge. Hàng 63: nhóm cột B1, C1, B2, C2, B3, C3, B4, C4; hàng 72: Dim TOP / BOTTOM / CIRCUIT HIGHT; hàng 73-79: Nominal, Tol, USL, LSL; hàng 92-123: pcs 1..32.
- Không có ảnh logfile thô VHX của bước này.

### 2. VHX nhập tay (VHX 5500, VHX970, "VHX không xuất logfile")

- [Sự thật] Requirement 9: "VHX 5500: Nhập trực tiếp lên web".
- [Sự thật] Ref.03 shape: "Nhìn giá trị đo trên máy VHX rồi nhập vào file". Ref.08 shape: "Đo bằng máy VHX và nhập thủ công vào file". [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 9 và 26: Phương pháp `Nhập kết quả đo trực tiếp từ máy vào file tổng hợp`, Công đoạn lấy kq `Đo mạch F1`.
- [Sự thật] Row 27-28 (SR Heat cure): Method QCP `Measure at coupon by Mitutoyo equipment`, Method actual `Machine VHX 5500`. Row 42-44 (ENIG finger width, SMD/NSMD pad): `VHX (Không xuất logfile)`. [50-2did-laser-marking.md](../source/process-control/50-2did-laser-marking.md) row 7: VHX machine, record `Manual`.
- **DFR Development (Ref.03).** [Sự thật] [ref-03-dfr-development-rows9-16.csv](../source/ref/data/ref-03-dfr-development-rows9-16.csv): file tổng hợp, mỗi hàng = một lot (Date, Item Code, Batch No); 4 khối B1..B4, mỗi khối `Center` + cột 1..32; cuối: `Just (OK\NG)`, `Công nhân`, `Công nhân nhập`. Dữ liệu mẫu chỉ điền 8 giá trị cho B1, B2; cột Center là `#REF!`. WI ảnh [01-A17](../source/assets/ref-03-dfr-development/01-A17.png): B1 (Mặt A), B2, B3 (Mặt B), "12 pcs/sheet x 1 sheets/ lot đầu tiên của build", VHX machine X200. WCS ảnh [02-AA17](../source/assets/ref-03-dfr-development/02-AA17.png): Độ lệch tâm Via/TH-Button, Mặt A/B × Sheet 1/2 × 5 + X + R.
- **SR Development (Ref.08).** [Sự thật] [ref-08-sr-development-rows8-16.csv](../source/ref/data/ref-08-sr-development-rows8-16.csv): hàng = lot; Aside B1, B2, B3 và Bside B4, B5, B6; mỗi khối Center, Min, Max, Max, Min, Ave, R, cpk + 1..5; `Just (OK\NG)`, `Công nhân ĐO`, `Công nhân nhập`, `Comment`. WI ảnh [01-A19](../source/assets/ref-08-sr-development/01-A19.png): "Đo đường kính vùng mở SR bằng máy VHX5500 và VHX970, độ phóng đại x500", A side B1/B2/B3, 5 pcs/sheet x 1 sheet/Lot. WCS ảnh [03-I19](../source/assets/ref-08-sr-development/03-I19.png): Vùng mở SR Điểm1..12 × pcs 1..6 + X + R.

### 3. Laser microscope: nhiều pcs một file (Ref.04)

- [Sự thật] Requirement 9: "Laser microscope: Nhiều pcs một file".
- **Thư mục và tên file.** [Sự thật] Ảnh [01-A9](../source/assets/ref-04-rr-ss-etching/01-A9.png): folder `CR_1_69DRCT_4M0023_02060_1.94_#5_511000_W05`, chứa `B_Plane(Point height).csv` (3 KB) và `B_Profile.csv` (2 KB). Shape: "1. Tên file tương ứng với các nội dung đo khác nhau của PCS".
- [Suy luận] Các trường của tên folder trùng với các cột của file tổng hợp Etching (rows 44-53, [CSV](../source/ref/data/ref-04-rr-ss-etching-rows44-53.csv)): `CR` ↔ cột G "Chú ý" (giá trị CR/SK); `69DRCT` = Item name; `4M0023` = Item; `02060` = Lot; `1.94` ↔ cột E "Điều kiện Etching" (vd `2,02`); `#5` ↔ cột F "LAZER NO" (vd `5`); `511000` = ID người đo; `W05` ↔ cột D (vd `W047`). Trường `1` chưa rõ. Tiền tố `B_` của tên file có thể là Mặt B.
- **Nội dung file.** [Sự thật] Ảnh [02-J9](../source/assets/ref-04-rr-ss-etching/02-J9.png) (Plane): hàng 1 header `Measurement | Plane(Point height) …`, hàng 2 `Laser + Optical` và chỉ số `2, 3, 4`, hàng 3 đơn vị `um`; từ hàng 4: cột A = `B1-1`, `B1-10`, `B1-11`, `B1-12`, `B1-2`… (B1, B2 có 12 pcs; B3 chỉ có cột D, E); cột D, E, F = giá trị. Ảnh [03-V9](../source/assets/ref-04-rr-ss-etching/03-V9.png) (Profile): cột C `Profile / Perp.1 / 1 / um`, từ hàng 5: `B1-1`, `B3-1`, `B2-1`, `B1-2`… Shape: "Cột A: Tên điểm đo-pcs no vd: B1-1: Điểm đo B1 - Pcs 1"; "Nội dung 1/2/3" (Plane), "Nội dung 4" (Profile).
- [Suy luận] Plane cột D ≈ 18 (≈ spec Top 20±5), E ≈ 23 (≈ Bottom 25±5), F ≈ 26; Profile ≈ 10 (≈ độ dày đồng 11 +3/-2.5) theo WI ảnh [04-A169](../source/assets/ref-04-rr-ss-etching/04-A169.png). Ánh xạ chính xác cột → IPQC content chưa được ghi trong nguồn.
- **File tổng hợp nhiều lot.** [Sự thật] [CSV rows44-53](../source/ref/data/ref-04-rr-ss-etching-rows44-53.csv): "Daily report of Etching machine Inner"; mỗi hàng = một lot; các khối `B1 - T`, `B1 - B`, `Độ dày đồng-B1`, `Etching factor`, `C1`, … đến B7; mỗi khối có `Center, MIN, MAX, Min, Max, Aver, R` + cột 1..36 (khối Etching factor: `Chuẩn` + 1..6); tiếp theo `Just (OK\NG)`, `ID ĐO`, `ID NHẬP`, các khối D1-1..D2-4, `CODE 1..3` (vd `4M0020-00009-170-6`). Hàng 48: "KHÔNG XÓA DÒNG NÀY NHÉ". Có lot điền 5 pcs, có lot điền 36 pcs. [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 10-17: Phương pháp `Copy kết quả đo vào file tổng hợp nhiều lot`.
- **IPQC Content.** [Sự thật] Row 10-17: MD/TD trace width top/bottom, MD/TD space, Copper thickness, Etching factor; Method actual `Cross cut + VHX & Laser Microscope`; NPI 32 pcs/lot, MP 5 pcs/lot. WI ảnh [04-A169](../source/assets/ref-04-rr-ss-etching/04-A169.png): Mặt A B1, B2, C1, C2, B3; Mặt B B5, B6, B7, C5, C6; Laser microscope X50; "IPQC: Đối với đo Laser Microscope: 5pcs/sheet x 1sheet/lot x All Lot". WCS ảnh [05-F169](../source/assets/ref-04-rr-ss-etching/05-F169.png): Mặt A/B × (Top/Bottom/Khoảng cách) 1..5 × 5 pcs + X + R.

### 4. Mitutoyo (OMM) (Ref.09)

- **Nhận diện.** [Sự thật] [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 37 (Fiducial to fiducial, CVL full lamination), Link: `…\9. THÁNG 9\21. Mitutoyo\7. KET QUA HANG CL SHIFT`. Ảnh [01-A7](../source/assets/ref-09-cvl-full-lamination/01-A7.png) có breadcrumb `…ET QUA HANG CL SHIFT > 4M0024-00041_510841+CL`. [Suy luận] Logfile Ref.09 là của máy Mitutoyo; Ref.09 chỉ gọi là "OMM".
- **Thư mục và tên file.** [Sự thật] Ảnh 01-A7: `4M0024-00041.xlsx`, `C.CSV`, `C.txt`, `MA.CSV`, `MA.txt`, `MB.CSV`, `MB.txt`, `XN FAI A3 PT1+7+19+23.CSV`, `XN FAI A3 PT1+7+19+23.txt`. Báo cáo ảnh [02-E7](../source/assets/ref-09-cvl-full-lamination/02-E7.png): Item `4M0024`, Lot No `00041`, Công đoạn `CL`, ID đo `510841`.
- [Suy luận] Folder = `Item-Lot_ID đo+Công đoạn`. `C` ↔ dim C1, C2; `MA`/`MB` có thể là Mặt A/Mặt B hoặc nhóm điểm; `XN FAI A3 PT1+7+19+23` = đo xác nhận lại FAI A3 ở pcs 1, 7, 19, 23. Chưa xác nhận.
- **Nội dung CSV.** [Sự thật] Ảnh [03-K7](../source/assets/ref-09-cvl-full-lamination/03-K7.png): cột `Feature Type | FeatureLabel | FeatureID | Output Item | Actual | Nominal | Deviation | Upper Tol | LowerTol | PassFail`; hàng: `Distance | A1[1,1] | 8 | DY | 0.646 | 0.615 | 0.031 | 0.15 | -0.15 | PASS`, `A1[1,2]` … `A1[3,6]`.
- [Suy luận, đã đối chiếu số] `A1[i,j]` ↔ pcs `(i-1)*6 + j`: 12 giá trị A1 đầu tiên trong CSV (0.646, 0.6472, 0.6526, 0.6619, 0.6694, 0.6754, 0.6502, 0.6454, 0.6521, 0.6666, 0.6835, 0.6952) khớp làm tròn với pcs 1..12 cột A1 của CPK sheet (0.646 … 0.695). Có thể 6 = số cột pcs trên sheet.
- **Báo cáo.** [Sự thật] CPK Data Sheet - Rev 06: cột A1, A2, A3, FAI 11, FAI 14, C1, C2 (Dimension Description `OMM`); hàng pcs 1..32 (C1, C2 chỉ 5 pcs).
- **IPQC Content.** [Sự thật] Ảnh [04-A29](../source/assets/ref-09-cvl-full-lamination/04-A29.png): FAI 11, FAI 14, CL shift A-1/A-2/A-3: "32pcs/ lot x All lot, đo tại vị trí 1->32 trên bản vẽ", OMM; Alignment data (vị trí mark C): 5pcs/lot, OMM machine. WCS ảnh [05-J29](../source/assets/ref-09-cvl-full-lamination/05-J29.png): Kích thước vùng mở CL Điểm 1..16 × 6 pcs, 6pcs/sheet/lot.
- **Nơi khác dùng Mitutoyo.** [Sự thật] 2DID code size & location ([50-2did-laser-marking.md](../source/process-control/50-2did-laser-marking.md) row 10, record Manual); Ref.12 "Đo vùng inkjet sau in bằng máy T-King hoặc Mitutoyo" ([03-H18](../source/assets/ref-12-inkjet/03-H18.png) mục 6). Không có mẫu logfile cho các chỗ này.

### 5. T-King (Ref.06)

- [Sự thật] Ảnh [01-M19](../source/assets/ref-06-guide-hole/01-M19.png) (ảnh chụp màn hình bằng điện thoại): `LOGFILE TKING.xlsx`, Sheet1. Cột B nhãn: Name, Standard value, The tolerance, Under Tolerance, Max, Min, Average, Ca, Cp, Cpk, Range; cột C..R tiêu đề "Distance from the two round". Hàng dữ liệu: cột A `19/10/2026 13:56`, 16 giá trị (xen kẽ ≈240 và ≈132, vd `240,1193`, `132,0274`), cột S `OK`. Dùng **dấu phẩy thập phân**.
- [Sự thật] Shape: "Công nhân copy thủ công chuyển dữ liệu từ hàng ngang sang cột dọc". Template giấy rows 10-55 ([ref-06-guide-hole.md](../source/ref/ref-06-guide-hole.md)): "Kết Quả Đo Đường Kính Lỗ Đục Của Máy Guide Hole", header Ngày / Máy GH no / Ca / Công nhân GH / Máy T-King no / Item / Lot / Đường kính cần đo / Tần suất "32 lỗ/đường kính"; bảng chuẩn đường kính 0.5–4 mm (Đinh đục ± 0.030); 2 head × STT 1..40 × (Kết quả đo, OK/NG). Mã form `PR-GH-0001-04-Rev02`.
- [Sự thật] QCP ảnh [02-A60](../source/assets/ref-06-guide-hole/02-A60.png): Đo đường kính lỗ (Φ2.1), 5pcs/lot (4 góc + 1 giữa), Phương pháp `T-King / VHX / OMM`, Công đoạn lấy kết quả `Guide Hole`. WCS ảnh [04-X60](../source/assets/ref-06-guide-hole/04-X60.png): Hole type 1/2 × 5 + X + R. [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 24: Method actual `T-King`, Công đoạn lấy kq `CL Tack`, Phương pháp `Copy thủ công vào file báo cáo`.
- [Suy luận] 16 giá trị/hàng là khoảng cách giữa hai tâm lỗ, không phải đường kính trực tiếp; cách quy đổi sang "đường kính lỗ" và cách gán pcs/head chưa có trong nguồn.

### 6. Impedance (Ref.04, Ref.11)

- [Sự thật] [ref-04-rr-ss-etching.md](../source/ref/ref-04-rr-ss-etching.md) rows 126-168 ("Impedance - QA Lab") + [CSV rows133-157](../source/ref/data/ref-04-rr-ss-etching-rows133-157.csv): CPK Data Sheet - Rev 06; Part Number `821-02069-02`, Part Description `D705 D-Flex Carrier SE1&SE2`, Item `4M0023`, Lot `02831`, Công đoạn `CROSSCUT`, ID; hàng 142 Dim No `FAI 1` … `FAI 65`, `CHAN 1`, `CHAN 2`; chỉ `CHAN 1` (BP) và `CHAN 2` (BQ) có dữ liệu, Nominal 44, Tol ±8.8; hàng 162-167 = pcs 1..6.
- [Sự thật] WI ảnh [04-A169](../source/assets/ref-04-rr-ss-etching/04-A169.png): "Điện trở impedance sau SUS Press: 83.0+15.8/-18.5 (64.5~98.8) Ohm, Cpk ≥ 1.33, VNA machine, 8pcs/block x 4 blocks/Lot x All Lot". Ref.11 ảnh [01-A35](../source/assets/ref-11-sus-pre-tack/01-A35.png): "Đo impedance Single, 32pcs/lot x all lot, Kiểm tra điện trở mạch điện".
- [Sự thật] Biên bản họp [04-meeting-minutes.md](../source/04-meeting-minutes.md) row 9 (2026-10-21): "Khảo sát logfile: Mitutoyo, Impedance". **Không có ảnh logfile thô** của máy impedance.
- [Sự thật] [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 18: Registration MD & TD, Method `Impedance`. [Suy luận] Có thể nhập sai (Registration thường đo bằng OMM, xem ảnh [06-J169](../source/assets/ref-04-rr-ss-etching/06-J169.png)).

### 7. Zygo (Ref.10)

- [Sự thật] Ảnh [01-A11](../source/assets/ref-10-enig/01-A11.png): "ACF ROUGHNESS RESULT"; header Date, Item `4M0023`, Lot `03068`, Machine `NO3`; Standard Sa < 0.5um, Sq < 0.75um, Sdr > 0.0075um. Bảng trái: Sample 1..6 × A1, A2, B1, B2 × Sa, Sq, Sz, Sdr và khối thống kê (Min, Max, Range, Mean, NValid, …). Bảng phải: Pt No 1..6 × A1-Sa, A1-Sq, A2-Sdr, B1-Sa, B1-Sq, B2-Sdr; USL/LSL/Min/Max/Mean/STDEV/Cp/Cpku/Cpkl/Cpk/Judge. "Chú ý: nếu không đo đủ 32 pcs thì không quản lý CPK". Mã `OPA-QA-0164-17-Rev01`. Sheet tab: `Form 1 đ -6pcs`, `Form 1 đ -32pcs (2)`, `Form 2đ -6pcs`, `Form 4 đ -6pcs` (đang mở), `Form 6 đ-6 pcs`, `Form 4 đ-32 pcs`, `Form 6 đ-32 pcs`.
- [Sự thật] [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 47: Roughness Sa, Sq, Sdr; 32 pcs/lot (NPI), 6 pcs/lot (MP); `Zygo machine`; link `…\14. Roughness (Nham)\16-9\CA1`.
- [Suy luận] Bảng trái là dữ liệu xuất/dán từ Zygo, bảng phải là phần template tự tính. Định dạng file xuất gốc của Zygo không có trong nguồn.

### 8. Nikon

- [Sự thật] Requirement 9: "Nikon: Sử dụng định dạng template". Biên bản họp row 3 (2026-10-09): "Xử lí logfile: Mitutoyo, Nikon, VHX, Laser".
- **Không có** Ref, ảnh, link folder hay IPQC content nào trong `docs/source/` gắn với Nikon. Không biết Nikon dùng ở công đoạn nào.

### 9. XRF

- [Sự thật] [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 40: Plating thickness Ni | Pd | Au, 1 panel/lot (NPI), 5 pcs/lot (MP), `XRF`, In line; link `\\10.212.1.135\Home02\PRODUCTION\20.Gold plating\00000.Do day xray\NAM 2026\THANG 9\18-9-2026`. Ref.10 ảnh [02-A44](../source/assets/ref-10-enig/02-A44.png): "4 điểm/pcs x 5pcs/ sheet / lot x all lot", Au 0.035~0.085 um, Ni 2~6 um.
- **Không có** mẫu logfile/template.

### 10. Thiết bị khác được nêu tên (không có logfile mẫu, phần lớn nhập tay)

[Sự thật] Nguồn: [03-ipqc-contents.md](../source/03-ipqc-contents.md) (cột I, J), `process-control/*.md`, ảnh WI/QCP của các Ref.

| Thiết bị | Nơi xuất hiện | Ghi chú trong nguồn |
|---|---|---|
| Micrometer / height gauge / drop gauge | 03 row 30, 35; Ref.09 04-A29 (Độ dày FPC); Ref.12 03-H18 | Không có template |
| Push tester / Peeling tester / Peel test | 03 row 38, 52-53; Ref.09 06-P29; Ref.11 01-A35, 03-V35 | WCS nhập 1 giá trị hoặc SUS1-3/PI1-3 |
| 4-wire tester / 4W multimeter | 03 row 51; Ref.11 01-A35; 53-e-check | Có link `…\10. Sus Resistance\9-9\CA 1`, không có ảnh |
| BONDING TESTER 4000HS | 03 row 46; Ref.10 02-A44, 03-K44 | Link folder `…\17. High speed ball shear\GOLD 18-9\EL5\69DRCT-4M0024-00201-519796-L5-C2-18-9` |
| SEM / EDX / CP-SEM / XPS | 03 row 41, 48-49, 70, 72-73; 54-plasma-cleaning, 55-di-water | "Excel file from PR", "Manual" |
| Kruss Mobile Surface Analyzer / Wet contact angle | 03 row 71-75; 54, 55, 56 | "Excel file from PR"; link `…\22. Contact Angle (Tham thau)\…\PANEL 1` |
| Cognex DM363 | 03 row 59, 61-62; 50, 51 | Manual |
| Cân (weighting loss) | 03 row 7-8; Ref.02 rows 40-61 | Bảng nhập tay 9 điểm |
| VNA machine | Ref.04 04-A169 | Impedance sau SUS Press |
| VHX600 / VHX5000 / VHX970 / Digital Microscope | Ref.09 04-A29; Ref.08 01-A19; 03 row 39 | Tên model khác "VHX" và "VHX 5500" |
| QC gate machine, AOI/AOM | 57-qc-gate; 50 ảnh A39 | Manual / P-chart |

## Special cases

Tất cả đều là quan sát từ nguồn; cách xử lí chưa quyết định.

1. **Một Equipment type, nhiều định dạng.** VHX vừa có logfile CSV 1 pcs/file (Ref.01, 05, 07), vừa có template CPK Data Sheet (Ref.04 QA Lab), vừa nhập tay ("VHX không xuất logfile", VHX 5500). Định dạng phụ thuộc **model máy và công đoạn**, không chỉ phụ thuộc "VHX" ([02-requirements.md](../source/02-requirements.md) mục 9; [03-ipqc-contents.md](../source/03-ipqc-contents.md) row 27-28, 42-44).
2. **Một công đoạn, nhiều Equipment type cho cùng IPQC content.** Etching (Ref.04): `Cross cut + VHX & Laser Microscope` cho cùng nhóm content; Guide hole: `T-King / VHX / OMM`; InkJet: `T-King hoặc Mitutoyo`.
3. **Một file chứa nhiều IPQC content và nhiều pcs, đánh địa chỉ bằng nhãn.** Laser microscope: cột A `B1-1` = điểm đo B1, pcs 1; Mitutoyo: `A1[i,j]` = dim A1, pcs `(i-1)*6+j` (suy luận). Thứ tự hàng **không theo số pcs**: Plane sắp theo chuỗi (`B1-1, B1-10, B1-11, B1-12, B1-2…`), Profile xen kẽ điểm (`B1-1, B3-1, B2-1, B1-2…`) (Ref.04 ảnh 02-J9, 03-V9).
4. **Số pcs khác nhau giữa các điểm trong cùng file.** Plane: B1, B2 có giá trị ở D, E, F; B3 chỉ có D, E (Ref.04 ảnh 02-J9). CPK sheet Ref.09: A1..FAI 14 có 32 pcs, C1/C2 chỉ 5 pcs.
5. **Một pcs, nhiều file.** VHX UV Laser: `n.csv` (BVH) và `n-TH.csv` (TH). Copper/SR cross-cut: mỗi pcs có `n.csv` + `n.jpg` + `nS.jpg`, và chia folder theo loại lỗ/mặt (`BVH BS`, `BVH NBS`, `PTH`) hoặc điểm đo (`HA`, `I1AB`, `I1B`, `I2AB`) và theo loại nội dung (`DODAY`, `DK`).
6. **Cùng format CSV VHX nhưng nhãn đo khác.** UV Laser: `Diameter`; SR cross-cut: `Parallel`. Số dòng trong `[Main]` thay đổi theo vị trí (2, 4, 6…). Ô lấy giá trị phụ thuộc thứ tự đo của người vận hành.
7. **Giá trị tính, không đo.** Taper Bottom/Top (Ref.01, Ref.02/05), Etching factor (Ref.04), Etc amount/rate (Ref.02), X, R, Cpk. Màn cấu hình prototype có ô "Công thức" (`#1/#2*100`) (Ref.01 ảnh 03-G10).
8. **Ô lấy giá trị phụ thuộc Item.** Màn cấu hình có lựa chọn `Theo Item (2)` cho "Ô lấy giá trị" (Ref.01 ảnh 03-G10).
9. **Dấu thập phân.** T-King dùng dấu phẩy (`240,1193`); file tổng hợp Etching có `Điều kiện Etching = 2,02`; Laser microscope hiển thị `18,117` (Ref.06 ảnh 01-M19; CSV rows44-53 hàng 50; Ref.04 ảnh 02-J9). Chưa rõ `18,117` là 18.117 hay 18117.
10. **Dữ liệu theo hàng ngang, nhiều lần đo trong một file cố định.** `LOGFILE TKING.xlsx` không mang Item/Lot; mỗi lần đo thêm một hàng có timestamp; công nhân phải xoay hàng → cột thủ công (Ref.06 shape).
11. **Template có nhiều biến thể theo số điểm/số pcs.** Zygo: 7 sheet `Form N đ - 6/32 pcs`. "Nếu không đo đủ 32 pcs thì không quản lý CPK" (Ref.10 ảnh 01-A11). UV Laser: 3 sơ đồ vị trí (32 lỗ NPI, 3 lỗ mass, 3 lỗ coupon cuối roll) (Ref.01 ảnh 04-A39).
12. **NPI vs MP khác số pcs.** Etching: 32 pcs/lot (NPI) vs 5 pcs/lot (MP); file tổng hợp có lot 5 pcs và lot 36 pcs (CSV rows44-53 hàng 49 và 52). Roughness: 32 vs 6. UV Laser: 32 lỗ vs 3 lỗ.
13. **WCS chỉ nhận 5 (hoặc 6) cột + X + R**, trong khi logfile có 3, 6, 12, 32, 36 pcs (Ref.01 06-J39, Ref.04 05-F169, Ref.05 06-S27, Ref.09 05-J29…).
14. **Tên folder mã hóa khác nhau theo công đoạn**, xem bảng; có trường chưa rõ nghĩa (`520704+RR14_76281`, `507356 SAY`, `1`, `W05`). Báo cáo có thể gộp lot trong tên (`4M0024-00166+00204.xlsx`) hoặc mang Judgement (`…-OK.xlsx`).
15. **Hai người trên một bản ghi.** `ID ĐO` và `ID NHẬP` riêng; có ô ghi `61940+505788` (2 ID trong một ô) (CSV rows44-53 hàng 52). CPK sheet VHX QA Lab có 2 ID (Ref.04 row 60).
16. **Lỗi/dấu vết trong template.** `#REF!` ở cột Center (Ref.03), `#DIV/0!`/`#VALUE!` ở CPK sheet (Ref.04), dòng "KHÔNG XÓA DÒNG NÀY NHÉ" (Ref.04 hàng 48), nhãn trùng (`5:` hai lần ở Ref.02 hàng 31).
17. **Mâu thuẫn giữa các nguồn.** Guide hole: Công đoạn lấy kq `CL Tack` (03 row 24) vs `Guide Hole` (Ref.06 02-A60). DFR: WI 12 pcs/sheet (Ref.03 01-A17) vs dữ liệu chỉ có 8 pcs, FAI "8 coupon" (Ref.03 03-K18). SR Development: WI chỉ A side B1..B3 (Ref.08 01-A19) vs file tổng hợp có Bside B4..B6. SR Heat cure: QCP ghi Mitutoyo, actual ghi VHX 5500 (03 row 27-28).

## Gaps / cần hỏi

1. **Nikon:** không có mẫu logfile/template, không biết công đoạn nào dùng, "định dạng template" nghĩa là gì.
2. **XRF:** không có mẫu file (chỉ có link folder `Do day xray`); không biết 1 file chứa bao nhiêu pcs/điểm.
3. **Impedance:** chỉ có CPK Data Sheet (CHAN 1/CHAN 2, 6 pcs); chưa có logfile thô của máy (VNA?). Việc khảo sát còn mở theo biên bản 2026-10-21.
4. **Mitutoyo:** ý nghĩa tên file `C`, `MA`, `MB`, `XN FAI …`, vai trò file `.txt` đi kèm, quy tắc `[i,j]` → pcs; Mitutoyo dùng ở 2DID và InkJet có cùng format không.
5. **VHX CSV của Copper cross-cut (Ref.05) và Etch back (Ref.02):** không có ảnh nội dung CSV; cần xác nhận hàng 30 của Ref.02 có phải bảng ánh xạ số đo → cột hay không; ý nghĩa `.jpg` vs `S.jpg`, `DODAY`/`DK`.
6. **Laser microscope:** ánh xạ cột D/E/F (Plane) và C (Profile) → IPQC content; định dạng số `18,117`; ý nghĩa đầy đủ của tên folder.
7. **T-King:** cách quy 16 giá trị "Distance from the two round" về đường kính và về pcs/head; T-King ở InkJet dùng format nào.
8. **Zygo:** định dạng file xuất gốc của máy; cách chọn sheet `Form N đ`.
9. **VHX 5500/VHX970/VHX600/VHX5000:** model nào xuất được logfile, model nào bắt buộc nhập tay.
10. **Các thiết bị khác** (Micrometer, Push/Peel tester, 4-wire tester, Bonding tester 4000HS, SEM/EDX, Kruss, Cognex, cân, XPS…): có thuộc phạm vi "Equipment type" của hệ thống không, và có logfile không.
11. **Mâu thuẫn ở mục Special cases 17** cần chủ tài liệu chọn bản đúng.
12. **Ref.02 ảnh WCS [02-I1](../source/assets/ref-02-de-smear-plasma/02-I1.png)** độ phân giải thấp, chỉ đọc được: form `R_R Desmear_Form2`, Coupon etching back 5 giá trị + X + R.
13. Requirement 34 dùng tên Equipment Type `Crosscut & VHX` trong đường dẫn server; chưa rõ đây là tên Equipment type chính thức hay chỉ là ví dụ.

## Nguồn

- [docs/source/README.md](../source/README.md): mục lục, quy ước chuyển đổi.
- [docs/source/02-requirements.md](../source/02-requirements.md): mục 9 (Equipment type, Định dạng xử lí logfile), 15 (Khai báo layout), 28–34 (service, folder Temp, đọc tệp, đánh giá, copy server).
- [docs/source/03-ipqc-contents.md](../source/03-ipqc-contents.md): cột I/J (Method), K (Công đoạn lấy kq), L (Phương pháp), M (Link); số "row" trong tài liệu này là số dòng Excel (cột `Row`).
- [docs/source/04-meeting-minutes.md](../source/04-meeting-minutes.md): row 3 (2026-10-09), row 9 (2026-10-21).
- [docs/source/01-concept.md](../source/01-concept.md): hộp "Yêu cầu" (rà soát special cases, high summary cho các loại template).
- Ref: [ref-01](../source/ref/ref-01-uv-laser.md), [ref-02](../source/ref/ref-02-de-smear-plasma.md), [ref-03](../source/ref/ref-03-dfr-development.md), [ref-04](../source/ref/ref-04-rr-ss-etching.md), [ref-05](../source/ref/ref-05-copper-plating.md), [ref-06](../source/ref/ref-06-guide-hole.md), [ref-07](../source/ref/ref-07-printing.md), [ref-08](../source/ref/ref-08-sr-development.md), [ref-09](../source/ref/ref-09-cvl-full-lamination.md), [ref-10](../source/ref/ref-10-enig.md), [ref-11](../source/ref/ref-11-sus-pre-tack.md), [ref-12](../source/ref/ref-12-inkjet.md), kèm ảnh trong `docs/source/assets/ref-*/`.
- CSV: [ref-01 rows32-37](../source/ref/data/ref-01-uv-laser-rows32-37.csv), [ref-03 rows9-16](../source/ref/data/ref-03-dfr-development-rows9-16.csv), [ref-04 rows44-53](../source/ref/data/ref-04-rr-ss-etching-rows44-53.csv), [ref-04 rows133-157](../source/ref/data/ref-04-rr-ss-etching-rows133-157.csv), [ref-04 rows159-160](../source/ref/data/ref-04-rr-ss-etching-rows159-160.csv), [ref-08 rows8-16](../source/ref/data/ref-08-sr-development-rows8-16.csv).
- Process control: [50-2did-laser-marking.md](../source/process-control/50-2did-laser-marking.md) (+ ảnh A39), [51](../source/process-control/51-2did-cognex-reading.md), [53](../source/process-control/53-e-check.md), [54](../source/process-control/54-plasma-cleaning.md), [55](../source/process-control/55-di-water.md), [56](../source/process-control/56-fpc-n2-baking.md), [57](../source/process-control/57-qc-gate.md). Sheet 52, 58, 59 chưa có dữ liệu.
