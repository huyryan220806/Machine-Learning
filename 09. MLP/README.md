![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 09 — Mạng nơ-ron nhiều lớp (MLP)

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Tự tính lan truyền tiến, giải XOR, kiểm tra độ lớn mạng và điều chuẩn, chuẩn hóa và nhận dạng chữ số. Phần bài tập có tự dự đoán từ trọng số, so kích hoạt/tốc độ học, dò lưới và hồi quy giá nhà.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab9_NguyenDinhHuy.ipynb](code/Lab9_NguyenDinhHuy.ipynb) | 5 mục thực hành, mỗi mục một cell code theo mã thầy. |
| Bài tập | [BaiTap9.ipynb](code/BaiTap9.ipynb) | 6 bài tập mục 7, mỗi bài một cell code, có nhận xét tiếng Việt. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [gia_nha.csv](data/gia_nha.csv) | 60 dòng, 4 cột | `dien_tich`, `so_phong`, `tuoi_nha`, `gia` |
| [hai_vang_trang.csv](data/hai_vang_trang.csv) | 300 dòng, 3 cột | `x1`, `x2`, `nhan` |
| [sinh_vien_mo_rong.csv](data/sinh_vien_mo_rong.csv) | 120 dòng, 4 cột | `gio_on`, `diem_giua_ky`, `chi_tieu`, `qua_mon` |
| [xor.csv](data/xor.csv) | 400 dòng, 3 cột | `x1`, `x2`, `nhan` |
| `load_digits()` | 1797 ảnh 8 × 8 | 64 độ sáng và nhãn 0–9; có sẵn trong scikit-learn. |

Giữ nguyên CSV được cung cấp; không có giá trị thiếu. XOR là dữ liệu mô phỏng; dữ liệu giá nhà dùng cho bài tập hồi quy một biến. Mọi phép chọn siêu tham số bằng CV chỉ dùng tập học. Đề gốc nằm trong `Lab9_MLP/`, chỉ lưu trên máy và không đưa lên GitHub.

## Phần thực hành

