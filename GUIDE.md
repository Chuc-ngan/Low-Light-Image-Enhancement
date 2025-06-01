# 📘 Hướng Dẫn Sử Dụng Dự Án Low-Light-Image-Enhancement

## 1. Mô tả chung
Dự án tăng cường ảnh thiếu sáng bằng nhiều phương pháp khác nhau như:
- Histogram Equalization (HE)
- Retinex
- Wavelet
- Mô hình học sâu CNN

**Toàn bộ dataset được lưu trên Google Drive.** Bạn có thể tải về theo đường dẫn sau:
📎 [Link Google Drive](https://drive.google.com/your-link)

---

## 2. Cấu trúc thư mục dữ liệu

| Thư mục | Mô tả |
|--------|-------|
| `dataset/images` | Ảnh gốc ban đầu |
| `dataset/low_light` | Ảnh giả lập thiếu sáng |
| `dataset/low_light_noise` | Ảnh thiếu sáng có nhiễu |
| `dataset/enhanced_*` | Ảnh sau khi tăng cường bằng từng phương pháp |

---

## 3. Các bước thực hiện

1. **Tạo ảnh thiếu sáng:**  
   Chạy file `simulate_low_light.py`

2. **Tăng cường bằng các phương pháp:**  
   - `he_enhancement.py`  
   - `retinex_enhancement.py`  
   - `wavelet_enhancement.py`  
   - `cnn_enhancement.py`

3. **Đánh giá kết quả:**  
   Chạy `calculate_metrics.py` để tính PSNR & SSIM.

---

## 4. Yêu cầu môi trường

```bash
pip install -r requirements.txt
