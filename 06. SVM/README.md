![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 6 — Máy vectơ hỗ trợ (SVM)

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Thực hành SVM tuyến tính, lề mềm, kernel, dò tham số và nhận dạng chữ số viết tay. Mã thực hành giữ dữ liệu ví dụ, cách tính, tham số và thứ tự xử lý của giảng viên; bổ sung đường dẫn dùng chung và mã lưu hình. Mỗi mục/bài có một tiêu đề Markdown và đúng một cell code. Thư mục đề `Lab6_SVM/` (hoặc `Lab/`) chỉ lưu trên máy, không đưa lên GitHub.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab6_NguyenDinhHuy.ipynb](code/Lab6_NguyenDinhHuy.ipynb) | 5 cell code, tương ứng g1–g5 tại mục 2–6. |
| Bài tập | [BaiTap6.ipynb](code/BaiTap6.ipynb) | 6 cell code, tương ứng 6 bài tập mục 7, có giải thích tiếng Việt. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [sinh_vien.csv](data/sinh_vien.csv) | 120 dòng × 3 cột | `gio_on`, `diem_giua_ky`, `qua_mon`. |
| [sinh_vien_mo_rong.csv](data/sinh_vien_mo_rong.csv) | 120 dòng × 4 cột | `gio_on`, `diem_giua_ky`, `chi_tieu`, `qua_mon`. |
| [hai_vang_trang.csv](data/hai_vang_trang.csv) | 300 dòng × 3 cột | `x1`, `x2`, `nhan`. |
| `load_digits()` | 1.797 ảnh × 64 đặc trưng | Ảnh 8 × 8, độ sáng 0–16; nhãn chữ số 0–9. Có sẵn trong scikit-learn. |

Ba CSV được giữ nguyên nội dung, đặt trực tiếp trong `data/`; không cần thư mục `data/data/`. `qua_mon=1` là qua môn, `0` là rớt; `chi_tieu` tính bằng nghìn đồng. Các CSV không có giá trị thiếu.

Mục 2 tự sinh 24 điểm bằng `make_blobs(n_samples=24, centers=[[2, 2], [6, 6]], cluster_std=0.9, random_state=0)` rồi đảo nhãn `y=1-y`. Bài tập 6 tự sinh 2.000, 5.000, 10.000 và 20.000 mẫu bằng `make_classification(n_features=20, random_state=0)`.

Các phép chia đều dùng `test_size=0.25`, `random_state=17`, `stratify=y`: sinh viên 90 học/30 kiểm tra; hai vầng trăng 225/75; chữ số 1.347/450. Dò tham số dùng `cv=5` trên tập học. Khi cần chuẩn hóa, `StandardScaler` nằm trong pipeline để tránh rò rỉ dữ liệu giữa các phần CV.

## Phần thực hành

