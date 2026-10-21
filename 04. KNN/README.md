![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 04 — K láng giềng gần nhất (KNN)

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Tìm hiểu KNN từ khoảng cách Euclid và bỏ phiếu đến chuẩn hóa, chọn số láng giềng bằng kiểm định chéo, so sánh mô hình và hồi quy giá nhà. Có đúng **2 notebook**: thực hành **5 cell code** và bài tập mục 7 **6 cell code**. Mỗi mục có tiêu đề riêng; mã và hình của một mục nằm chung một cell. Phần thực hành giữ thuật toán, ví dụ và tham số trong mã giảng viên, chỉ bổ sung đường dẫn và hình minh họa.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab4_NguyenDinhHuy.ipynb](code/Lab4_NguyenDinhHuy.ipynb) | 5 mục theo mã e1–e5 của giảng viên, mỗi mục một cell code. |
| Bài tập | [BaiTap4.ipynb](code/BaiTap4.ipynb) | 6 bài ở mục 7, mỗi bài một cell code có nhận xét. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [sinh_vien_mo_rong.csv](data/sinh_vien_mo_rong.csv) | 120 sinh viên, 4 cột | `gio_on`, `diem_giua_ky`, `chi_tieu`, `qua_mon` |
| [hai_vang_trang.csv](data/hai_vang_trang.csv) | 300 điểm, 3 cột | `x1`, `x2`, `nhan` |
| [gia_nha.csv](data/gia_nha.csv) | 60 căn nhà, 4 cột | `dien_tich`, `so_phong`, `tuoi_nha`, `gia` |

Cả ba bộ dữ liệu mô phỏng phục vụ giảng dạy. `qua_mon` và `nhan` là nhãn nhị phân. `chi_tieu` tính bằng nghìn đồng; diện tích nhà tính bằng m², giá tính bằng tỷ đồng. Khi đổi đơn vị ở bài tập 3, chỉ thay trên bản sao trong bộ nhớ, giữ nguyên CSV.

## Phần thực hành

