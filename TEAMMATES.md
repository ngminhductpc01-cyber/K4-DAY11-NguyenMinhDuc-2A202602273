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
- Commit chốt bài: `efa3206c789abf91227bdb30cc26005358efa03c` — `Complete Day11 SVM360 lab`

## 2. Ba vai chính

| Vai | Họ và tên | MSSV | Tên định danh trong mode | Trách nhiệm | Bằng chứng đóng góp |
|---|---|---|---|---|---|
| A · Gán nhãn | Nguyễn Minh Đức | 2A202602273 | `duc` | Parking/C0/slice `B3-center`, self-QC, lock, rework | P2: annotation `B3-center`, self-QC, lock `4B05-4C53`, commit `1947a5a`; P5: C0 v2 `exports/c0-v2.zip`; B3 v2 `exports/r2-v2.zip`; lock rework `F6A8-6EF7`. Parking Job 53 được giữ nguyên theo annotation mới đã được cung cấp. |
| B · QA độc lập | Nguyễn Lâm Bách | 2A202602143 | `bach` | Review trước reference, finding QA, kiểm lại ca sửa | P3: review mù 3/3 frame trong `submission/r2_qa/qa_review.md`, findings `r2_qa` và screenshot evidence; P5: `submission/rework/recheck.md` xác nhận các ca được phân xử trên v2. |
| C · Chẩn đoán & điều phối | Nguyễn Tuấn Minh | 2A202602194 | `minh` | Báo cáo, phân xử, kế hoạch, tích hợp, check và nộp | P4: reports L/R/M + IoU, diagnosis và decision log; P5/P6: kế hoạch sampling/gold, error card, exit ticket, manifest và final check; commit chốt `efa3206c789abf91227bdb30cc26005358efa03c`. |

Bảng này xác định vai của nhóm. Vòng QA tự sinh trong `team.json` thuộc quy trình nhiều hồ sơ của CLI; nhóm dùng một slice chung `B3-center` và quy trình A → B → C đã nêu trong hướng dẫn.

## 3. Bàn giao theo pha

| Mốc | Người giao → nhận | File / commit / mã khóa | Người nhận đã kiểm gì? | Trạng thái / vướng mắc |
|---|---|---|---|---|
| P0 · Chốt môi trường và vai | Nguyễn Tuấn Minh (C) → Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) | `submission/00_setup/mode.json`; slice `B3-center`; phân vai A/B/C | Đã xác định A=`duc`, B=`bach`, C=`minh`; slice chung của nhóm là `B3-center` | **Hoàn thành** — Python 3.9 ✓, CVAT 2.74.1 ✓, `.env` không bị Git track ✓; `gh` chưa cài nhưng repo Public đã được kiểm tra |
| P2 · Khóa bản đầu | Nguyễn Minh Đức (A) → Nguyễn Lâm Bách (B), Nguyễn Tuấn Minh (C) | `submission/r1_craft/annotations.xml`; `submission/r1_craft/lock.txt`; slice `B3-center`; mã khóa `4B05-4C53`; commit `1947a5a` | A hoàn thành annotation, self-QC, sửa lỗi phát hiện trong self-QC, export bản cuối và khóa `r1_craft` | **Hoàn thành** — bản r1 được bàn giao cho B thực hiện QA độc lập; lock-code mismatch được giữ lại trong hồ sơ để audit |
| P3 · Chốt QA mù | Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C), Nguyễn Minh Đức (A) | `submission/r2_qa/qa_review.md`; 3 dòng `r2_qa`; `submission/screenshots/r2_qa_*` | B review mù 3/3 frame trên CVAT + ảnh gốc + XML + rules; không dùng reference/model/worked trước khi chốt QA | **Hoàn thành** — QA mù đã được chốt; lock-code mismatch được ghi nhận pending verification |
| P4 · Quyết định sửa | Nguyễn Tuấn Minh (C) → Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) | `submission/r1_craft/compare.*`; `submission/r3_diag/`; `submission/40_decision_log.csv`; `submission/r3_diag/rework_handoff.md` | C chạy reference, compare, local-quality, model, IoU sweep; triage findings; phân xử KEEP/REWORK/ESCALATE | **Hoàn thành** — rework handoff đã xác định rõ trước khi tạo version 2 |
| P5 · Kiểm bản sửa | Nguyễn Minh Đức (A) → Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C) | `exports/c0-v2.zip`; `exports/r2-v2.zip`; `submission/rework/lock2.txt` — `F6A8-6EF7`; `submission/rework/recheck.md`; `submission/rework/delta.md` | C0 bổ sung đủ 4 box thiếu; B3 sửa đúng 5 quyết định; B kiểm lại các ca sửa. Delta center: missing `1→0`, spurious `2→0` | **Hoàn thành** — Parking được giữ nguyên; C0 và B3-center đã có version 2 |
| P6 · Chốt nộp | Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C) | `submission/manifest.json`; sampling/gold/error card/exit ticket; commit `efa3206c789abf91227bdb30cc26005358efa03c` | `triage` hợp lệ; `doctor` đạt ngoại trừ cảnh báo thiếu `gh`; `check` có `failed_gates: []`; `git diff --check` không có lỗi; repo sau push sạch | **Hoàn thành** — hồ sơ đã commit và push lên `origin/main` |

