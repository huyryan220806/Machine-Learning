![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 08 — Phân cụm K-Means

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Tự viết K-Means, phân khúc khách hàng, chọn K, nhận diện các bẫy và nén màu ảnh. Phần bài tập bổ sung silhouette NumPy, tuổi, khởi tạo, ảnh cá nhân, DBSCAN và phân cụm chữ số.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab8_NguyenDinhHuy.ipynb](code/Lab8_NguyenDinhHuy.ipynb) | 5 mục thực hành, mỗi mục một cell code theo mã thầy. |
| Bài tập | [BaiTap8.ipynb](code/BaiTap8.ipynb) | 6 bài tập mục 7, mỗi bài một cell code, có nhận xét tiếng Việt. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [hai_vang_trang.csv](data/hai_vang_trang.csv) | 300 dòng, 3 cột | `x1`, `x2`, `nhan` |
| [khach_hang.csv](data/khach_hang.csv) | 210 dòng, 3 cột | `tuoi`, `thu_nhap`, `diem_chi_tieu` |
| [2474802010140.jpg](data/2474802010140.jpg) | 974 × 732 pixel | Ảnh cá nhân do sinh viên cung cấp cho bài 4. |
| `load_digits()` | 1797 ảnh 8 × 8 | 64 độ sáng và nhãn 0–9; có sẵn trong scikit-learn. |
| `load_sample_image("china.jpg")` | 427 × 640 pixel | Ảnh RGB mẫu có sẵn trong scikit-learn. |

Giữ nguyên CSV được cung cấp; không có giá trị thiếu. Khách hàng là dữ liệu mô phỏng không có nhãn. Nhãn hai vành trăng và chữ số chỉ dùng để đánh giá sau phân cụm. Đề gốc nằm trong `Lab8_K-Means/`, chỉ lưu trên máy và không đưa lên GitHub.

## Phần thực hành