Mở [Lab6_NguyenDinhHuy.ipynb](code/Lab6_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| 2 — Lề rộng nhất | SVM tuyến tính C=1000, đọc w và b, tính lề, kiểm tra vectơ hỗ trợ và dự đoán hai điểm mới. |
| 3 — Lề mềm và C | Thử C từ 0.01 đến 100; so dữ liệu ba cột có/không chuẩn hóa. |
| 4 — Kernel | Nâng chiều bằng x²; so tuyến tính, đa thức, RBF, Logistic Regression và KNN. |
| 5 — C và gamma | Thử gamma; dò lưới 16 cặp bằng GridSearchCV và vẽ bảng điểm CV. |
| 6 — Chữ số | SVM RBF trên digits; tìm ảnh sai; so SVM chuẩn hóa, KNN và Logistic Regression. |

## Phần bài tập

Mở [BaiTap6.ipynb](code/BaiTap6.ipynb). Mỗi bài tự thiết lập dữ liệu và mô hình, có thể chạy riêng sau khi cài thư viện. Các nhận xét được in vào nhật ký.

| Bài | Nội dung |
| --- | --- |
| 1 — Khoảng cách | Tự tính f(x) bằng nhân/cộng và khoảng cách đến ranh giới; giải thích nửa độ rộng lề. |
| 2 — Thêm điểm | Thêm riêng điểm lớp 1 tại (-1, -1) và (4.5, 4); so hệ số và vectơ hỗ trợ. |
| 3 — Đa thức | Chuẩn hóa, thử bậc 2/3/4; dò `svc__C` và so với RBF của mục 5. |
| 4 — Lưới mịn | Dò C=[3, 10, 30], gamma=[0.3, 1, 3]; so CV và tập kiểm tra. |
| 5 — Lỗi chữ số | In confusion matrix 10 × 10, liệt kê cặp nhầm và lưu riêng từng ảnh sai. |
| 6 — Dữ liệu lớn | Đo riêng thời gian fit SVC() và LinearSVC() trên 4 cỡ dữ liệu, in tỷ lệ tăng thời gian. |

## Cấu trúc thư mục

```text
06. SVM/
├── code/
│   ├── Lab6_NguyenDinhHuy.ipynb
│   └── BaiTap6.ipynb
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

Mở terminal tại thư mục `06. SVM`, chạy:

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

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Mỗi cell tìm `data/` ở thư mục hiện tại hoặc thư mục cha; không gắn đường dẫn ổ đĩa hay tên người dùng.

**Trên Colab:** Tải cả ba CSV lên `/content/` hoặc đặt trong `/content/data/`, rồi mở notebook và Run All. Nếu clone repository, chuyển thư mục bằng `%cd "/content/Machine-Learning/06. SVM"` trước khi chạy. Dữ liệu chữ số có sẵn trong scikit-learn. Hình lưu dưới `figures/` của thư mục Lab hoặc `/content/figures/` khi chỉ tải riêng notebook và CSV.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab6_NguyenDinhHuy.txt](outputs/Lab6_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [BaiTap6.txt](outputs/BaiTap6.txt) | Kết quả phần bài tập. |
| [le_rong_nhat.png](figures/le_rong_nhat.png) | Ranh giới, hai mép lề và ba vectơ hỗ trợ. |
| [tham_so_c.png](figures/tham_so_c.png) | Số vectơ hỗ trợ và độ rộng lề khi C thay đổi. |
| [nang_chieu.png](figures/nang_chieu.png) | Thêm cột x² để tách dữ liệu bằng đường thẳng. |
| [so_sanh_kernel.png](figures/so_sanh_kernel.png) | Biên tuyến tính và RBF trên hai vầng trăng. |
| [anh_huong_gamma.png](figures/anh_huong_gamma.png) | Biên quyết định với gamma 0.1, 1 và 100. |
| [luoi_tham_so.png](figures/luoi_tham_so.png) | Điểm CV của 16 cặp C và gamma. |
| [chu_so_tap_hoc.png](figures/chu_so_tap_hoc.png) | Tám ảnh đầu tiên của tập học chữ số. |
| [them_mot_diem.png](figures/them_mot_diem.png) | Bài tập 2: ranh giới khi thêm điểm xa hoặc gần lề. |
| [kernel_da_thuc.png](figures/kernel_da_thuc.png) | Bài tập 3: so sánh ba bậc đa thức sau khi dò C. |
| [luoi_min.png](figures/luoi_min.png) | Bài tập 4: điểm CV của lưới mịn. |
| [ma_tran_nham_lan.png](figures/ma_tran_nham_lan.png) | Bài tập 5: ma trận nhầm lẫn 10 × 10. |
| [chu_so_sai_006_that_9_doan_3.png](figures/chu_so_sai_006_that_9_doan_3.png) | Ảnh kiểm tra 6: thật 9, đoán 3. |
| [chu_so_sai_018_that_8_doan_1.png](figures/chu_so_sai_018_that_8_doan_1.png) | Ảnh kiểm tra 18: thật 8, đoán 1. |
| [chu_so_sai_161_that_4_doan_8.png](figures/chu_so_sai_161_that_4_doan_8.png) | Ảnh kiểm tra 161: thật 4, đoán 8. |
| [chu_so_sai_428_that_7_doan_9.png](figures/chu_so_sai_428_that_7_doan_9.png) | Ảnh kiểm tra 428: thật 7, đoán 9. |
| [thoi_gian_svm.png](figures/thoi_gian_svm.png) | Bài tập 6: thời gian fit của SVC và LinearSVC. |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Các mốc thực hành dưới đây lấy từ lần chạy đã lưu và khớp tài liệu giảng viên.

| Nội dung | Kết quả |
| --- | --- |
| 24 điểm | w1=-0.831, w2=-0.355, b=4.820; lề 2.2126; 3 vectơ hỗ trợ. |
| Sinh viên, C=0.01 → 100 | Số vectơ hỗ trợ 74 → 27; lề 3.84 → 1.05 trên dữ liệu chuẩn hóa. |
| Sinh viên ba cột | Không chuẩn hóa 0.6000; chuẩn hóa 0.9000 accuracy. |
| Nâng chiều x² | Một ngưỡng trên x đạt 0.7143; SVM trên (x, x²) đạt 1.0000. |
| Hai vầng trăng | Tuyến tính 0.8667; RBF 0.9200; RBF mặc định có 89 vectơ hỗ trợ/225 mẫu học. |
| Gamma=100 | Accuracy học 0.9422; kiểm tra 0.8133; 217 vectơ hỗ trợ. |
| Lưới thưa | C=10, gamma=1; CV 0.8711; kiểm tra 0.9200. |
| Chữ số | RBF 0.9911, sai 4/450; 626 vectơ hỗ trợ/1.347 ảnh học. |
| So sánh chữ số | SVM chuẩn hóa 0.9778; KNN 0.9867; logistic chuẩn hóa 0.9711. |

| Bài tập | Kết quả và nhận xét |
| --- | --- |
| 1 | Khoảng cách của (3, 3) là 1.395779, của (5, 4.5) là 1.032530. Ba vectơ hỗ trợ cách ranh giới xấp xỉ 1.106282, tức nửa lề. Dùng hệ số chưa làm tròn; chênh nhỏ do dung sai bộ giải. |
| 2 | Điểm (-1, -1) không là vectơ hỗ trợ, không đổi hệ số; điểm (4.5, 4) là vectơ hỗ trợ, đổi w thành (-2.603014, -0.806843), b thành 15.940939. |
| 3 | Bậc 3, C=1 tốt nhất theo CV (0.8178); kiểm tra 0.8267, chưa vượt RBF 0.9200. |
| 4 | C=30, gamma=1; CV tăng lên 0.8756, kiểm tra vẫn 0.9200. Lưới mịn có lợi nhỏ ở CV nhưng không tăng accuracy kiểm tra trong lần chia này. |
| 5 | Có 4 nhầm lẫn: 9→3, 8→1, 4→8, 7→9; mỗi cặp một ảnh. Đã lưu từng ảnh riêng. |
| 6 | Khi tăng 5.000→10.000 mẫu, thời gian SVC tăng 11.58 lần, LinearSVC 2.41 lần; từ 10.000→20.000 tương ứng 3.07 và 2.14 lần trong lần đo đã lưu. |

Thời gian fit đo bằng `time.perf_counter()`, không tính thời gian sinh dữ liệu hoặc vẽ. Lần chạy đã lưu đo SVC/LinearSVC trên 20.000 mẫu lần lượt khoảng 10.606/0.039 giây. Mỗi cỡ chỉ đo một lần theo yêu cầu bài; các số đo phụ thuộc phần cứng, tải máy, bộ giải và dữ liệu sinh ra. Lần chạy sau có thể khác; nhật ký mới trong `outputs/BaiTap6.txt` là kết quả của lần chạy đó. SVC dùng RBF còn LinearSVC dùng ranh giới tuyến tính, nên so tốc độ không có nghĩa hai mô hình có cùng khả năng biểu diễn.

Điểm CV dùng để chọn tham số, tập kiểm tra dùng để báo cáo. Khi đồng điểm, GridSearchCV chọn cấu hình xuất hiện trước trong lưới. `decision_function` là điểm quyết định, không phải xác suất. Với SVM tuyến tính có lề mềm, không phải mọi vectơ hỗ trợ đều cách ranh giới đúng nửa lề; kết luận ở bài 1 áp dụng cho bộ 24 điểm tách được đã dùng.
