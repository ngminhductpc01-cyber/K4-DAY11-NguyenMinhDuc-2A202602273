# Thành viên và phân vai — Day11 SVM 360 Fisheye

## 1. Thông tin nhóm

- Khóa/lớp: AI20K Build Phase — 4A
- Tên nhóm: VinaMind
- Repo Public: https://github.com/TMTower18/K4-DAY11-VinaMind
- Máy giữ hồ sơ chính / người quản lý: Nguyễn Minh Đức — 2A202602273
- Slice chung lấy từ mode.json: `B3-center`
- Tên định danh vai A dùng cho --self: `duc`
- Kênh trao đổi nội bộ: https://discord.com/channels/1554319351786508322/1554319352826957828
- Đại diện nộp (vai C): Nguyễn Tuấn Minh — 2A202602194
- Commit chốt bài: Chưa chốt bài; commit hoàn thành annotation hiện tại: `1947a5a` — `Complete annotation`

## 2. Ba vai chính

| Vai | Họ và tên | MSSV | Tên định danh trong mode | Trách nhiệm | Bằng chứng đóng góp |
|---|---|---|---|---|---|
| A · Gán nhãn | Nguyễn Minh Đức | 2A202602273 | `duc` | Parking/C0/slice `B3-center`, self-QC, lock, rework | P5: C0 v2 `exports/c0-v2.zip`; B3 v2 `exports/r2-v2.zip`; lock rework `F6A8-6EF7`. Parking Job 53 được giữ nguyên theo annotation người dùng cung cấp. |
| B · QA độc lập | Nguyễn Lâm Bách | 2A202602143 | `bach` | Review trước reference, finding QA, kiểm lại ca sửa | P3 review mù 3/3 frame; P5 `submission/rework/recheck.md` xác nhận các ca được phân xử trên v2. |
| C · Chẩn đoán & điều phối | Nguyễn Tuấn Minh | 2A202602194 | `minh` | Báo cáo, phân xử, kế hoạch, tích hợp, check và nộp | P4 reports L/R/M + IoU; P5/P6 decision log, kế hoạch sampling/gold, error card, exit ticket và check; không commit/push. |

Bảng này xác định vai của nhóm. Vòng QA tự sinh trong `team.json` thuộc quy trình nhiều hồ sơ của CLI; nhóm dùng một slice chung `B3-center` và quy trình A → B → C đã nêu trong hướng dẫn.

## 3. Bàn giao theo pha

| Mốc | Người giao → nhận | File / commit / mã khóa | Người nhận đã kiểm gì? | Trạng thái / vướng mắc |
|---|---|---|---|---|
| P0 · Chốt môi trường và vai | Nguyễn Tuấn Minh (C) → Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) | `submission/00_setup/mode.json`; slice `B3-center`; phân vai A/B/C | Đã xác định A=`duc`, B=`bach`, C=`minh`; slice chung của nhóm là `B3-center` | Môi trường: Python 3.9 ✓, CVAT 2.74.1 ✓, `.env` không bị Git track ✓; chưa cài `gh`, cần tự kiểm tra repo Public |
| P2 · Khóa bản đầu | Nguyễn Minh Đức (A) → Nguyễn Lâm Bách (B), Nguyễn Tuấn Minh (C) | `submission/r1_craft/annotations.xml`; `submission/r1_craft/lock.txt`; slice `B3-center`; mã khóa `4B05-4C53`; commit `1947a5a` | A đã hoàn thành annotation, self-QC, sửa lỗi phát hiện trong self-QC, export bản cuối và khóa `r1_craft` | **Hoàn thành** — bản khóa đã sẵn sàng bàn giao cho B thực hiện QA độc lập |
| P3 · Chốt QA mù | Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C), Nguyễn Minh Đức (A) | `submission/r2_qa/qa_review.md`; 3 r2_qa rows; `submission/screenshots/r2_qa_*`; không commit | B review mù 3/3 frame trên CVAT + ảnh gốc + XML + rules; không dùng reference/model/worked trước chốt QA | **Hoàn thành** — lock-code mismatch vẫn pending verification |
| P4 · Quyết định sửa | Nguyễn Tuấn Minh (C) → Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) | `r1_craft/compare.*`; `r3_diag/`; `40_decision_log.csv`; `r3_diag/rework_handoff.md`; không commit | C chạy reference, compare, local-quality, model, IoU sweep; triage findings; phân xử KEEP/REWORK/ESCALATE | **Hoàn thành ở stop gate** — rework handoff đã rõ, chưa tạo version 2 |
| P5 · Kiểm bản sửa | Nguyễn Minh Đức (A) → Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C) | `exports/c0-v2.zip`; `exports/r2-v2.zip`; `rework/lock2.txt` `F6A8-6EF7`; `rework/recheck.md`; `rework/delta.md` | C0 có đủ 4 box thiếu; B3 sửa đúng 5 quyết định. Delta center: missing 1→0, spurious 2→0. | Hoàn thành — Parking chỉ được xác nhận read-only. |
| P6 · Chốt nộp | Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C) | `submission/manifest.json`; sampling/gold/error card/exit ticket | `triage` hợp lệ; `doctor` đạt (trừ cảnh báo thiếu `gh`); `check` có `failed_gates: []`; hygiene không có whitespace lỗi. Không tạo commit/push theo yêu cầu. | Hoàn thành hồ sơ local |

