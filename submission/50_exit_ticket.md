# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Hai box sát seam chỉ được coi là cùng một physical object khi policy cross-camera cho phép và có bằng chứng đồng bộ thời gian, calibration/extrinsics và quan sát nhất quán. Nếu chưa có các điều kiện đó, giữ chúng là annotation theo từng camera; không tự xóa hay ghép chỉ vì vị trí nhìn có vẻ gần.
2. Trong cùng một camera, giữ track ID khi đó vẫn là cùng physical object còn nhìn thấy; dùng keyframe để cập nhật hình học/thuộc tính khi thay đổi và dùng Outside khi vật thể rời FOV. Qua camera chỉ nối ID khi policy tracking đa camera, timestamp và calibration xác nhận được cùng đối tượng; nếu không, tạo track theo camera.
3. Bất đồng thực tế tại `adasind_212280.jpg`: teaching reference R1 thiếu người đi bộ trong khi ảnh gốc hỗ trợ pair L1 Pedestrian + L2 Bike theo R03. Bản rework giữ pair này, chỉ xóa L5 duplicate và đặt Bus L3 `truncated=true`; reference được escalated thay vì ép learner theo reference. Lần sau quy trình sẽ chốt QA mù trên ảnh/rule trước, sau đó mới dùng reference/model như tín hiệu chẩn đoán và ghi rõ mọi ngoại lệ vào decision log.
