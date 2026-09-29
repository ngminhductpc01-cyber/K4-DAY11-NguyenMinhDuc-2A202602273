# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B3 | DUPLICATE | 2 |
| center | B3 | MISSING | 4 |
| center | B3 | SPURIOUS | 4 |
| center | B3 | WRONG_CLASS | 1 |
| center | C0 | MISSING | 2 |
| edge | B3 | ATTRIBUTE | 2 |
| edge | B3 | MISSING | 2 |
| edge | B3 | SPURIOUS | 3 |
| edge | C0 | MISSING | 1 |
| mid | B3 | ATTRIBUTE | 1 |
| mid | B3 | IGNORE_SCOPE | 1 |
| mid | B3 | MISSING | 3 |
| mid | B3 | SPURIOUS | 6 |
| mid | C0 | MISSING | 1 |

## Top defects
- MISSING: 13 (ví dụ frame adasind_019560.jpg)
- SPURIOUS: 13 (ví dụ frame adasind_152940.jpg)
- ATTRIBUTE: 3 (ví dụ frame adasind_212280.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Các lỗi nổi bật tập trung ở object nhỏ/sát biên fisheye (C0 ThreeWheeler, B3 Bike dưới ngưỡng H) và ở quyết định semantic (Truck/Car, duplicate, `truncated`). Đây là các tình huống mà geometry một mình không đủ: cần ảnh gốc và R01/R04/R05. Riêng reference R1 ở 212280 mâu thuẫn R03 nên được tách thành escalation, không dùng để sửa learner.
- Cách sửa và ai nhận việc (`owner`): A đã xuất C0 v2 với bốn box thiếu và B3 v2 với năm thay đổi đã phân xử; B recheck XML/ảnh gốc sau export; C giữ pair Pedestrian+Bike và theo dõi hai escalation không thuộc rework.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `findings.csv`, `r3_diag/rework_handoff.md`, `rework/recheck.md`, `p1_calib/rework_v2.md`, `screenshots/r2_qa_adasind_152940_L3.png`, `screenshots/r2_qa_adasind_212280_L2_L5.png`, `screenshots/r2_qa_adasind_212280_L3.png`; rules R01, R03, R04, R05.
