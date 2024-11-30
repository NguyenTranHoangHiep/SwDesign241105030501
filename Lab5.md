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
# II.Payroll System Subsystem Element
## ![Diagram](https://www.planttext.com/api/plantuml/png/Z9RFRjmW4CRlVWgKKtl82woYLPAc_mwLLdLkKGuidcpesc01ZhIg-cGzz97w2i5Wxmus1dEmjER7y37pCTx_V__TQaELwPgwQ2axqWEGgnqzALdNf3nf0yqL-LqGEzpZp9J0EiNDYVoWmhvGfEpsEk3xmMggDHdP4RsvqIEytLxWVene2UgDCz0VFfwd_nJ-6Uguf-BeTLuKRCXS0-8Is-zysEokEyM56JIcJXvmY_lkb7pZ5JWuk_Ndfgtb2M18V0F2f1ICEA8Jv_SKqj2FHsNtpkfwv0qS0Lek3Yaz64lvm4WrrJ4Jjr2RmRsVQCswcXekHR947iTqGjU8JRMLNTjAPIPlO_IYQ5UR1wwDuljkXUgU3_2KhvMqbqbFv7sZeghpsdv2VpJo5GIeR3ezZDY4ge7AvpAkwximSCWhmbX2p0CrT4_rLCmTMzE5XivoLpLSz2N9Yl8B9doWZgoucIKiPgdmys7ZlNvwvLK5ulbw6saCsIKnqMuHQgwOZvZKuK5Nn0kcvd5qf8FXDQYXhC7drzrBcdU1DIUPkHqlGiPpC3RYghGM95gHQF78Ph289fss5Erzg-CbNTWJXV0c94oA5txe_BIUbJgU61jcQ3SsK3lqDRk5q9HTueGUYDJUXXdxWmtJqtHV0r4Equkb3XrXWxYlboOmVZQDdIMLlUof414xR2xTt1tBVMDUf3f7rej6MipJ-ISAQUGaujnZeRTid2zWsAjBa_m5pBZZEMquMu7zyXQeXdv8EBAnRIwt8Ah-t-8x0000__y30000)

