![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)

# Bài 03 — Naive Bayes

- **Họ và tên:** Nguyễn Đình Huy
- **MSSV:** 2474802010140
- **Môn:** Học Máy Và Ứng Dụng
- **LHP:** 261_71ITAI41203_0101
- **GVHD:** ThS. Nguyễn Thái Anh ([GitHub](https://github.com/AnhNguyenVLU))

Lab 3 gồm **5 notebook thực hành và 6 notebook bài tập mục 7**, mỗi bài một tệp chạy độc lập. Nội dung dựa trên tài liệu *Bài 3: Naive Bayes* của giảng viên. Mã thực hành giữ công thức, dữ liệu ví dụ, cách tách từ, tham số và cách chia dữ liệu trong tài liệu; phần thiết lập đường dẫn và các cell vẽ hình được bổ sung để dễ chạy và lưu kết quả.

## Dataset

| Tệp | Nội dung |
| --- | --- |
| `data/tin_nhan.csv` | 300 tin nhắn mô phỏng phục vụ giảng dạy: 180 tin thường, 120 tin rác. Cột `noi_dung` là văn bản, `la_rac` là nhãn (0: thường, 1: rác). |
| `data/sinh_vien.csv` | 120 sinh viên; các cột `gio_on`, `diem_giua_ky`, `qua_mon`. Dùng lại dữ liệu Lab 2 để so sánh GaussianNB và Logistic Regression. |

## Phần thực hành

| Notebook | Theo tài liệu | Nội dung |
| --- | --- | --- |
| [d1_bayes_tay.ipynb](code/d1_bayes_tay.ipynb) | Mục 2.4 | Tính Bayes bằng tay: ví dụ xét nghiệm, thay đổi tiên nghiệm và hai dây chuyền sản xuất. |
| [d2_tui_tu.ipynb](code/d2_tui_tu.ipynb) | Mục 3.3 | Đọc tin nhắn, CountVectorizer và thống kê số lần xuất hiện của từ theo lớp. |
| [d3_loc_thu_rac.ipynb](code/d3_loc_thu_rac.ipynb) | Mục 4.2 | MultinomialNB, ma trận nhầm lẫn, accuracy/precision/recall và thử ba tin mới. |
| [d4_lam_tron.ipynb](code/d4_lam_tron.ipynb) | Mục 5.3 | Tự tính xác suất trên kho sáu tin, so sánh alpha = 0 và alpha = 1. |
| [d5_gaussian.ipynb](code/d5_gaussian.ipynb) | Mục 6.2 | So sánh GaussianNB với Logistic Regression, đọc tham số từng lớp và dự đoán sinh viên mới. |

## Bài tập mục 7

| Notebook | Nội dung |
| --- | --- |
| [bai1_bayes_ba_nguyen_nhan.ipynb](code/bai1_bayes_ba_nguyen_nhan.ipynb) | Tính hậu nghiệm ba nhóm sinh viên và kiểm tra tổng bằng 1. |
| [bai2_tu_to_cao.ipynb](code/bai2_tu_to_cao.ipynb) | Tìm 5 từ nghiêng mạnh nhất về mỗi lớp bằng hiệu `feature_log_prob_`. |
| [bai3_doi_alpha.ipynb](code/bai3_doi_alpha.ipynb) | Thử alpha = 0.001, 0.1, 1, 10, 100 và nhận xét các số đo. |
| [bai4_tu_viet_bo_loc.ipynb](code/bai4_tu_viet_bo_loc.ipynb) | Tự đếm từ, làm trơn, tính tổng log và so với MultinomialNB trên cùng tập kiểm tra. |
| [bai5_sai_bien_the.ipynb](code/bai5_sai_bien_the.ipynb) | Thử MultinomialNB trên số liệu liên tục, so với GaussianNB và giải thích. |
| [bai6_lop_hiem.ipynb](code/bai6_lop_hiem.ipynb) | Giữ 180 tin thường và 20 tin rác đầu tiên; phân tích accuracy, recall và tiên nghiệm. |

## Cấu trúc thư mục

```text
03. Naive_Bayes/
├── code/                # 11 notebook độc lập, đã lưu kết quả chạy
├── data/                # tin_nhan.csv và sinh_vien.csv
├── figures/             # 5 hình PNG được tạo khi chạy
├── outputs/             # 11 tệp TXT, tên khớp từng notebook
├── scripts/
│   └── run_all.py
├── requirements.txt
└── README.md
```

Tên thư mục gốc có thể khác trên máy cá nhân (ví dụ `03. Navie Bayes`); mã không phụ thuộc tên này. Giữ nguyên `code/`, `data/` và `scripts/` trong cùng thư mục bài.

## Cài đặt và chạy toàn bộ

Mở terminal tại thư mục Lab 3, cài thư viện và chạy:

```sh
python -m pip install -r requirements.txt
python scripts/run_all.py
```

`run_all.py` tự tìm thư mục bài từ vị trí của script, nên cũng có thể gọi bằng đường dẫn đầy đủ từ thư mục khác. Script chạy `d1` đến `d5` rồi `bai1` đến `bai6`, mỗi notebook có kernel riêng sử dụng đúng Python đang chạy script.

Khi thành công, script cập nhật kết quả trong notebook và ghi bản chữ vào `outputs/<tên_notebook>.txt`. Hình được lưu bằng `savefig(..., dpi=150)` trước `show()`. Nếu gặp lỗi, script dừng, ghi lỗi vào nhật ký và không ghi đè notebook đang lỗi. Mỗi cell có thời gian chạy tối đa 300 giây.

## Chạy từng notebook hoặc chạy trên Colab

Mở notebook trong VS Code hoặc khởi động Jupyter từ thư mục Lab 3:

```sh
python -m notebook
```

Chọn kernel đã cài thư viện và bấm **Run All** trong notebook cần chạy. Không cần chạy notebook khác trước.

Trên Colab, tải `tin_nhan.csv` và `sinh_vien.csv` vào Files (thường là `/content`) hoặc thư mục `data/`, rồi chạy notebook. Các hình được lưu trong `figures/`. Để xuất toàn bộ nhật ký TXT trên Colab, tải đủ dự án và chạy `scripts/run_all.py` từ thư mục bài. Nếu chỉnh sửa trên Colab rồi muốn chạy trên máy, tải notebook mới về đúng `code/` trước khi chạy script; script không tự đồng bộ với Colab.

## Hình minh họa

- [Ma trận nhầm lẫn bộ lọc](figures/d3_ma_tran_nham_lan.png).
- [Làm trơn Laplace](figures/d4_lam_tron_laplace.png).
- [Hai phân phối Gaussian](figures/d5_duong_chuong.png).
- [Biên quyết định GaussianNB và Logistic Regression](figures/d5_bien_quyet_dinh.png).
- [Các từ phân biệt hai lớp mạnh nhất](figures/bai2_tu_to_cao.png).

## Đối chiếu với tài liệu

Các bài có chia dữ liệu dùng `test_size=0.25`, `random_state=17`, `stratify=y`; bộ lọc chuẩn dùng `alpha=1.0`. Các notebook thực hành và bài 3/6 giữ thứ tự vector hóa toàn bộ rồi chia như mã mẫu. Với một dự án thực tế, nên chia văn bản trước và chỉ học từ điển trên tập học; bài tập 4 thực hiện cách này cho cả bộ lọc tự viết lẫn mô hình đối chiếu.

Kết quả cần đối chiếu: Bayes ví dụ xét nghiệm **0.5000**, dây chuyền B **0.5556**, từ điển **40 từ**; bộ lọc chuẩn có **TN=45, FP=0, FN=4, TP=26**, accuracy **0.9467**, precision **1.0000**, recall **0.8667**. GaussianNB và Logistic Regression trên dữ liệu sinh viên đều có accuracy **0.9000**.

Bài tập 6 ghép nhóm tin thường trước rồi nhóm 20 tin rác đầu tiên, đặt lại chỉ mục trước khi chia. Thứ tự này được ghi rõ trong notebook để tái lập kết quả.
