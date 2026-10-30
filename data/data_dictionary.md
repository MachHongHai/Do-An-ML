# Từ điển dữ liệu

Dữ liệu khách hàng của một cửa hàng bán lẻ trực tuyến giả định, được chuẩn bị
bằng mô phỏng để minh họa thuật toán. Không sử dụng dữ liệu khách hàng thật.
Các CSV có sẵn và không được sinh lại khi chạy notebook.

| Cột | Ý nghĩa | Đơn vị và kiểu dữ liệu | Phạm vi |
|---|---|---|---|
| ma_khach_hang | Mã nhận diện, không đưa vào phân cụm | Chuỗi | A000001… hoặc MH01… |
| so_don_hang_thang | Số đơn đã thanh toán trong 30 ngày | Đơn, số nguyên | 0–50 trong tập lớn; 1–18 trong ví dụ |
| tong_chi_tieu_thang_nghin_vnd | Tổng giá trị đơn tháng, trước hoàn trả | Nghìn VND, số thực | Không âm; bằng 0 khi không có đơn |
| so_ngay_tu_lan_mua_cuoi | Số ngày từ lần mua gần nhất trong ví dụ | Ngày, số nguyên | 2–12 |

`khach_hang_2d.csv` có 30.000 dòng, gồm mã khách, số đơn và tổng chi tiêu.
Hai đặc trưng được chuẩn hóa trước khi phân cụm. Chúng chỉ mô tả tần suất mua
và chi tiêu, chưa phản ánh toàn bộ hành vi khách hàng. Các giá trị phân tán lớn
được giữ nguyên trong thực nghiệm.

`minh_hoa_birch.csv` có 20 dòng, gồm mã khách, số đơn và số ngày từ lần mua cuối.
Các giá trị nhỏ được chọn để tính CF bằng tay và tạo tình huống tách cây với
threshold=1, branching_factor=2. Ví dụ dùng giá trị thô với đơn vị khác nhau
để minh họa phép tính; không dùng thiết lập này cho thực nghiệm khách hàng lớn.

Hai CSV không có nhãn phân nhóm đầu vào. Các nhãn cụm trong kết quả do thuật toán
gán. K=5 ở tập lớn là tham số đặt trước cho thí nghiệm, chưa phải số cụm tối ưu.
