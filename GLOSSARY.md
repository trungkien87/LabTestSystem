# LAB Test system

Hệ thống quản lý yêu cầu đo kiểm IPQC giữa sản xuất (PR), kỹ thuật công đoạn (PE) và phòng LAB: khai báo tiêu chuẩn, tạo và nhận yêu cầu đo, đọc kết quả từ thiết bị đo và đánh giá theo tiêu chuẩn.

## Language

### Sản xuất

**Sequence**:
Số thứ tự 4 chữ số chỉ trình tự của một công đoạn trong quy trình sản xuất; là số nguyên dương, tăng dần theo trình tự, ví dụ `0020`, `0030`. Viết tắt được chấp nhận: Seq, SEQ.
_Avoid_: thứ tự công đoạn, bước, routing step

### Đo kiểm

**Laboratory Location**:
Phòng vật lý nơi mẫu được chuyển tới để đo, có đặt thiết bị đo; mỗi phòng là một Laboratory Location dù do bộ phận nào sử dụng; đặt tên theo quy tắc `Nhà máy-Tầng-Phòng`, ví dụ `F1-Tầng 1-QALab`.
_Avoid_: Measurement Location, Location, vị trí, khu vực đo, "Công đoạn lấy kq"