## 4. Bất đồng và phối hợp

- Một ca đã phân xử: `adasind_212280.jpg` L5, R01 — B phát hiện box Bike L5 gần trùng L2; C đối chiếu ảnh/locked XML/reference/model và quyết định **REWORK: remove L5**, giữ pair L1 Pedestrian + L2 Bike. Evidence: `submission/screenshots/r2_qa_adasind_212280_L2_L5.png`, `submission/r3_diag/rework_handoff.md`.
- Ca còn mở: `r1_craft` lock-code mismatch pending verification; `adasind_212280.jpg` teaching reference R1 cần QA theo R03 (escalated), không ép learner theo reference.
- Đóng góp của A/B/C vào kế hoạch và exit ticket:
  - **A — Nguyễn Minh Đức:** hoàn thành annotation ban đầu, self-QC; xuất C0 v2 và B3 v2; khóa B3 rework với mã `F6A8-6EF7`; Parking giữ nguyên annotation mới đã được cung cấp.
  - **B — Nguyễn Lâm Bách:** QA độc lập bản của A trước khi xem reference/model; ghi findings và evidence; kiểm lại các thay đổi v2 trong `submission/rework/recheck.md`.
  - **C — Nguyễn Tuấn Minh:** điều phối; chẩn đoán disagreement; tổng hợp reports/findings; hoàn thiện decision log, sampling/gold/error card/exit ticket; chạy final check và chốt repo.
- Thay đổi phân công nếu có: Không thay đổi phân công. Máy Nguyễn Minh Đức được sử dụng làm máy giữ hồ sơ chính do Đức đảm nhiệm vai A và trực tiếp thao tác CVAT.

## 5. Xác nhận trước khi nộp

- [x] A — Nguyễn Minh Đức xác nhận annotation và export đúng phiên bản: C0 `exports/c0-v2.zip`; B3 `exports/r2-v2.zip`, khóa rework `F6A8-6EF7`; Parking không bị thao tác lại.
- [x] B — Nguyễn Lâm Bách xác nhận đã QA độc lập trước reference/model và kiểm lại ca sửa theo `submission/rework/recheck.md`.
- [x] C — Nguyễn Tuấn Minh xác nhận báo cáo đúng phiên bản, các file đầy đủ và `check` exit 0.
- [x] `submission/manifest.json` có `failed_gates` rỗng.
- [x] Repo nhóm Public, ảnh và các bằng chứng mở được.
- [x] Bài hoàn chỉnh đã được push lên `origin/main` tại commit `efa3206c789abf91227bdb30cc26005358efa03c`.

Chỉ đánh dấu việc đã kiểm thật. Nhóm nộp một hồ sơ chung; check không tự chấm đóng góp từng người. Giữ nguyên header/các cột enum của `findings.csv`; tên người được ghi trong tài liệu này hoặc phần note thích hợp.