![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 02 — Logistic Regression

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Xây dựng mô hình phân loại sinh viên qua môn từ số giờ ôn và điểm giữa kỳ. Bài gồm hai notebook: thực hành theo tài liệu và lời giải bài tập 1–6.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab2_NguyenDinhHuy.ipynb](code/Lab2_NguyenDinhHuy.ipynb) | 6 bước thực hành theo tài liệu. |
| Bài tập | [BaiTap2.ipynb](code/BaiTap2.ipynb) | 6 bài tập, mỗi bài một cell code có tiêu đề. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [sinh_vien.csv](data/sinh_vien.csv) | 120 sinh viên, 3 cột | `gio_on`, `diem_giua_ky`, `qua_mon` |

Nhãn `qua_mon` bằng 1 nghĩa là qua môn, bằng 0 nghĩa là rớt môn. Dữ liệu có 71 sinh viên qua môn và 49 sinh viên rớt môn.

## Phần thực hành

Mở [Lab2_NguyenDinhHuy.ipynb](code/Lab2_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| Bước 1 | Đọc dữ liệu và thống kê theo nhóm qua/rớt môn. |
| Bước 2 | Tính hàm sigmoid, kiểm tra tính chất và mô hình giả định. |
| Bước 3 | Huấn luyện Logistic Regression một biến và dự đoán sinh viên mới. |
| Bước 4 | Chia dữ liệu, đọc confusion matrix và tính bốn thước đo. |
| Bước 5 | Thay ngưỡng phân loại, quan sát precision và recall. |
| Bước 6 | Thêm điểm giữa kỳ, so sánh mô hình một biến và hai biến. |

## Phần bài tập

Mở [BaiTap2.ipynb](code/BaiTap2.ipynb). Mỗi bài có một cell code và tiêu đề riêng. Chạy từ bài 1 đến bài 6 để khởi tạo đầy đủ dữ liệu và mô hình.

| Bài | Nội dung |
| --- | --- |
| Bài 1 | Thống kê và so sánh tỷ lệ qua môn theo nhóm điểm giữa kỳ. |
| Bài 2 | Vẽ sigmoid trên đoạn từ −8 đến 8, thêm đường mức 0.5 và trục z = 0. |
| Bài 3 | Viết hàm dự đoán z, xác suất và nhãn cho số giờ ôn cụ thể. |
| Bài 4 | Tự tính accuracy, precision, recall và F1 từ TP, TN, FP, FN. |
| Bài 5 | Dò ngưỡng từ 0.05 đến 0.95 để tìm F1 cao nhất. |
| Bài 6 | Đổi lớp dương thành lớp rớt môn, so sánh precision và recall. |

## Cấu trúc thư mục

```text
02. Logistic_Regression/
├── code/
│   ├── Lab2_NguyenDinhHuy.ipynb
│   └── BaiTap2.ipynb
├── data/                # Dữ liệu CSV
├── figures/             # Biểu đồ PNG
├── outputs/             # Kết quả dạng chữ của từng notebook
├── scripts/
│   └── run_all.py        # Chạy toàn bộ notebook
├── requirements.txt
└── README.md
```

Giữ nguyên `code/`, `data/`, `scripts/` và `requirements.txt` trong cùng thư mục bài khi tải ZIP, clone hoặc di chuyển dự án. `figures/` và `outputs/` được tạo hoặc cập nhật khi chạy.

## Cài đặt và chạy toàn bộ

Mở terminal tại thư mục `02. Logistic_Regression`, chạy:

```sh
python -m pip install -r requirements.txt
python scripts/run_all.py
```

Script chạy notebook thực hành trước, sau đó notebook bài tập. Mỗi notebook dùng kernel riêng với đúng Python đang chạy script. Có thể gọi script bằng đường dẫn đầy đủ từ thư mục khác; script tự tìm thư mục bài từ vị trí của chính nó.

Kết quả được cập nhật trong notebook và xuất thành các tệp `.txt` ở `outputs/`; hình được lưu vào `figures/`. Mỗi lần chạy thay thế nhật ký cũ. Mỗi cell có tối đa 300 giây; nếu gặp lỗi, script dừng và không ghi đè notebook đang lỗi. Xem thông báo terminal và nhật ký trong `outputs/` để kiểm tra.

## Chạy từng notebook và Google Colab

Mở notebook bằng VS Code hoặc khởi động Jupyter từ thư mục bài:

```sh
python -m notebook
```

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Các notebook dùng đường dẫn dữ liệu trong dự án, không phụ thuộc ổ đĩa hay tên người dùng.

**Trên Colab:** Tải `sinh_vien.csv` trực tiếp vào Files hoặc giữ cấu trúc `data/sinh_vien.csv`. Hình sigmoid được lưu vào `figures/`.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab2_NguyenDinhHuy.txt](outputs/Lab2_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [BaiTap2.txt](outputs/BaiTap2.txt) | Kết quả phần bài tập. |
| [sigmoid.png](figures/sigmoid.png) | Đồ thị sigmoid và các đường tham chiếu của bài tập 2. |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Giữ `test_size=0.25`, `random_state=17` và `stratify=y`: 90 sinh viên dùng để học, 30 sinh viên dùng để kiểm tra.

Mô hình một biến khớp toàn bộ dữ liệu có `w = 0.392819`, `b = -5.064890`; xác suất qua môn bằng 0.5 tại khoảng **12.89 giờ ôn**. Khi đánh giá mô hình một biến trên tập kiểm tra với ngưỡng 0.5: **TN=9, FP=3, FN=1, TP=17**, accuracy **0.8667**, precision **0.8500**, recall **0.9444**, F1 **0.8947**.

Khi đổi ngưỡng hoặc lớp dương, giữ nguyên mô hình và tập kiểm tra để giải thích đúng sự thay đổi của các chỉ số.
