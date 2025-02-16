
# Đề Xuất Trang Sức Phù Hợp Theo Khuôn Mặt

Ứng dụng này sử dụng OpenCV để nhận diện khuôn mặt từ webcam và đề xuất trang sức phù hợp dựa trên tỷ lệ khuôn mặt. Gợi ý trang sức sẽ xuất hiện trên màn hình theo các loại khuôn mặt như: dài, trái xoan, tròn, vuông và tam giác.

---

## Tính Năng
- Nhận diện khuôn mặt trong thời gian thực bằng OpenCV.
- Phân loại khuôn mặt theo tỷ lệ chiều rộng và chiều cao.
- Đề xuất trang sức phù hợp với từng loại khuôn mặt.
- Hiển thị gợi ý trang sức trên màn hình bằng Pillow (PIL).

---

## Công Nghệ Sử Dụng
- **Python 3.x**
- **OpenCV**: Nhận diện khuôn mặt.
- **Pillow (PIL)**: Hiển thị gợi ý trang sức.
- **Numpy**: Chuyển đổi định dạng ảnh giữa OpenCV và Pillow.

---

## Cài Đặt
1. **Cài đặt Python 3.x** nếu chưa có trên máy.

2. **Cài đặt các thư viện cần thiết:**
   ```sh
   pip install opencv-python-headless pillow numpy
   ```

3. **Tải Font Arial:**
   - Đảm bảo có file `arial.ttf` trong cùng thư mục với mã nguồn hoặc cập nhật đường dẫn trong đoạn code sau:
     ```python
     font_path = "arial.ttf"
     ```

4. **Tải Mô Hình Haarcascade:**
   - OpenCV tự động tải mô hình nhận diện khuôn mặt `haarcascade_frontalface_default.xml`. Nếu gặp lỗi, tải thủ công từ:
     [https://github.com/opencv/opencv/tree/master/data/haarcascades](https://github.com/opencv/opencv/tree/master/data/haarcascades)
   - Sau đó, đặt file này vào cùng thư mục với mã nguồn.

---

## Cách Chạy Chương Trình
Mở terminal và chạy lệnh sau:
```sh
python your_script_name.py
```

- Webcam sẽ tự động bật và nhận diện khuôn mặt.
- Gợi ý trang sức sẽ xuất hiện trên màn hình theo từng loại khuôn mặt.
- Nhấn phím `q` để thoát chương trình.

---

## Phân Loại Khuôn Mặt
Chương trình sử dụng tỷ lệ chiều rộng và chiều cao của khuôn mặt để phân loại:

| Loại Khuôn Mặt      | Tỷ Lệ W/H         | Gợi Ý Trang Sức                              |
|---------------------|-------------------|-----------------------------------------------|
| Khuôn mặt dài       | < 0.8             | Trang sức thanh mảnh, dây chuyền dài           |
| Khuôn mặt trái xoan | 0.8 - 1.0          | Trang sức cân đối, kiểu dáng đơn giản           |
| Khuôn mặt tròn      | 1.0 - 1.2         | Trang sức góc cạnh, tạo hiệu ứng thon gọn      |
| Khuôn mặt vuông     | 1.2 - 1.4         | Trang sức mềm mại, đường cong                   |
| Khuôn mặt tam giác  | > 1.4             | Trang sức tập trung vào phần dưới, bông tai dài|

---

## Lưu Ý
- Chương trình yêu cầu webcam hoạt động tốt.
- Đảm bảo có ánh sáng đủ để nhận diện khuôn mặt chính xác hơn.
- Chương trình đang sử dụng cách tính tỷ lệ W/H, có thể không chính xác tuyệt đối trong mọi trường hợp.

---

