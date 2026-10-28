# Bản demo của maker: nguồn tham chiếu "as-built"

Thư mục này là **bản chụp nguyên trạng** hai tài liệu mô tả bản demo LAB TEST SYSTEM mà maker đang chạy. Chủ dự án nhận và cung cấp ngày 2026-10-28, để dùng thay cho quyền truy cập trực tiếp vào demo (ticket [#5](https://github.com/trungkien87/LabTestSystem/issues/5)).

| Tài liệu | Nội dung | Vị trí |
|---|---|---|
| `LabTestSystem_KB_VI_20261028_Rev01.zip` | Knowledge base Markdown: 17 file + 53 ảnh chụp web demo | [LabTestSystem_KB_VI_20261028_Rev01/](LabTestSystem_KB_VI_20261028_Rev01/00_INDEX.md) (giữ nguyên văn) |
| `LabTestSystem_UserGuide_VI_20261028_Rev01.xlsx` (34 sheet) | User Guide gốc của maker (Rev00, 23 sheet), cộng ghi chú cập nhật Rev01 (cột R) và 8 sheet mới | [LabTestSystem_UserGuide_VI_20261028_Rev01.md](LabTestSystem_UserGuide_VI_20261028_Rev01.md) |

Báo cáo đối chiếu demo với `docs/source`: [MakerDemoReview_VI_20261028_Rev01.md](../../research/MakerDemoReview_VI_20261028_Rev01.md).

## Nguồn gốc và mức tin cậy

- **Ai viết:** cả hai tài liệu do Claude soạn trong một phiên làm việc khác, theo yêu cầu của chủ dự án (sheet `Revision` của User Guide). Đây **không phải tài liệu của maker**, trừ phần nội dung Rev00 trong User Guide.
- **Cách làm:** rà soát read-only trên web demo ngày 2026-10-28, giao diện tiếng Việt, tài khoản quyền Administrator. Không thao tác Lưu, Xoá, Nhận mẫu hay Upload.
- **Phần chưa kiểm chứng:**
  - Ứng dụng Service trên PC thiết bị đo (4 sheet Service) chưa được rà soát lại. Nội dung và ảnh lấy từ User Guide Rev00 của maker.
  - Hành vi khi Lưu/Xoá lấy từ tài liệu cũ, đánh dấu `[Từ tài liệu cũ]`.
- **Ký hiệu trong KB:** không đánh dấu = quan sát trực tiếp; `[Từ tài liệu cũ]`; `[Suy luận]`; `[Chưa xác minh]`. Khi trích dẫn, giữ nguyên ký hiệu này.
- **Vai trò trong dự án:** mô tả hệ thống maker **đang có** (as-built), không phải yêu cầu. Quyết định của dự án vẫn ghi ở `GLOSSARY.md`, `docs/adr/` và resolution comment của ticket. Chỗ nào demo khác với quyết định đã chốt, quyết định đã chốt thắng.

## Quy ước chuyển đổi

- **KB:** chép nguyên văn từ file zip, gồm 17 file `.md` và thư mục `images/`. Bỏ file `LabTestSystem_KB_ALL_VI_20261028_Rev01.md` vì nó chỉ là bản gộp các file kia; đã kiểm tra mọi dòng của các file lẻ đều có trong bản gộp.
- **User Guide:** chuyển bằng script, giữ nguyên câu chữ. Mỗi sheet là một mục, mỗi dòng Excel là một dòng bảng; cột `Row` và tên cột là tọa độ ô.
  - Ảnh chụp chỉ tách cho 4 sheet Service, vào [assets/user-guide/](assets/user-guide/), tên file theo ô neo. Đây là hình ảnh duy nhất của ứng dụng Service.
  - Các sheet web còn lại có ảnh bản cũ; ảnh không được tách vì bộ KB đã có ảnh mới của cùng màn hình.
- **Dữ liệu nhạy cảm:** giá trị máy chủ FTP đã được che sẵn trong ảnh KB. Tài liệu còn chứa IP nội bộ của web demo, tên và mã nhân viên trên ảnh chụp. Repo này đang ở chế độ private; nếu chia sẻ ra ngoài cần rà lại.
