# 🌙 Low-Light Image Enhancement

## 🔍 Giới thiệu

Dự án này tập trung vào việc **nâng cao chất lượng hình ảnh trong điều kiện ánh sáng yếu** thông qua việc xây dựng các bộ dữ liệu mô phỏng và áp dụng nhiều phương pháp cải thiện ảnh bao gồm:

- ⚙️ **Histogram Equalization (HE)**
- 🌈 **Retinex**
- 🔁 **Wavelet Transform**
- 🤖 **Deep Learning – Convolutional Neural Network (CNN)**

Dữ liệu được thu thập từ **Google Scraped Image Dataset** với 4 lớp:  
`Art & Culture`, `Architecture`, `Food and Drinks`, `Travel and Adventure`.

---

## 📁 Cấu trúc thư mục dữ liệu

> ⚠️ **Toàn bộ dữ liệu (ảnh gốc, ảnh thiếu sáng, ảnh đã xử lý...) không được đẩy trực tiếp lên GitHub do dung lượng lớn. Tất cả đã được lưu trữ trên Google Drive tại đây:**
👉 [Link Google Drive chứa toàn bộ dataset](https://drive.google.com/drive/folders/1cPuaHka-uqKS79abDetF2TGYamH9aE5e?usp=drive_link)


---

## 📦 Mô tả công dụng từng thư mục

| Thư mục                       | Mô tả                                                                 |
|------------------------------|----------------------------------------------------------------------|
| `images/`                    | Chứa ảnh gốc ban đầu, chưa qua xử lý                                 |
| `train/`, `validation/`, `test/` | Ảnh đã được chia theo tỷ lệ (60/10/30) để huấn luyện, xác thực và kiểm thử |
| `low_light/`                 | Ảnh được làm tối để mô phỏng điều kiện thiếu sáng                   |
| `low_light_noise/`          | Ảnh thiếu sáng có thêm nhiễu Gaussian hoặc Salt & Pepper           |
| `lowlight_enhance_trainset/`| Tập ảnh thiếu sáng dùng để huấn luyện mô hình CNN tăng cường ảnh   |
| `enhanced_he_*`             | Ảnh đã xử lý bằng phương pháp Histogram Equalization (HE)          |
| `enhanced_retinex_*`        | Ảnh đã xử lý bằng phương pháp Retinex                              |
| `enhanced_wavelet_*`        | Ảnh đã xử lý bằng biến đổi Wavelet Transform                      |
| `enhanced_cnn_*`            | Ảnh đã tăng cường bằng mô hình học sâu (CNN)                       |


---

## 🧪 Mục tiêu & Đánh giá

### 🎯 Mục tiêu nghiên cứu:
1. Tạo 2 tập dữ liệu mô phỏng ánh sáng yếu:
   - `Dataset 1`: Giảm độ sáng tổng thể.
   - `Dataset 2`: Giảm sáng + thêm nhiễu (Gaussian Noise) + làm mờ (Gaussian, Average, Median, Bilateral).
2. Ứng dụng các phương pháp tăng cường ảnh (HE, Retinex, Wavelet, CNN).
3. Xây dựng mô hình phân loại **EfficientNetB0** và đánh giá trên:
   - (1) Ảnh gốc
   - (2) Ảnh thiếu sáng
   - (3) Ảnh sau tăng cường
4. Tinh chỉnh siêu tham số (fine-tuning).
5. So sánh ảnh đầu ra bằng PSNR & SSIM.
6. Đánh giá độ chính xác phân loại bằng: **Accuracy**, **Precision**, **Recall**, **F1 Score**.

---

## 📂 Hướng dẫn sử dụng

1. Tải dataset đầy đủ tại link Google Drive.
2. Đặt đúng cấu trúc thư mục như trên trong thư mục `dataset/`.
3. **Chạy file notebook `CreateDataLowLight.ipynb`** để tạo các tập dữ liệu mô phỏng ánh sáng yếu:
   - `low_light/`: Ảnh bị làm tối (nhân hệ số ngẫu nhiên 0.1 – 0.5), không thêm nhiễu. Mô phỏng ảnh thiếu sáng thuần túy.
   - `low_light_noise/`: Ảnh bị làm tối (0.2 – 0.5) và thêm nhiễu ngẫu nhiên (Gaussian, Salt & Pepper, Poisson, Speckle).
   - `lowlight_enhance_trainset/`: Tạo tập huấn luyện cho mô hình tăng cường ảnh CNN, áp dụng quy trình làm tối và thêm nhiễu tương tự.
4. **Chạy các file notebook cải thiện ảnh** để áp dụng các phương pháp tăng cường ánh sáng:

   - 📊 `HE.ipynb` – **Histogram Equalization**  
     Tăng độ tương phản bằng cách phân bố lại histogram của ảnh.

   - 🌈 `Retinex.ipynb` – **Retinex Theory**  
     Mô phỏng cách mắt người cảm nhận ánh sáng và màu sắc, cải thiện độ sáng cục bộ.

   - 📐 `Wavelet.ipynb` – **Wavelet Transform**  
     Phân tích và tăng cường ảnh thông qua biến đổi đa tần số.

   - 🤖 `CNN.ipynb` – **Convolutional Neural Network**  
     Huấn luyện mô hình deep learning để khôi phục ảnh từ ảnh thiếu sáng có nhiễu.


   👉 Các ảnh đầu ra sẽ được lưu tương ứng trong các thư mục:
   - `enhanced_he_*`
   - `enhanced_retinex_*`
   - `enhanced_wavelet_*`
   - `enhanced_cnn_*`

5. Cuối cùng, chạy `efficientnetb0_enhanced_low_light_classification.ipynb` để:
   - Phân loại ảnh bằng EfficientNetB0  
   - Tính toán PSNR & SSIM  
   - Vẽ Confusion Matrix  
   - Lưu kết quả dự đoán trong thư mục `report/`.
---

## 📌 Lưu ý

- Dữ liệu lớn nên không được commit lên GitHub.
- Sử dụng `.gitignore` để loại trừ toàn bộ thư mục `dataset/`.


---

## 📫 Liên hệ

Nguyễn Chúc Ngân – MSSV: `21130451`  
Email: `21130451@st.hcmuaf.edu.vn`
