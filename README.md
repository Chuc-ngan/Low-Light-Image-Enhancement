# Low-Light-Image-Enhancement

## 🔍 Giới thiệu
Tiểu luận này tập trung vào việc **tăng cường ảnh trong điều kiện thiếu sáng** bằng các phương pháp như:
- Histogram Equalization (HE)
- Retinex
- Wavelet
- Mạng nơ-ron tích chập (CNN)

---

## 📁 Cấu trúc thư mục dữ liệu

> ⚠️ **Toàn bộ dữ liệu (ảnh gốc, ảnh thiếu sáng, ảnh đã xử lý...) không được đẩy trực tiếp lên GitHub do dung lượng lớn. Tất cả đã được lưu trữ trên Google Drive tại đây:**
👉 [Link Google Drive chứa toàn bộ dataset](https://drive.google.com/drive/folders/1cPuaHka-uqKS79abDetF2TGYamH9aE5e?usp=drive_link)


---

## 📦 Mô tả công dụng từng thư mục

| Thư mục | Mô tả |
|--------|-------|
| `images/` | Chứa ảnh gốc ban đầu chưa qua xử lý |
| `train/`, `validation/`, `test/` | Dữ liệu được chia để huấn luyện và đánh giá mô hình |
| `low_light/` | Ảnh được làm tối để mô phỏng điều kiện thiếu sáng |
| `low_light_noise/` | Ảnh thiếu sáng có thêm nhiễu Gaussian hoặc Salt & Pepper |
| `enhanced_he_*` | Ảnh đã xử lý bằng phương pháp **Histogram Equalization** |
| `enhanced_retinex_*` | Ảnh đã xử lý bằng **Retinex** |
| `enhanced_wavelet_*` | Ảnh được tăng cường bằng **biến đổi Wavelet** |
| `enhanced_cnn_*` | Ảnh được tăng cường bằng mô hình **Convolutional Neural Network (CNN)** đã huấn luyện |

---

## 🧪 Đánh giá kết quả

Các ảnh đầu ra được so sánh với ảnh gốc dựa trên các chỉ số:
- **PSNR (Peak Signal-to-Noise Ratio)**
- **SSIM (Structural Similarity Index Measure)**

Kết quả được lưu tại:  
📄 `metrics/metrics_<method_name>.csv`

---

## 📂 Hướng dẫn sử dụng

1. Tải dataset đầy đủ tại link Google Drive.
2. Đặt đúng cấu trúc thư mục như trên trong thư mục `dataset/`.
3. Chạy file `calculate_and_save_metrics_per_image.py` để tính PSNR & SSIM.
4. Huấn luyện mô hình CNN (nếu cần) và so sánh các kết quả.

---

## 📌 Lưu ý

- Dữ liệu lớn nên không được commit lên GitHub.
- Sử dụng `.gitignore` để loại trừ toàn bộ thư mục `dataset/`.


---

## 📫 Liên hệ

Nguyễn Chúc Ngân – MSSV: `21130451`  
Email: `21130451@st.hcmuaf.edu.vn`
