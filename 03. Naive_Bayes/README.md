![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 03 — Naive Bayes

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

## Tổng quan

Tìm hiểu định lý Bayes, mô hình túi từ, bộ lọc thư rác và GaussianNB cho dữ liệu liên tục. Bài gồm hai notebook: thực hành có 5 cell code, bài tập mục 7 có 6 cell code; mỗi mục có tiêu đề riêng. Mã thực hành giữ công thức, ví dụ và tham số của giảng viên; bổ sung đường dẫn và hình minh họa trong từng cell.

| Phần | Notebook | Nội dung |
| --- | --- | --- |
| Thực hành | [Lab3_NguyenDinhHuy.ipynb](code/Lab3_NguyenDinhHuy.ipynb) | 5 mục thực hành, mỗi mục một cell code. |
| Bài tập | [BaiTap3.ipynb](code/BaiTap3.ipynb) | 6 bài tập mục 7, mỗi bài một cell code. |

## Dữ liệu

| Tệp | Quy mô | Các cột |
| --- | --- | --- |
| [tin_nhan.csv](data/tin_nhan.csv) | 300 tin nhắn, 2 cột | `noi_dung`, `la_rac` |
| [sinh_vien.csv](data/sinh_vien.csv) | 120 sinh viên, 3 cột | `gio_on`, `diem_giua_ky`, `qua_mon` |

Tin nhắn là dữ liệu mô phỏng phục vụ giảng dạy: 180 tin thường (`la_rac=0`) và 120 tin rác (`la_rac=1`). Dữ liệu sinh viên dùng lại từ Lab 2; `qua_mon=1` là qua môn, `qua_mon=0` là rớt môn.

## Phần thực hành

Mở [Lab3_NguyenDinhHuy.ipynb](code/Lab3_NguyenDinhHuy.ipynb) và chạy các cell từ trên xuống.

| Mục | Nội dung |
| --- | --- |
| Cell 1 — Mục 2.4 | Tính Bayes bằng tay: xét nghiệm, thay đổi tiên nghiệm và hai dây chuyền sản xuất. |
| Cell 2 — Mục 3.3 | Đọc tin nhắn, CountVectorizer và đếm từ theo lớp. |
| Cell 3 — Mục 4.2 | MultinomialNB, confusion matrix, accuracy/precision/recall và ba tin mới. |
| Cell 4 — Mục 5.3 | Tự tính xác suất trên sáu tin, so sánh alpha = 0 và alpha = 1. |
| Cell 5 — Mục 6.2 | So sánh GaussianNB với Logistic Regression, đọc tham số và dự đoán sinh viên mới. |

## Phần bài tập

Mở [BaiTap3.ipynb](code/BaiTap3.ipynb). Đây là toàn bộ 6 bài tập ở mục 7 của tài liệu. Mỗi bài có một cell code và tiêu đề riêng.

| Bài | Nội dung |
| --- | --- |
| Bài 1 | Tính hậu nghiệm ba nhóm sinh viên và kiểm tra tổng bằng 1. |
| Bài 2 | Tìm 5 từ nghiêng mạnh nhất về mỗi lớp bằng hiệu `feature_log_prob_`. |
| Bài 3 | Thử alpha = 0.001, 0.1, 1, 10, 100 và nhận xét các số đo. |
| Bài 4 | Tự đếm từ, làm trơn, tính tổng log và so với MultinomialNB. |
| Bài 5 | Thử MultinomialNB trên số liệu liên tục, so với GaussianNB và giải thích. |
| Bài 6 | Giữ 180 tin thường và 20 tin rác đầu tiên; phân tích accuracy, recall và tiên nghiệm. |

## Cấu trúc thư mục

```text
03. Naive_Bayes/
├── code/
│   ├── Lab3_NguyenDinhHuy.ipynb
│   └── BaiTap3.ipynb
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

Mở terminal tại thư mục `03. Naive_Bayes`, chạy:

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

Chọn kernel đã cài thư viện, mở notebook trong `code/` và chọn **Run All**. Mã tìm dữ liệu từ thư mục bài hoặc `code/` mà không phụ thuộc tên thư mục gốc; bản trên máy có thể dùng tên `03. Navie Bayes`.

**Trên Colab:** Tải `tin_nhan.csv` và `sinh_vien.csv` trực tiếp vào Files hoặc thư mục `data/`. Các hình được lưu trong `figures/`.

Để xuất nhật ký `.txt` trên Colab, tải đủ thư mục bài và chuyển tới thư mục chứa `requirements.txt`, rồi chạy:

```python
%pip install -r requirements.txt
!python scripts/run_all.py
```

Chỉ bấm **Run All** trong notebook sẽ hiển thị kết quả trong notebook; `run_all.py` mới xuất nhật ký vào `outputs/`. Sau khi chỉnh sửa trên Colab, tải tệp `.ipynb` về đúng vị trí trong `code/` trước khi chạy script trên máy. Script không tự đồng bộ với Colab.

## Kết quả và hình ảnh

| Tệp | Nội dung |
| --- | --- |
| [Lab3_NguyenDinhHuy.txt](outputs/Lab3_NguyenDinhHuy.txt) | Kết quả phần thực hành. |
| [BaiTap3.txt](outputs/BaiTap3.txt) | Kết quả phần bài tập. |
| [d3_ma_tran_nham_lan.png](figures/d3_ma_tran_nham_lan.png) | Ma trận nhầm lẫn bộ lọc thư rác. |
| [d4_lam_tron_laplace.png](figures/d4_lam_tron_laplace.png) | Ảnh hưởng của làm trơn Laplace. |
| [d5_duong_chuong.png](figures/d5_duong_chuong.png) | Hai phân phối Gaussian của giờ ôn theo lớp. |
| [d5_bien_quyet_dinh.png](figures/d5_bien_quyet_dinh.png) | Biên quyết định GaussianNB và Logistic Regression. |
| [bai2_tu_to_cao.png](figures/bai2_tu_to_cao.png) | Các từ phân biệt hai lớp mạnh nhất. |

Kết quả chạy và biểu đồ cũng được lưu trong notebook. Mã xuất hình gọi `savefig` trước `show` để lưu đúng hình đang vẽ.

## Đối chiếu kết quả

Các bài có chia dữ liệu dùng `test_size=0.25`, `random_state=17`, `stratify=y`; bộ lọc chuẩn dùng `alpha=1.0`. Các cell thực hành và bài 3/6 giữ thứ tự vector hóa toàn bộ rồi chia như mã mẫu. Với một dự án thực tế, nên chia văn bản trước và chỉ học từ điển trên tập học; bài tập 4 thực hiện cách này cho cả bộ lọc tự viết lẫn mô hình đối chiếu.

Kết quả cần đối chiếu: Bayes ví dụ xét nghiệm **0.5000**, dây chuyền B **0.5556**, từ điển **40 từ**; bộ lọc chuẩn có **TN=45, FP=0, FN=4, TP=26**, accuracy **0.9467**, precision **1.0000**, recall **0.8667**. GaussianNB và Logistic Regression trên dữ liệu sinh viên đều có accuracy **0.9000**.

Bài tập 6 ghép nhóm tin thường trước rồi nhóm 20 tin rác đầu tiên, đặt lại chỉ mục trước khi chia. Thứ tự này được ghi rõ trong notebook để tái lập kết quả.
