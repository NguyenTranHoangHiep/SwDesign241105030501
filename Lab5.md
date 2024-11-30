# I. Các hệ thống con chính:
## 1.Security Manager Subsystem: 
### - Cung cấp việc triển khai cho các dịch vụ bảo mật 
## 2.BankSystem Subsystem: 
### - Đóng gói giao tiếp với tất cả các hệ thống ngân hàng bên ngoài.
## 3.PrintService Subsystem:
### - Cung cấp các tiện ích dể tạo bảng in
## 4.Employee Management Subsystem
### - Quản lý thông tin nhân viên: thêm, sửa, xóa thông tin.
### - Theo dõi các loại hợp đồng (hourly, salaried, commissioned).
## 5.Timekeeping Subsystem
### - Lưu trữ và xử lý dữ liệu thời gian làm việc.
### - Cung cấp chức năng quản lý "Timecard".
## 6.Payroll Calculation Subsystem
### - Tính toán lương dựa trên thời gian làm việc, lương cơ bản và hoa hồng.
### - Hỗ trợ tính lương theo giờ, tháng, và doanh thu (commission).
### - Tính giờ làm thêm với mức 1.5x cho nhân viên tính lương theo giờ.
## 7.Payment Distribution Subsystem
### - Xử lý và phân phối lương theo các phương thức thanh toán (thư, ngân hàng, nhận tại văn phòng).
### - Kiểm tra và quản lý lỗi trong thanh toán.
## 8.Report Generation Subsystem
### -Tạo báo cáo cho giao dịch lương, số giờ làm việc, và thông tin nhân viên.
### -Hỗ trợ báo cáo định kỳ và tùy chỉnh theo yêu cầu.
## 9.Integration Subsystem
### - Tích hợp với cơ sở dữ liệu Project Management Database (DB2 trên IBM mainframe).
### - Truy cập thông tin về số dự án và charge numbers nhưng không sửa đổi dữ liệu gốc.
## 10.System Administration Subsystem
### - Quản lý tài khoản hệ thống và cấu hình.
### - Cài đặt lịch trình tự động hóa cho hệ thống trả lương.


