# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Xe máy/người lái bị che bởi xe ego hoặc xe đông | Dễ bỏ sót rider hoặc gộp nhầm xe nhỏ | Giữ intrinsics/extrinsics phiên bản đã dùng, image-space theo từng camera | Hai annotator độc lập, adjudication trên ảnh gốc, kiểm rule R01/R03/R04/R05 |
| rear | Đối tượng lùi, đi vào/ra biên ảnh | Dễ sai `truncated` hoặc bỏ box ở mép | Giữ mapping rear và mốc biên lens; không chuyển box sang camera khác | Review keyframe, kiểm thuộc tính `truncated`, đối chiếu ảnh gốc |
| left | ThreeWheeler/xe nhỏ sát rìa fisheye | Méo fisheye làm sai lớp, kích thước và ngưỡng H=40 | Giữ calibration left và quy ước đo chiều cao theo ảnh gốc | Peer review độc lập, đo H, adjudicate các ca sát ngưỡng |
| right | Xe cắt seam và xe bị che một phần | Có nguy cơ duplicate hoặc ghép nhầm đối tượng giữa camera | Giữ calibration right, timestamp đồng bộ và policy seam | Review trong camera trước, chỉ ghép cross-camera khi policy/evidence đầy đủ |

- Refresh gold set khi đổi camera/lens, cập nhật intrinsics hoặc extrinsics, đổi taxonomy/threshold/thuộc tính, hoặc khi error drift theo camera vượt ngưỡng review đã thống nhất.
- Ca seam/cross-camera phải có policy xác định điều kiện ghép, timestamp đồng bộ, calibration/extrinsics tương ứng, bằng chứng cùng physical object và quy tắc output (một hay nhiều box) trước khi hợp nhất.
- Peer agreement hoặc quality report của một camera chỉ chứng minh mức nhất quán trên ảnh và calibration của camera đó; chúng không kiểm tra distortion, visibility, seam hay distribution shift của ba camera còn lại.
