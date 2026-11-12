![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 7 — Đánh giá mô hình (Accuracy & Metrics)

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Đánh giá mô hình trên dữ liệu lệch lớp: mô hình cơ sở, ma trận nhầm lẫn, precision/recall/F1, ngưỡng quyết định, ROC/AUC và cân bằng lớp. Phần bài tập mở rộng sang chữ số viết tay và các sai số hồi quy. Mã thực hành giữ cách tính, mô hình, tham số và cách chia dữ liệu của thầy; bổ sung đường dẫn dùng chung và phần lưu hình. Mỗi mục/bài có tiêu đề Markdown và đúng một cell code. Thư mục đề `Lab7_Accuracy/` (hoặc `Lab/`) chỉ lưu trên máy, không đưa lên GitHub.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab7_NguyenDinhHuy.ipynb](code/Lab7_NguyenDinhHuy.ipynb) | 6 cell code, tương ứng h1–h6 tại mục 2–7. |
| Bài tập | [BaiTap7.ipynb](code/BaiTap7.ipynb) | 6 cell code, tương ứng 6 bài tập mục 8; có nhận xét tiếng Việt. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [sinh_vien_bo_hoc.csv](data/sinh_vien_bo_hoc.csv) | 1.200 dòng × 5 cột | `diem_tb`, `so_buoi_vang`, `tin_chi_no`, `gio_lam_them`, `bo_hoc`. |
| [gia_nha.csv](data/gia_nha.csv) | 60 dòng × 4 cột | `dien_tich`, `so_phong`, `tuoi_nha`, `gia`. |
| `load_digits()` | 1.797 ảnh × 64 đặc trưng | Ảnh 8 × 8, nhãn chữ số 0–9; có sẵn trong scikit-learn. |

Dữ liệu sinh viên là dữ liệu mô phỏng phục vụ giảng dạy. `bo_hoc=1` là lớp dương: 119 sinh viên bỏ học; lớp 0 có 1.081 sinh viên. Các CSV giữ nguyên nội dung và không có giá trị thiếu. `gia` tính bằng tỷ đồng, `dien_tich` tính bằng m².

Phân loại dùng `test_size=0.25`, `random_state=17`, `stratify=y`: sinh viên 900 học/300 kiểm tra (30 ca bỏ học trong tập kiểm tra); chữ số 1.347/450. CV dùng 5 phần trên tập học. Bài giá nhà giữ mô hình một biến `dien_tich`, chia `test_size=0.2`, `random_state=42` như Lab 1. Chuẩn hóa nằm trong pipeline.

## Phần thực hành