Mở [Lab4_NguyenDinhHuy.ipynb](code/Lab4_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| Cell 1 — Mục 2.3 | Tự tính khoảng cách Euclid, chuẩn hóa và tìm 5 láng giềng cho bạn mới. |
| Cell 2 — Mục 3.2 | So sánh KNN chưa chuẩn hóa, có chuẩn hóa và bỏ cột chi tiêu. |
| Cell 3 — Mục 4.2 | Quan sát ảnh hưởng của k; chọn k bằng kiểm định chéo 5 phần trên tập học. |
| Cell 4 — Mục 5 | So sánh KNN, Logistic Regression và GaussianNB trên hai vầng trăng. |
| Cell 5 — Mục 6 | KNN hồi quy giá nhà, so MAE và dự đoán ngoài miền dữ liệu. |

## Phần bài tập

Mở [BaiTap4.ipynb](code/BaiTap4.ipynb). Bao gồm toàn bộ 6 bài tập mục 7. Các cell có thiết lập dữ liệu riêng; dùng Run All để lưu đủ kết quả.

| Bài | Nội dung |
| --- | --- |
| Bài 1 | Viết `knn_du_doan` bằng NumPy, đánh giá k=13 và đối chiếu scikit-learn. |
| Bài 2 | Chọn k bằng khoảng cách Manhattan và so sánh Euclid. |
| Bài 3 | Đổi chi tiêu từ nghìn sang triệu đồng, so sánh trước/sau chuẩn hóa. |
| Bài 4 | Thử `weights="distance"` với k=1, 13, 101, so với trọng số đều. |
| Bài 5 | Chọn k=1…20 bằng MAE kiểm định chéo, so với hồi quy tuyến tính. |
| Bài 6 | Đo fit và predict 1.000 điểm mới trên 1.000, 10.000, 100.000 mẫu học. |

## Cấu trúc thư mục

```text
04. KNN/
├── code/
│   ├── Lab4_NguyenDinhHuy.ipynb
│   └── BaiTap4.ipynb
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

Mở terminal tại thư mục `04. KNN`, chạy:

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

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Mỗi notebook tìm dữ liệu từ thư mục bài hoặc `code/`; không chứa đường dẫn ổ đĩa cố định.

**Trên Colab:** Tải đủ `sinh_vien_mo_rong.csv`, `hai_vang_trang.csv` và `gia_nha.csv` vào Files hoặc thư mục `data/`. Hình lưu tại `figures/`. Muốn giữ kết quả sau khi phiên Colab kết thúc, tải notebook và các tệp kết quả về máy.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab4_NguyenDinhHuy.txt](outputs/Lab4_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [BaiTap4.txt](outputs/BaiTap4.txt) | Kết quả phần bài tập. |
| [e1_lang_gieng.png](figures/e1_lang_gieng.png) | Năm láng giềng của sinh viên mới. |
| [e2_chuan_hoa.png](figures/e2_chuan_hoa.png) | Accuracy trước/sau chuẩn hóa và bỏ chi tiêu. |
| [e3_bien_theo_k.png](figures/e3_bien_theo_k.png) | Biên quyết định với k=1, 13, 101. |
| [e3_chon_k_cv.png](figures/e3_chon_k_cv.png) | Điểm kiểm định chéo dùng chọn k. |
| [e4_so_sanh.png](figures/e4_so_sanh.png) | Biên quyết định của ba mô hình. |
| [e5_hoi_quy.png](figures/e5_hoi_quy.png) | Đường dự đoán giá nhà trong/ngoài miền dữ liệu. |
| [bai6_thoi_gian.png](figures/bai6_thoi_gian.png) | Thời gian fit và predict đo trên máy thực thi. |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Phân loại dùng `test_size=0.25`, `random_state=17`, `stratify=y`; hồi quy giá nhà dùng `test_size=0.2`, `random_state=42`. Chọn k bằng CV 5 phần **chỉ trên tập học**. KNN hai vầng trăng không chuẩn hóa theo mã thầy vì hai đặc trưng có thang đo gần nhau; bài sinh viên dùng `make_pipeline(StandardScaler(), KNeighborsClassifier(...))` để tránh rò rỉ dữ liệu.

Các mốc trong tài liệu để đối chiếu khi chạy:

| Phép thử | Kết quả mẫu |
| --- | --- |
| Khoảng cách A–B / A–C trước chuẩn hóa | 102.2 / 3000.0 |
| Khoảng cách A–B / A–C sau chuẩn hóa | 3.85 / 1.79 |
| Năm láng giềng bạn mới | 4 qua, 1 rớt → qua môn |
| Ba cột chưa chuẩn hóa / có chuẩn hóa | Accuracy 0.5333 / 0.8667 |
| Bỏ chi tiêu và chuẩn hóa | Accuracy 0.9000 |
| KNN hai vầng trăng được chọn bằng CV | k=13, CV 0.8667, kiểm tra 0.9200 |
| Logistic Regression / GaussianNB trên hai vầng trăng | Accuracy cùng bằng 0.8533 |
| Hồi quy giá nhà: KNN k=5 / đường thẳng | MAE 0.4030 / 0.2578 tỷ đồng |

Cell thực hành 1 chuẩn hóa toàn bộ dữ liệu để minh họa khoảng cách, chưa đánh giá khả năng tổng quát hóa. Cell 3 giữ bảng điểm học/kiểm tra theo mã mẫu để minh họa; **không dùng bảng đó để chọn k**. Khi CV có nhiều k bằng điểm, lấy k xuất hiện trước như `max(..., key=...)` trong mã thầy.

Thời gian ở bài tập 6 là số đo thực tế và có thể thay đổi theo máy/lần chạy. Giữ `algorithm="auto"` của scikit-learn; tìm kiếm bằng cây trên dữ liệu 2 chiều có thể làm thời gian không tăng tuyến tính theo số mẫu.

Ảnh đề trong thư mục `Lab04_KNN/` chỉ lưu trên máy, không nằm trong repository và không được push lên GitHub.
