![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 02 — Logistic Regression

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Nội dung bài thực hành

Bài 02 xây dựng mô hình phân loại dự đoán sinh viên qua môn từ số giờ ôn và điểm giữa kỳ. Nội dung gồm:

- Đọc và thống kê dữ liệu sinh viên.
- Tính và kiểm tra hàm sigmoid.
- Huấn luyện Logistic Regression bằng scikit-learn.
- Đánh giá bằng confusion matrix, accuracy, precision, recall và F1.
- Khảo sát ảnh hưởng của ngưỡng phân loại.
- So sánh mô hình một biến và hai biến.

Hai notebook chính:

- `code/Lab2_NguyenDinhHuy.ipynb`: các bước thực hành theo tài liệu.
- `code/BaiTap2.ipynb`: lời giải sáu bài tập, gồm nhận xét và biểu đồ sigmoid.

## Cấu trúc thư mục

```text
02. Logistic_Regression/
├── code/
│   ├── Lab2_NguyenDinhHuy.ipynb
│   └── BaiTap2.ipynb
├── data/
│   └── sinh_vien.csv
├── figures/
│   └── sigmoid.png
├── outputs/
│   ├── Lab2_NguyenDinhHuy.txt
│   └── BaiTap2.txt
├── scripts/
│   └── run_all.py
├── README.md
└── requirements.txt
```

| Thư mục / tệp | Chức năng |
| --- | --- |
| `code/` | Chứa notebook thực hành và bài tập. |
| `data/sinh_vien.csv` | Dữ liệu 120 sinh viên gồm số giờ ôn, điểm giữa kỳ và kết quả qua môn. |
| `figures/sigmoid.png` | Đồ thị hàm sigmoid từ bài tập 2. |
| `outputs/` | Kết quả dạng chữ được xuất từ hai notebook. |
| `scripts/run_all.py` | Chạy toàn bộ notebook, lưu kết quả vào notebook và xuất nhật ký. |
| `requirements.txt` | Danh sách thư viện Python cần cài. |

## Chạy toàn bộ và xuất kết quả

Mở terminal trong thư mục `02. Logistic_Regression`, chạy:

```sh
python -m pip install -r requirements.txt
python scripts/run_all.py
```

Script chạy `code/Lab2_NguyenDinhHuy.ipynb` trước, sau đó `code/BaiTap2.ipynb`. Mỗi notebook có kernel riêng, dùng đúng Python đang chạy script. Có thể gọi script bằng đường dẫn đầy đủ từ thư mục khác.

Sau khi chạy thành công:

- `outputs/Lab2_NguyenDinhHuy.txt`: kết quả thực hành, gồm cả bảng được in bằng `display()`.
- `outputs/BaiTap2.txt`: kết quả sáu bài tập.
- `figures/sigmoid.png`: biểu đồ sigmoid của bài tập 2.
- Hai notebook trong `code/` được lưu lại với kết quả thực thi mới, giữ nguyên mã và các tiêu đề đã chỉnh trên Colab.

Mỗi lần chạy sẽ cập nhật các tệp kết quả, không nối lặp nhật ký cũ. Nếu một cell lỗi, script dừng, lưu nhật ký lỗi trong `outputs` và không ghi đè notebook đang lỗi.

## Khi chỉnh sửa trên Colab

Sau khi chỉnh notebook trên Colab, tải lại tệp `.ipynb` và lưu đè bản tương ứng trong `code/`, rồi chạy script. Script dùng bản trên máy, không tự đồng bộ thay đổi trên Colab.

Nếu chạy script ngay trên Colab, cần tải toàn bộ thư mục bài (gồm `code`, `data`, `scripts`, `requirements.txt`) lên Colab hoặc Google Drive rồi chuyển tới thư mục bài. Chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả ở notebook; việc xuất các tệp `.txt` trong `outputs` được thực hiện bởi `run_all.py`.

## Chạy từng notebook

Có thể mở Jupyter từ thư mục bài:

```sh
python -m notebook
```

Mở notebook trong `code/`, chọn kernel đã cài đủ thư viện và chạy các cell từ trên xuống. Khi chạy trên Colab, tải `sinh_vien.csv` vào thư mục hiện tại hoặc giữ cấu trúc `data/sinh_vien.csv`.