Mở [Lab7_NguyenDinhHuy.ipynb](code/Lab7_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| 2 — Accuracy | So DummyClassifier luôn đoán lớp đông với hồi quy logistic. |
| 3 — Ma trận | Tự đếm TP/FP/FN/TN bằng NumPy, đối chiếu confusion_matrix. |
| 4 — Các thước đo | Tính precision, recall, F1 bằng tay và thư viện; classification_report. |
| 5 — Ngưỡng | Minh họa đổi ngưỡng; chọn ngưỡng F1 bằng cross_val_predict trên tập học. |
| 6 — ROC/AUC | ROC logistic và so 6 mô hình ở cùng ngưỡng xác suất 0.5. |
| 7 — Cân bằng lớp | Ảnh hưởng của stratify; CV nhiều thước đo; logistic class_weight="balanced". |

## Phần bài tập

Mở [BaiTap7.ipynb](code/BaiTap7.ipynb). Mỗi bài tự đọc dữ liệu và học mô hình, không phụ thuộc biến của bài trước. Nhận xét được in để xuất hiện trong nhật ký.

| Bài | Nội dung |
| --- | --- |
| 1 — Hàm đánh giá | Viết `danh_gia(y_that, y_doan)` chỉ dùng NumPy; xử lý mẫu số 0 và đối chiếu thư viện. |
| 2 — Chữ số | Báo cáo 10 lớp, tìm lớp có recall/precision thấp nhất, giải thích macro/weighted avg. |
| 3 — Recall 80% | Chọn ngưỡng lớn nhất bằng xác suất ngoài fold; chốt rồi đánh giá kiểm tra một lần. |
| 4 — Vẽ ROC | Logistic và rừng 200 cây trên cùng hình `roc.png`; nhận xét AUC và giao nhau. |
| 5 — Cân bằng | Rừng và SVM trước/sau balanced, phân biệt predict với ngưỡng xác suất 0.5. |
| 6 — Một dự đoán hỏng | MAE, RMSE, R² trước/sau cộng 5 tỷ vào đúng một dự đoán giá nhà. |

## Cấu trúc thư mục

```text
07. Accuracy_Metrics/
├── code/
│   ├── Lab7_NguyenDinhHuy.ipynb
│   └── BaiTap7.ipynb
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

Mở terminal tại thư mục `07. Accuracy_Metrics`, chạy:

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

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Mỗi cell tự tìm `data/` từ thư mục hiện tại hoặc thư mục cha; không chứa đường dẫn ổ D hay tên tài khoản.

**Trên Colab:** Tải `sinh_vien_bo_hoc.csv` và `gia_nha.csv` vào `/content/` hoặc `/content/data/`, rồi Run All. Nếu clone repository, dùng `%cd "/content/Machine-Learning/07. Accuracy_Metrics"` trước khi chạy. Dữ liệu chữ số có sẵn trong scikit-learn. Hình lưu vào `figures/` dưới thư mục Lab hoặc `/content/figures/` khi chỉ tải riêng notebook và CSV.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab7_NguyenDinhHuy.txt](outputs/Lab7_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [BaiTap7.txt](outputs/BaiTap7.txt) | Kết quả phần bài tập. |
| [accuracy_va_recall.png](figures/accuracy_va_recall.png) | Accuracy và recall của mô hình lười và logistic. |
| [ma_tran_nham_lan.png](figures/ma_tran_nham_lan.png) | Ma trận nhầm lẫn của hai mô hình. |
| [chon_nguong.png](figures/chon_nguong.png) | Đánh đổi precision/recall và chọn ngưỡng F1 bằng dự đoán ngoài fold. |
| [roc_logistic.png](figures/roc_logistic.png) | ROC logistic, đánh dấu ngưỡng 0.5 và 0.2. |
| [can_bang_logistic.png](figures/can_bang_logistic.png) | Precision, recall, F1 trước và sau cân bằng lớp. |
| [bao_cao_chu_so.png](figures/bao_cao_chu_so.png) | Bài 2: đánh giá riêng từng chữ số. |
| [nguong_recall_80.png](figures/nguong_recall_80.png) | Bài 3: tìm ngưỡng lớn nhất thỏa recall OOF ít nhất 0.8. |
| [roc.png](figures/roc.png) | Bài 4: ROC logistic và rừng ngẫu nhiên, có AUC trong chú thích. |
| [can_bang_rung_svm.png](figures/can_bang_rung_svm.png) | Bài 5: so nhãn predict trước/sau cân bằng của rừng và SVM. |
| [mae_rmse_du_doan_hong.png](figures/mae_rmse_du_doan_hong.png) | Bài 6: MAE, RMSE và sai số khi một dự đoán bị cộng 5 tỷ. |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Các kết quả dưới đây lấy từ lần chạy hai notebook. Các mốc thực hành khớp tài liệu giảng viên.

| Nội dung thực hành | Kết quả |
| --- | --- |
| Accuracy | Mô hình lười 0.9000, tìm 0/30 ca bỏ học; logistic 0.9467, tìm 17/30. |
| Ma trận logistic | TN=267, FP=3, FN=13, TP=17. |
| Ngưỡng 0.5 | Precision 0.8500; recall 0.5667; F1 0.6800. |
| Ngưỡng chọn bằng OOF | 0.25; F1 ngoài fold 0.6473. Kiểm tra: precision 0.6571, recall 0.7667, F1 0.7077. |
| ROC/AUC | Logistic có 28 điểm ROC, AUC 0.9449; rừng 200 cây AUC 0.9249. |
| CV trên tập học | Accuracy 0.9289; precision 0.7044; recall 0.4810; F1 0.5652. |
| Logistic cân bằng | Precision 0.4483; recall 0.8667; F1 0.5909. |

| Bài tập | Kết quả và nhận xét |
| --- | --- |
| 1 | Hàm NumPy khớp scikit-learn. Precision của mô hình lười là 0/0, được quy ước trả 0 giống `zero_division=0`. |
| 2 | Chữ số 8 có cả recall và precision thấp nhất, 0.9767. Mỗi lớp có 43–46 ảnh kiểm tra nên macro/weighted avg gần nhau. |
| 3 | Ngưỡng lớn nhất khoảng 0.171773644908; recall OOF 72/89=0.8090. Kiểm tra: recall 0.8000, precision 0.5106, báo 47 sinh viên. |
| 4 | Logistic có AUC cao hơn nhưng hai đường có cắt nhau. Ví dụ logistic cao hơn trong FPR (0, 0.0037), rừng cao hơn trong (0.0037, 0.0074). |
| 5 | Với `predict`, recall SVM tăng 0.5000→0.8333, rừng giảm 0.5667→0.4000. SVM thay đổi nhiều nhất theo độ đổi tuyệt đối của recall. |
| 6 | MAE 0.257784→0.674451; RMSE 0.373041→1.550516 tỷ đồng; R² 0.962229→0.347467. RMSE chịu ảnh hưởng mạnh hơn từ một sai số lớn. |

**Cách chọn ngưỡng ở bài 3:** dùng các giá trị xác suất OOF khác nhau làm ngưỡng ứng viên, vì recall chỉ đổi khi vượt một giá trị này. Nhờ vậy tìm được ngưỡng lớn nhất thực sự trên dự đoán OOF. Nếu chỉ dùng lưới bước 0.05 của mục 5, ngưỡng lớn nhất trong lưới là 0.15; notebook in mốc này để đối chiếu nhưng chỉ đánh giá tập kiểm tra bằng ngưỡng đã chốt 0.171773644908. Ngưỡng được giữ ở độ chính xác đầy đủ khi áp dụng. Đạt 80% trên OOF không bảo đảm đạt 80% trên mọi dữ liệu mới.

**Quy tắc dự đoán ở bài 5:** bảng chính dùng `predict` như mục 7. Bảng bổ sung dùng `predict_proba >= 0.5` như mục 6, cho SVM thường/balanced có recall 0.5000/0.4333 và rừng thường/balanced có recall 0.5667/0.4333. Xác suất SVM được hiệu chỉnh riêng nên nhãn ở ngưỡng 0.5 có thể khác `predict`; rừng có thể khác ở xác suất đúng 0.5 vì xử lý hòa. Cần so cùng quy tắc trước/sau, không trộn hai bảng.

Bài 6 sửa dự đoán căn đầu tiên của tập kiểm tra (chỉ số dữ liệu 0, diện tích 35.5 m²), từ 3.2179 thành 8.2179 tỷ đồng; các dự đoán còn lại giữ nguyên. RMSE tăng 4.16 lần, MAE tăng 2.62 lần. R² không có cùng đơn vị với hai sai số nên cần đọc theo ý nghĩa riêng.

Các so sánh này áp dụng cho bộ dữ liệu và lần chia đã nêu. Bảng đổi ngưỡng trên tập kiểm tra ở phần thực hành chỉ minh họa đánh đổi theo mã thầy; việc chọn ngưỡng sử dụng dự đoán ngoài fold trên tập học.
