![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 01 — Hồi quy tuyến tính

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Xây dựng mô hình dự đoán giá nhà bằng hồi quy tuyến tính, từ công thức bình phương tối thiểu đến scikit-learn và gradient descent. Bài gồm hai notebook: thực hành theo tài liệu và lời giải bài tập 1–6.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab1_NguyenDinhHuy.ipynb](code/Lab1_NguyenDinhHuy.ipynb) | 7 bước thực hành theo tài liệu. |
| Bài tập | [Baitap.ipynb](code/Baitap.ipynb) | 6 bài tập, kèm nhận xét và biểu đồ. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [gia_nha.csv](data/gia_nha.csv) | 60 căn nhà, 4 cột | `dien_tich`, `so_phong`, `tuoi_nha`, `gia` |

Diện tích tính bằng mét vuông, tuổi nhà tính bằng năm và giá tính bằng tỷ đồng. Diện tích trong dữ liệu trải từ 35.5 đến 117.5 m².

## Phần thực hành

Mở [Lab1_NguyenDinhHuy.ipynb](code/Lab1_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| Bước 1 | Đọc CSV, xem dữ liệu và kiểm tra giá trị thiếu. |
| Bước 2 | Tính sai số và MSE của các đường thẳng giả định. |
| Bước 3 | Tìm hệ số bằng công thức bình phương tối thiểu. |
| Bước 4 | Khớp mô hình bằng scikit-learn và dự đoán giá. |
| Bước 5 | Chia tập học/kiểm tra; đánh giá MAE, MSE, RMSE và R². |
| Bước 6 | Tự tối ưu mô hình bằng gradient descent. |
| Bước 7 | Thêm số phòng và tuổi nhà vào mô hình nhiều biến. |

## Phần bài tập

Mở [Baitap.ipynb](code/Baitap.ipynb). Chạy cell đầu để nhập thư viện và thiết lập đường dẫn, sau đó chạy lần lượt 6 cell bài tập.

| Bài | Nội dung |
| --- | --- |
| Bài 1 | Lọc nhà có diện tích trên 100 m², đếm và tính giá trung bình. |
| Bài 2 | Vẽ giá theo số phòng và nhận xét xu hướng. |
| Bài 3 | Hồi quy giá theo tuổi nhà, giải thích dấu hệ số và xem biểu đồ. |
| Bài 4 | Dùng diện tích và số phòng, so sánh R² với mô hình một biến. |
| Bài 5 | Thử các tốc độ học, so sánh MSE sau 200 vòng lặp. |
| Bài 6 | Viết hàm dự đoán giá có cảnh báo khi diện tích ngoài miền dữ liệu. |

## Cấu trúc thư mục

```text
01. Linear_Regression/
├── code/
│   ├── Lab1_NguyenDinhHuy.ipynb
│   └── Baitap.ipynb
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

Mở terminal tại thư mục `01. Linear_Regression`, chạy:

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

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Hai notebook tìm `data/gia_nha.csv` từ thư mục hiện tại và các thư mục cha, nên chạy được từ thư mục bài hoặc `code/` mà không sửa đường dẫn ổ đĩa.

**Trên Colab:** Giữ cấu trúc `data/gia_nha.csv` cạnh `code/`, hoặc tạo thư mục `data` trong Files rồi tải `gia_nha.csv` vào đó. Lab 1 cần CSV nằm trong `data/`, không đặt trực tiếp ở thư mục hiện tại.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab1_NguyenDinhHuy.txt](outputs/Lab1_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [Baitap.txt](outputs/Baitap.txt) | Kết quả phần bài tập. |
| [bai2.png](figures/bai2.png) | Biểu đồ phân tán giá nhà theo số phòng. |
| [bai3.png](figures/bai3.png) | Biểu đồ phân tán giá nhà theo tuổi nhà. |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Giữ `test_size=0.2` và `random_state=42`: 48 căn dùng để học, 12 căn dùng để kiểm tra.

Mô hình một biến theo diện tích có `w = 0.078367`, `b = 0.401752`; dự đoán căn 80 m² khoảng **6.671 tỷ đồng**. MSE trên toàn bộ dữ liệu là **0.1790**, R² trên tập kiểm tra là **0.9622**. Khi thử tốc độ học, giữ số vòng lặp bằng 200 để so sánh công bằng.
