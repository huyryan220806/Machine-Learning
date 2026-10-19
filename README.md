![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Machine Learning — Học Máy Và Ứng Dụng

Repository lưu mã nguồn, dữ liệu và kết quả các bài thực hành môn Học Máy Và Ứng Dụng tại Trường Đại học Văn Lang.

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Danh sách bài thực hành

| Bài | Nội dung | Hướng dẫn |
| --- | --- | --- |
| 01 | Hồi quy tuyến tính: phân tích dữ liệu giá nhà, bình phương tối thiểu, đánh giá mô hình, gradient descent và hồi quy nhiều biến. | [Bài 01 — Hồi quy tuyến tính](01.%20Linear_Regression/README.md) |
| 02 | Logistic Regression: sigmoid, phân loại sinh viên, confusion matrix, các thước đo đánh giá, ngưỡng phân loại và mô hình nhiều biến. | [Bài 02 — Logistic Regression](02.%20Logistic_Regression/README.md) |
| 03 | Naive Bayes: định lý Bayes, túi từ, lọc thư rác, làm trơn Laplace, GaussianNB và 6 bài tập mục 7. | [Bài 03 — Naive Bayes](03.%20Naive_Bayes/README.md) |

## Cấu trúc repository

```text
Machine-Learning/
├── 01. Linear_Regression/
│   ├── code/                 # Notebook thực hành và bài tập
│   ├── data/                 # Dữ liệu gia_nha.csv
│   ├── figures/              # Biểu đồ PNG
│   ├── outputs/              # Nhật ký kết quả
│   ├── scripts/
│   │   └── run_all.py        # Chạy toàn bộ notebook của bài 01
│   ├── requirements.txt
│   └── README.md
├── 02. Logistic_Regression/
│   ├── code/                 # Notebook thực hành và bài tập
│   ├── data/                 # Dữ liệu sinh_vien.csv
│   ├── figures/              # Đồ thị sigmoid
│   ├── outputs/              # Kết quả chạy hai notebook
│   ├── scripts/
│   │   └── run_all.py        # Chạy toàn bộ notebook của bài 02
│   ├── requirements.txt
│   └── README.md
├── 03. Naive_Bayes/
│   ├── code/                 # 5 notebook thực hành và 6 notebook bài tập
│   ├── data/                 # tin_nhan.csv và sinh_vien.csv
│   ├── figures/              # 5 hình minh họa PNG
│   ├── outputs/              # Kết quả TXT của từng notebook
│   ├── scripts/
│   │   └── run_all.py        # Chạy toàn bộ 11 notebook của bài 03
│   ├── requirements.txt
│   └── README.md
├── .gitignore
└── README.md
```

## Tải và chạy bài 01

Clone repository hoặc chọn **Code → Download ZIP**, rồi giải nén toàn bộ để giữ nguyên cấu trúc thư mục.

```sh
git clone https://github.com/huyryan220806/Machine-Learning.git
cd "Machine-Learning/01. Linear_Regression"
```

Cài các thư viện bằng Python của môi trường đang dùng, sau đó chạy toàn bộ bài:

```sh
python -m pip install -r requirements.txt
python scripts/run_all.py
```

Script chạy notebook Lab trước, sau đó notebook bài tập. Kết quả được lưu trong notebook, nhật ký dạng chữ ở `outputs/`, và biểu đồ ở `figures/`.

Để đọc và chạy từng cell, mở Jupyter từ thư mục `01. Linear_Regression`:

```sh
python -m notebook
```

Mở notebook trong `code/`, chọn kernel đã cài thư viện và chạy từ trên xuống bằng **Run All**. Có thể mở dự án bằng VS Code để làm việc với các notebook.

## Tệp bài 01

- [Notebook thực hành](01.%20Linear_Regression/code/Lab1_NguyenDinhHuy.ipynb).
- [Notebook bài tập 1–6](01.%20Linear_Regression/code/Baitap.ipynb).
- [Dữ liệu giá nhà](01.%20Linear_Regression/data/gia_nha.csv).
- [Biểu đồ](01.%20Linear_Regression/figures/) và [kết quả chạy](01.%20Linear_Regression/outputs/).
- [Hướng dẫn chi tiết và cấu trúc thư mục](01.%20Linear_Regression/README.md).

Đường dẫn dữ liệu được xác định trong dự án, không phụ thuộc ổ đĩa hay tên người dùng. Khi chia sẻ hoặc di chuyển bài thực hành, giữ nguyên `code/`, `data/` và `scripts/` trong cùng thư mục bài.

## Tải và chạy bài 02

```sh
cd "Machine-Learning/02. Logistic_Regression"
python -m pip install -r requirements.txt
python scripts/run_all.py
```

Script chạy notebook thực hành và notebook bài tập, lưu kết quả mới vào notebook, xuất nhật ký dạng chữ ở `outputs/` và lưu đồ thị sigmoid tại `figures/sigmoid.png`.

Các tệp chính:

- [Notebook thực hành](02.%20Logistic_Regression/code/Lab2_NguyenDinhHuy.ipynb).
- [Notebook bài tập 1–6](02.%20Logistic_Regression/code/BaiTap2.ipynb).
- [Dữ liệu sinh viên](02.%20Logistic_Regression/data/sinh_vien.csv).
- [Biểu đồ](02.%20Logistic_Regression/figures/) và [kết quả chạy](02.%20Logistic_Regression/outputs/).
- [Hướng dẫn chi tiết](02.%20Logistic_Regression/README.md).

## Tải và chạy bài 03

Từ thư mục chứa repository, chạy:

```sh
cd "Machine-Learning/03. Naive_Bayes"
python -m pip install -r requirements.txt
python scripts/run_all.py
```

Mỗi bài có một notebook độc lập trong `code/`. Script chạy 5 bài thực hành trước, sau đó 6 bài tập mục 7; cập nhật kết quả trong notebook, lưu bản chữ vào `outputs/` và hình vào `figures/`. Đường dẫn được xác định theo vị trí dự án nên không cần sửa khi tải về máy khác.

- [11 notebook thực hành và bài tập](03.%20Naive_Bayes/code/).
- [Dữ liệu tin nhắn](03.%20Naive_Bayes/data/tin_nhan.csv) và [dữ liệu sinh viên](03.%20Naive_Bayes/data/sinh_vien.csv).
- [Hình minh họa](03.%20Naive_Bayes/figures/) và [kết quả chạy](03.%20Naive_Bayes/outputs/).
- [README Lab 3: từng bài, cách chạy và đối chiếu kết quả](03.%20Naive_Bayes/README.md).
