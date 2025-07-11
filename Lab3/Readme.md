
# 🖼️ Xử lý Ảnh Số với Python

## 📦 Cài đặt thư viện

```bash
pip install numpy scipy imageio matplotlib
```

## 📌 Nội dung các bài

- **Cắt ảnh và lưu lại:**
```python
data = iio.imread('fruit.jpg')
bmg = data[800:1200 ,1500:2000]
iio.imsave('orange.jpg', bmg)
```

- **Dịch chuyển ảnh x/y:**
```python
data = iio.imread('fruit.jpg', pilmode='L')
shifted = nd.shift(data, (50, -30))
```

- **Phóng to / Thu nhỏ ảnh:**
```python
zoom_in = nd.zoom(data, (3, 3, 1))
zoom_out = nd.zoom(data, (0.3, 0.3, 1))
```

- **Xoay ảnh 45°:**
```python
nd.rotate(data, 45, reshape=True)
nd.rotate(data, 45, reshape=False)
```

- **Dilation & Erosion (5x5):**
```python
dilate = nd.grey_dilation(data, size=(5, 5, 1))
erode = nd.grey_erosion(data, size=(5, 5, 1))
```

- **Biến đổi hình học (wave effect):**
```python
def GeoFun(c): return 5*np.sin(c[0]/5)+c[0], 5*np.sin(c[1]/5)+c[1]
warped = nd.geometric_transform(data, GeoFun)
```
## 📌 Nội dung các bài

### Bài 1: Tịnh tiến và hiệu ứng sóng ảnh Kiwi
- Dịch ảnh kiwi 50px sang phải, 30px xuống dưới.
- Áp dụng hiệu ứng sóng bằng `map_coordinates`.
- Hiển thị và lưu ảnh kết quả: `kiwi_wave.jpg`.

### Bài 2: Gradient màu cho trái cây
- Đọc ảnh đu đủ và dưa hấu (`RGBA`).
- Áp dụng gradient màu:
  - Đu đủ: đỏ → xanh lá.
  - Dưa hấu: vàng → tím.
- Ghép 2 ảnh có alpha nền trong suốt, lưu `papaya_watermelon_gradient.png`.

### Bài 3: Xoay và phản chiếu ảnh núi và thuyền
- Xoay 45° không thay đổi kích thước.
- Phản chiếu dọc (vertical mirror).
- Ghép lên nền trắng và lưu: `mountain_boat_mirror.jpg`.

### Bài 4: Phóng to và uốn cong ảnh chùa
- Phóng to ảnh 5 lần.
- Uốn cong bằng tọa độ sin → hiệu ứng wave warp.
- Lưu ảnh kết quả: `pagoda_warped.jpg`.

### Bài 5: Menu xử lý ảnh tương tác
- Cho phép chọn ảnh từ danh sách.
- Các phép xử lý hỗ trợ:
  - Tịnh tiến ảnh (theo x/y).
  - Xoay ảnh (tùy chọn reshape).
  - Phóng to / thu nhỏ.
  - Làm mờ Gaussian.
  - Biến đổi sóng (wave distortion).
- Lưu ảnh kết quả: `transformed_image.jpg`.

## 📌 Nội dung các bài lab3-goc.ipynb

### Bài 1: Tịnh tiến & Hiệu ứng sóng
- Dịch ảnh kiwi (50px phải, 30px xuống).
- Áp dụng hiệu ứng sóng (`map_coordinates`).
- Lưu: `kiwi_wave.jpg`.

### Bài 2: Gradient màu
- Đọc ảnh đu đủ, dưa hấu (`RGBA`).
- Gradient: đỏ → xanh (đu đủ), vàng → tím (dưa hấu).
- Ghép ảnh, lưu: `papaya_watermelon_gradient.png`.

### Bài 3: Xoay & Phản chiếu
- Xoay ảnh núi/thuyền 45° (giữ kích thước).
- Phản chiếu dọc, ghép nền trắng.
- Lưu: `mountain_boat_mirror.jpg`.

### Bài 4: Phóng to & Uốn cong
- Phóng to ảnh chùa 5 lần.
- Uốn cong (hiệu ứng wave warp).
- Lưu: `pagoda_warped.jpg`.

### Bài 5: Menu tương tác (OpenCV)
- **Chọn ảnh**:
  - `colorful-ripe-tropical-fruits.jpg`
  - `quang_ninh.jpg`
  - `pagoda.jpg`
- **Phép xử lý**:
  - Tịnh tiến (X/Y do người dùng nhập).
  - Xoay (góc độ nhập).
  - Phóng to/thu nhỏ (tỷ lệ nhập).
  - Coordinate Map (hiển thị tọa độ).
- **Kết quả**: Hiển thị ảnh gốc/kết quả, lưu `result_{T/X/P/H}.jpg`.
- **Thoát**: Nhấn `Q`.

---
## 🧪 Yêu cầu

- Ảnh `fruit.jpg`, `world_cup.jpg` có trong thư mục.
- Kết quả hiển thị bằng matplotlib hoặc lưu bằng `iio.imsave()`.

🎓 Thực hành xử lý ảnh cơ bản bằng Python.
