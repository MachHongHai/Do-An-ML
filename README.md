# Thuật toán phân cụm BIRCH

Notebook **Do-An-Birch.ipynb** trình bày lý thuyết CF, CF Tree, cài đặt BIRCH bằng
Python theo hướng đối tượng và minh họa từng bước. BIRCH cùng weighted K-Means
được tự cài đặt bằng NumPy. StandardScaler và Silhouette dùng scikit-learn;
các mô hình thư viện được gọi riêng trong phần so sánh.

## Chạy notebook

Dùng Python 3.10 trở lên. Tại thư mục gốc repository:

```powershell
python -m pip install -r requirements.txt
python -m jupyterlab
```

Mở `Do-An-Birch.ipynb` bằng JupyterLab hoặc VS Code, chọn đúng kernel và chạy
**Restart Kernel and Run All**. Chương trình chạy trên CPU.

## Nội dung

- Tập 20 điểm: tính CF bằng tay, theo dõi hấp thụ và tách lá, nút trong, gốc.
- Tập 30.000 khách mô phỏng: phân cụm bằng số đơn và tổng chi tiêu tháng.
- So sánh BIRCH tự viết, BIRCH thư viện và K-Means trên cùng 3.000 điểm cố định.
- Thời gian gồm fit và lấy nhãn, đo một lần với một thread; Silhouette dùng
  chung mẫu cố định 1.200 điểm, tính ngoài phép đo thời gian.

## Các file

```text
Do-An-Birch.ipynb
data/
  khach_hang_2d.csv
  minh_hoa_birch.csv
  data_dictionary.md
outputs/
  benchmark_2d.csv
  thong_ke_cum_2d.csv
  (các hình từ lần chạy notebook)
README.md
requirements.txt
```

Notebook đọc CSV có sẵn, không sinh dữ liệu khi Run All. Mã khách không đưa vào
ma trận đặc trưng. Xem [từ điển dữ liệu](data/data_dictionary.md) để biết đơn vị.
Báo cáo Word được lưu riêng trong Documents; Google Docs trình bày cùng nội dung.

## Phạm vi và giới hạn

Code sử dụng vector, có thể xử lý nhiều chiều; thực nghiệm chỉ dùng 2D.
threshold là bán kính RMS tối đa sau gộp, branching_factor giới hạn số entry
mỗi nút. K=5 là số cụm đặt trước, chưa tìm K tối ưu. Hai bản BIRCH khác bước
gom cuối: weighted K-Means tự viết và Agglomerative trong bản thư viện.

Chưa cài tái xây cây theo giới hạn bộ nhớ, partial_fit và tinh chỉnh lặp của
BIRCH nguyên bản. CF Tree nhạy với thang đo, threshold và thứ tự chèn.
Dữ liệu mô phỏng chưa phản ánh đầy đủ hành vi thực tế. Thời gian đo một lần có
thể dao động; chưa đo bộ nhớ thực thi.

Kiểm tra ngày 30/10/2026: toàn bộ 14 cell code chạy từ kernel sạch, không lỗi,
trong khoảng 24 giây trên máy kiểm tra. Số liệu benchmark được tạo khi chạy.
