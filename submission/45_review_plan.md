# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| B3-center / adasind_212280.jpg | 3 learner findings: duplicate Bike, truncated attribute, and reference disagreement on walking rider | Multiple decisions affect one pedestrian/bike/bus scene; R03 and R05 require original-image review before any rework | Three P3 screenshots, `qa_review.md`, `local_quality_conflicts.csv`, decision-log entries P4-04 to P4-06 |
| B3-center / adasind_167700.jpg | class mismatch Truck/Car plus model-only hypotheses | Class correction is a P1 learner rework; model conflicts must not be used as labels without image evidence | `local_quality_conflicts.csv`, `model_compare.md`, decision-log entry P4-03 |

Giới hạn của kết luận từ ba frame ADASIND: đây là một camera và ba frame, nên không suy ra tần suất lỗi toàn hệ SVM hoặc kết luận model-domain. Center/mid/edge là radial zone trên ảnh, không phải gần/xa hay camera trước/sau.

## Chuyển sang kế hoạch bốn camera giả lập

P4 chưa hoàn thành hoặc thay đổi kế hoạch 200 frame bốn camera; nội dung đó nằm ngoài stop gate trước P5/P6. Khi nhóm tiếp tục, chọn scene cách nhau theo thời gian, giữ phân tầng normal/hard cho từng camera, và không đếm các frame liền kề của cùng một cảnh như các ca độc lập. Kế hoạch chỉ chọn nơi cần review; không tự ước lượng tỷ lệ lỗi.