Mở [Lab8_NguyenDinhHuy.ipynb](code/Lab8_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| 2 | Tự viết K-Means |
| 3 | Phân khúc khách hàng |
| 4 | Chọn số cụm K |
| 5 | Ba cái bẫy của K-Means |
| 6 | Nén màu ảnh |

## Phần bài tập

Mở [BaiTap8.ipynb](code/BaiTap8.ipynb). Mỗi bài có tiêu đề Markdown riêng; phần giải thích được in cùng kết quả.

| Bài | Nội dung |
| --- | --- |
| 1 | Tự tính silhouette bằng NumPy |
| 2 | Thêm cột tuổi |
| 3 | K-Means++ và khởi tạo ngẫu nhiên |
| 4 | Lưu ảnh nén và dùng ảnh cá nhân |
| 5 | DBSCAN trên hai vầng trăng |
| 6 | Phân cụm chữ số viết tay |

## Cấu trúc thư mục

```text
08. K-Means/
├── code/
│   ├── Lab8_NguyenDinhHuy.ipynb
│   └── BaiTap8.ipynb
├── data/                # CSV và ảnh cá nhân
├── figures/             # Biểu đồ PNG
├── outputs/             # Kết quả dạng chữ của từng notebook
├── scripts/
│   └── run_all.py        # Chạy toàn bộ notebook
├── requirements.txt
└── README.md
```

Giữ nguyên `code/`, `data/`, `scripts/` và `requirements.txt` trong cùng thư mục bài khi tải ZIP, clone hoặc di chuyển dự án. `figures/` và `outputs/` được tạo hoặc cập nhật khi chạy.

## Cài đặt và chạy toàn bộ

Mở terminal tại thư mục `08. K-Means`, chạy:

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

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Các cell tự tìm `data/` khi chạy từ thư mục bài hoặc `code/`, không dùng đường dẫn riêng của máy.

**Trên Colab:** Tải các tệp trong `data/` vào `/content/data/` hoặc trực tiếp `/content/`, rồi Run All. Nếu clone repository, dùng `%cd "/content/Machine-Learning/08. K-Means"` trước khi chạy. Bài 4 cần cả ảnh `2474802010140.jpg`; nếu dùng ảnh khác, sửa tên ảnh trong cell bài 4. Hình lưu trong `figures/` dưới thư mục Lab hoặc `/content/figures/` khi tải riêng notebook.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab8_NguyenDinhHuy.txt](outputs/Lab8_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [BaiTap8.txt](outputs/BaiTap8.txt) | Kết quả phần bài tập. |
| [kmeans_tung_vong.png](figures/kmeans_tung_vong.png) | Ba vòng K-Means trên bảy điểm. |
| [phan_khuc_khach_hang.png](figures/phan_khuc_khach_hang.png) | Năm nhóm khách hàng và tâm cụm. |
| [chon_k.png](figures/chon_k.png) | Inertia và silhouette theo K. |
| [bay_chuan_hoa_khoi_tao.png](figures/bay_chuan_hoa_khoi_tao.png) | Ảnh hưởng của thang đo và khởi tạo. |
| [bay_hai_vang_trang.png](figures/bay_hai_vang_trang.png) | K-Means và nhãn thật của hai vành trăng. |
| [nen_mau_so_sanh.png](figures/nen_mau_so_sanh.png) | Ảnh mẫu gốc và các bản 4/16/64 màu. |
| [silhouette_nho_nhat.png](figures/silhouette_nho_nhat.png) | Vị trí khách thứ 114 có silhouette nhỏ nhất. |
| [chon_k_them_tuoi.png](figures/chon_k_them_tuoi.png) | Chọn K với ba biến. |
| [so_sanh_khoi_tao.png](figures/so_sanh_khoi_tao.png) | 50 seed: random và k-means++. |
| [anh_goc.png](figures/anh_goc.png) | Ảnh mẫu lưu bằng PNG. |
| [anh_16_mau.png](figures/anh_16_mau.png) | Ảnh mẫu sau nén 16 màu. |
| [anh_ca_nhan_goc.png](figures/anh_ca_nhan_goc.png) | Ảnh cá nhân lưu bằng PNG để so cùng định dạng. |
| [anh_ca_nhan_16_mau.png](figures/anh_ca_nhan_16_mau.png) | Ảnh cá nhân sau nén 16 màu. |
| [so_sanh_anh_ca_nhan.png](figures/so_sanh_anh_ca_nhan.png) | Ảnh cá nhân trước và sau nén. |
| [dbscan_hai_vang_trang.png](figures/dbscan_hai_vang_trang.png) | K-Means và DBSCAN với ba eps. |
| [tam_cum_chu_so.png](figures/tam_cum_chu_so.png) | Mười tâm cụm chữ số dưới dạng ảnh 8 × 8. |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Các số liệu sau lấy từ lần chạy đã lưu trong notebook và TXT. Phần thực hành khớp các mốc của tài liệu.

| Nội dung | Kết quả |
| --- | --- |
| Tự viết K-Means | Dừng sau 3 vòng; inertia 8.5250, bằng scikit-learn. |
| Khách hàng, hai biến | K = 5, inertia 23.0167; silhouette 0.7227055108. Hai khách mới vào cụm 4 và 0. |
| Silhouette nhỏ nhất | Khách thứ 114 (index 113), tuổi 38, thu nhập 25.4 triệu, điểm chi tiêu 41; s = 0.028571. |
| Thêm tuổi | K tốt nhất vẫn là 5, silhouette 0.4808; ARI so với phân cụm hai biến = 0.9357. |
| Khởi tạo 50 lần | `random`: 30/50; `k-means++`: 50/50 đạt inertia làm tròn một chữ số bằng 23.0. |
| Ảnh mẫu 16 màu | Sai lệch trung bình 7.97 mức sáng; PNG 550154 → 134431 byte, nhỏ hơn 4.09 lần. |
| Ảnh cá nhân 16 màu | Sai lệch 3.37 mức sáng; PNG 545830 → 87072 byte, nhỏ hơn 6.27 lần. |
| DBSCAN eps 0.2/0.3/0.4 | Đều cho 1 cụm; lần lượt 40/10/3 điểm nhiễu. Không tách hai lớp tốt hơn K-Means trong ba cấu hình này. |
| Phân cụm chữ số | Số 0 gom gọn nhất (98.88% trong một cụm); số 6 và 7 cũng trên 97%. Số 1/8 thường chung cụm; số 9/8/5 có nét gần nhau. |

**Silhouette:** tính khoảng cách trên dữ liệu đã chuẩn hóa; `a` loại chính điểm đang xét, `b` là trung bình tới cụm gần nhất khác. Cụm một điểm được quy ước s = 0. Khách thứ 114 nằm ở rìa phải của nhóm thu nhập vừa, gần nhóm thu nhập cao chi ít; a = 0.917758 gần b = 0.944750 nên s nhỏ. Hàm NumPy đã đối chiếu với thư viện.

**Thêm tuổi:** bốn khách của nhóm giữa chuyển sang nhóm thu nhập thấp chi nhiều, một khách của nhóm thu nhập cao chi nhiều chuyển vào nhóm giữa. Tâm nhóm giữa đổi từ (17.39, 49.30) thành (17.58, 49.18) theo thu nhập/chi tiêu. Không so nhóm chỉ bằng số hiệu vì số cụm là tùy ý.

**Khởi tạo:** inertia tốt thực tế là 23.0167, đề hiển thị 23.0 sau làm tròn. K-Means++ đáng tin hơn trong 50 seed đã thử, nhưng không bảo đảm nghiệm tối ưu cho mọi dữ liệu. Tăng `n_init` giúp thử nhiều điểm bắt đầu.

**Nén ảnh:** 6 lần trong đề là tỷ lệ lý thuyết 24/4 bit cho chỉ số màu, chưa tính bảng màu. PNG do `plt.imsave` tạo vẫn dùng RGB/RGBA và nén lossless, nên kích thước thực không bắt buộc giảm 6 lần. Hai ảnh gốc/nén được lưu cùng định dạng để so sánh công bằng; ảnh cá nhân được đọc bằng `plt.imread`, mã có xử lý bỏ alpha.

**DBSCAN:** dữ liệu được cung cấp có nhiều điểm nối giữa hai vành trăng. ARI của K-Means = 0.2475; DBSCAN lần lượt -0.0014/0.0012/-0.0001. Giảm eps quá mức làm xuất hiện nhiều nhiễu; tăng eps nối các vùng thành một cụm. Không sửa dataset hay thay eps để ép kết quả đẹp hơn. Nhãn thật chỉ dùng để đánh giá sau khi phân cụm.

Các CSV và ảnh đầu vào được giữ nguyên. Kết quả có thể có sai khác nhỏ theo phiên bản thư viện; số hiệu cụm có thể hoán đổi mà cách phân nhóm vẫn giống nhau.
