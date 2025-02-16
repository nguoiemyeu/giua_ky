# Đề xuất trang sức phù hợp dựa trên hình dạng khuôn mặt  

## Mô tả dự án  
Ứng dụng sử dụng OpenCV và MediaPipe để nhận diện khuôn mặt từ webcam và phân loại hình dạng khuôn mặt. Dựa trên hình dạng khuôn mặt, ứng dụng sẽ đề xuất và chèn hình ảnh trang sức phù hợp (khuyên tai và vòng cổ).  

## Tính năng  
- Phát hiện khuôn mặt và các điểm landmark bằng MediaPipe Face Mesh.  
- Phân loại hình dạng khuôn mặt thành các loại: dài, trái xoan, tròn, vuông, và tam giác.  
- Tính toán tỉ lệ chiều dài/chiều rộng và tỉ lệ hàm/trán để phân loại hình dạng khuôn mặt.  
- Đề xuất trang sức phù hợp với từng loại khuôn mặt.  
- Chèn hình ảnh trang sức (khuyên tai, vòng cổ) lên khuôn mặt trong thời gian thực.  

## Công nghệ sử dụng  
- Python 3.x  
- OpenCV  
- MediaPipe  
- Pillow (PIL)  
- NumPy  
- Math  

## Cách cài đặt và sử dụng  

### 1. Yêu cầu hệ thống  
- Python 3.x  
- Webcam  

### 2. Cài đặt thư viện  
Chạy lệnh sau để cài đặt các thư viện cần thiết:  
```bash
pip install opencv-python-headless mediapipe pillow numpy
```

### 3. Cấu trúc thư mục  
```
project_folder/
│   main.py                   # Source code chính
│   arial.ttf                 # Font chữ hiển thị
│
└─── images/
     │   earring_long.png
     │   earring_oval.png
     │   earring_round.png
     │   earring_square.png
     │   earring_triangle.png
     │   necklace_long.png
     │   necklace_oval.png
     │   necklace_round.png
     │   necklace_square.png
     │   necklace_triangle.png
```

### 4. Chạy chương trình  
- Đảm bảo đã kết nối webcam.  
- Mở terminal và chạy:  
```bash
python main.py
```

### 5. Thao tác  
- Chương trình sẽ mở webcam và nhận diện khuôn mặt trong thời gian thực.  
- Để thoát khỏi chương trình, nhấn phím 'q'.  

## Giải thích chi tiết các chức năng  

### 1. classify_face_shape_from_landmarks(landmarks)  
- Phân loại hình dạng khuôn mặt dựa trên các điểm landmark:  
  - Tính khoảng cách Euclid giữa các điểm landmark quan trọng như: đỉnh trán, cằm, hai bên khuôn mặt, và trán.  
  - Sử dụng tỉ lệ chiều dài/chiều rộng và tỉ lệ hàm/trán để phân loại hình dạng khuôn mặt.  
  - Các loại hình dạng khuôn mặt: dài, trái xoan, tròn, vuông, tam giác.  

### 2. calculate_jewelry_size_and_position(...)  
- Tính toán kích thước và vị trí chèn hình ảnh trang sức dựa trên bounding box của khuôn mặt và loại khuôn mặt.  

### 3. add_jewelry(...)  
- Chèn hình ảnh trang sức (khuyên tai và vòng cổ) lên ảnh.  
- Chọn hình ảnh trang sức dựa trên loại khuôn mặt đã phân loại.  
- Sử dụng thư viện Pillow để xử lý và chèn ảnh.  

### 4. suggest_jewelry_mediapipe()  
- Khởi tạo webcam và MediaPipe Face Mesh.  
- Xử lý từng frame từ webcam:  
  - Phát hiện khuôn mặt và các điểm landmark.  
  - Phân loại hình dạng khuôn mặt.  
  - Chèn hình ảnh trang sức tương ứng.  
  - Hiển thị kết quả trong thời gian thực bằng OpenCV.  

## Các lưu ý quan trọng  
- Đảm bảo đã tải về và đặt đúng các file hình ảnh trang sức trong thư mục `images/`.  
- Đảm bảo có font `arial.ttf` trong thư mục dự án.  
- Điều chỉnh vị trí và kích thước trang sức có thể cần thiết để phù hợp với từng khuôn mặt cụ thể.  

## Troubleshooting  
- **Lỗi không mở được webcam:**  
  - Đảm bảo đã kết nối webcam và không có ứng dụng nào khác đang sử dụng nó.  
- **Không nhận diện được khuôn mặt:**  
  - Điều chỉnh ánh sáng trong phòng để khuôn mặt rõ ràng hơn.  
  - Đảm bảo không có vật cản che khuôn mặt.  
- **Lỗi không hiển thị trang sức:**  
  - Kiểm tra lại đường dẫn và sự tồn tại của các file hình ảnh trang sức.  

## Ghi chú  
- Dự án này chỉ mang tính chất minh họa và có thể cần điều chỉnh thêm để phù hợp với từng trường hợp sử dụng cụ thể.  
