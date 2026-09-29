# Tự soát

- adasind_152940.jpg L3: chiều cao < H (xem lại phạm vi)
- adasind_152940.jpg L6: truncated khác dự kiến
- adasind_167700.jpg L3: truncated khác dự kiến
- adasind_212280.jpg L3: chiều cao < H (xem lại phạm vi)
- adasind_212280.jpg L4: truncated khác dự kiến
- adasind_212280.jpg: hai box cùng class IoU > 0.7
- Tên task thiếu raw_fisheye

## Checklist thủ công
- [x] Phạm vi H=40 và vật cần vẽ
- [x] lens_border và ego_body
- [x] Class sáu nhãn
- [x] Rider và Bike
- [x] Geometry trên ảnh fisheye gốc
- [x] truncated và occluded
- [x] Vật thiếu hoặc box trùng
- [x] ignore_region có reason
- [x] Tên task raw_fisheye và export CVAT 1.1 — tên task hiện thiếu `raw_fisheye`; cần sửa tên task trước khi đánh dấu hoàn tất.

## Fill ratio (K12)
- adasind_152940.jpg box 6 mid: 0.680
- adasind_167700.jpg box 10 center: 0.600
- adasind_167700.jpg box 9 edge: 0.880
- adasind_212280.jpg box 4 edge: 0.767
mean edge: 0.823 (n=2)
mean center: 0.600 (n=1)
