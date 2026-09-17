# Báo cáo Day 5

- Mã học viên theo lớp: [Cần bổ sung]
- Ngày / CVAT local: 18/09/2026 / CVAT local của lớp.
- Công cụ đã dùng: CVAT, Brush; notebook tự kiểm và script chấm của repo.

## 1. Bài đã nộp

Các ZIP nằm trong `submissions/`. Cột điểm dưới đây là điểm tối đa, không phải điểm tự chấm.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Tự kiểm: đủ 9 ZIP, không có lỗi cấu trúc. Ba phần chính đạt **47,6/82** theo [bảng điểm](reports/tiers/SCORECARD.md). Theo hướng dẫn của thầy được thông báo, mỗi checkpoint có bài được tính 3 điểm, không cần đối chiếu đáp án; đủ 6 checkpoint được **18/18**. Tổng theo cách tính này: **47,6 + 18 = 65,6/100**, chưa tính bonus.

## 2. Một quyết định trước khi dùng gợi ý

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Người phụ nữ mặc áo dài ở gần giữa, lệch trái ảnh `000000181542.jpg`. Tôi tự vẽ người này đầu tiên bằng Brush.
- Class và quy tắc tôi dùng để chọn biên: Chọn `person`; tô phần cơ thể và quần áo nhìn thấy, bám theo tóc, vai, tay, tà áo và chân, tách khỏi xe máy phía sau và mặt đường.
- Gợi ý tự động sau đó: Tôi tự vẽ object đầu tiên bằng Brush. Chưa ghi nhận thông tin về việc dùng gợi ý tự động sau đó hoặc vùng đã sửa/giữ từ gợi ý.

## 3. Một lỗi tôi tìm thấy và sửa

- Task/ảnh/vùng: `hard_panoptic`, ảnh `000000460147.jpg`, vùng trời và cây trên dải phân cách.
- Lỗi thuộc loại: Phủ vùng — thiếu nhãn.
- Bằng chứng tôi nhìn thấy: Bản ZIP trước không có nhãn `sky` và `vegetation` cho ảnh này dù ảnh có trời và cây.
- Quy tắc và hành động sửa: Cần gán nhãn đủ phần nhìn thấy thuộc các lớp của task. Tôi đã thay ZIP bằng bản mới; bản mới có cả `sky` và `vegetation` trong ảnh này.
- Sau sửa đã Save và export lại chưa? Đã có ZIP mới trong `submissions/` và đã kiểm/chấm lại; chưa xác nhận riêng thao tác Save trong CVAT.

Sau khi thay ZIP, điểm Hard tăng từ **4,3 lên 10,6/30**; PQ (chất lượng phân vùng toàn cảnh) tăng từ **0,264 lên 0,359**. Bản mới vẫn còn vùng chưa khớp đáp án.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| Hard `000000460147.jpg`, trời sát cành cây phía trên bên trái | Tô cả vùng sáng là sky hoặc tách cành/lá khỏi trời | Có khoảng trời xen giữa cành; gán nhãn theo phần nhìn thấy | Với cành quá mảnh và mờ, nên tách đến mức chi tiết nào? |
| Hard `000000460147.jpg`, dải phân cách giữa đường | Gộp cả dải vào vegetation hoặc tách cây với nền/bó vỉa | Cây và nền là các bề mặt khác nhau | Phần nền dải phân cách nên thuộc lớp nào trong task? |
| Hard `000000460147.jpg`, xe chở xe ở giữa ảnh | Gộp thành một vật hoặc tách xe chở và từng xe được chở | Các xe là vật riêng dù nằm sát nhau; không đoán phần khuất | Cần tách từng xe nhìn thấy; xin xác nhận class của xe chở. |
