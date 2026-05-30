1. Tiền xử lý dữ liệu
1.1 Weather Dataset (weather_data.csv)
Bộ dữ liệu chứa các quan sát thời tiết hằng ngày tại nhiều thành phố ở New Zealand trong giai đoạn 2016–2017.
Các bước tiền xử lý:
- Nhóm dữ liệu theo city và month.
- Tính nhiệt độ trung bình (avg_temp) cho từng thành phố theo từng tháng.
- Chuyển đổi dữ liệu sang dạng ma trận (pivot table) để phục vụ việc vẽ heatmap.
- Chuẩn hóa cột lượng mưa (precip):
	- Chuyển các giá trị sang kiểu số.
	- Thay thế giá trị thiếu bằng 0.0.
	- Chuyển ký hiệu lượng mưa rất nhỏ (T) thành giá trị số tương ứng.
- Tạo bảng màu riêng cho từng thành phố để hỗ trợ trực quan hóa.

1.2 Global Temperature Dataset (global_temp.csv)
Bộ dữ liệu nhiệt độ bất thường toàn cầu (Global Temperature Anomalies) của NASA từ năm 1880 đến 2025.
Các bước tiền xử lý:
- Loại bỏ hoặc chuyển đổi các giá trị không hợp lệ (***) thành giá trị thiếu (NaN).
- Chuyển các cột nhiệt độ sang kiểu số.
- Chuyển đổi dữ liệu từ dạng rộng (wide format) sang dạng dài (long format) bằng pandas.melt().
- Ánh xạ các tháng từ dạng chữ (Jan, Feb, ...) sang số (1–12) để đảm bảo sắp xếp đúng thứ tự thời gian.
- Chuyển dữ liệu trở lại dạng ma trận để vẽ heatmap.

1.3 Minnesota Weather Dataset (minnesota_weather.csv)
Bộ dữ liệu tổng hợp thời tiết hàng tháng tại sáu địa điểm nông nghiệp ở Minnesota giai đoạn 1927–1936.
- Các bước tiền xử lý:
- Chuyển các cột year, mo, precip sang kiểu số
- Loại bỏ các dòng chứa dữ liệu thiếu.
- Kết hợp year và mo để tạo cột thời gian (date) dưới định dạng datetime.
- Sắp xếp dữ liệu theo thời gian trước khi trực quan hóa.

2. Kết quả trực quan hóa
2.1 Average Monthly Temperature by City (Hình: weather_heatmap.png)
Mô tả

Biểu đồ heatmap thể hiện nhiệt độ trung bình theo tháng của từng thành phố.
- Trục ngang: Tháng trong năm.
- Trục dọc: Thành phố.
- Màu sắc:
- Đỏ: nhiệt độ cao.
- Xanh: nhiệt độ thấp.

Kết luận
- Nhiệt độ thay đổi rõ rệt theo mùa.
- Các thành phố có xu hướng ấm hơn vào mùa hè và lạnh hơn vào mùa đông.
- Sự khác biệt nhiệt độ giữa các thành phố có thể quan sát trực tiếp thông qua độ đậm nhạt của màu sắc.
- Heatmap giúp phát hiện nhanh các tháng có nhiệt độ cực đại hoặc cực tiểu mà không cần đọc từng giá trị riêng lẻ.


2.2 Daily Weather: Temperature vs Humidity with Precipitation (Hình: weather_scatter.png)

Mô tả

Biểu đồ scatter plot biểu diễn mối quan hệ giữa:

- Độ ẩm trung bình (avg_humidity)
- Nhiệt độ trung bình (avg_temp)
- Lượng mưa (precip)
- Thành phố (city)

Trong đó:
- Màu sắc biểu diễn thành phố.
- Kích thước điểm biểu diễn lượng mưa.
Kết luận
- Các điểm dữ liệu phân bố thành nhiều cụm tương ứng với từng thành phố.
- Những ngày có lượng mưa lớn thường xuất hiện ở vùng độ ẩm cao.
- Mối quan hệ giữa nhiệt độ và độ ẩm không hoàn toàn tuyến tính.
- Việc sử dụng đồng thời màu sắc và kích thước điểm cho phép biểu diễn nhiều chiều dữ liệu trên cùng một đồ thị. 

2.3 Global Land–Ocean Temperature Anomalies (1880–2025) (Hình: global_temp_heatmap.png)

Mô tả

Heatmap biểu diễn độ lệch nhiệt độ toàn cầu theo từng tháng từ năm 1880 đến năm 2025.

- Trục ngang: Tháng.
- Trục dọc: Năm.
- Màu đỏ: Nhiệt độ cao hơn mức trung bình giai đoạn 1951–1980.
- Màu xanh: Nhiệt độ thấp hơn mức trung bình giai đoạn 1951–1980.
Kết luận
- Các năm đầu thế kỷ XX chủ yếu mang màu xanh hoặc trung tính.
- Từ khoảng cuối thế kỷ XX trở đi, màu đỏ xuất hiện ngày càng nhiều.
- Giai đoạn gần đây (2000–2025) cho thấy mức độ nóng lên rõ rệt trên hầu hết các tháng.
- Kết quả phản ánh xu hướng biến đổi khí hậu toàn cầu và hiện tượng nóng lên toàn cầu (global warming).


2.4 Monthly Precipitation by Minnesota Site (1927–1936)

Hình: minnesota_precip_line.png

Mô tả
Biểu đồ đường thể hiện lượng mưa hàng tháng tại sáu địa điểm ở Minnesota.
- Trục ngang: Thời gian.
- Trục dọc: Lượng mưa (inch).
- Mỗi đường tương ứng với một địa điểm khảo sát.
Kết luận
- Lượng mưa biến động đáng kể theo mùa và theo từng năm.
- Một số địa điểm có xu hướng nhận lượng mưa cao hơn các địa điểm khác.
- Các đỉnh lượng mưa thường xuất hiện trong các giai đoạn nhất định trong năm, cho thấy ảnh hưởng của chu kỳ thời tiết theo mùa.
- Biểu đồ đường giúp quan sát xu hướng dài hạn và so sánh trực tiếp giữa các địa điểm.