Mở [Lab9_NguyenDinhHuy.ipynb](code/Lab9_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| 2 | Tự tính lan truyền tiến |
| 3 | Một nơ-ron và một lớp ẩn trên XOR |
| 4 | Độ lớn mạng và điều chuẩn |
| 5 | Mạng nơ-ron khi quên chuẩn hóa |
| 6 | Nhận dạng chữ số viết tay |

## Phần bài tập

Mở [BaiTap9.ipynb](code/BaiTap9.ipynb). Mỗi bài có tiêu đề Markdown riêng; phần giải thích được in cùng kết quả.

| Bài | Nội dung |
| --- | --- |
| 1 | Tự dự đoán bằng trọng số đã học |
| 2 | Một mạng XOR khác |
| 3 | So sánh các hàm kích hoạt |
| 4 | Tốc độ học |
| 5 | Dò lưới cho mạng nơ-ron |
| 6 | Mạng nơ-ron cho hồi quy |

## Cấu trúc thư mục

```text
09. MLP/
├── code/
│   ├── Lab9_NguyenDinhHuy.ipynb
│   └── BaiTap9.ipynb
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

Mở terminal tại thư mục `09. MLP`, chạy:

```sh
python -m pip install -r requirements.txt
python scripts/run_all.py
```

Script chạy notebook thực hành trước, sau đó notebook bài tập. Mỗi notebook dùng kernel riêng với đúng Python đang chạy script. Có thể gọi script bằng đường dẫn đầy đủ từ thư mục khác; script tự tìm thư mục bài từ vị trí của chính nó.

Kết quả được cập nhật trong notebook và xuất thành các tệp `.txt` ở `outputs/`; hình được lưu vào `figures/`. Mỗi lần chạy thay thế nhật ký cũ. Mỗi cell có tối đa 1200 giây; nếu gặp lỗi, script dừng và không ghi đè notebook đang lỗi. Xem thông báo terminal và nhật ký trong `outputs/` để kiểm tra. Script giới hạn BLAS/OpenMP ở một luồng để giảm chi phí điều phối với ma trận nhỏ; không đổi thuật toán hay tham số. Phần dò lưới gồm 60 lượt huấn luyện CV nên có thể mất vài phút.

## Chạy từng notebook và Google Colab

Mở notebook bằng VS Code hoặc khởi động Jupyter từ thư mục bài:

```sh
python -m notebook
```

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Các cell tự tìm `data/` khi chạy từ thư mục bài hoặc `code/`, không dùng đường dẫn riêng của máy.

**Trên Colab:** Tải các tệp trong `data/` vào `/content/data/` hoặc trực tiếp `/content/`, rồi Run All. Nếu clone repository, dùng `%cd "/content/Machine-Learning/09. MLP"` trước khi chạy. Dữ liệu chữ số được nạp sẵn từ scikit-learn; không cần tải thêm. Hình lưu trong `figures/` dưới thư mục Lab hoặc `/content/figures/` khi tải riêng notebook.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab9_NguyenDinhHuy.txt](outputs/Lab9_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [BaiTap9.txt](outputs/BaiTap9.txt) | Kết quả phần bài tập. |
| [ham_kich_hoat.png](figures/ham_kich_hoat.png) | Sigmoid, tanh và ReLU. |
| [ranh_gioi_xor.png](figures/ranh_gioi_xor.png) | Logistic và MLP 8 nơ-ron trên XOR. |
| [do_lon_va_dieu_chuan.png](figures/do_lon_va_dieu_chuan.png) | Ba ranh giới trên hai vành trăng. |
| [chon_alpha.png](figures/chon_alpha.png) | Accuracy CV khi dò alpha trên tập học. |
| [chuan_hoa_mlp.png](figures/chuan_hoa_mlp.png) | So sánh trước và sau chuẩn hóa. |
| [mat_mat_va_dung_som.png](figures/mat_mat_va_dung_som.png) | Loss và accuracy kiểm định nội bộ khi dừng sớm. |
| [chu_so_doan_sai.png](figures/chu_so_doan_sai.png) | Bảy ảnh chữ số MLP dự đoán sai. |
| [so_sanh_kich_hoat.png](figures/so_sanh_kich_hoat.png) | Accuracy học/kiểm tra theo hàm kích hoạt. |
| [toc_do_hoc.png](figures/toc_do_hoc.png) | Bốn đường loss với bốn tốc độ học. |
| [hoi_quy_ngoai_suy.png](figures/hoi_quy_ngoai_suy.png) | So sánh hồi quy và dự đoán ngoài miền tại 250 m². |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Kết quả dưới đây lấy từ lần chạy đã lưu, dùng scikit-learn 1.8.0, NumPy 2.3.4 và SciPy 1.17.0. Giữ dữ liệu, tham số và cách chia của thầy; không sửa kết quả để khớp tài liệu.

| Thực hành | Kết quả chạy |
| --- | --- |
| Một nơ-ron | z = 1.80; sigmoid = 0.8581. |
| XOR tự đặt trọng số | [0, 1, 1, 0]. |
| XOR, logistic / MLP 4 / MLP 8 | Accuracy kiểm tra 0.4500 / 0.9300 / 0.9100. |
| Hai vành trăng, mạng nhỏ | Học 0.8444; kiểm tra 0.8533. |
| Hai lớp 100, alpha = 1e-5 | Học 1.0000; kiểm tra 0.7467. |
| Hai lớp 100, alpha = 1 | Học 0.8844; kiểm tra 0.9067. |
| Chọn alpha bằng CV | alpha = 1; accuracy CV 0.8578, kiểm tra 0.9067. |
| Sinh viên, không/có chuẩn hóa | Accuracy 0.4000 / 0.9000. Mạng chưa chuẩn hóa đoán cả 30 bạn đều rớt. |
| Chữ số | 7510 tham số; 144 vòng; loss 2.5206 → 0.0052; accuracy 0.9844, sai 7/450. |
| Dừng sớm | 44 vòng; accuracy 0.9578. |
| Đối chiếu chữ số | Logistic 0.9711; KNN 0.9867; SVM 0.9911. |

**Chênh lệch với tài liệu ở mục 4:** mạng lớn alpha = 1e-5 đạt kiểm tra 0.7467 thay vì 0.7333; alpha = 1 đạt học 0.8844 thay vì 0.8800. Accuracy CV tại alpha 0.001/0.1 là 0.7689/0.7689 thay vì 0.7733/0.7644. Mã và tham số được giữ nguyên; tối ưu L-BFGS trên mạng phi tuyến có thể nhạy với phiên bản thư viện, phép tính dấu phẩy động và môi trường số học. Đây là khả năng giải thích, chưa có môi trường gốc của thầy để xác định nguyên nhân duy nhất. Kết luận học vẹt khi điều chuẩn quá nhỏ và alpha được CV chọn vẫn giữ nguyên.

| Bài tập | Kết quả và nhận xét |
| --- | --- |
| 1 — Lan truyền tiến | Năm xác suất tự tính khớp `predict_proba`, sai lệch lớn nhất 1.110 × 10⁻¹⁶. |
| 2 — XOR khác | h1 + h2 = \|x1 − x2\|, bằng XOR khi x1, x2 chỉ nhận 0 hoặc 1. |
| 3 — Kích hoạt | Logistic: 0.8533; tanh và ReLU cùng cao nhất 0.9067 trên tập kiểm tra. |
| 4 — Tốc độ học | Bảng chi tiết bên dưới; tốc độ 0.1 dừng nhanh nhưng accuracy thấp nhất trong bốn lần chạy. |
| 5 — Dò lưới | Lớp ẩn (50,), alpha = 1; CV 0.9785, kiểm tra 0.9822, chưa vượt SVM 0.9911. |
| 6 — Hồi quy | MAE MLP 0.500795 tỷ, tuyến tính 0.257784 tỷ. Dự đoán 250 m²: MLP 28.175828 tỷ, tuyến tính 19.913943 tỷ. |

| learning_rate_init | Số vòng | Loss cuối | Accuracy kiểm tra |
| --- | ---: | ---: | ---: |
| 0.0001 | 582 | 0.018928 | 0.988889 |
| 0.001 | 144 | 0.005210 | 0.984444 |
| 0.01 | 38 | 0.001077 | 0.977778 |
| 0.1 | 30 | 0.099601 | 0.948889 |

**Cách chia và chọn mô hình:** các bài phân loại dùng `test_size=0.25`, `random_state=17`, `stratify=y`: XOR 300/100, hai vành trăng 225/75, sinh viên 90/30, chữ số 1347/450 mẫu học/kiểm tra. Dò alpha và GridSearchCV đều dùng 5 fold trên tập học. Scaler nằm trong pipeline, được fit riêng trong từng fold. Grid gồm 12 cặp tham số, 60 lượt CV rồi refit cặp tốt nhất trên toàn bộ tập học. SVM đối chiếu giữ mặc định như mục 6, trên cùng lần chia.

**Tốc độ học:** bước nhỏ cần nhiều vòng; bước lớn có thể làm loss dao động hoặc dừng ở nghiệm kém. Adam tự điều chỉnh bước theo tham số nên không áp một ranh giới phân kỳ cố định. Loss nhỏ hơn trên tập học cũng không bảo đảm accuracy kiểm tra cao hơn.

**Hồi quy:** dùng duy nhất `dien_tich`, chia 48/12 với `test_size=0.2`, `random_state=42` như bài 1. Chỉ chuẩn hóa X trên tập học, không tự thêm biến khác. MLP có MAE kiểm tra cao hơn hồi quy tuyến tính ở dữ liệu này. Diện tích quan sát 35.5–117.5 m²; không có giá thật của căn 250 m² để xác nhận độ chính xác ngoại suy. ReLU tạo hàm tuyến tính từng đoạn, nên ngoài miền học mạng có thể kéo dài với độ dốc khác đường hồi quy. Cả hai con số 250 m² đều là ngoại suy, không phải giá đã được kiểm chứng.

Phần thực hành thêm lưu hình và đường dẫn tương đối; các phép tính, thuật toán, seed và siêu tham số giữ theo mã giảng viên. Các bảng trên tập kiểm tra là minh họa theo đề, không dùng chúng để tiếp tục điều chỉnh mô hình sau khi đánh giá.
