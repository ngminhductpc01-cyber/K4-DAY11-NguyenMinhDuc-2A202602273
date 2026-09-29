# Sensor context

- **Rig / camera:** Dữ liệu thực hành sử dụng ảnh từ **một camera fisheye**. Ảnh có biến dạng fisheye rõ ở vùng rìa và trường nhìn rộng. Trong phạm vi dữ liệu được cung cấp, không có đủ thông tin để xác nhận chính xác vị trí lắp camera, hướng camera, FOV, intrinsic/extrinsic parameters hoặc cấu hình calibration của hệ thống. Vì vậy nhóm chỉ sử dụng các đặc điểm quan sát trực tiếp trên ảnh khi gán nhãn.

- **`ego_body`:** `ego_body` là phần thân xe của chính xe mang camera xuất hiện trong ảnh, có thể quan sát ở vùng phía dưới của một số frame. Chỉ tạo `ignore_region` với `reason=ego_body` khi phần thân xe thực sự nhìn thấy trong frame. Không giả định `ego_body` tồn tại nếu ảnh không cho thấy nó. Theo hướng dẫn của lab, `adasind_006840.jpg` và `adasind_271039.jpg` không có ego body nhìn thấy nên không thêm polygon `ego_body` cho hai frame này.

- **Vòng kính / `lens_border`:** Ảnh fisheye có vùng ảnh hữu ích nằm bên trong vòng kính và vùng ngoài biên kính không được xem như vùng quan sát bình thường của camera. `lens_border` được dùng để biểu diễn/soát vùng biên này. Polygon prefill của `lens_border` phải được kiểm lại theo vòng kính thực tế nhìn thấy trên từng frame, thay vì mặc định prefill luôn chính xác.

- **Giới hạn dữ liệu:** Tập ADASIND trong bài chỉ đại diện cho **một camera fisheye**. Vì vậy các quan sát từ những frame này không được dùng để suy ra đầy đủ hệ thống SVM 360° gồm `front/rear/left/right`. Dữ liệu cũng không cung cấp đủ thông tin để khẳng định calibration, timestamp, quan hệ hình học giữa nhiều camera hoặc chính sách ghép đối tượng tại vùng seam.

- **Nguyên tắc sử dụng:** Nhóm A/B/C kiểm tra `ego_body`, vòng kính, object và vùng ignore trực tiếp trên ảnh gốc. Những thông tin không thể xác nhận bằng ảnh hoặc tài liệu đi kèm được giữ ở trạng thái chưa xác định thay vì suy đoán.