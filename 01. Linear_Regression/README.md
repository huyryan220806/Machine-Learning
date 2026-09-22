![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 01 — Hồi quy tuyến tính

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Nội dung bài thực hành

Hai notebook dùng bộ dữ liệu 60 căn nhà trong `data/gia_nha.csv`:

- `code/Lab1_NguyenDinhHuy.ipynb`: các bước thực hành theo tài liệu.
- `code/Baitap.ipynb`: lời giải bài tập 1–6, có nhận xét và biểu đồ.

## Chạy sau khi tải từ GitHub

1. Clone repository hoặc tải **Download ZIP** rồi giải nén toàn bộ. Giữ nguyên thư mục `data` cạnh thư mục `code`.
2. Mở terminal trong thư mục chứa tệp `requirements.txt`, cài thư viện:

   ```sh
   python -m pip install -r requirements.txt
   ```

3. Mở Jupyter Notebook:

   ```sh
   python -m notebook
   ```

4. Mở một notebook trong `code/`, chọn kernel Python đã cài thư viện và chạy **Run All** theo thứ tự từ trên xuống.

Cũng có thể mở thư mục dự án bằng VS Code và chạy notebook với kernel Python đã cài các thư viện trên.

## Chạy toàn bộ bằng một lệnh

Sau khi cài `requirements.txt`, mở terminal tại thư mục dự án và chạy:

```sh
python scripts/run_all.py
```

Script chạy notebook Lab trước, sau đó Baitap (và các notebook khác trong `code/` nếu có). Mỗi notebook chạy trong kernel riêng, dùng đúng Python đang chạy script. Không cần mở giao diện Jupyter.

- Kết quả và biểu đồ được lưu lại ngay trong các notebook ở `code/`.
- Nhật ký dạng chữ được lưu trong `outputs/`, theo tên notebook.
- Baitap xuất biểu đồ thành `figures/bai2.png` và `figures/bai3.png`.
- Mỗi cell có tối đa 300 giây để chạy. Nếu gặp lỗi, script dừng và không ghi đè notebook đang lỗi; xem nhật ký và thông báo trên terminal để sửa.

Có thể chạy từ thư mục khác bằng đường dẫn đầy đủ tới `scripts/run_all.py`; script tự tìm thư mục dự án dựa trên vị trí của chính nó.

## Cấu trúc thư mục

```text
01. Linear_Regression/
├── code/
│   ├── Baitap.ipynb
│   └── Lab1_NguyenDinhHuy.ipynb
├── data/
│   └── gia_nha.csv
├── figures/
│   ├── bai2.png
│   └── bai3.png
├── outputs/
│   ├── Lab1_NguyenDinhHuy.txt
│   └── Baitap.txt
├── scripts/
│   └── run_all.py
├── README.md
└── requirements.txt
```

Các tệp trong `figures/` và `outputs/` được tạo hoặc cập nhật khi chạy bài.

| Thư mục / tệp | Chức năng |
| --- | --- |
| `code/` | Chứa hai notebook. Chạy các cell theo thứ tự từ trên xuống để các biến và dữ liệu được khởi tạo đầy đủ. |
| `code/Lab1_NguyenDinhHuy.ipynb` | Các bước thực hành: đọc dữ liệu, tính sai số, bình phương tối thiểu, scikit-learn, đánh giá mô hình, gradient descent và hồi quy nhiều biến. |
| `code/Baitap.ipynb` | Bài tập 1–6, gồm mã, nhận xét và biểu đồ. Cell đầu nhập thư viện và thiết lập đường dẫn. |
| `data/gia_nha.csv` | Dữ liệu 60 căn nhà, gồm `dien_tich`, `so_phong`, `tuoi_nha` và `gia`. Cần giữ tệp này khi tải hoặc chia sẻ dự án. |
| `figures/` | Lưu biểu đồ PNG: `bai2.png` là giá theo số phòng, `bai3.png` là giá theo tuổi nhà. |
| `outputs/` | Lưu kết quả dạng chữ của từng notebook sau khi chạy `run_all.py`. Mở các tệp `.txt` để xem kết quả và kiểm tra lỗi. |
| `scripts/run_all.py` | Chạy toàn bộ notebook trong `code/`, lưu kết quả vào notebook và xuất nhật ký vào `outputs/`. |
| `requirements.txt` | Danh sách thư viện cần cài để chạy notebook và script. |
| `README.md` | Thông tin bài thực hành, cấu trúc thư mục và hướng dẫn chạy. |

## Cách xử lý đường dẫn

Hai notebook tìm `data/gia_nha.csv` từ thư mục đang chạy và các thư mục cha. Vì vậy có thể chạy từ thư mục gốc dự án hoặc `code/`, kể cả khi đổi tên hoặc di chuyển toàn bộ dự án. Không cần sửa đường dẫn ổ đĩa hay tên người dùng.

Biểu đồ bài 2 và bài 3 được lưu tại `figures/bai2.png` và `figures/bai3.png`. Nếu chỉ tải riêng notebook mà thiếu thư mục `data`, chương trình sẽ báo rõ tệp dữ liệu cần bổ sung.

Giữ `test_size=0.2` và `random_state=42` để phép chia tập học/kiểm tra khớp tài liệu.
