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
| A · Gán nhãn | Nguyễn Minh Đức | 2A202602273 | `duc` | Parking/C0/slice `B3-center`, self-QC, lock, rework | Hoàn thành Parking, C0 và annotation slice `B3-center`; self-QC; khóa `r1_craft` mã `4B05-4C53`; commit `1947a5a` (`Complete annotation`) |
| B · QA độc lập | Nguyễn Lâm Bách | 2A202602143 | `bach` | Review trước reference, finding QA, kiểm lại ca sửa | [Điền link review/findings/commit sau khi hoàn thành QA] |
| C · Chẩn đoán & điều phối | Nguyễn Tuấn Minh | 2A202602194 | `minh` | Báo cáo, phân xử, kế hoạch, tích hợp, check và nộp | [Điền link report/decision/commit sau khi hoàn thành] |

Bảng này xác định vai của nhóm. Vòng QA tự sinh trong `team.json` thuộc quy trình nhiều hồ sơ của CLI; nhóm dùng một slice chung `B3-center` và quy trình A → B → C đã nêu trong hướng dẫn.

## 3. Bàn giao theo pha

| Mốc | Người giao → nhận | File / commit / mã khóa | Người nhận đã kiểm gì? | Trạng thái / vướng mắc |
|---|---|---|---|---|
| P0 · Chốt môi trường và vai | Nguyễn Tuấn Minh (C) → Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) | `submission/00_setup/mode.json`; slice `B3-center`; phân vai A/B/C | Đã xác định A=`duc`, B=`bach`, C=`minh`; slice chung của nhóm là `B3-center` | Môi trường: Python 3.9 ✓, CVAT 2.74.1 ✓, `.env` không bị Git track ✓; chưa cài `gh`, cần tự kiểm tra repo Public |
| P2 · Khóa bản đầu | Nguyễn Minh Đức (A) → Nguyễn Lâm Bách (B), Nguyễn Tuấn Minh (C) | `submission/r1_craft/annotations.xml`; `submission/r1_craft/lock.txt`; slice `B3-center`; mã khóa `4B05-4C53`; commit `1947a5a` | A đã hoàn thành annotation, self-QC, sửa lỗi phát hiện trong self-QC, export bản cuối và khóa `r1_craft` | **Hoàn thành** — bản khóa đã sẵn sàng bàn giao cho B thực hiện QA độc lập |
| P3 · Chốt QA mù | Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C), Nguyễn Minh Đức (A) | [review, findings, ảnh, commit] | [Điền sau QA] | Chưa thực hiện |
| P4 · Quyết định sửa | Nguyễn Tuấn Minh (C) → Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) | [finding, decision log, commit] | [Điền sau diagnosis] | Chưa thực hiện |
| P5 · Kiểm bản sửa | Nguyễn Minh Đức (A) → Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C) | [v2, lock2, review kiểm lại, delta] | [Điền sau rework] | Chưa thực hiện |
| P6 · Chốt nộp | Nguyễn Minh Đức (A), Nguyễn Lâm Bách (B) → Nguyễn Tuấn Minh (C) | [manifest, commit chốt] | [Điền khi cả nhóm kiểm bài] | Chưa thực hiện |

## 4. Bất đồng và phối hợp

- Một ca đã phân xử: [Điền sau khi thực hiện QA và diagnosis: frame/object/rule; ý kiến A/B; bằng chứng; quyết định và link]
- Ca còn mở: Chưa bắt đầu P3 QA mù; chưa có ca QA cần phân xử.
- Đóng góp của A/B/C vào kế hoạch và exit ticket:
  - **A — Nguyễn Minh Đức:** đã gán nhãn Parking, C0 và slice `B3-center`; thực hiện self-QC, sửa các vấn đề phát hiện trong self-QC, export bản cuối và khóa `r1_craft` với mã `4B05-4C53`.
  - **B — Nguyễn Lâm Bách:** sẽ QA độc lập bản khóa của A trước khi xem reference; ghi findings và kiểm lại các ca đã sửa.
  - **C — Nguyễn Tuấn Minh:** điều phối, chẩn đoán disagreement, tổng hợp báo cáo/findings, lập kế hoạch sampling/gold set, kiểm hồ sơ và đại diện nộp bài.
- Thay đổi phân công nếu có: Không thay đổi phân công. Máy Nguyễn Minh Đức được sử dụng làm máy giữ hồ sơ chính do Đức đảm nhiệm vai A và trực tiếp thao tác CVAT.

## 5. Xác nhận trước khi nộp

- [x] A — Nguyễn Minh Đức xác nhận nhãn và export đúng phiên bản: bản cuối `r1_craft` đã khóa với mã `4B05-4C53`; commit `1947a5a` (`Complete annotation`).
- [ ] B — Nguyễn Lâm Bách xác nhận đã QA độc lập trước reference và kiểm lại ca sửa: [Điền sau P3/P5]
- [ ] C — Nguyễn Tuấn Minh xác nhận báo cáo đúng bản khóa, các file đầy đủ và check exit 0: [Điền sau P6]
- [ ] `manifest.json` tại commit chốt có `failed_gates` rỗng.
- [ ] Repo nhóm Public, ảnh và các bằng chứng mở được.
- [ ] C đã push và gửi link repo nhóm + commit qua kênh lớp công bố.

Chỉ đánh dấu việc đã kiểm thật. Nhóm nộp một hồ sơ chung; check không tự chấm đóng góp từng người. Giữ nguyên header/các cột enum của `findings.csv`; tên người được ghi trong tài liệu này hoặc phần note thích hợp.