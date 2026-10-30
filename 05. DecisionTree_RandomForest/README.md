![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 5 — Cây quyết định và Rừng ngẫu nhiên

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Thực hành Decision Tree và Random Forest trên dữ liệu khách vay và giá nhà: tính Gini, chọn câu hỏi, kiểm soát độ phức tạp, đọc độ quan trọng của biến và so sánh hồi quy. Phần thực hành giữ cách tính, tham số và cách chia dữ liệu của giảng viên; bổ sung đường dẫn dùng chung và mã lưu hình. Mỗi mục/bài có tiêu đề Markdown và đúng một cell code. Thư mục ảnh đề `Lab5_DT_RF/` (hoặc `Lab/`) chỉ lưu trên máy, không đưa lên GitHub.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab5_NguyenDinhHuy.ipynb](code/Lab5_NguyenDinhHuy.ipynb) | 7 cell code, tương ứng f1–f7 tại mục 2–8 của tài liệu. |
| Bài tập | [BaiTap5.ipynb](code/BaiTap5.ipynb) | 6 cell code, tương ứng 6 bài tập mục 9; có nhận xét bằng tiếng Việt. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [khach_vay.csv](data/khach_vay.csv) | 600 dòng × 5 cột | `thu_nhap`, `ty_le_no`, `co_viec_on_dinh`, `so_nguoi_phu_thuoc`, `tra_dung_han`. |
| [gia_nha.csv](data/gia_nha.csv) | 60 dòng × 4 cột | `dien_tich`, `so_phong`, `tuoi_nha`, `gia`. |

`thu_nhap` tính bằng triệu đồng/tháng; `tra_dung_han = 1` là đúng hạn, `0` là trễ hạn. `dien_tich` tính bằng m², `gia` tính bằng tỷ đồng. Hai CSV không có giá trị thiếu và được giữ nguyên.

Phân loại dùng `test_size=0.25`, `random_state=17`, `stratify=y`: 450 khách học và 150 khách kiểm tra. Hồi quy giá nhà chỉ dùng `dien_tich`, chia `test_size=0.2`, `random_state=42`: 48 căn học và 12 căn kiểm tra. Cây và rừng dùng `random_state=0`. Việc chọn độ sâu hoặc `min_samples_leaf` dùng `cv=5` trên tập học.

## Phần thực hành

