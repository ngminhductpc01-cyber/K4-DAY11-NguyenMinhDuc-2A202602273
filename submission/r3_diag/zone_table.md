# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 10 | 1 | 2 | 3 | 3 | WRONG_CLASS (1) |
| mid | 6 | 1 | 1 | 2 | 4 | ATTRIBUTE (1) |
| edge | 2 | 0 | 0 | 2 | 3 | ATTRIBUTE (1) |

## Nhận xét

- Lỗi learner tập trung nhất ở **center**: 1 missing và 2 spurious, gồm class sai `Truck`/`Car` và bản sao Bike. **Mid** có 1 missing và 1 spurious; **edge** không có missing/spurious của learner trong bảng này, nhưng vẫn có khác biệt attribute của Bus bị cắt. Vì vậy center/mid/edge ở đây chỉ mô tả vị trí tương đối trên vòng kính, không nói vật gần/xa xe hay camera trước/sau.
- Model có nhiều bất đồng hơn learner ở cả ba zone: center 3 missing + 3 thừa, mid 2 + 4, edge 2 + 3. Các box M-only/M-missing xuất hiện quanh rider/vehicle chồng lấp và xe bị méo/cắt ở rìa, nhưng slice chỉ có ba frame nên đây là giả thuyết cần kiểm tra thêm, **không** đủ để kết luận E4 model-domain.
- Class cần ưu tiên kiểm lại là `ThreeWheeler` (một thiếu learner ở mid và một model nhầm thành Truck ở edge) và `Car`/`Truck` (một class mismatch center). `ego_body` và hai `lens_border` đã được thấy trong từng frame; không có bằng chứng ở slice này để quy lỗi cho ignore scope ngoài ca L3 frame 167700 đã được report.
