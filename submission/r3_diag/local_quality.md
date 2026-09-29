# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `4b054c53a7074b663ef9d32ba951d167a6e3316a2554f5d20909fe0a3172e058`; slice `B3-center`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_152940.jpg, adasind_167700.jpg, adasind_212280.jpg. Frame thiếu trong export: không.
TP=16; FP=3; FN=2; số lần đối chiếu=20; mean IoU của TP=0.835.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.800 | 0.958 | 0.950 |
| precision | 0.842 | 0.726 | 0.000 |
| recall | 0.889 | 0.750 | 0.000 |
| jaccard | 0.762 | 0.643 | 0.000 |
| dice | 0.865 | 0.716 | 0.000 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 8 | 1 | 0 | 0.950 | 0.889 | 1.000 | 0.889 | 0.941 |
| Bus | 1 | 0 | 0 | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |
| Car | 0 | 0 | 1 | 0.950 | 0.000 | 0.000 | 0.000 | 0.000 |
| Pedestrian | 2 | 1 | 0 | 0.950 | 0.667 | 1.000 | 0.667 | 0.800 |
| ThreeWheeler | 1 | 0 | 1 | 0.950 | 1.000 | 0.500 | 0.500 | 0.667 |
| Truck | 4 | 1 | 0 | 0.950 | 0.800 | 1.000 | 0.800 | 0.889 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_152940.jpg | 5 | 0 | 1 | 0.833 | 1.000 | 0.833 |
| adasind_167700.jpg | 8 | 1 | 1 | 0.889 | 0.889 | 0.889 |
| adasind_212280.jpg | 3 | 2 | 0 | 0.600 | 0.600 | 1.000 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Bus | Car | Pedestrian | ThreeWheeler | Truck | <missing> |
|---|---:|---:|---:|---:|---:|---:|---:|
| Bike | 8 | 0 | 0 | 0 | 0 | 0 | 0 |
| Bus | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| Car | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| Pedestrian | 0 | 0 | 0 | 2 | 0 | 0 | 0 |
| ThreeWheeler | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| Truck | 0 | 0 | 0 | 0 | 0 | 4 | 0 |
| <extra> | 1 | 0 | 0 | 1 | 0 | 0 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