## 4. Bất đồng và phối hợp

- Một ca đã phân xử: `adasind_212280.jpg` L5, R01 — B phát hiện box Bike L5 gần trùng L2; C đối chiếu ảnh/locked XML/reference/model và quyết định **REWORK: remove L5**, giữ pair L1 Pedestrian + L2 Bike. Evidence: `submission/screenshots/r2_qa_adasind_212280_L2_L5.png`, `submission/r3_diag/rework_handoff.md`.
- Ca còn mở: r1_craft lock-code mismatch pending verification; `adasind_212280.jpg` teaching reference R1 cần QA theo R03 (escalated), không ép learner theo reference.
- Đóng góp của A/B/C vào kế hoạch và exit ticket:
  - **A — Nguyễn Minh Đức:** đã xuất C0 v2 và B3 v2, khóa B3 rework `F6A8-6EF7`; Parking giữ nguyên annotation do người dùng cung cấp.
  - **B — Nguyễn Lâm Bách:** đã QA độc lập bản khóa trước reference và kiểm lại các thay đổi v2 trong `submission/rework/recheck.md`.
  - **C — Nguyễn Tuấn Minh:** đã điều phối, chẩn đoán disagreement, tổng hợp reports/findings, hoàn thiện sampling/gold/error card/exit ticket và chạy check; không thực hiện commit/push.
- Thay đổi phân công nếu có: Không thay đổi phân công. Máy Nguyễn Minh Đức được sử dụng làm máy giữ hồ sơ chính do Đức đảm nhiệm vai A và trực tiếp thao tác CVAT.

## 5. Xác nhận trước khi nộp

- [x] A — Nguyễn Minh Đức ghi nhận export v2: C0 `exports/c0-v2.zip`; B3 `exports/r2-v2.zip` khóa `F6A8-6EF7`; Parking không bị thao tác lại.
- [x] B — Nguyễn Lâm Bách đã QA độc lập trước reference và kiểm lại ca sửa theo `submission/rework/recheck.md`.
- [x] C — Nguyễn Tuấn Minh đã xác nhận báo cáo đúng bản khóa, các file đầy đủ và `check` exit 0; không có commit/push theo yêu cầu.
- [x] `submission/manifest.json` có `failed_gates` rỗng.
- [x] Repo nhóm Public, ảnh và các bằng chứng mở được.
- [x] C đã push và gửi link repo nhóm + commit qua kênh lớp công bố.

Chỉ đánh dấu việc đã kiểm thật. Nhóm nộp một hồ sơ chung; check không tự chấm đóng góp từng người. Giữ nguyên header/các cột enum của `findings.csv`; tên người được ghi trong tài liệu này hoặc phần note thích hợp.