Mở [Lab5_NguyenDinhHuy.ipynb](code/Lab5_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| 2 — Gini | Tính Gini trên 10 khách, thử ngưỡng thu nhập và đối chiếu cây một tầng. |
| 3 — Cây năm lá | `max_leaf_nodes=5`, đọc quy tắc, chấm accuracy và dự đoán hai khách mới. |
| 4 — Độ sâu | So cây tự do với độ sâu 1–15; chọn bằng kiểm định chéo 5 phần. |
| 5 — Chuẩn hóa | So dữ liệu gốc, StandardScaler và thu nhập nhân 1.000. |
| 6 — Rừng | Lấy mẫu bootstrap, thử số cây và so với hai cây đơn. |
| 7 — Độ quan trọng | Đọc `feature_importances_` và thử thêm cột ngẫu nhiên. |
| 8 — Hồi quy | Cây sâu 3 so với đường thẳng; MAE và dự đoán ngoài miền dữ liệu. |

## Phần bài tập

Mở [BaiTap5.ipynb](code/BaiTap5.ipynb). Mỗi bài tự đọc dữ liệu và thiết lập phép chia nên không phụ thuộc biến của bài trước. Nhận xét được in trong kết quả.

| Bài | Nội dung |
| --- | --- |
| 1 — Tự vẽ cây | Lưu cây năm lá và cây sâu 2; giải thích vì sao hai lá cùng nhãn vẫn được tách. |
| 2 — Tìm câu hỏi gốc | Viết `tim_cau_hoi(X, y)`, thử mọi cột và ngưỡng trên 450 khách học. |
| 3 — Gini hay entropy | Dò độ sâu 1–15 bằng CV, so accuracy kiểm tra của hai tiêu chí. |
| 4 — Số khách tối thiểu ở lá | Dò `min_samples_leaf` trong `[1, 2, 5, 10, 20, 40]`, so với cây sâu 5. |
| 5 — Xáo trộn | `permutation_importance`, `n_repeats=20`, `random_state=0`; so thứ hạng cột ngẫu nhiên. |
| 6 — Rừng hồi quy | Rừng 200 cây, MAE và giá căn 250 m²; giải thích giới hạn ngoại suy. |

## Cấu trúc thư mục

```text
05. DecisionTree_RandomForest/
├── code/
│   ├── Lab5_NguyenDinhHuy.ipynb
│   └── BaiTap5.ipynb
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

Mở terminal tại thư mục `05. DecisionTree_RandomForest`, chạy:

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

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Mỗi cell tự tìm `data/` ở thư mục hiện tại hoặc thư mục cha; không cần sửa đường dẫn khi mở notebook từ `code/`.

**Trên Colab:** Mở một notebook rồi tải cả `khach_vay.csv` và `gia_nha.csv` lên thư mục làm việc `/content/`, hoặc giữ chúng trong `/content/data/`. Notebook tự nhận cả hai cách đặt CSV. Nếu clone repository, chuyển thư mục bằng `%cd "/content/Machine-Learning/05. DecisionTree_RandomForest"` trước khi chạy. Hình nằm trong `figures/` bên dưới thư mục Lab hoặc `/content/figures/` khi chỉ tải riêng notebook và CSV.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab5_NguyenDinhHuy.txt](outputs/Lab5_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [BaiTap5.txt](outputs/BaiTap5.txt) | Kết quả phần bài tập. |
| [gini.png](figures/gini.png) | Gini theo tỷ lệ lớp 1. |
| [chon_do_sau.png](figures/chon_do_sau.png) | Accuracy học và kiểm định chéo theo độ sâu. |
| [so_cay_trong_rung.png](figures/so_cay_trong_rung.png) | Accuracy kiểm tra khi dùng 1, 10, 50, 200 và 400 cây. |
| [do_quan_trong.png](figures/do_quan_trong.png) | Độ quan trọng của bốn biến thật và khi thêm biến ngẫu nhiên. |
| [cay_hoi_quy.png](figures/cay_hoi_quy.png) | Dự đoán bậc thang của cây và hồi quy tuyến tính. |
| [cay_nam_la.png](figures/cay_nam_la.png) | Bài tập 1: cây năm lá. |
| [cay_sau_2.png](figures/cay_sau_2.png) | Bài tập 1: cây sâu 2, hai lá trái cùng kết luận trễ hạn. |
| [gini_va_entropy.png](figures/gini_va_entropy.png) | Bài tập 3: so sánh kiểm định chéo của Gini và entropy. |
| [chon_so_khach_o_la.png](figures/chon_so_khach_o_la.png) | Bài tập 4: chọn số khách tối thiểu ở lá. |
| [permutation_importance.png](figures/permutation_importance.png) | Bài tập 5: MDI và permutation importance. |
| [rung_hoi_quy.png](figures/rung_hoi_quy.png) | Bài tập 6: cây, rừng và đường thẳng khi dự đoán giá nhà. |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Các kết quả dưới đây lấy từ lần chạy hai notebook; các mốc thực hành khớp tài liệu giảng viên.

| Nội dung thực hành | Kết quả |
| --- | --- |
| Gini gốc, 10 khách | 0.4800; ngưỡng tốt nhất 12.0, Gini giảm 0.1633. |
| Cây năm lá | Accuracy học 0.7978; kiểm tra 0.7467. |
| Cây tự do | Sâu 13, 92 lá; accuracy học 1.0000, kiểm tra 0.7667. |
| Độ sâu được chọn | 5; CV 0.8333; accuracy kiểm tra 0.8533. |
| Chuẩn hóa / đổi đơn vị | Accuracy cùng 0.8533, không đổi nhãn dự đoán; ngưỡng gốc 15.05 → 15050.00 khi nhân thu nhập 1.000. |
| Rừng 200 cây | Accuracy học 1.0000; kiểm tra 0.9000. |
| Độ quan trọng | Thu nhập 0.479; tỷ lệ nợ 0.339; cột ngẫu nhiên khi thêm vào được 0.150. |
| Hồi quy giá nhà | MAE cây sâu 3: 0.5039; đường thẳng: 0.2578 tỷ đồng. |

| Bài tập | Kết quả và nhận xét |
| --- | --- |
| 1 | Hai lá trái cùng lớp 0; phép chia giảm Gini có trọng số của nút từ 0.3933 xuống 0.3394. |
| 2 | Câu hỏi `thu_nhap <= 15.05`; Gini giảm 0.122145, khớp scikit-learn. |
| 3 | Entropy chọn độ sâu 5, CV 0.8222, accuracy 0.8467; Gini đạt 0.8533. Chênh 0.67 điểm phần trăm, tương ứng 1/150 khách. |
| 4 | Chọn `min_samples_leaf=10`, CV 0.8089; accuracy 0.8467, thấp hơn cây sâu 5 (0.8533). |
| 5 | Cột ngẫu nhiên từ hạng 3 theo MDI xuống hạng 5 theo permutation; accuracy giảm trung bình chỉ 0.0017 khi xáo trộn. |
| 6 | MAE rừng 0.4559 tỷ đồng: tốt hơn cây sâu 3, kém đường thẳng. Rừng dự đoán căn 250 m² là 9.1973 tỷ đồng, bằng căn 150 m². |

Khi nhiều cấu hình có cùng điểm CV cao nhất, lấy cấu hình xuất hiện đầu tiên trong danh sách tăng dần, giống cách dùng `max` trong tài liệu. Cột ngẫu nhiên ở bài 5 được sinh bằng `np.random.default_rng(0)` cho tập học trước, sau đó tiếp tục cùng bộ sinh cho tập kiểm tra. Permutation importance dùng accuracy mặc định của mô hình phân loại.

Các phép so sánh chỉ phản ánh bộ dữ liệu và cách chia này. Độ quan trọng không chứng minh quan hệ nhân quả. Cây và rừng hồi quy dự đoán từ trung bình ở lá nên không kéo dài xu hướng giá ra ngoài vùng dữ liệu học.
